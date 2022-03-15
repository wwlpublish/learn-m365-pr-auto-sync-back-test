The Effective Access tab in Advanced Security Settings enables you to view the effective permissions for a user, group, or device account.

The Effective Access feature determines the permissions a user or group has on an object by calculating the permissions that are granted to the user or group. The calculation takes into account the group membership permissions and any of the permissions inherited from the parent object.

The calculation determines all of the domain and local groups of which the user or group is a member.

:::image type="content" source="../media/effective-access-4220e79a.jpg" alt-text="Screenshot of the Advanced Security Settings for Folder showing the name of the user selected.":::


> [!NOTE]
> The Effective Access feature always includes the Everyone group when calculating effective permissions, as long as the selected user or group is not a member of the Anonymous Logon group.

:::image type="content" source="../media/view-effective-access-412c6076.jpg" alt-text="Screenshot of the Advanced Security Settings for Folder showing the indivdual permissions for the user.":::


The Effective Access feature only produces an approximation of the permissions that a user has. The actual permissions a user is assigned might be different, because permissions can be granted or denied based on how a user signs in. The Effective Permissions feature cannot determine this information specific to the sign-in, because the user might not sign in. Therefore, the effective permissions it displays reflect only those permissions that a user or group specifies, not the permissions that the sign-in specifies. For example, if a user connects to a computer through a file share, the sign-in for that user is marked as a Network Logon. You then can grant or deny permissions to the well-known security identifier Network that the connected user receives. This way, users have different permissions when they sign in locally than when they sign in over a network.

You can view effective access permissions in the **Advanced Security Settings** dialog box for files or folders stored on the NTFS or ReFS file system. You can access this dialog box from a folder’s **Properties** dialog box by using the **Advanced** button on the **Security** tab, or directly from the **Share** menu on the ribbon.

> [!NOTE]
> Windows supports claims, so you can include the user and device claims when evaluating effective access. A claim is information about a user or device that a domain controller published, and you can use it to evaluate if a user has access to data.
