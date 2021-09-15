In this unit, you'll learn how to incorporate dialogs in Excel workbooks. You'll learn how to open dialogs and how to submit and retrieve inputs and outputs for the dialog.

## Dialogs

The Dialog API is an extension of the user experience developers can customize in Office. Developers can use it to open dialogs from custom add-ins that interact with the user and the custom add-in user experience.

The primary scenario for the Dialog API is authentication with third-party providers. Most identity providers prevent their sign-in experiences from being displayed in an iframe because of click-jacking concerns. This is troublesome with an add-in as they're displayed in iframes in some of the clients such as the web versions of Office client applications.

Another challenge with authentication scenarios is predicting the domains that will need to load. In federated sign-in scenarios the potential list of domains could be endless, which again is troublesome in an add-in where all domains need to be registered in the manifest.

It's important to note that Office offers a single sign-on experience specific for Microsoft identities. If your add-in requires data about the Office user or their resources accessible through Microsoft Graph, such as Microsoft 365 or OneDrive, Microsoft recommends you use the single sign-on API whenever you can. If you use the APIs for single sign-on, then you won't need the Dialog API.

Beyond authentication, the Dialog API can provide more screen real estate for elements difficult to display in a traditional task pane of content add-in. A good example would be hosting a video that would be too small if confined to a task pane

The Dialog API can display any HTTPS web page, but it must be launched to an app domain first and then redirect.

## Open dialogs

Open a dialog using the `displayDialogAsync()` method from an Office add-in:

```javascript
Office.context.ui.displayDialogAsync("<URL />", options, optionalCallback);
```

The `displayDialogAsync()` method accepts three parameters:

- The `<URL />` is the page to be displayed in the dialog. It most initially is a page hosted from an app domain as defined in the manifest. However, the page can immediately redirect to a different page.
- The `options` parameter allows the developer to modify the size of the dialog. By default, the dialog will display as 80% of the height and width of the device screen. The values for height and width are expressed as percentage of the device screen.

    Developers can optionally set the `displayInIframe` property in the options. Setting this to `true` will cause the dialog to display as a floating Iframe rather than an independent window (in clients that support this), which makes it open faster.

- The `optionalCallback` allows the add-in's host page to respond to messages and events from the dialog.

## Dialog input and output

The primary way to pass information to a dialog is through the browser's local storage (`window.localStorage`) or through URL parameters in the dialog URL. In this sample, the host page is passing an ID of "123" to the dialog via a url parameter.

```javascript
/******* START Host page script *******/

// Open the dialog passing the parameter id=123
let dialog = null;
Office.context.ui.displayDialogAsync(
  'https://domain/popup.html?id=123',
  {
    height: 45,
    width: 55
  },
  function(result) {
    dialog = result.value;
    // Listen for messages coming from the dialog
    dialog.addEventHandler(
      Microsoft.Office.WebExtension.EventType.DialogMessageReceived,
      processMessage
    );
  }
);
function processMessage(arg) {
  // Log the message send from the dialog and close the dialog
  console.log(arg.message);
  dialog.close();
}
/******* End Host page script *******/

/******* Start Dialog page script *******/
// dialog must call Office.initialize
Office.initialize = function() {
  // send the parent/host a message
  Office.context.ui.messageParent('Hello from the dialog!!!');
}
```

A dialog can pass messages back to the host by calling `Office.context.ui.messageParent` to send either a Boolean value or a string message to the host page. At the bottom of the sample, you can see the dialog script where it's passing the message "Hello from the dialog!!!" to the parent.

The `messageParent()` method can only be called on a page with the same domain (including protocol and port) as the host page.

The host page must listen for messages by subscribing to the `DialogMessageReceived` handler. In the sample, the host page registers this handler using the `processMessage()` function, where it logs the message to the console.

## Summary

In this unit, you learned how to incorporate dialogs in Excel workbooks. You also learned how to open dialogs and how to submit and retrieve inputs and outputs for the dialog.
