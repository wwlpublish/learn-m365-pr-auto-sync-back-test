A list of files with no way to download them is sure to disappoint users, so we need to add a download feature! You might think those files would have simple hyperlinks, but remember that Microsoft 365 is a secure environment, so the download needs to be secured. Microsoft Graph handles this by providing a short-lived download URL that has the security built right in, but that needs to be used immediately.

To handle this when retrieving the list of files, instead of retrieving URLs that would be invalid before a user could click them, the code requests the ID of each file. The file ID is exchanged for a download URL at the instant the user clicks the link. Here’s that call again for your reference:

```javascript
const response = await graphClient
    .api('/me/drive/root/children')
    .select('id,name,folder,package')
    .get();
```

When a user clicks on a file link, an `onClick` event will send the user to a function named `downloadFile()` that retrieves the short-lived URL and downloads the file immediately.

```javascript
async function downloadFile(file) {
    try {
        const response = await graphClient
            .api(`/me/drive/items/${file.id}`)
            .select('@microsoft.graph.downloadUrl')
            .get();
        const downloadUrl =
            response["@microsoft.graph.downloadUrl"];
        window.open(downloadUrl, "_self");
    } catch (error) {
        console.error(error);
     }
}
```

The `/me/drive/items/<file ID>` call retrieves metadata about the specified file; notice the `select()` option requesting `@microsoft.graph.downloadUrl`; this property needs to be explicitly requested for the short-lived download URL as it’s not returned by default.

The `window.open()` call with a target of `_self` instructs the browser to download the file rather than navigating to it.

