Many organizations configure public folder client permissions, or access rights, for their users. These permissions are used to restrict the actions users can complete in the public folder.

Client permissions haven't changed compared to previous versions of Exchange Server. Organizations can assign permissions to their users by using roles such as Owner or Publishing Editor. They can also assign custom permissions by using various access rights.

In Exchange Server and Exchange Online, administrative permissions to manage public folders are enabled through Role-Based Access Control (RBAC). To grant users permission to manage public folders, you must add them to the Public Folder Management role group.

### Public folder client permissions

The following list describes public folder client permissions:

 -  **ReadItems.** The user can read items in the specified public folder.
 -  **CreateItems.** The user can create items in the specified public folder and send email messages to the public folder if it's mail-enabled.
 -  **EditOwnedItems.** The user can edit the items that the user owns in the specified public folder.
 -  **DeleteOwnedItems.** The user can delete items that the user owns in the specified public folder.
 -  **EditAllItems.** The user can edit all items in the specified public folder.
 -  **DeleteAllItems.** The user can delete all items in the specified public folder.
 -  **CreateSubfolders.** The user can create subfolders in the specified public folder.
 -  **FolderOwner.** The user is the owner of the specified public folder. The user can view and move the public folder, create subfolders, and set permissions for the folder. The user can't read, edit, delete, or create items.
 -  **FolderContact.** The user is the contact for the specified public folder.
 -  **FolderVisible.** The user can view the specified public folder but can't read or edit items in the folder.

### Public folder roles with permissions

The following table identifies the predefined public folder roles and the permissions that are included in each role.

|     **Role**      | **Create Items** | **Read Items** | **Create Subfolders** | **Folder Visible** | **Edit AllItems** | **Edit/Delete OwnedItems** | **Delete AllItems** | **Folder Owner** | **Folder Contact** |
|:-----------------:|:----------------:|:--------------:|:---------------------:|:------------------:|:-----------------:|:--------------------------:|:-------------------:|:----------------:|:------------------:|
|       None        |                  |                |                       |         X          |                   |                            |                     |                  |                    |
|       Owner       |        X         |       X        |           X           |         X          |         X         |             X              |          X          |        X         |         X          |
| PublishingEditor  |        X         |       X        |           X           |         X          |         X         |             X              |          X          |                  |                    |
|      Editor       |        X         |       X        |                       |         X          |         X         |             X              |          X          |                  |                    |
| PublishingAuthor  |        X         |       X        |           X           |         X          |                   |             X              |          X          |                  |                    |
|      Author       |        X         |       X        |                       |         X          |                   |             X              |                     |                  |                    |
| Non-EditingAuthor |        X         |       X        |                       |         X          |                   |                            |                     |                  |                    |
|     Reviewer      |                  |       X        |                       |         X          |                   |                            |                     |                  |                    |
|    Contributor    |        X         |                |                       |         X          |                   |                            |                     |                  |                    |

You can configure client permissions or public folder roles in the EAC by selecting the public folder and then selecting **Manage** under **Folder permissions**. You can also configure client permissions by accessing the public folder properties in Outlook, or by using the **Add-PublicFolderClientPermission** and **Remove-PublicFolderClientPermission** cmdlets.

Permissions are assigned to a public folder as follows:

 -  When you create a public folder, it automatically inherits the same client permissions as the parent public folder.
 -  When you change the permissions on a parent folder, you can enforce the permission change for all subfolders.

The default permissions assigned to new root folders are **Author** for authenticated users and **None** for anonymous users.
