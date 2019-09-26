Custom functions have several unique capabilities and restrictions because they run in a separate runtime from the task pane and other types of Office Add-ins.

## Custom function runtime restrictions

The custom function runtime only runs JavaScript or TypeScript. There's no document object model (DOM) or local storage, as you would find in a browser-based JavaScript runtime environment so you can only run the function code. You can't access the Office.js API to interact with the document (like you can from a task pane). You can't load any libraries that use the DOM (such as jQuery). If you want to store data, you need to use the storage API described later.

## Use storage API to communicate with the task pane

Custom function code can't call code in the task pane, and the task pane can't call custom function code. They can share data through a storage API. A common scenario is when the add-in needs to share a security token for calling a network API. If a custom function runs first, it will need to have the user sign in. After that, it retrieves the security token and stores it using the storage API. The storage API shares data with the task pane so when the user later opens the task pane, it can use the security token and the user won't have to sign in again.

This scenario could also work in reverse. If the user opens the task pane first, the task pane can have the user sign in, and store the security token. When a custom function is used later, the custom function can get the security token through the storage API.

### Storage API example

The following code sample shows how to store and retrieve an item.

```js
function storeValue(key, value) {
  return OfficeRuntime.storage.setItem(key, value).then(function (result) {
      return "Success: Item with key '" + key + "' saved to storage.";
  }, function (error) {
      return "Error: Unable to save item with key '" + key + "' to storage. " + error;
  });
}

function getValue(key) {
  return OfficeRuntime.storage.getItem(key);
}
```

## Dialog API

Custom functions have their own dialog API since they can't access the Office.js API. The functionality is similar. The most common scenario is to launch a dialog to store an access token.

## Creating a custom functions project

You create a custom functions project by running the yo office generator. Then choose the option for a custom functions project. By default, the project will also have a task pane.

If you're using Visual Studio Code, you can debug custom functions in Excel on Windows.

> [!IMPORTANT]
> You can't create a custom function project in Visual Studio.
