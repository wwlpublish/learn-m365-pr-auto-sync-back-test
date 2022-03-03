In this exercise, you'll complete the download capability in your app so you can select a filename to download the file.

1. Add the following function to the end of the **graph.js** file:

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

1. In **ui.js**, add this line immediately after the `a.href = assignment` statement:

    ```javascript
    a.onclick = () => { downloadFile(file); };
    ```

    The completed `displayFiles()` function should look like this:

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
          a.onclick = () => { downloadFile(file); };
          a.appendChild(document.createTextNode(file.name));
          let li = document.createElement('li');
          li.appendChild(a);
          ul.appendChild(li);
        }
      }
    }
    ```

1. Now refresh the page. You should be able to select a file to download it.
