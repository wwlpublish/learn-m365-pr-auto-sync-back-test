In this exercise, you'll extend the app to display a list of files in the user's root folder in OneDrive for Business.

## Get the list of files

Start by adding the Microsoft Graph call to the application.

1. In your code editor, open the **graph.js** file.
1. At the end of the file, add a new async function named `getFiles()` to retrieve the list of files. Use the select function to retrieve the `id`, `name`, `folder`, and `package` properties for each file.

    ```javascript
    // Get files in root of user's OneDrive
    async function getFiles() {
      ensureScope('files.read');
      try {
        const response = await graphClient
            .api('/me/drive/root/children')
            .select('id,name,folder,package')
            .get();
        return response.value;
      } catch (error) {
        console.error(error);
      }
    }
    ```

## Add an HTML placeholder to show the files

Next, add HTML that will display the list of files.

1. In your code editor, open the **index.html** file.
1. Extend the `content` block with a horizontal rule, label, and unordered list, as shown next.

    ```html
    <div id="content" style="display: none;">
      <h4>Welcome <span id="userName"></span></h4>
      <!-- Add for file download -->
      <hr />
      <label>Files in your OneDrive root folder:</label>
      <ul id="downloadLinks"></ul>
    </div>
    ```

## Display files in the app

The last step is to add a small amount of code to call the function you added earlier and display the list of files.

1. In your code editor, open the **ui.js** file.
1. At the end of the file, add the `displayFiles()` function.

    ```javascript
    async function displayFiles() {
      const files = await getFiles();
      const ul = document.getElementById('downloadLinks');
      while (ul.firstChild) {
        ul.removeChild(ul.firstChild);
      }
      for (let file of files) {
        if (!file.folder && !file.package) {
          let a = document.createElement('a');
          a.href = '#';
          a.appendChild(document.createTextNode(file.name));
          let li = document.createElement('li');
          li.appendChild(a);
          ul.appendChild(li);
        }
      }
    }
    ```

    Notice the `if` statement skips over any folders or packages to only show the files. There's no way to filter these items in the API at this time. Also note that the files are rendered as anchor tags (hyperlinks). In the next exercise, you'll add a feature to download each file when this link is selected.

1. At the end of the `displayUI()` function, right before the closing brace, add a call to `displayFiles()`.

    ```javascript
      // beginning of function omitted for brevity
      content.style = "display: block";

      displayFiles();
    }
    ```

## Run your app

You've now extended your app to show some of the user's files by using Microsoft Graph. Ensure there are some files in the root folder of the user's instance of OneDrive, and then run the app locally.

1. Preview the web app by executing the following command in the terminal:

    ```console
    npm start
    ```

1. Your browser should point to `http://localhost:8080`.
1. Select the **Sign in with Microsoft** button to sign in with your Microsoft 365 account.
1. If you're running the app for the first time, you'll be prompted to grant the app access to your files. To continue, consent to the request.

    :::image type="content" source="../media/4-consent-2.png" alt-text="Screenshot that shows the consent form to allow reading files." border="false":::

1. You should see the list of files.

    :::image type="content" source="../media/5-files.png" alt-text="Screenshot that shows the list of files." border="false":::

1. Keep your Node.js server running because you'll use it in the next part of the exercise.
