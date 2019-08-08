(Introductory sentence)
 
## Configuring OneDrive and Office in Windows Virtual Desktop 
In Windows Virtual Desktop, you can leverage Office and OneDrive policy settings to direct files to Office 365 storage locations and take advantage of the 1 TB and greater storage in OneDrive, plus the collaboration capabilities this enables, like improved sharing, seamless secure access across devices, improved discovery of recently used files, and real-time coauthoring with coworkers and partners.  

Active Directory Group Policy can be used with Office 365 ProPlus and Office 2019 Volume Licensing editions. Administrative template files can be downloaded from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49030).  

Once you have accounts provisioned for OneDrive, you can get the most of those services by configuring Office default save locations and implementing OneDrive Known Folder Move using policy. 

## Office Group Policy settings 
Office default file locations are configured in Group Policy Editor (gpedit.msc) typically in “User Configuration\Administrative Templates\(Your Office App)\App Options\File Locations”, but the location for this setting can vary slightly per app. These settings are frequently used for Excel, Word, and PowerPoint in Remote Desktop Services environments.  

## OneDrive Group Policy settings 
Moving on to OneDrive policy settings, you’ll first want to import administrative templates for OneDrive from "%localappdata%\Microsoft\OneDrive\BuildNumber\adm" on an updated Windows 10 system. Now from Group Policy Editor, you can set the following OneDrive settings in "Computer Configuration\Administrative Templates\OneDrive":

- **Silently sign in to users to OneDrive sync with their Windows credentials** – these need to match synched accounts in Azure AD 
- **Silently move known folders to OneDrive** – this will ensure documents, pictures and desktop folders are synched to the users’ OneDrive accounts 
- **Use OneDrive Files on Demand** – enabling this setting both turns the capability on and prevents users from turning it off 
- **Set maximum size of a user’s OneDrive that can download automatically** – to prevent using too much local storage in virtual machines 

Because OneDrive services are also part of Microsoft’s cloud infrastructure, users can easily access files kept in OneDrive. The proximity and connection speeds between virtual machines in Windows Virtual Desktop and OneDrive services mean that even large files can be hydrated quickly.  