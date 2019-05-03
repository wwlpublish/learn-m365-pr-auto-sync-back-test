If your organization is using OneDrive or is adding OneDrive as part of a deployment, there’s a new option available for migration. Using the cloud to synchronize user files, the OneDrive Known Folder Move feature provides a level of flexibility not possible with local network-based file migration options. If enabled prior to migration, it provides secure access on new or refreshed PCs, and it eliminates the need to create temporary migration stores on your own servers. It also has the potential to be completely transparent to the user.

Within OneDrive and SharePoint, users can select the folders and locations they would like to sync from to their devices, but that puts the burden on the end user. With Known Folder Move, IT admins can target the documents, desktop, and pictures folders within a user profile and protect it all on OneDrive using Group Policy settings.
 
With Known Folder Move, users don’t change their workflow – everything looks the same before, during, and after synchronization with OneDrive is complete. Through Group Policy you can even choose whether or not to notify users that their documents, pictures, and desktop are protected in OneDrive, as the process happens in the background. As soon as a user signs in to their OneDrive account, these files are restored to their new PC. Using OneDrive also means users can access their files securely at any time from their phones and other devices.

Authentication for OneDrive is powered by Azure Active Directory, so for extra security, you can enable multi-factor authentication and set policies to control the upload and download bandwidth OneDrive uses to limit network activity. 

If you are performing a large scale migration, you don’t have to migrate every user at the same time - you may want to phase the roll-out of the Group Policy settings or limit file sync to domain-joined PCs.

