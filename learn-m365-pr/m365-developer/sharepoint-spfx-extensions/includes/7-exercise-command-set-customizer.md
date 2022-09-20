In this exercise, you'll create a SharePoint Framework (SPFx) command set extension that will display custom buttons in a SharePoint list.

> [!IMPORTANT]
> The instructions below assume you're using v1.15.2 of the SharePoint Framework Yeoman generator. For more information on the use of the SharePoint Framework Yeoman generator, see [Yeoman generator for the SharePoint Framework](https://aka.ms/spfx-yeoman-info).

Open a command prompt and change to the folder where you want to create the project.

Run the SharePoint Yeoman generator by executing the following command:

```console
yo @microsoft/sharepoint
```

Use the following to complete the prompt that is displayed (*if more options are presented, accept the default answer)*:

- **What is your solution name?**: SPFxCommandSet
- **Which type of client-side component to create?**: Extension
- **What type of client-side extension to create?**: ListView Command Set
- **What is your Command Set name?**: CommandSetDemo

After provisioning the folders required for the project, the generator will install all the dependency packages by running `npm install` automatically. When npm completes downloading all dependencies, open the project folder in **Visual Studio Code**.

## Define the command set buttons

The first step to create a command set extension is to define the buttons. Buttons are defined in the component's manifest file.

Locate and open the **./src/extensions/commandSetDemo/CommandSetDemoCommandSet.manifest.json** file. Replace the existing `items` property with the following JSON:

```json
"items": {
  "ONE_ITEM_SELECTED": {
    "title": { "default": "One Item Selected" },
    "iconImageUrl": "icons/request.png",
    "type": "command"
  },
  "TWO_ITEM_SELECTED": {
    "title": { "default": "Two Items Selected" },
    "iconImageUrl": "icons/cancel.png",
    "type": "command"
  },
  "ALWAYS_ON": {
    "title": { "default": "Always On" },
    "iconImageUrl": "icons/cancel.png",
    "type": "command"
  }
}
```

## Update the command set code

After defining the buttons, the next step is to write the code that implements the extension.

Locate and open the **./src/extensions/commandSetDemo/CommandSetDemoCommandSet.ts** file. Locate the interface `ICommandSetDemoCommandSetProperties` and update its members to the following code:

```typescript
messagePrefix: string;
```

Locate the method `onInit()` in the `CommandSetDemoCommandSet` class and replace its contents with the following code. This code controls what happens when the extension is initialized.

```typescript
Log.info(LOG_SOURCE, 'Initialized CommandSetDemoCommandSet');

const one_item_selected: Command = this.tryGetCommand('ONE_ITEM_SELECTED');
one_item_selected.visible = false;

const two_item_selected: Command = this.tryGetCommand('TWO_ITEM_SELECTED');
two_item_selected.visible = false;

this.context.listView.listViewStateChangedEvent.add(this, this._onListViewStateChanged);

return Promise.resolve();
```

Locate the event handler `_onListViewStateChanged` in the `CommandSetDemoCommandSet` class and replace its contents with the following code. This code will show or hide two of the buttons depending on the number of items selected in the list.

```typescript
Log.info(LOG_SOURCE, 'List view state changed');

const one_item_selected: Command = this.tryGetCommand('ONE_ITEM_SELECTED');
if (one_item_selected) {
  one_item_selected.visible = this.context.listView.selectedRows?.length === 1;
}
const two_item_selected: Command = this.tryGetCommand('TWO_ITEM_SELECTED');
if (two_item_selected) {
  two_item_selected.visible = this.context.listView.selectedRows?.length === 2;
}

// You should call this.raiseOnChage() to update the command bar
this.raiseOnChange();
```

Locate the method `onExecute()` in the `CommandSetDemoCommandSet` class and replace its contents with the following code. This code controls what happens when custom button is selected.

```typescript
/* eslint-disable @typescript-eslint/no-floating-promises */
switch (event.itemId) {
  case 'ONE_ITEM_SELECTED':
    Dialog.alert(`${this.properties.messagePrefix} ONE_ITEM_SELECTED command checked; Title = ${event.selectedRows[0].getValueByName('Title')}`);
    break;
  case 'TWO_ITEM_SELECTED':
    Dialog.alert(`${this.properties.messagePrefix} TWO_ITEM_SELECTED command checked; Title = ${event.selectedRows[event.selectedRows.length-1].getValueByName('Title')}`);
    break;
  case 'ALWAYS_ON':
    Dialog.alert(`${this.properties.messagePrefix} ALWAYS_ON command checked. Total selected: ${event.selectedRows.length}`);
    break;
  default:
    throw new Error('Unknown command');
}
/* eslint-enable @typescript-eslint/no-floating-promises */
```

## Update the deployment configuration

Command sets, when deployed to production, are implemented by provisioning a new custom action that is associated with the custom script defined in the command set's bundle file.

Locate and open the **./sharepoint/assets/elements.xml** file. Update the `ClientSideComponentProperties` property on the `<CustomAction>` element, setting the values on the public properties on the command set:

```xml
ClientSideComponentProperties="{&quot;messagePrefix&quot;:&quot;[command_set_prefix]&quot;}"
```

## Test the command set

In a browser, navigate to a SharePoint Online site collection where you created the **Work Status** list in the previous exercise. Select the **Site contents** link in the left-hand navigation. Select the **Work Status** list:

![Screenshot of sample data in a list.](../media/05-field-customizer-setup-list-04.png)

Locate and open the **./config/serve.json** file.

Copy in the full URL (including **AllItems.aspx**) of the list `serveConfigurations.default.pageUrl` property.

Locate the `serveConfigurations.default.customActions.properties` object.

Change the value of the `properties` object to the following JSON:

```json
"properties": {
  "messagePrefix": "[command_set_prefix]"
}
```

Run the project by executing the following command:

```console
gulp serve
```

When prompted, select the **Load debug scripts** button.

Notice a new button in the toolbar after the page loads. When the **Always On** button is selected, a dialog appears that displays the message prefix defined in the public properties and the total number of items selected. If the buttons aren't added to the toolbar, switch back to the command prompt, wait for the **reload** subtask to finish executing, and then refresh.

![Screenshot of the command set Always On button.](../media/07-command-set-test-01.png)

Select one item in the list. Notice a new button appears. Select the button and notice how the dialog has changed:

![Screenshot of the command set One Item Selected button.](../media/07-command-set-test-02.png)

Select a second item in the list. Notice a new button appears. Select the button and notice how the dialog has changed:

![Screenshot of the command set Two Item Selected button.](../media/07-command-set-test-03.png)

Stop the local web server by pressing <kbd>CTRL</kbd>+<kbd>C</kbd> in the command prompt.

## Summary

In this exercise, you created a SharePoint Framework (SPFx) command set extension that displays custom buttons in a SharePoint list.
