In the next exercise, you'll extend the app to support file uploads. There are two ways to upload a file by using Microsoft Graph. The easiest way is to use a single PUT request with a resource such as `/me/drive/root:/FolderA/FileB.txt:/content`. This method is limited to 4 MB. The more complex method involves a series of HTTP requests as an *upload session*.

The Microsoft Graph SDK makes the complex method easy. The `OneDriveLargeFileUploadTask` object handles all the details:

```javascript
const uploadTask = await MicrosoftGraph.OneDriveLargeFileUploadTask.create(
  graphClient, file, {
    path: "/",
    fileName: file.name,
    rangeSize: 1024 * 1024 // must be a multiple of 320 KiB
  }
);
const response = await uploadTask.upload();
```

The file argument is a file stream object. In the web browser, it's the one returned by the browser file input element.

```html
<input type="file" onchange="fileSelected(this);" />
```

When the user selects a file, the `onchange` event handler can access the selected file.

```javascript
function fileSelected(e) {
  // Add your code here; e.files[0] contains the file stream to upload the
  // 1st file selected by the user; e.files[1] if a 2nd file was uploaded etc.
}
```
