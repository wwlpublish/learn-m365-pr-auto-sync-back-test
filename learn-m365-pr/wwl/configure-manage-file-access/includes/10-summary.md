Permissions are used to control which users have access to data. These can either be applied using File Explorer or using PowerShell on volumes that are formatted using NTFS or ReFS. Permission settings include whether a user has the ability to view or change files. Permissions are typically set at the top level of a hierarchy, such as a drive or folder. Folders and files inherit those permissions from the parent folder unless more permissions are explicitly assigned to prevent inheritance. Conditions can be defined to dynamically allow or deny access based on criteria such as a user's group membership.

Permissions can become complex if multiple permissions are defined. Using the Effective Access tab enables administrators to verify a user's permissions to a particular resource based on all of the permission assignments that affect that user. Both users and Administrators should be cautious when copying or moving files, as permissions of files and folder can change based on their target locations.

### Learn more

 -  [icacls \| Microsoft Docs](/windows-server/administration/windows-commands/icacls)
 -  [Set-Acl (Microsoft.PowerShell.Security) - PowerShell](/powershell/module/microsoft.powershell.security/)
