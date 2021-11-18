Microsoft Exchange enables users and groups to receive and respond to messages and meeting requests on another user's behalf. As a messaging administrator, you can use the Exchange admin center (EAC) or the Exchange Management Shell to assign permissions to users and groups to provide this functionality.

Users or groups who receive permission to act on behalf of someone else are commonly referred to as delegates. You can also grant additional permissions that allow delegates to read, create, or have more control over items in your Exchange Server mailbox. For example, department managers may delegate permissions to their assistants to read mail, respond to email on the manager’s behalf, or manage the manager’s calendar.

Permissions can be assigned to user mailboxes, linked mailboxes, resource mailboxes, and shared mailboxes. You can also assign permissions to distribution groups, dynamic distribution groups, and mail-enabled security groups to allow delegates to send messages on behalf of the group.

The following permissions are used to access mailboxes or send messages on behalf of mailboxes or groups:

 -  **Full Access.** This permission allows a delegate to open a user’s mailbox and access the contents of the mailbox.
 -  **Send As.** This permission allows delegates to use the mailbox to send messages.
 -  **Send on Behalf.** After this permission is assigned to a delegate, the From address in any message sent by the delegate indicates the message was sent by the delegate on behalf of the mailbox owner.

The following procedure shows how to assign permissions to a user mailbox.

1.  In the EAC, expand the **Recipients** group in the left-hand navigation pane, and then select **Mailboxes**.
2.  In the **Mailboxes** page, select the mailbox that you want to assign permissions to (select the display name; don't select the check box to the left of the display name). This opens the Properties pane for the mailbox.
3.  On the mailbox properties page, under the **Mailbox permissions** section, select **Manage mailbox delegation**.
4.  To assign permissions to delegates, select the **Edit** button next to the appropriate permission to display a page that lists all recipients in your Exchange organization that can be assigned the permission. Select the recipients you want, add them to the list, and then select **Save**. You can also search for a specific recipient by typing the recipient’s name in the search box and then selecting the **Search** icon.
5.  To remove a permission for a recipient, under the appropriate permission, select the recipient and then select the **X** to the right of the recipient.
6.  Select **Save** to save your changes.

> [!NOTE]
> You follow a similar procedure to assign permissions to resources or shared mailboxes by navigating to the **Resources** or **Shared** page in the EAC and selecting the mailbox to assign the permissions to.

The following example gives the Exchange Online user, Holly Spencer, Send As permission for the mailbox Help Desk:

```powershell
Add-RecipientPermission "Help Desk" -AccessRights SendAs -Trustee "Holly Spencer"
```

The following example assigns the Send As permission to the Helpdesk group on the shared mailbox Helpdesk Support Team in an on-premises Exchange organization:

```powershell
Add-ADPermission -Identity helpdesksupport -User helpdeskgroup -ExtendedRights "Send As"
```

The following example assigns the delegate Patti Fernandez the Send on Behalf permission to the mailbox of Alan Deyoung:

```powershell
Set-Mailbox -Identity aland@contoso.com -GrantSendOnBehalfTo pattif
```

Automapping is an Exchange feature that allows Outlook clients to automatically map to any mailbox to which a user has Full Access permissions. As such, if a user has Full Access permissions to another user's mailbox or to a shared mailbox, Outlook automatically loads all the mailboxes to which the user has Full Access.

Sometimes it’s necessary to disable automapping. For example, a user may have Full Access permissions to so many mailboxes that it causes performance issues when starting Outlook.

You can disable automapping by using PowerShell. For example, if you want to grant the user Ed Jones Full Access permission to Kim Chastain’s mailbox and disable the automapping feature, you would run the following command:

```powershell
Add-MailboxPermission -Identity KimC -User ‘Ed Jones’ -AccessRight FullAccess -InheritanceType All -Automapping $false
```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.