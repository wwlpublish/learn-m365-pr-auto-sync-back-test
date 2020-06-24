In this unit, you'll learn about the admin role in Exchange Online, and how you can use Roles to assign it to your existing users. 

By default, new users are assigned the user role and don't have any administrative privileges. To help you administer Office 365, you can assign users permissions to manage your organization's email and mailboxes from the Exchange admin center. You do this by assigning them to the Exchange admin role.

When assigning someone to the Exchange admin role, you also assign them to the Service admin role. This way, they can see important information in the Microsoft 365 admin center, such as the health of the Exchange Online service, and change and release notifications.

Here are some of the key tasks users can do when they are assigned to the Exchange admin role:

- Recover deleted items in a user mailbox
- Set up an archive and deletion policy
- Set up mailbox features like the mailbox sharing policy, which lets users share calendars and contact information with others outside of your organization
- Set up "Send As" and "Send on Behalf" delegates for someone's mailbox. For example, an executive may want their assistant to have the ability to send mail on their behalf.
- Create a shared mailbox so a group of people can monitor and send email from a shared email address
- Manage Microsoft 365 Groups

## Assigning admin roles

Be selective, and only grant users an appropriate role. For example, if you need someone to help reset passwords, they don't need the global admin role. Instead, assign them the password admin role. Having too many global admins, with unlimited access to your data and online business, is a security risk.

There are two ways to assign users to a role:
- You can go to the user's details, and Manage roles to assign a role to the user.
- Or you can go to Roles and select the role, and then add multiple users to it.

### Assign an admin role to users using Roles
1.	In the Exchange admin center, go to *Roles**. Select **Roles** to view all of the admin roles available for your organization.
2.	Select the admin role that you want to assign to the user.
   1. Select **Assigned admins**, and then select **Add**.
   2. Enter the user's display name or username, and then select the user from the list of suggestions.
   3. You can add the role to more users by selecting them here.
3.	Select **Save**.

### Assign a user to an admin role from Active users
1.	In the Exchange admin center, go to **Users**, and then select **Active users**.
2.	Select the user whose admin role you want to change. 
3.	Next to **Roles**, select **Manage roles**.
4.	Select the admin role that you want to assign to the user.
5.	Select **Save**. The user will be added to the list of assigned admins.