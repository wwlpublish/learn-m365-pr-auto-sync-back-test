The Office Add-in programming model relies on two JavaScript object models:

- Host-specific JavaScript API - Host-specific APIs for Excel and Word provide strongly-typed objects that you can use to access specific elements in the host application. For example, the Excel API contains objects that represent worksheets, ranges, tables, charts, and more.
- Common API - Introduced with Office 2013, the Common API enables you to access features such as:
  - UI
  - Dialogs
  - Client settings that are common across multiple types of Office applications
  
Custom functions use a slightly different programming model and will be covered in a later unit.

## Requirement sets

You may not always have control over the version of Office your users have installed. Depending on the version of Office and platform it runs on, there are different APIs and features supported for your add-in. For example, Office 2016 supports more capabilities than Office 2013. To handle this situation, we provide requirement sets to help you determine whether an Office host supports the capabilities you need in your Office Add-in.
  
Requirement sets can be specific to Office hosts, such as an ExcelApi 1.7 set, or common to multiple hosts, such as the Dialog API. Requirement set support varies by Office host and host version.

It's possible to programmatically check if requirement sets are supported by your add-in's Office host, using `isSetSupported`. If the requirement set is supported, `isSetSupported` returns `true` and your add-in can run the additional code that uses the API members from that requirement set. If the Office host doesn't support the requirement set, `isSetSupported` returns `false` and the additional code won't run. The following code shows the syntax to use with `isSetSupported`.

```js
if (Office.context.requirements.isSetSupported(RequirementSetName, MinimumVersion))
{
   // Code that uses API members from RequirementSetName.
}
```

> [!NOTE]
> **Office Insider's Program**
>
> To get the earliest or monthly changes to any of the Office hosts, you can join the Office Insider's program. This program is for Windows PC only and requires an Office 365 subscription. From any Office application, select **File > Account > Office Insider** to quickly join the program.

## Using Office JS APIs

To use these APIs, include a CDN reference to at least one of the two JavaScript object models, typically by adding the following code to your page's `<head>` tag.

```HTML
// Reference the production CDN
<script src="https://appsforoffice.microsoft.com/lib/1/hosted/Office.js" type="text/javascript"></script>
```

```HTML
// Reference the beta/preview CDN
<script src="https://appsforoffice.microsoft.com/lib/beta/hosted/Office.js" type="text/javascript"></script>
```

Along with adding your preferred CDN link, all Office Add-ins require an `Office.onReady()` call. You put your add-in code in this method, and it gets called once the Office.js library has initialized. Inside the `onRead()` method, you can determine which host your add-in is running in by checking the `Office.HostType` enum value (for example, Excel or Word). You can check which platform your add-in is running on with an `Office.PlatformType` enum value (for example, PC, Mac, or Office on the web).
  
If you're using additional JavaScript frameworks that include their own initialization handler or tests, they should be placed within the response to `Office.onReady()`. For example, JQuery's `$(document).ready()` function would be referenced as follows.

```js
Office.onReady(function() {
     // Office is ready.
     $(document).ready(function () {
         // The document is ready.
     });
});
```

## Asynchronous model and proxy objects

When you work with a document, requested read or write actions are batched up using a proxy object. Your API calls don't actually read or update the underlying document until you call the `sync()` method.

For better security, your add-in runs in a sandboxed JavaScript environment that cannot directly access the document, or other add-ins. The Office Add-ins platform provides a `RequestContext` object that in turn provides proxy objects to represent the document (such as worksheets, ranges, and tables). The `RequestContext` is typically passed to your code as a parameter named `context`. You can use the `context` object to get any proxy objects you need to work with the document.

Before you can read the properties of a proxy object, you must load the properties to populate the proxy object with data from the Office document. You do this by calling the `load()` method on the proxy object for any properties you need. Then call the `context.sync()` method, which will load all of the requested properties. For example, if you create a proxy range object to work with a user-selected range in an Excel worksheet, and then want to read the selected range's `address` property, you need to load the `address` property before you can read it. To request properties of a proxy object to be loaded, call the `load()` method on the object and specify the properties to load.

The example below shows a batch function that defines a local proxy object (`selectedRange`), loads the properties of that object, and then uses JavaScript Promises to call `context.sync()` to synchronize the state between proxy objects and objects in the Excel file. `Excel.run` is required for this specific host, to load properties that affect platform behavior when the function runs. Not all hosts contain a run call.

```js
Excel.run(function (context) {
    var selectedRange = context.workbook.getSelectedRange();
    selectedRange.load('address');
    return context.sync()
      .then(function () {
        console.log('The selected range is: ' + selectedRange.address);
    });
}).catch(function (error) {
    console.log('error: ' + error);
    if (error instanceof OfficeExtension.Error) {
        console.log('Debug info: ' + JSON.stringify(error.debugInfo));
    }
});
```
