> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2SpvT]

## Migrate user data manually

When it comes to deciding what to transfer and what to discard, some users may want to keep everything, and others may want to take the opportunity to clean up their drives. IT departments may choose to handle user file migration manually, such as having support teams visit users or setting up support centers for users to bring their PCs to the support team. Either way users can be involved in deciding what to transfer and what to discard.

Whether the manual approach is an option in your organization will depend on the scale of the migration. It is important to remember the natural limitations of the time and logistics involved in working directly with users, understanding their needs, and copying files across to their new or updated PCs. Some organizations take a standardized approach for all users in order to make the migration as efficient as possible while meeting business requirements. If you are opting for a manual migration, you may need to assess whether you’ll be able to complete the task by January 2020 when support for Windows 7 ends. 

## Migrate user data automatically with the User State Migration Tool

For large-scale deployments you can automate much of the process using task sequence-based deployment automation tools such as System Center Configuration Manager or the Microsoft Deployment Toolkit (MDT). Both these solutions make use of the User State Migration Tool (USMT) as part of the end-to-end deployment process. USMT is part of the Windows Assessment and Deployment Kit (Windows ADK) and captures user accounts, user files, operating system settings, and application settings, and then migrates them to a new Windows installation. It also gives IT admins control of exactly what gets migrated and, optionally, can exclude unwanted file types – for example, audio and video files, or executables.

During the migration process you will need to have sufficient server storage capacity available to act as your temporary migration store, which is where USMT offers two important features: It can estimate, per PC, the amount of storage you will need, and it allows for migration stores to be encrypted, reducing the risk of data being compromised while being stored on file servers.

If you are performing a PC refresh and not reformatting the primary Windows partition, you also have the option of using a hard-link migration store with USMT. This process preserves the user state on the PC while the old operating system and apps are removed and refreshed. With the restore process coming from the same local partition, this option offers significant improvements in performance and reduces network traffic.

