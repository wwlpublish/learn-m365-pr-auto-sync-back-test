Office Add-ins provide several options for how your solution can interact with an Office application. In this unit, we discuss two of those options:

- Task pane
- Content

## Task pane add-ins

Task pane add-ins allow user interaction through a UI panel displayed within an Office application. Through the task pane interface, you can enable the user to modify documents or emails, or view data from a data source.

![Task pane add-in on the right side in the Office application window](../media/about-addins-taskpane.png)

*Task pane add-in*

In newer versions of Word, Excel, and PowerPoint, you can also configure the task pane to be displayed automatically when a user opens a document. The user will need to have your add-in installed first to activate this behavior.

### Key configuration

To configure an add-in as a task pane add-in, the key setting in the manifest is the following for all Office applications except Outlook.

- `OfficeApp` type is "TaskPaneApp"

For Outlook, the key setting is:

- `OfficeApp` type is "MailApp"

## Content add-ins

Content add-ins allow the user to insert or embed an object into their Excel spreadsheet or PowerPoint presentation. That object can be a web-based data visualization, media, or other external content.

![Content add-in in the middle of the Office application window](../media/about-addins-contentaddin.png)

*Content add-in*

### Key configuration

To configure an add-in as a content add-in, the key setting in the manifest is:

- `OfficeApp` type is "ContentApp"