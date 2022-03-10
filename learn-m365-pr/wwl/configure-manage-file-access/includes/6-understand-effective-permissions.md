Each file or folder on the NTFS file system or ReFS has inherited or explicit permissions assigned, or both. Windows determines effective permissions by combining the user and group permissions and comparing them to the permissions of the selected user.

You also can evaluate what the effective permissions will be if you add a user or a device to additional groups, and configure whether to include user and device claims. For example, if you assign a user Read permission and assign the Modify permission to a group of which the user is a member, the effective permissions are a superset of the Read and Modify permissions. This superset is the Modify permission, because Modify permission also includes Read permission.

You also can evaluate what type of permissions the user would have if you add the user to the IT and Managers groups (without actually doing so) and whether the effective permissions should be different if the user’s token includes a Country = US user claim.

> [!NOTE]
> When you combine permissions, Windows evaluates the Deny permissions before the Allow permissions that are set at the same level. Therefore, the Deny permission takes precedence and overrides the Allow permission set on the same level.

If you set Deny and Allow permissions at different levels (for example, if Deny is set at the folder and Allow is set at its subfolder) Allow can take precedence and override Deny.
