Traditionally, you control permissions to files and folders by using group membership. However, if your Windows–based computer is a domain member, you can extend this traditional access control by using conditions to limit access. Windows 8 and Windows Server 2012 introduced this feature, which allows you to utilize user or computer properties to limit access beyond group membership. For example, if the users have a defined department in AD DS, you can limit access to files or folders to users from a specific department, regardless of their group membership. You also can limit access to users who are in the department and in a specific group. You do this by extending a user token, which all users receive upon sign-in, with the claims. Claims are AD DS properties and their values, and an administrator must configure which properties can be used as claims in AD DS.

:::image type="content" source="../media/impliment-file-limit-c3beead4.jpg" alt-text="Screenshot of the permission entry for folder window.":::


Even if an administrator does not specify in AD DS which properties to use as claims, you can use conditions to limit access to files or folders based on user or device-group membership. When viewing the permissions for a file or folder, the Condition column in the Advanced Security Settings lists the applied conditions.

When you specify conditions:

 -  You use a Group condition so that you can specify that the permission will apply to the user based on the following group-membership rules:
    
     -  Member of Any of the specified groups.
     -  Member of Each of the specified groups.
     -  Not Member of Any of the specified groups.
     -  Not Member of Each of the specified groups.
 -  You use a Device condition so that you can specify that the permission will apply if a user accesses the file from a specified computer or computers. The next unit provides more detail about this condition.

You can specify multiple conditions for the configured permission to apply. For example, you can create a permission that would give members of the Financial group Full Control permissions if they also are members of the Managers group and are accessing the folder from Computer1.
