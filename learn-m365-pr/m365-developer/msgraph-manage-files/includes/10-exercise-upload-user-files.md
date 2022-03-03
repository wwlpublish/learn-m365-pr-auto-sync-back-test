Here are the steps to add an upload feature to your app.

## Display a browser input element and event handler for the upload

1. Open the **index.html** file.
1. Locate the line `<ul id="downloadLinks"></ul>` and add the following markup immediately after it:

    ```html
    <!-- Add for file upload -->
    <hr />
    <input type="file" onchange="fileSelected(this);" />
    <div id="uploadMessage"></div>
    ```

    The resulting `<div>` content block should look like the following:

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

1. Now, open the **ui.js** file in your code editor, and add the following code to the end of the file:

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

## Add a function to upload the file by using the Microsoft Graph SDK

1. Open the **graph.js** file in your code editor.
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
        const uploadTask = await MicrosoftGraph.OneDriveLargeFileUploadTask
            .create(graphClient, file, options);
        const response = await uploadTask.upload();
        console.log(`File ${response.name} of ${response.size} bytes uploaded`);
        return response;
      } catch (error) {
        console.error(error);
      }
    }
    ```

1. Ensure you save the **graph.js** file before you continue.

## Run the app

Refresh your browser. When you sign in, you should see an upload button.

:::image type="content" source="../media/6-upload-1.png" alt-text="Screenshot that shows the File upload button in the browser." border="false":::

Select the button, and choose a file from your computer. You might notice that the first time you upload you see a new consent pop-up window requesting permission to write and read files. When the file begins uploading, a message appears.

:::image type="content" source="../media/7-upload-2.png" alt-text="Screenshot that shows choosing a file to upload." border="false":::

The first time you do this, you'll see another consent pop-up window because now you're asking to write files.

:::image type="content" source="../media/8-consent-3.png" alt-text="Screenshot that shows consenting to upload files." border="false":::

When the upload is complete, the message shows the number of bytes uploaded and the file appears in the files list.

:::image type="content" source="../media/10-upload-4.png" alt-text="Screenshot that shows a file list with an upload button." border="false" :::

Stop your Node.js server by selecting <kbd>CTRL</kbd>+<kbd>C</kbd> in your terminal window.
