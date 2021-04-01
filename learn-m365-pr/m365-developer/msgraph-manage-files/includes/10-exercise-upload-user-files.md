Here are the steps to add an upload feature to your app:

## Display a browser input element and event handler for the upload

1. , open the `index.html` file.

1. Extend the `content` block with the content shown below the Add for file upload comment.

```html
<div id="content" style="display: none;">
    <h4>Welcome <span id="userName"></span></h4>
    <!-- Add for file download -->
    <hr />
    <label>Files in your OneDrive root folder:</label>
    <ul id="downloadLinks"></ul>
    <!-- Add for file upload -->
    <hr />
    <input type="file" onchange="fileSelected(this);" />
    <div id="uploadMessage"></div>
</div>
```

3. Now open the **ui.js** file in your code editor and add these functions at the bottom:

```javascript
function fileSelected(e) {
    displayUploadMessage(`Uploading ${e.files[0].name}...`);
    uploadFile(e.files[0])
    .then((response) => {
      displayUploadMessage(`File ${response.name} of ${response.size} bytes uploaded`);
      displayFiles();
    });
}

function displayUploadMessage(message) {
    const messageElement = document.getElementById('uploadMessage');
    messageElement.innerText = message;
}
```

## Add a function to upload the file using the Microsoft Graph SDK

1. Open the graph.js file in your code editor

1. Add this function at the bottom of the file:

```javascript
async function uploadFile(file) {
    try {
        ensureScope('files.readwrite');
        let options = {
            path: "/",
            fileName: file.name,
            rangeSize: 1024 * 1024 // must be a multiple of 320 KiB
        };
        const uploadTask = 
            await MicrosoftGraph.OneDriveLargeFileUploadTask
              .create(graphClient, file, options);
        const response = await uploadTask.upload();
        console.log(`File ${response.name} of ${response.size} bytes uploaded`);
        return response;
    } catch (error) {
        console.error(error);
    }
}
```

3. Ensure you save the graph.js file before continuing.

## Run the App

Refresh your browser; when you log in, you should see an upload button.

:::image type="content" source="../media/6-Upload1.png" alt-text="File upload button in browser":::

Click the button and choose a file from your computer. You may notice that the first time you upload you see a new consent pop-up requesting permission to write as well as read files. When the file begins uploading, a message will be displayed.

:::image type="content" source="../media/7-Upload2.png" alt-text="Choosing a file to upload":::

The first time you do this, you'll see an additional consent pop-up because now you're asking to write files.

:::image type="content" source="../media/8-Consent3.png" alt-text="Choosing a file to upload":::

When the upload is complete, the message will show the number of bytes uploaded and the file will appear in the files list.

:::image type="content" source="../media/10-Upload4.png" alt-text="File list with upload button":::

Stop your Node.js server by pressing Control + C in your terminal window.