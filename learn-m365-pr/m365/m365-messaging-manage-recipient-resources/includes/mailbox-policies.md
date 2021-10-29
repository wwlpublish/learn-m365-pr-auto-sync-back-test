In Exchange Online, you can use the Exchange admin center or Exchange Online PowerShell to assign permissions to a mailbox or group. This means that other users can access the mailbox (the Full Access permission), or send email messages that appear to come from the mailbox or group (the Send As or Send on Behalf permissions). Users who are assigned these permissions on other mailboxes or groups are called delegates.

## Manage mailbox and group permissions

You can assign the following permissions to delegates for mailboxes and groups in Exchange Online:

- **Full Access**: Allows the delegate to open the mailbox to view, add, and remove the contents of the mailbox. Doesn't allow the delegate to send messages from the mailbox.
- **Send As**: Allows the delegate to send messages as if they came directly from the mailbox or group. There's no indication that the message was sent by the delegate.  
- **Send on Behalf**: Allows the delegate to send messages from the mailbox or group. The From address of these messages clearly shows that the message was sent by the delegate ("**on behalf of**").

To configure and manage mailbox permissions, the account you're logged in with needs either the Organization Management permission or the Recipient Management permission.

### Assign permissions to individual mailboxes  

1. In the Exchange admin center, go to **Recipients**. Depending on the type of mailbox permission you want to assign and work with, select from the Mailboxes, Resources, or Shared tabs.
2. Select the mailbox that you want to assign permissions for, and then select **Edit**.
3. On the mailbox properties page that opens, select **Mailbox delegation**. Configure one or more of the following permissions: Send As, Send on Behalf, Full Access.
4. To assign permissions to delegates, select **Add** under the appropriate permission.
5. To remove a permission from a delegate, select the delegate in the list under the appropriate permission, and then select **Remove**.
6. Select **Save**.

### Assign permissions to multiple mailboxes at the same time

1. In the Exchange admin center, go to **Recipients > Mailboxes**.
2. Select all the mailboxes that you want to assign permissions to. You'll see the title of the details pane change to **Bulk Edit**.
3. At the bottom of the details pane, select **More options**.  
4. Under the **Mailbox Delegation**, choose **Add** or **Remove**. Depending on your selection, do one of the following steps:

   - **Add**: Select **Add** under the appropriate permission (**Send As**, **Send on Behalf**, or **Full Access**). Select the users or groups to add, and then select **Save**.
   - **Remove**: Select **Remove** under the appropriate permission (**Send As**, **Send on Behalf**, or **Full Access**). Select the users or groups to remove, and then select **Save**.

### Assign permissions to groups

1. In the Exchange admin center, go to **Recipients > Groups**.
2. Select the group that you want to assign permissions for, and then select **Edit**.
3. Select **Group delegation**, and configure one of the following permissions: **Send As** or **Send on Behalf**.
4. To assign permissions to delegates, select **Add** under the appropriate permission. You'll see a list of the users or groups that can have the specific permission.  
   1. Select the user or group, and then select **Add**.  
   2. Repeat this process as many times as necessary. You can also search for users or groups in the search box, by typing all or part of the name, and then selecting **Search**.  
   3. Select **OK**.
5. To remove a permission from a delegate, select the delegate in the list under the appropriate permission, and then select **Remove**.
6. Select **Save**.

## Configure mailbox policies

In Exchange Online, Outlook on the web mailbox policies control the availability of settings and features in Outlook on the web (formerly known as Outlook Web App). You can only apply one Outlook on the web mailbox policy to a mailbox. You can create different policies for different types of users in your Exchange Online organization.

Every Exchange Online organization has a default Outlook on the web mailbox policy, named **OwaMailboxPolicy-Default**, that's applied to all user mailboxes. You can use this policy or create additional policies as needed to meet the needs of your organization.

To configure mailbox policies, the account you use will need either the Organization Management permission or the Recipient Management permission.

### Create an Outlook on the web mailbox policy using the Exchange admin center

1. In the Exchange admin center, go to **Permissions**, select **Outlook Web App policies**, and then select **New**.
2. Configure the following settings:
   - **Policy name**: Enter a unique name for your policy.
   - Enable or disable features by selecting or clearing them. By default, the most common features are displayed.
3. Select **Save**.

### Create an Outlook on the web mailbox policy using Exchange Online PowerShell

In Exchange Online PowerShell, creating an Outlook on the web mailbox policy is a two-step process - you create the policy and then modify it.

This example creates an Outlook on the web mailbox policy named Executives:

```PowerShell
New-OwaMailboxPolicy -Name Executives
```

This example modifies the mailbox policy to enable calendar access:

```PowerShell
Set-OwaMailboxPolicy -Identity Executives -CalendarEnabled $true
```

## Learn more

- [Manage mailbox permissions](/Exchange/recipients-in-exchange-online/manage-permissions-for-recipients)
- [Configure mailbox policies](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/outlook-web-app-mailbox-policies)
- [Mailbox policy properties](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/configure-outlook-web-app-mailbox-policy-properties)
