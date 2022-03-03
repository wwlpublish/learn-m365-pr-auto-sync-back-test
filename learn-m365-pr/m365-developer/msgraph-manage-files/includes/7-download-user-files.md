A list of files with no way to download them is sure to disappoint users, so we need to add a download feature. You might think those files would have simple hyperlinks, but remember that Microsoft 365 is a secure environment, so the download needs to be secured. Microsoft Graph provides a short-lived download URL that has the security built right in, but it needs to be used immediately.

When you retrieve a list of files, instead of retrieving URLs that would be invalid before a user could select them, the code requests the ID of each file. The file ID is exchanged for a download URL at the instant the user selects the link. Here's that call again for your reference:

```javascript
const response = await graphClient
    .api('/me/drive/root/children')
    .select('id,name,folder,package')
    .get();
```

When a user selects a file link, an `onClick` event sends the user to the `downloadFile()` function that retrieves the short-lived URL and downloads the file immediately.

```javascript
async function downloadFile(file) {
  try {
    const response = await graphClient
        .api(`/me/drive/items/${file.id}`)
        .select('@microsoft.graph.downloadUrl')
        .get();
    const downloadUrl = response["@microsoft.graph.downloadUrl"];
    window.open(downloadUrl, "_self");
  } catch (error) {
    console.error(error);
  }
}
```

The `/me/drive/items/<file ID>` call retrieves metadata about the specified file. Notice the `select()` option that requests `@microsoft.graph.downloadUrl`. This property must be explicitly requested for the short-lived download URL because it isn't returned by default.

The `window.open()` call with a target of `_self` instructs the browser to download the file instead of navigating to it.
