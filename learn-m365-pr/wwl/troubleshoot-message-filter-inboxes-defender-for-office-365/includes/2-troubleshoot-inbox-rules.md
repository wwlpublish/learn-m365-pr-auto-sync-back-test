Outlook inbox rules can help users to organize or respond to email automatically but, when these rules are numerous or complex, it can cause confusion or unintended behavior.

In the marketing company where you work, users often set up inbox rules to categorize the many responses they receive, and sort them into campaign folders. Sometimes users lose campaign emails or find them in the wrong folder. You must find out why the emails have gone to the wrong place and correct the inbox rules.

Here, you’ll learn how to list, troubleshoot, and correct inbox rules for users.

## Understand inbox rules

Many Outlook users receive large quantities of email, and spend significant time filtering relevant and important emails from less relevant and nuisance items. They might also want to differentiate and take different actions on important and business-critical messages. To help with these processes, Outlook includes inbox rules, which can move, mark, and delete email, or take other actions based on the content.

For example, suppose you work on many different email marketing campaigns. You might receive large numbers of mails about different campaigns simultaneously. You’d like to move them into the appropriate campaign folder in your mailbox based on their subject lines or message body. You can create inbox rules to automate that move action.

> [!NOTE]
> Inbox rules are not the same as mail transport rules. Inbox rules are usually created by the end user in Outlook and act after a mail arrives at an inbox. Transport rules are created by Exchange Online administrators and act when emails are in transit through your Exchange organization.

Inbox rules are of two types:

- **Server-side rules.** These rules run on the server and run even if the user is not logged in to an Outlook session.
- **Client-side rules.** These rules run in Outlook and are only executed when a user is logged into Outlook.

The condition you choose when you create the rule determines whether it executes server-side or client-side. Most actions can be completed on the server but some, such as playing a specific sound, can only execute in Outlook. These rules are set up as client-side rules.

Although inbox rules are useful and simple, some users can end up in difficulties with them. When there are many rules, it can be difficult to know which one is applied or what the end result should be. When emails are not found in the right place or Outlook’s behavior is otherwise unexpected, you might need to investigate a user’s inbox rules and remove some badly configured rules.

## Determine which rules are triggered when an email arrives at a user’s inbox

Users can check the inbox rules that are enabled in their own inbox. In Outlook, select **Rules,** and then select **Manage Rules & Alerts**:

:::image type="content" source="../media/02-inbox-rules.png" alt-text="Screen shot showing how to manage inbox rules in Outlook.":::

As an Exchange Online administrator, you can use Exchange PowerShell to list all the inbox rules for a given user and obtain full details of each one.

To list the inbox rules in a user’s inbox, use this command:

``` powershell
Get-InboxRule -Mailbox kiana.anderson@contoso.com
```

This command lists all the rules in Kiana’s inbox.

When you have listed all the inbox rules, you can obtain full details of each one using this command:

``` powershell
Get-InboxRule "MoveToProjectX" -Mailbox kiana.anderson@contoso.com
```

When inbox rules are not behaving as a user intends, check the following factors:

- Are the relevant rules enabled or disabled?
- Are there two or more rules that might act on the same message and take different actions?
- What are the priorities of each rule? Rules with a lower priority number execute first.
- Does a rule include “stop processing more rules”?

> [!NOTE]
> If you have a mix of server-side and client-side rules, rules can execute in an unexpected order. For example, when the user is offline, a server-side rule with priority 2 might execute before a client-side rule with priority 1 because the client-side rule can only execute when the user next logs in. This execution order can be unexpected for users.

## Troubleshoot issues with corrupted inbox rules

By accessing inbox rules using Outlook and PowerShell, you can resolve most problems. However, it is possible for inbox rules to obtain an inconsistent set of raw properties and sometimes this situation can prevent a rule being displayed in Outlook and PowerShell. These rules are referred to as **corrupted** or **hidden,** and can be difficult to identify and fix.

> [!NOTE]
> It’s possible for malicious users to attack your Exchange Online organization by deliberately creating hidden inbox rules through the MAPI interface. If an attacker obtains access to a mailbox, for example by phishing for the user’s credentials, the user can defend by changing their password. However, if the attacker creates a hidden rule while they have access, security can remain compromised even after the change in credentials. The hidden rule can remain in place and, for example, forward all mail to an external email address. This hidden rule might be difficult to detect.

The `-IncludeHidden` option for the `Get-InboxRule` cmdlet may display hidden rules:

``` powershell
Get-InboxRule -Mailbox kiana.anderson@contoso.com -IncludeHidden
```

Having identified hidden rules that way you can delete them with this command:

``` powershell
Remove-InboxRule -Mailbox kiana.anderson@contoso.com -Identity "FowardAllMailExternally"
```

Another way to identify hidden and corrupted inbox rules is to use the **MFCMAPI** tool.

> [!NOTE]
> The MFCMAPI tool enables you to access low-level MAPI properties for an Exchange Online mailbox and make changes. It must be used with care to avoid corrupting Exchange Online objects including mailboxes, messages, public folders, and other essential items. It’s recommended that you back up data in a mailbox before you use MFCMAPI, so you can restore it if something goes wrong.

1.  Download the MFCMAPI tool from its GitHub repository.
1.  Ensure that there are no Outlook sessions accessing the mailbox in question.
1.  Start MFCMAPI and log on as an Exchange administrator.

    > [!NOTE]
    > Only an Exchange administrator who has full permissions to the mailbox can use MFCMAPI to delete an inbox rule.

1.  Double-click the default Exchange mailbox store.
1.  Expand **Root container/Top of Information Store/Inbox**.
1.  Right-click **Inbox,** and then select **Open associated contents table**.
1.  Inbox rules are listed with the Message Class **IPM.Rule2.Message**. Compare this list of rules with those visible in Outlook. Any rules that are not visible in Outlook might be corrupted.

To delete a corrupted rule:

1.  Right-click the **IPM.Rule2.Message,** and then select **Delete message**.
1.  In the **Deletion style** dropdown list, select **Permanent delete passing DELETE\_HARD\_DELETE (unrecoverable),** and then select **OK**.
1.  Close all MFCMAPI windows and log off.

## Learn more

- [GitHub MFCMAPI repository](https://github.com/stephenegriffin/mfcmapi)
- [Server-side vs. client-only rules](https://support.microsoft.com/office/server-side-vs-client-only-rules-e1847992-8aa1-4158-8e24-ad043decf1eb)
- [Get-InboxRule](/powershell/module/exchange/get-inboxrule)
- [Remove-InboxRule](/powershell/module/exchange/remove-inboxrule)
- [How to delete junk email rules by using MFCMAPI in an Exchange Server environment](/exchange/troubleshoot/administration/delete-junk-email-rules-mfcmapi-exchange)
