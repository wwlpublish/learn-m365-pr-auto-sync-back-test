Custom functions have several unique capabilities and restrictions because they run in a separate runtime from other add-in interactions, like task panes.

## Custom function capabilities

You can create custom JavaScript or TypeScript functions that can be accessed like built-in Excel functions such as `SUM()`. You can also create streaming custom functions which return a value based on a timer. For example, you can update the current time value in a cell every second. You can make network calls from custom functions as well.

### Custom function JavaScript example

The following code sample defines the custom function `add` that accepts two numbers then returns their sum.

```js
/**
 * Adds two numbers.
 * @customfunction
 * @param first First number.
 * @param second Second number.
 * @returns The sum of the two numbers.
 */

function add(first, second){
  return first + second;
}
```

#### JSDoc code comment descriptions

The JSDoc tags in the code comments are used to generate a JSON metadata file that describes the custom function to Excel. The JSON metadata file enables Excel to accurately present information to a user and pass expected parameters to your custom function.

- `@customfunction`: Is declared first and indicates it's a custom function. Required.
- `@param`: Describes the parameter. Include for each parameter defined by the function.
- `@returns`: Describes what the function outputs.

**Note**: The comment description "Adds two numbers." is also added to the JSON Metadata file for Excel to display when the user is viewing your custom function.

## Custom function runtime restrictions

The custom function runtime only runs JavaScript. There's no document object model (DOM) or local storage, as you would find in a browser-based JavaScript runtime environment. This means you can't load any libraries that use the DOM, such as jQuery. Also, you can't access the Office.js API to interact with the document like you can from a task pane. Instead, the custom functions runtime is optimized for tasks such as performing rapid calculations and generally doesn't need to use some of the Office.js APIs such as formatting tools in Excel.

Custom functions have a webpage that loads the custom functions runtime. Since the custom functions runtime doesn't have a UI, there's nothing for the webpage to display. You'll find the following script tag in the webpage that loads the library for the custom functions runtime.

```html
<script src="https://appsforoffice.microsoft.com/lib/1.1/hosted/custom-functions-runtime.js" type="text/javascript"></script>
```

Typically custom functions are combined with a task pane in the same add-in. If you create your add-in project using the Yeoman Generator for Office Add-ins, the project will have a webpage for the custom functions, and a web page with UI for the task pane.

## Using storage API to communicate with the task pane

Custom function code and task pane code (which uses Office.js) can't call or communicate directly with each other. But you can use a storage API that allows them to share data. A common scenario for using the storage API is when the add-in needs to share a security token for accessing a secure network resource. The user might first call a custom function that requires them to be signed in. After authentication, it receives the security token. Then it shares the security token using the storage API so that later, when the user opens the task pane, the task pane doesn't need to sign them in again.

Alternatively, the user might open the task pane first. In this case, the task pane will sign in the user and share the security token through the storage API. When a custom function is used later, the custom function can get the security token through the storage API.

### Storage API example

The following code sample shows how to store and retrieve any value created by the user.

```js
/**
 * @customfunction
 * @description Stores a value in OfficeRuntime.storage.
 * @param {any} key Key in the key-value pair you will store.
 * @param {any} value Value in the key-value pair you will store.
 */
function storeValue(key, value) {
  return OfficeRuntime.storage.setItem(key, value).then(function (result) {
      return "Success: Item with key '" + key + "' saved to storage.";
  }, function (error) {
      return "Error: Unable to save item with key '" + key + "' to storage. " + error;
  });
}

/**
 * @customfunction
 * @description Gets value from OfficeRuntime.storage.
 * @param {any} key Key of item you intend to get.
 */
function getValue(key) {
  return OfficeRuntime.storage.getItem(key);
}
```

## Dialog API

Custom functions have their own dialog API since they can't access the Office.js API. However, the functionality is similar. The most common scenario is to launch a dialog to sign in a user and receive a security token.

The following code sample shows how to display a web dialog from a custom function.

```js
OfficeRuntime.displayWebDialog('https://myDomain/myDialog.html', {height: 30, width: 20});
```

## Creating a custom functions project

You can create a custom functions project by using the Yeoman generator for Office Add-ins. Run `yo office` to start the generator, then choose the **Excel Custom Functions Add-in project** option. Once created, your project will contain a **/src/taskpane/** folder for the task pane source files, and a **/src/functions** folder for the custom function source files.

> [!NOTE]
> You can't create a custom functions project in Visual Studio.
