In the next exercise, you'll extend the app to support file uploads. There are two ways to upload a file using Microsoft Graph. The easiest way is to use a single **PUT** request:

```csharp
var driveItem = await _graphServiceClient
    .Me.Drive.Root
    .ItemWithPath(itemPath)
    .Content
    .Request()
    .PutAsync<DriveItem>(stream);
```

However, this method is limited to 4 MB. The more complex method involves a series of HTTP requests as an “upload session”. Fortunately, the Microsoft Graph SDK makes the complex method more straightforward! The aptly named `LargeFileUploadTask` object handles all the details.

To use `LargeFileUploadTask` object, an upload session must first be created:

```csharp
var uploadSession = await _graphServiceClient.Me.Drive.Root
    .ItemWithPath(itemPath)
    .CreateUploadSession(uploadProps)
    .Request()
    .PostAsync();
```

The upload session is passed into the `LargeFileUploadTask` constructor along with the stream to upload and maximum slice size. The maximum slice size value must be a multiple of 320 KB:

```csharp
int maxSliceSize = 320 * 1024;
var fileUploadTask = new LargeFileUploadTask<DriveItem>(uploadSession, stream, maxSliceSize);
```

To track the file upload progress, a `Progress` object can be created and passed into the `LargeFileUploadTask` object's `UploadAsync` method.

```csharp
IProgress<long> progress = new Progress<long>(prog =>
{
  _logger.LogInformation($"Uploaded {prog} bytes of {stream.Length} bytes");
});

var uploadResult = await fileUploadTask.UploadAsync(progress);
```

To start the file upload, an HTML form can be added into the webpage with a file input and button:

```html
<form method="post" enctype="multipart/form-data">
  <input asp-for="UploadedFile" type="file"></input>
  <input type="submit" value="Upload File"></input>
</form>
```

When a user submits a file upload, the data is assigned to a property named `UploadedFile` in the Razor Page model named `FilesModel`. The property's name matches the `asp-for` value defined in the form's file input control.

```csharp
[BindProperty]
public IFormFile UploadedFile { get; set; }
```

Let's look at how these different parts can be put together to support file uploads.
