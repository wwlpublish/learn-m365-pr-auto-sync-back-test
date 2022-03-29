When you copy or move a file or folder, the permissions can change, depending on where you move the file or folder. Therefore, when you copy or move files or folders, it's important to understand the effect on permissions.

#### Effects of copying files and folders

When you copy a file or folder from one folder to another, or from one volume to another, permissions for the files or folders might change. Copying a file or folder creates new objects with the same content as the original files or folders, and it has the following effects on permissions:

 -  When you copy a file or folder within a single volume, the copy of the folder or file inherits the permissions of the destination folder.
 -  When you copy a file or folder to a different volume, the copy of the folder or file inherits the permissions of the destination folder.
 -  When you copy a file or folder to a volume that doesn't support permissions (non-NTFS and non-ReFS), such as a FAT file system, the copy of the folder or file loses its permissions. This is because the target volume doesn't support permissions.

> [!NOTE]
> When you copy a file or folder within a single volume or between volumes, you must have the Read permission for the source folder and the Write permission for the destination folder.

#### Effects of moving files and folders

When you move a file or folder, permissions might change, depending on the destination folder’s permissions. Moving a file or folder has the following effects on permissions:

 -  If you move a file or folder within the same volume, only the pointer(s) are updated, and data isn't moved. Permissions that are inherited at the source location no longer apply and the file or folder that you moved inherits the permissions from the new parent folder. If the file or folder has explicitly assigned permissions, it retains those permissions, in addition to the newly inherited permissions.

> [!NOTE]
> Most files don't have explicitly assigned permissions. Instead, they inherit permissions from their parent folder. If you move files that have only inherited permissions, they don't retain the inherited permissions during the move.

 -  When you move a file or folder to a different volume, the folder or file inherits the destination folder’s permissions, but it doesn't retain the explicitly assigned or inherited permissions from the source location. When you move a folder or file between volumes, Windows copies the folder or file to the new location and deletes the original file from the source location.
 -  When you move a file or folder to a volume that doesn't support permissions (non-NTFS and non-ReFS), the folder or file loses its permissions because the target volume doesn't support permissions.

> [!NOTE]
> When you move a file or folder within a volume or between volumes, you must have both the Write permission for the destination folder and the Modify permission for the source file or folder. You require the Modify permission to move a folder or file, because Windows deletes the folder or file from the source folder after it copies it to the destination folder.

The **Copy** command isn't aware of the security settings on folders or files. However, commands that are more robust have this awareness. For example:

 -  **Xcopy** has the /o switch to include Ownership and ACL settings.
 -  **Robocopy** has several switches that cause security information to be copied:
    
     -  **/Copy:copyflag(s)** the default setting is the equivalent of **/Copy:DAT** where **D**=Data, **A**=Attributes, and **T**=Timestamps. You can add the **S** flag where **S**=Security, such as NTFS ACLs.
     -  **/Sec** is the equivalent of **/Copy:DATS**.
