There are two ways that you can assign permissions to files and folders, including:

 -  **Explicit permissions**. When you set permissions directly on a file or a folder, the permissions are applied explicitly. You can assign permissions to the object directly by modifying the security settings in the object’s properties dialog box.
 -  **Inherited permissions**. Files and folders typically are arranged in a nested structure, where a folder contains subfolders and files, and those subfolders contain files and folders. Permission inheritance allows for child objects to inherit the parent object’s permissions settings. This allows you to assign explicit permissions to a parent folder and have inheritance pass those permissions settings down to the parent folder’s subfolders and files. You can control inheritance behavior. Inherited permissions ease the task of managing permissions, and they ensure the consistency of permissions among all of a container’s objects.

:::image type="content" source="../media/permission-inheritance-overview-066be175.jpg" alt-text="Diagram showing the process of inheriting permissions.":::


Permission inheritance allows the permissions that you set on a folder to apply automatically to files that users create in that folder and its subfolders. This means that you can set permissions for an entire folder structure at a single point. If you have to modify permissions, you then have to perform the change at that single point only.

For example, when you create a folder called Folder1, all subfolders and files created within Folder1 automatically inherit that folder’s permissions. Therefore, Folder1 has explicit permissions, while all subfolders and files within it have inherited permissions.

Permissions on a file are a combination of inherited and explicit permissions. For example, if you assign Group1 Read permissions on a folder and Write permissions on a file in the folder, members of Group1 can read and write in the file. If inherited and explicit permissions conflict, explicit permissions take precedence.

### **Inheritance for all objects**

If the **Allow** or **Deny** check boxes that are associated with each of the permissions appear shaded, a file or folder has inherited permissions from one of its parent folders. There are two ways that you can make changes to inherited permissions:

 -  Make changes to a parent folder at which you set permissions explicitly. The file or folder will inherit these modified permissions.
 -  Choose not to inherit permissions from a parent object. You then can make changes to the permissions or remove a user or group from the permissions list of the file or folder.

> [!NOTE]
> You can make changes to inherited permissions also by selecting the opposite permission (Allow or Deny) to override the inherited permission. You should be aware that this might cause a different result than many users expect, because when you set both the Deny and the Allow permissions at the same level, Deny has a higher precedence than Allow. Therefore, we recommend that you avoid using this option.

You also can deny permissions explicitly. For example, Alice might not want Bob to be able to read her file, even though they are a member of the Marketing group, which has Read permissions. She can exclude Bob by explicitly denying him permission to read the file. Typically, you use explicit denial to exclude a subset, such as Bob, from a larger group, such as Marketing, that has permission to perform an operation.

Note that although explicit denials are possible, their use increases the complexity of the authorization policy, which can create unexpected errors. For example, you might want to allow domain administrators to perform an action, but deny domain users the ability to perform it. If you attempt to implement this by explicitly denying domain users, you also deny any domain administrators who are domain users. Though it's sometimes necessary, you should avoid the use of explicit denials.

In most cases, Deny overrides Allow unless a folder inherits conflicting settings from different parents. In that case, the setting inherited from the parent closest to the object in the subtree takes precedence.

> [!NOTE]
> Inherited Deny permissions don't prevent access to an object if the object has an explicit Allow permission entry. Explicit permissions take precedence over inherited permissions, including inherited Deny permissions.

Child objects only inherit permissions that they're capable of inheriting. When you set permissions on a parent object, you can decide whether folders, subfolders, and files can inherit permissions. Perform the following procedure to assign permissions that child objects can inherit:

1.  In **File Explorer**, right-click the file or subfolder, select **Properties**, select the **Security** tab, and then select **Advanced**.
2.  In the **Advanced Security Settings for file or folder** dialog box, the **Inherited From** column lists from where the permissions are inherited. The **Applies To** column lists the folders, subfolders, or files to which the permissions are applied.
3.  Double-click the user or group for which you want to adjust permissions.
4.  In the **Permissions Entry for name** dialog box, select the Applies to drop-down list, and then select one of the following options:
    
     -  This folder only
     -  This folder, subfolders, and files
     -  This folder and subfolder
     -  This folder and files
     -  Subfolders and files only
     -  Subfolders only
     -  Files only
5.  Select **OK** in the **Permission Entry for name** dialog box, select **OK** in the **Advanced Security Settings for name** dialog box, and then select **OK** in the **Properties** dialog box.

If the **Special permissions** entry in **Permissions for User or Group** box is shaded, it doesn't imply that this permission is inherited. Rather, this means that a special permission is selected.

> [!NOTE]
> If you add permissions for CREATOR OWNER at the folder level, those permissions will apply to the user who created the file in the folder.

### **Preventing inheritance**

After you set permissions on a parent folder, new files and subfolders that users create in the folder inherit these permissions. You can block permission inheritance to restrict access to these files and subfolders. For example, you can assign all Accounting users the Modify permission to the Accounting folder. On the subfolder Invoices, you can block inherited permissions and grant only a few specific users permissions to the folder.

> [!NOTE]
> When you block permission inheritance, you have the option to convert inherited permissions into explicit permissions, or you can remove all inherited permissions. If you want to restrict a particular group or user, you can convert inherited permissions into explicit permissions to simplify configuration.

To prevent a child file or folder from inheriting permissions from a parent folder, select This folder only in the Applies to drop-down list box when you configure permissions for the parent folder.

To prevent a folder or file from inheriting permissions from a parent folder, perform the following procedure:

1.  In **File Explorer**, right-click the file or subfolder, select **Properties**, select the **Security** tab, and then select **Advanced**.
2.  In the **Advanced Security Settings for file or folder** dialog box, select **Disable inheritance**.
3.  In the Block Inheritance dialog box, select any of the following options:
    
     -  **Convert inherited permissions into explicit permissions on this object**
     -  **Remove all inherited permissions from this object**
     -  **Cancel**
4.  Select **OK** in the **Advanced Security Settings for name** dialog box, and then select **OK** in the **Properties** dialog box.

### Forcing permission inheritance

The **Advanced Security** dialog box for folders includes a **Replace all child object permission entries** check box with inheritable entries from this object. Selecting this check box will replace the permissions on all child objects for which you can change permissions, including child objects that had Block inheritance configured. This is useful if you need to change permissions on a large number of subfolders and files, especially if you set the original permissions incorrectly.
