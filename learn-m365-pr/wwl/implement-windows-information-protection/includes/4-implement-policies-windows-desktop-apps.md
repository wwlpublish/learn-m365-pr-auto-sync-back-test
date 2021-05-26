Working with Windows 10 desktop apps, such as Microsoft Office or Notepad, is the most common way of processing Windows Information Protection (WIP) content.

### Comparing enlightened and non-enlightened apps

The term “Enlightened” describes applications with that can identify corporate and personal data, and correctly determine which to protect. The term “Non-Enlightened” (or "Unenlightened") refers to applications that can only recognize all their data as corporate work data.

#### Different app types

The basic differences between Enlightened apps and Unenlightened apps with limited functions are outlined in the following table.

:::row:::
  :::column:::
    

**App Type**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
  :::column:::
    

**Example of apps**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Enlightened apps


  :::column-end:::
  :::column:::
    

Can differentiate between corporate and personal data, correctly determining which to protect, based on your policies.


  :::column-end:::
  :::column:::
    

 -  Microsoft Edge
 -  Internet Explorer 11
 -  Mobile Office apps (Word, Excel, PowerPoint, OneNote, Outlook Mail, and Calendar)
 -  Office apps (Word, Excel, PowerPoint, OneNote, and Outlook)
 -  OneDrive app
 -  OneDrive sync client (OneDrive.exe, the next generation sync client)
 -  Notepad
 -  Groove Music
 -  Microsoft Photos
 -  Microsoft People
 -  Microsoft Paint
 -  Microsoft Movies &amp; TV
 -  Microsoft Messaging
 -  Microsoft Remote Desktop


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Unenlightened apps


  :::column-end:::
  :::column:::
    

Considers all data as corporate and encrypts everything. You can typically identify an unenlightened app because:

 -  Windows Desktop shows it as always running in enterprise mode.
 -  Windows Save As experiences only allow you to save your files as enterprise.


  :::column-end:::
  :::column:::
    

 -  Any app that isn't enlightened.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

WIP work-only apps


  :::column-end:::
  :::column:::
    

Unenlightened line-of-business apps that have been tested and considered safe for use in an enterprise with WIP and Mobile App Management (MAM) solutions.


  :::column-end:::
  :::column:::
    

 -  Skype for Business


  :::column-end:::
:::row-end:::


The list of enlightened apps is constantly growing because of ongoing development in the development community.

**Additional reading.** For more information, see the [latest list of enlightened apps](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/enlightened-microsoft-apps-and-wip?azure-portal=true).

#### Differences when saving a file

Enlightened apps can process personal and corporate data, depending on the user’s choice when saving the document. As soon as the file is marked as a work document, all protection features are applied to it, and it's displayed in the Windows Explorer with a small briefcase and an active File ownership.

:::image type="content" source="../media/save-as-window-with-work-type-199d11f8.png" alt-text="screenshot of Save As window and saving a doc as a Work type":::


Work files are protected against data leakage. For example, you can't copy any of its content into personal apps or destinations. Unenlightened apps can't differentiate between corporate and personal data. As a result, it must process all data as corporate work data.

> [!NOTE]
> Both enlightened and unenlightened apps can process company work data. They only differ in functions for usage flexibility. The opposite of protected apps is any app not defined as trusted, enlightened, unenlightened, or exempt.

### WIP file behavior

Your files and apps can be categorized as either work or personal. Where you get the file and where you save new files determines whether files are protected by WIP.

When working with existing files:

 -  If you get a file from a **corporate work** location, it will automatically be WIP-protected.
 -  If you get it from a **personal** location, it won't be WIP-protected.

When saving new files, the same applies:

 -  If you save it to a **corporate work** location, it will be WIP-protected.
 -  If you save it to a **personal** location, it won't be WIP-protected.

Enlightened apps (or apps that fully support WIP) also provide the option when saving a file to choose whether it's work-related or personal. However, if you store a work file to a personal location, WIP gives you the option of saving it as a personal file or saving it at a different location.

:::image type="content" source="../media/save-as-window-with-personal-option-91a1ab73.png" alt-text="screenshot of Save As window and saving to a personal location with menu option to choose whether it's work-related or personal":::


### Determine the Enterprise Context of an app

It's possible to check the context of an app that's running on your machine by using Windows Task Manager. However, to do so, the **Enterprise Context** column must be activated first. This column can be activated by completing the following steps:

1.  Open the **Task Manager** and, if you aren't already in the detail view, select **More details**.
2.  Select the **Details** tab for more information on the running processes.
3.  Right-click in the column heading area and then select **Select columns**.
4.  Scroll down, check the **Enterprise Context** option, and then select **OK** to close the box.
5.  The **Enterprise Context** column should now be available in Task Manager.<br><br>:::image type="content" source="../media/task-manager-enterprise-context-0453320c.png" alt-text="screenshot of Task Manager window displaying the Enterprise Context column":::
    

The Enterprise Context column displays what each app can do with your enterprise data, as outlined in the following table.

:::row:::
  :::column:::
    

**Enterprise Context**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Domain


  :::column-end:::
  :::column:::
    

If your work domain is displayed (such as, corp.contoso.com), the app is running in work-related mode and protects the content the app is currently accessing.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Personal


  :::column-end:::
  :::column:::
    

If Personal is displayed, the app is running in personal mode and can't touch any work data or resources.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Exempt


  :::column-end:::
  :::column:::
    

If Exempt is displayed, the app is running in trusted mode and WIP policies are bypassed.


  :::column-end:::
:::row-end:::


> [!NOTE]
> Enlightened apps can switch their context between Domain and Personal, depending on the content they're working with.

### Monitor WIP events

A device protected by WIP generates different events saved to the local machine’s event log about actions taken by WIP. Windows Information Protection creates audit events in the following situations:

 -  An employee changes the File ownership for a file from corporate to personal data.
 -  Data is marked as corporate data but shared to a personal app or webpage. For example, through copy and paste, drag and drop, sharing a contact, uploading to a personal webpage, or if the user grants a personal app temporary access to a protected file.
 -  An app has custom audit events.

You can use Windows Event Forwarding to collect and aggregate your WIP audit events and then view the audit events in the Event Viewer. Another solution is to use the Reporting configuration service provider (CSP) and collect events remotely.

### Changing file ownership

It's also possible to change the file ownership within Windows Explorer. Just check the File ownership and change it from Personal to Work, or the other way around. The operation will be saved in the event log.
