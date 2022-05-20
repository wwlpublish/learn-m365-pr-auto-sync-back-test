> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OG2Q]

In this unit, you’ll learn how to get lists and individual files from OneDrive with Microsoft Graph. Microsoft Graph can be used to get a list of files, or download an individual file using its unique ID or with a relative path to the file in a SharePoint site.

OneDrive is the files hub in Office 365. People work with files in different contexts such as Microsoft Teams, groups, SharePoint, and more. With OneDrive, users can access these files no matter where they're stored, and  Microsoft Graph enables you to use a single API to work with them.

Files in Office 365 are stored in drives. Users can store files in a personal drive - their OneDrive - or in a shared drive powered by a SharePoint document library. OneDrive's flexibility lets users collaborate however it works best for them. Users can share links to files, copy or move files to team drives, or even attach OneDrive files to mail messages in Outlook.

## Why integrate with OneDrive file storage in the cloud?

### Tap into billions of files

OneDrive users can access their files from any device, online or offline, and share files with people inside or outside their organization. OneDrive enables real-time coauthoring in familiar apps like Word, Excel, and PowerPoint. Files light up with rich thumbnails for hundreds of formats, video streaming, analytics, and more, powered by Microsoft Graph. Data in OneDrive is protected with advanced encryption, compliance, and security features that customers trust.

### Store your app's files in a powerful cloud

When you store your files in OneDrive, your app can take advantage of the features of the Microsoft cloud and your users can access their files anywhere. Use the file picker SDK to quickly open, download, save, or share files stored in OneDrive from within your own app, using the same experience OneDrive users are familiar with. Get information about selected files directly from the picker SDK, or use Microsoft Graph APIs directly to interact more deeply with files. Use special folders to store files in well-known locations on OneDrive, like Documents and Camera Roll, or give your app its own personal folder.

### Bring your app straight to users within OneDrive

OneDrive customers can use or launch your app directly from within OneDrive to open, edit, or preview files. Use OneDrive's file handler extensions to provide icons and previews for your own custom file extensions, add your app to the New button or even add your own custom actions to the menu bar to launch your app.

### Work with content in formats your app understands

Your app can get file content in the format that is most convenient for you. Your app can display custom-sized thumbnails for hundreds of different file formats. You can download files in different formats, like PDF, DOCX and others.

### Work with file content and metadata without downloading the binary

With Microsoft Graph, you can access rich content through REST APIs without having to download the binary. Explore extracted metadata from photo, audio, and video files. Use the Excel API to work directly with the raw data stored in an Excel workbook. Use the Notes API to access the contents of OneNote notebooks.

### React to file changes

With webhooks, your app can get notified when files change so you can quickly react. Use the delta API to see what changed since the last time your app synchronized with the cloud.

## Files resource in Microsoft Graph

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OO36]

Let's explore the Microsoft Graph files-related resource endpoints.

### Microsoft Graph exposes two resource types for working with files:

- Drive: Represents a logical container of files, like a document library or a user's OneDrive.
- DriveItem: Represents an item within a drive, like a document, photo, video, or folder.

These two resources expose data in the following ways:

- *Properties*, such as `id` and `name`, expose simple values as strings, numbers, and Booleans.
- *Facets*, such as `file` and `photo`, expose complex values. The presence of facets like `file` or `folder` indicate behaviors and properties of the DriveItem.
- *References*, such as `children` and `thumbnails`, point to other resource collections.

### Accessing a user's OneDrive

Access the currently signed in user's OneDrive using the `https://graph.microsoft.com/v1.0/me/drive` endpoint. This endpoint will return details about the user's OneDrive including the date it was created, last modified, quota information and what type of OneDrive it is: OneDrive for Business (`business`) or OneDrive Consumer (`personal`).

To view the contents of the user's OneDrive, use the `https://graph.microsoft.com/v1.0/me/drive/root` endpoint. This endpoint will return the root folder of the OneDrive account and include a `folder` property that contains the number of folders and files at the root of the OneDrive account. To view the contents of the folder, use the `/children` endpoint. You can also access a specific folder.

Developers can use one of the many Microsoft Graph SDKs to access a user's OneDrive account.

For example, to get the current signed-in user's root OneDrive folder with the Microsoft Graph SDK, you would use the following code:

```csharp
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
// get user's files & folders in the root
var oneDriveRoot = client.Me.Drive.Root
                                  .Children
                                  .Request()
                                  .GetAsync()
                                  .Result;
// display the results
foreach (var driveItem in results)
{
  Console.WriteLine(driveItem.Id + ": " + driveItem.Name);
}
```

Microsoft Graph also enables the signed-in user to access another user's OneDrive, provided they have been granted access to it, using the https://graph.microsoft.com/v1.0/users/{user-id}/drive endpoint.

Microsoft Graph can also access OneDrive accounts for more than just users. For instance, you can access a group's OneDrive account using the https://graph.microsoft.com/v1.0/groups/{group-id}/drive endpoint and a SharePoint site's default document library using the https://graph.microsoft.com/v1.0/sites/{site-id}/drive endpoint.

### Accessing OneDrive files and folders

OneDrive resources are returned as either a `Drive` or `DriveItem` object. A `DriveItem` represents either a folder or a file. Images are considered special types of files and have more properties such as a `height` and `width`.

You can determine the specific resource type of a `DriveItem` by the presence of a `folder`, `file`, or `image` property on the returned `DriveItem` object.

## Microsoft Graph OneDrive permissions

To do OneDrive operations, you'll need one of the following permissions. The specific permission required will depend on the operation you want to do.

For example, if you're creating, editing or deleting Drives or DriveItems, one of the write permissions is required. Some permissions can be granted by a user while others must be granted to the app by an administrator:

- Delegated permissions (granted by users)
  - Files.Read
  - Files.Read.All
  - Files.ReadWrite
  - Files.ReadWrite.All
- Application permissions (granted by administrators)
  - Files.Read.All (for SharePoint site collections)
  - Files.ReadWrite.All (for SharePoint site collections)

## Downloading files from OneDrive

The `DriveItem` resource has a property `content` that can be used to get access to the files. Only `DriveItem`s with the `file` property can be downloaded.

The `content` property returns the primary stream of the file. For example, to download a specific file using the Microsoft Graph .NET SDK, you would use the following code:

```csharp
var fileId = "REPLACE_WITH_FILE_ID";

// get reference to stream of file in OneDrive
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
var fileStream = graphClient.Me.Drive.Items[fileId]
                                     .Content
                                     .Request()
                                     .GetAsync()
                                     .Result;

var currentFolder = System.IO.Directory.GetCurrentDirectory();
var driveItemPath = Path.Combine(currentFolder, "proposal.docx");

// save stream to the local file
var driveItemFile = System.IO.File.Create(driveItemPath);
fileStream.Seek(0, SeekOrigin.Begin);
fileStream.CopyTo(driveItemFile);
```
