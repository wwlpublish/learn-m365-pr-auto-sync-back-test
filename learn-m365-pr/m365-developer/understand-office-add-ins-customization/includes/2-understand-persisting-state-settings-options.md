The Office Add-ins platform provides several ways for your add-in to persist state and settings. Your options depend on the Office applications you plan to support and on the type of add-in you plan to develop.

## Options to persist state and settings

The Office JavaScript API provides objects for your add-in to save state across user sessions. The following table lists the options, along with the supported add-in types and Office host applications.

|Office API object|Supported add-in types|Supported Office hosts|Storage information|
|---|---|---|---|
|CustomProperties|MailApp|Outlook|Item data is stored on the message or appointment the add-in is working on.\*|
|CustomXmlParts|TaskPaneApp|Excel (host-specific Excel JavaScript API),<br>Word (Office JavaScript Common API)|Data is stored in a custom XML part of the document or workbook.|
|RoamingSettings|MailApp|Outlook|Data is stored on the user's Exchange mailbox and associated with the specific add-in.\*|
|Settings|ContentApp, TaskPaneApp|Excel, PowerPoint, Word|Data is stored on the document, workbook, or presentation the add-in is working on.\*|

\* *Data stored in name/value pairs in a property bag*

You can also use HTML5 web storage and other techniques available through the add-in's underlying browser control.

> [!IMPORTANT]
> Don't store passwords and sensitive personally identifiable information (PII) on the user's device.
