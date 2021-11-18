Creating a shared mailbox in Exchange is a single-step process. Mailboxes can be created in either the Exchange admin center (EAC) or Exchange PowerShell. You can create a shared mailbox and grant users Full Access and Send As mailbox permissions when you create the mailbox.

You can also create and manage shared mailboxes with PowerShell by using the **New-Mailbox** command with the **-Shared** parameter. For example:

```powershell
New-Mailbox -Shared -Name "HR Department" -DisplayName "HR Department" -Alias HR@contoso.com | Set-Mailbox -GrantSendOnBehalfTo HRSG | Add-MailboxPermission -User HRSG -AccessRights FullAccess -InheritanceType All
```

### Manage shared mailboxes

When a user is granted Full Access permission to a shared mailbox, the delegated user can access the mailbox and view and manage all messages in the mailbox.

Granting Full Access permissions doesn't grant the delegated user the right to send mail as the selected mailbox. To allow a user to send mail from a delegated mailbox, you must also assign Send As permissions. When a user with Send As permissions sends a message from the delegated mailbox, any message sent from the mailbox will appear as if it was sent by the mailbox owner.

Shared mailboxes can have the following delegated permissions:

 -  **Full Access.** Users with Full Access permission can sign in and carry out actions consistent with a mailbox owner. However, to send mail, users with Full Access permission must also have Send As or Send on Behalf of permission. You can configure Full Access permission through the EAC or PowerShell.
 -  **Send As.** Users with Send As permission can impersonate the mailbox when sending mail. Messages received are “from” the mailbox, so they appear to come directly from, say, marketing@contoso.com. You can configure Send As permission through the EAC or PowerShell.
 -  **Send on Behalf of.** This permission grants the right to send messages, but those messages are stamped as coming from one user on behalf of another user. For example, from “Sara Davis on behalf of IT Department.” The Send on Behalf of permission is only configurable through PowerShell.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.