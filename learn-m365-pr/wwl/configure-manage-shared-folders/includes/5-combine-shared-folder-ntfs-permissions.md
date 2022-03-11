When you create a shared folder on a volume that is formatted with a file system that supports security, both the shared folder permissions and the file and folder permissions combine to control permissions to file resources when a user connects via a network. File and folder permissions apply whether users access a resource locally or over a network, but they filter against the shared folder permissions.

When you grant shared folder permissions, the following rules apply:

 -  Except when using the Share in Network File and Folder Sharing, the Everyone group has the Read shared folder permission.
 -  Users must have appropriate file system permissions for each file and subfolder in a shared folder to access those resources, in addition to appropriate shared folder permissions.
 -  When you combine file-system and shared-folder permissions, the resulting permission is the most restrictive one of the effective permissions between the two types. Typically, this is the highest common denominator of the file-system and shared-folder permissions.
 -  When a user attempts to connect to content through a share, the share permissions on a folder apply to that folder, all of its files and sub-folders, and all files in those sub-folders.

When you configure shared folder permissions per shared folder, you can allow or deny only Read, Change, and Full Control permissions, and these permissions apply to content in all folders and subfolders. You have much more granularity when you configure file-system permissions. You can configure permissions for each file, and you can allow or deny many more file-system permissions than share permissions.

The following analogy can help you understand what happens when you combine file system and share permissions:

 -  If you want to access a shared folder’s files over a network, you must go through the shared folder.
 -  If a share permission is set to Read, the most that you can do when connecting through a shared folder is read the file, even if the individual file system permission is set to Full Control. All file system permissions that are less restrictive than the share permissions filter out, so that only the most restrictive permissions remain – in this case, the Read permission
 -  If you configure the share permission to Change, you are allowed to read or modify the share’s data. If the file system permission is set to Full Control, the share permissions filter the effective permission to Modify.
 -  Alternatively, if the share permission is set to Full Control, but the users NTFS permissions for the folder are set to Read, the effective permission is Read.
