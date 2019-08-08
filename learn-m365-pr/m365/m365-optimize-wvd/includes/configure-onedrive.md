You can combine Windows Virtual Desktop with OneDrive in Office 365 to get access to the 1 TB of storage available in OneDrive, as well as access the collaboration capabilities included in OneDrive, like seamless secure access across devices and real-time coauthoring with coworkers and partners. You do this by using Office and OneDrive policy settings to direct files to Office 365 storage locations.

You can use Active Directory Group Policy with Office 365 ProPlus and Office 2019 Volume Licensing editions. You can download administrative template files (.ADMX) from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49030).  

Once you have accounts provisioned for OneDrive, you can use policies to configure Office default save locations and implement OneDrive Known Folder Move.

## Office Group Policy settings 
Configure Office default file locations in the Group Policy Editor (gpedit.msc), typically in “User Configuration\Administrative Templates(Your Office App)\App Options\File Locations.” (The exact location for this setting can vary slightly per app.) These settings are frequently used for Excel, Word, and PowerPoint in Remote Desktop Services environments.

## OneDrive Group Policy settings 
For the OneDrive policy settings, first import administrative templates for OneDrive from "%localappdata%\Microsoft\OneDrive\BuildNumber\adm" on an updated Windows 10 device. In the Group Policy Editor, you can set the following OneDrive settings in "Computer Configuration\Administrative Templates\OneDrive":

- **Silently sign in to users to OneDrive sync with their Windows credentials** – These need to match synched accounts in Azure AD. 
- **Silently move known folders to OneDrive** – This ensures documents, pictures, and desktop folders are synched to the users’ OneDrive accounts. 
- **Use OneDrive Files on Demand** – Enable this setting to turn the capability on and to prevent users from turning it off. 
- **Set maximum size of a user’s OneDrive that can download automatically** – Use this setting to prevent using too much local storage in virtual machines.

Because OneDrive services are part of Microsoft’s cloud infrastructure, users can easily access files stored in OneDrive. The proximity and connection speeds between virtual machines in Windows Virtual Desktop and OneDrive services mean that even large files can be hydrated quickly.