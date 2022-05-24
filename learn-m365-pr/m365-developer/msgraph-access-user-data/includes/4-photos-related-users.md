> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Oycs]

In this unit, you’ll learn how to get a reference to and download a user’s profile photo and how to get the user’s manager’s profile.

## User profile photos

Profile photos can be set on user accounts, groups, and contacts in Office 365. Developers can use Microsoft Graph to view, download, and manage profile photos for these three resource types.

Profile photos are stored as binary data that developers can convert to different formats in different use cases, such as base-64 for use in a web environment.

To do user operations, you'll need one of the following permissions. The specific permission required will depend on the operation you want to do. For example, if you're creating, editing or deleting a user, one of the *write* permissions is required. Some permissions can be granted by a user while others must be granted to the app by an administrator:

- Delegated Permissions (granted by users)
  - **User** resource type
    - User.Read
    - User.ReadBasic.All
    - User.Read.All
    - User.ReadWrite
    - User.ReadWrite.All
- Application Permissions (granted by administrators)
  - **User** resource type
    - User.ReadBasic.All
    - User.ReadWrite.All

### Accessing profile photos

To get a resource's profile photo, use the `/photo/$value` endpoint on the resource. For example, the signed-in user's profile photo can be accessed using the `https://graph.microsoft.com/v1.0/me/photo/$value` endpoint.

The same operation can be done using the Microsoft Graph .NET SDK:

```csharp
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
var profilePhoto = graphClient.Me.Photo.Request().GetAsync().Result;
```

### Photo sizes

Certain photo sizes can be requested using Microsoft Graph. The supported sizes of HD photos on Office 365 are as follows: 48x48, 64x64, 96x96, 120x120, 240x240, 360x360, 432x432, 504x504, and 648x648.

You can get the metadata of the largest available photo or specify a size to get the metadata for that photo size. If the size you request isn't available, you can still get a smaller size that the user has uploaded and made available. For example, if the user uploads a photo that is 504x504 pixels, all but the 648x648 size of photo will be available for download.

To get a photo of a specific size, use the `/me/photos/48x48/$value` endpoint, where 48x48 is the wanted size of the photo.

### Working with profile photo metadata

The object returned by Microsoft Graph contains the metadata for the profile photo. The following JSON contains the standard response returned by the Microsoft Graph `/photo/$value` endpoint:

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/photo/$entity",
  "@odata.id": "https://graph.microsoft.com/v1.0/users('ID')/photo",
  "@odata.mediaContentType": "image/jpeg",
  "@odata.mediaEtag": "",
  "id": "240X240",
  "width": 240,
  "height": 240
}
```

### Working with binary data of a photo

When you use the `/photo/$value` endpoint to get the binary data for a profile photo, you'll need to convert the data into a base-64 string to add it as an email attachment. You can also save the binary stream to the local disk to save it as an image file.

The following code uses the Microsoft Graph .NET SDK to request the profile photo of the current signed-in user and save it to disk as a JPEG:

```csharp
// get photo
GraphServiceClient graphClient = GetAuthenticatedGraphClient(...);
var requestUserPhotoFile = graphClient.Me.Photo.Content.Request();
var resultUserPhotoFile = requestUserPhotoFile.GetAsync().Result;

// create the file
var profilePhotoPath = System.IO.Path.Combine(System.IO.Directory.GetCurrentDirectory(), "profilePhoto_" + resultsUserPhoto.Id + ".jpg");
var profilePhotoFile = System.IO.File.Create(profilePhotoPath);
resultUserPhotoFile.Seek(0, System.IO.SeekOrigin.Begin);
resultUserPhotoFile.CopyTo(profilePhotoFile);
```

## Working with user's related resources: the user's manager

Each user resource has more referenced resources such as their email messages (`/messages`), calendar items (`/events`), and files in OneDrive Consumer or OneDrive for Business (`/drive`).

One of the resources linked off the user resource is the user's manager. The `/manager` property on a user resource is returned as a `DirectoryObject` type. If you're using one of the native Microsoft Graph SDKs, it should automatically convert the type to a `User` object, but if not, you can always cast it as a user:

```csharp
var userId = "{ID}";
var requestUserManager = graphClient.Users[userId]
                               .Manager
                               .Request();
var resultsUserManager = requestUserManager.GetAsync().Result;
var castedUserManager = (resultsUserManager as Microsoft.Graph.User);
Console.WriteLine("        User: " + userId);
Console.WriteLine("  Manager ID: " + resultsUserManager.Id);
Console.WriteLine("Manager Name: " + castedUserManager.DisplayName);
Console.WriteLine("Manager Mail: " + castedUserManager.Mail);
```
