As you develop your Office Add-in and prepare to make it available to your users, you need to decide which deployment option is best. The following table lists factors you should consider.

|Consider...|Examples|
|---|---|
|Development stage|local developer testing, ready for public use|
|Add-in interaction or feature support|task pane add-in, content add-in, add-in commands|
|Target Office applications|Excel, Outlook|
|Target platforms|Windows, Mac|
|Scope of user base|your organization, general public|

## Deployment options

You have several options for deploying your add-in. The following table notes each option and when it should be used.

|Option|Description|Best when...|
|---|---|---|
|Sideload|Install your add-in locally.|Developer building and testing add-in|
|Centralized deployment|Distribute your add-in to users via the Office 365 admin center.|Add-in ready for use in your organization on Office 365 or in a hybrid environment|
|SharePoint catalog|Distribute add-in to users via SharePoint.|Task pane or content add-in ready for use in your organization that's using an on-premises environment; Excel, Word, or PowerPoint is targeted but Mac isn't a target platform|
|AppSource|Make add-in available to the public.|Add-in ready for public use|
|Exchange server|Distribute add-in to users via Exchange.|Outlook add-in ready for use in an organization whose environment doesn't use Azure Active Directory identity service|
|Network share|Make add-in available to network users via a shared folder.|Add-in development and users are on Windows|
