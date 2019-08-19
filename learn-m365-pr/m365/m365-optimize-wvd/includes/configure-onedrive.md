In Windows Virtual Desktop, you can leverage Office and OneDrive policy settings to direct files to Office 365 storage locations. This lets you take advantage of the 1 TB and greater storage available in OneDrive, plus collaboration capabilities like improved sharing, seamless secure access across devices, improved discovery of recently used files, and real-time coauthoring with coworkers and partners.

You can use Active Directory Group Policy with Office 365 ProPlus and Office 2019 Volume Licensing editions. You can download administrative template files (.ADMX) from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49030).  

After you provision accounts for OneDrive, you can use policies to configure Office default save locations and to implement OneDrive Known Folder Move.

## Office Group Policy settings 
Configure Office default file locations in the Group Policy Editor (gpedit.msc), typically in **User Configuration\Administrative Templates\(Your Office App)\App Options\File Locations**. (The exact location for this setting varies slightly per app.) These settings are frequently used for Excel, Word, and PowerPoint in Remote Desktop Services environments.

## OneDrive Group Policy settings 
For the OneDrive policy settings, first import administrative templates for OneDrive from **%localappdata%\Microsoft\OneDrive\BuildNumber\adm** on an updated Windows 10 device. In the Group Policy Editor, set the following OneDrive settings in **Computer Configuration\Administrative Templates\OneDrive**:

- **Silently sign in to users to OneDrive sync with their Windows credentials** – These need to match synched accounts in Azure AD. 
- **Silently move known folders to OneDrive** – This setting ensures documents, pictures, and desktop folders are synched to OneDrive accounts. 
- **Use OneDrive Files on Demand** – This setting turns on the capability and prevents users from turning it off. 
- **Set maximum size of a user’s OneDrive that can download automatically** – This setting prevents using too much local storage in virtual machines.

Because OneDrive services are part of Microsoft’s cloud infrastructure, users can easily access files stored in OneDrive. The proximity and connection speeds between VMs in Windows Virtual Desktop and OneDrive services mean that even large files can be hydrated quickly.