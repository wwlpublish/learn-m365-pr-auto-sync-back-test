In this unit, you'll learn about the admin role in Exchange Online and why you might want to assign that role to some of your existing users.

By default, new users are assigned the *user* role and don't have any administrative privileges. To help you administer your environment, you can grant individual users permission to manage your organization's email and mailboxes. You do this by assigning them to the Exchange admin role.

When you assign someone to the Exchange admin role, you also assign them to the Service admin role. This way, they can see important information in the Microsoft 365 admin center, like the health of the Exchange Online service and release notifications.

Here are some of the key tasks users can do when you assign them the Exchange admin role:

- Recover deleted items in a user mailbox
- Set up an archive and deletion policy
- Set up mailbox features like the mailbox sharing policy, which lets users share calendars and contact information with others outside of your organization
- Set up "Send As" and "Send on Behalf" delegates for someone's mailbox. For example, an executive may want their assistant to have the ability to send mail on their behalf.
- Create a shared mailbox so a group of people can monitor and send email from a shared email address
- Manage Microsoft 365 Groups

## Assigning admin roles

Be selective, and only grant users the appropriate role for the tasks they'll be doing. For example, if you need someone to help reset passwords, they don't need the global admin role. Instead, assign them the password admin role. Having too many global admins, with unlimited access to your data and online business, is a security risk.

There are two ways to assign users to a role: from the role or from the user.

### Assign an admin role to users using Roles

If you're granting admin permissions to more than one user, start at the role.

1. In the Microsoft 365 admin center, go to **Roles**. Select **Roles** to view all of the admin roles available for your organization.
1. Select the admin role that you want to assign to the user.
    1. Select **Assigned admins**, and then select **Add**.
    2. Enter the user's display name or username, and then select the user from the list of suggestions.
    3. Repeat the previous step for each user you want to assign.
1. Select **Save**.

### Assign a user to an admin role from Active users

If you're granting admin permissions to just one user, you can either use the steps above to start from the admin role or you can edit the user directly to manage their roles.

1. In the Microsoft 365 admin center, go to **Users > Active users**.
1. Select the user whose admin role you want to change.
1. Next to **Roles**, select **Manage roles**.
1. Select the admin role that you want to assign to the user.
1. Select **Save**. The user will be added to the list of assigned admins.
