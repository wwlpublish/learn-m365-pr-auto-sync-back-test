Office Add-ins provide several options for how your solution can interact with an Office application. In this unit, we discuss two of those options:

- Task pane
- Content

## Task pane add-ins

Task pane add-ins allow user interaction through a panel displayed within an Office application. Through the task pane interface, you can enable the user to modify documents or emails, view data from a data source, and more. In the following image, the task pane is the panel that's displayed to the right of the document.

![Task pane add-in on the right side in the Office application window](../media/about-addins-taskpane.png)

*Task pane add-in displayed within an Office application*

In newer versions of Word, Excel, and PowerPoint, you can configure the task pane to be displayed automatically when a user opens a file. The user will need to have your add-in installed first to activate this behavior.

### Define the task pane add-in type

As described previously, an add-in's manifest file defines the settings and capabilities of the add-in.

To configure an add-in as a task pane add-in for any Office application except Outlook, set the `xsi:type` attribute to `TaskPaneApp` within the `OfficeApp` element of the manifest file, as shown in the following example.

```xml
<OfficeApp
  ...
  xsi:type="TaskPaneApp">
   ...
</OfficeApp>
```

To configure an add-in for Outlook, set the `xsi:type` attribute to `MailApp` within the `OfficeApp` element of the manifest file, as shown in the following example.

```xml
<OfficeApp
  ...
  xsi:type="MailApp">
   ...
</OfficeApp>
```

## Content add-ins

Content add-ins can be used to insert an object into an Excel spreadsheet or PowerPoint presentation. That object can be a web-based data visualization, media, or other external content. In the following image, the content add-in is displayed near the center of the document.

![Content add-in in the middle of the Office application window](../media/about-addins-contentaddin.png)

*Content add-in loaded within an Office application*

### Define the content add-in type

As described previously, an add-in's manifest file defines the settings and capabilities of the add-in. To configure an add-in as a content add-in, set the `xsi:type` attribute to `ContentApp` within the `OfficeApp` element of the manifest file, as shown in the following example.

```xml
<OfficeApp
  ...
  xsi:type="ContentApp">
   ...
</OfficeApp>
```
