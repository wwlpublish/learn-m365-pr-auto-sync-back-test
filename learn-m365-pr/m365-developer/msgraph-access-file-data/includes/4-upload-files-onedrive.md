In this unit, you’ll learn how to upload files to OneDrive using Microsoft Graph, including both small and large files.

Microsoft Graph supports through the REST API and through the multiple SDKs the ability to upload files to OneDrive. There are two approaches to uploading files:

- Simple upload: this API supports uploading files to OneDrive up to 4 MB in size.
- Large file upload: this resumable API supports uploading files larger than 4 MB in size.

## Uploading small files up to 4 MB

Microsoft Graph supports uploading files up to 4 MB in size using a simple HTTP PUT request. To upload a file, submit an HTTP PUT to the collection where the new file should be created. The end of the endpoint must include the name of the file to create and end with the `content` endpoint.

The request must include the HTTP request header `Content-Type` with a value that matches the type of file being uploaded. The contents of the file should be included in body of the request.

For example, to upload a text file to the currently signed-in user's root OneDrive account, use the following HTTP request:

```http
HTTP PUT https://graph.microsoft.com/v1.0/me/drive/root:/myNewSmallFile.txt:/content
Content-Type: text/plain

This is a new small file
```

To update or replace an existing file, submit an HTTP PUT to the location of the existing file using the file's Id in OneDrive:

```http
HTTP PUT https://graph.microsoft.com/v1.0/me/drive/items/{item-id}/content
Content-Type: text/plain

A new small file
```

You can also use the Microsoft Graph .NET SDK to perform the same action. Assuming a file named **myNewSmallFile.txt** is present in the current folder, use the following code to upload the file to the currently signed-in user's root OneDrive account:

```cs
// get reference to stream of file in OneDrive
var fileName = "myNewSmallFile.txt";
var currentFolder = System.IO.Directory.GetCurrentDirectory();
var filePath = Path.Combine(currentFolder, fileName);

// get a stream of the local file
FileStream fileStream = new FileStream(filePath, FileMode.Open);

// upload the file to OneDrive
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
var uploadedFile = graphClient.Me.Drive.Root
                              .ItemWithPath(fileName)
                              .Content
                              .Request()
                              .PutAsync<DriveItem>(fileStream)
                              .Result;
```

## Uploading large files greater than 4 MB

Microsoft Graph also supports uploading files larger than 4 MB up to the maximum file size supported by OneDrive.

The support for large files also enables developers to resume a transfer in scenarios where the upload was interrupted or paused. Uploading a large file involves creating an upload session followed by uploading bytes to the session.

As the upload session uploads the file, it reports back on the progress allowing developers to provide feedback to the user uploading the file.

To upload a large file, start by creating a new upload session:

```http
HTTP POST https://graph.microsoft.com/v1.0/me/drive/root/createUploadSession
Content-Type: application/json

{
  "item": { "name": "largefile.zip"}
}
```

This will return the upload session that contains the URL to upload the file and when the temporary upload location will expire:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "uploadUrl": "https://sn3302.up.1drv.com/up/fe6987415ace7X4e1eF866337",
  "expirationDateTime": "2019-12-29T09:21:55.523Z"
}
```

As long as the expiration date has not passed, you can resume the upload session when it's an interrupted or paused upload.

Once you've the upload session, you can then upload bytes to the temporary file in OneDrive. In this example, you're uploading the first 25 bytes for a 128-byte file

```http
HTTP PUT https://sn3302.up.1drv.com/up/fe6987415ace7X4e1eF866337
Content-Length: 26
Content-Range: bytes 0-25/128

<bytes 0-25 of the file>
```

The `Content-Range` specifies which chunk you are uploading and the total size of the file. The total size of the file should not change between upload sessions. If it does, the upload session will fail. The previous request will yield the following response that will again state the expiration time and the next expected range for the file:

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
{ "expirationDateTime": "2019-12-29T09:21:55.523Z", "nextExpectedRanges": ["26-"] }
```

When the last range of a file is received by the upload session, it will return an `HTTP 201 Created` or `HTTP 200 OK` response and include the `DriveItem` representing the completed file.

### Cancelling an upload session

To cancel an upload session, simply submit an HTTP DELETE request to the upload session endpoint as follows:

```http
HTTP DELETE https://sn3302.up.1drv.com/up/fe6987415ace7X4e1eF866337
```

### Resuming an upload session

Upload sessions can be resumed in scenarios where the session was interrupted or paused. To resume an upload session, first determine the missing range by submitting an HTTP GET to the upload session:

```http
HTTP GET https://sn3302.up.1drv.com/up/fe6987415ace7X4e1eF866337
```

This will return the same type of response returned when a range is uploaded. Use the response to determine the next part of the file to upload.

### Uploading large files with the Microsoft Graph .NET SDK

The following code uploads a large file to the currently signed-in user's OneDrive root folder using the Microsoft Graph .NET SDK:

```cs
var fileName = "largefile.zip";
var currentFolder = System.IO.Directory.GetCurrentDirectory();
var filePath = Path.Combine(currentFolder, fileName);

// load resource as a stream
using (Stream fileStream = new FileStream(filePath, FileMode.Open))
{
  GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
  var uploadSession = graphClient.Me.Drive.Root
                                 .ItemWithPath(fileName)
                                 .CreateUploadSession()
                                 .Request()
                                 .PostAsync()
                                 .Result;
  // create upload task
  var maxChunkSize = 320 * 1024;
  var largeUploadTask = new LargeFileUploadTask<DriveItem>(uploadSession, fileStream, maxChunkSize);

  // create upload progress reporter
  IProgress<long> uploadProgress = new Progress<long>(uploadBytes =>
  {
    Console.WriteLine($"Uploaded {uploadBytes} bytes of {fileStream.Length} bytes");
  });

  // upload file
  UploadResult<DriveItem> uploadResult = largeUploadTask.UploadAsync(uploadProgress).Result;
  if (uploadResult.UploadSucceeded)
  {
    Console.WriteLine("File uploaded to user's OneDrive root folder.");
  }
}
```

## Required permissions

In order to upload files to OneDrive, you'll need one of the following permissions. The specific permission required will depend on the operation you want to perform.

- Delegated permissions (granted by users)
  - Files.ReadWrite
  - Files.ReadWrite.All
  - Sites.ReadWrite.All
- Application permissions (granted by administrators)
  - Files.ReadWrite.All (for SharePoint site collections)
  - Sites.ReadWrite.All (for SharePoint site collections)

## Summary

In this unit, you learned how to upload files to OneDrive using Microsoft Graph, including both small and large files.
