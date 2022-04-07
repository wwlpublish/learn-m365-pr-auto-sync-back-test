Exchange Online can keep a journal of messages that were sent in your organization. You might want to use this journaling feature to comply with data protection laws or to make it easier to review communications in your company.

In your company that helps disadvantaged youth, you've enabled journaling to record all communications with your clients, so that you can easily check that your staff are behaving appropriately and treating clients with respect, in accordance with your company policies. However, during a recent review of the journaled messages, you noticed that there were fewer messages to examine than you were expecting. You need to verify that journaling rules are configured correctly and that all communications with clients are reaching the journal mailbox.

Here, you'll learn how to investigate and correct your journaling configuration in Exchange Online.

## What is journaling in Exchange Online?

In Exchange Online, you can use the journaling feature to record messages by sending a copy to a dedicated email address. You can either configure the system to record all message this way or use journaling rules to target only those messages sent to a specific email address. You can use journaling as part of your archiving strategy or to comply with mail retention legislation.

To use journaling, you must configure journaling rules, either by using the classic Exchange Admin Center (EAC) or by using PowerShell. A journaling rule consists of:

- **A recipient address.** You can either select **Apply to all messages**, in which case all messages in your organization will be journaled, or select a specific email address or distribution list, in which case only messages sent to that recipient are journaled.
- **A scope.** You can select either **Internal messages only**, which will journal messages sent between internal mailboxes, or **External messages only**, which will journal messages sent from or to email addresses outside your organization. You can also select **All messages**, which will journal bot internal and external messages.
- **A journal email address.** This address is the location journaled messages are sent to.

Once a rule is configured and enabled, messages in your organization that match the recipient address and scope are copied to the journal email address. Messages are copied as journal reports:

- The body of the journal report includes information about the original message such as the sender address, the subject, and the message ID.
- The original message is included as an attachment to the journal report.

> [!NOTE]
> The journal email address can't specify a mailbox in Exchange Online. Instead use a mailbox in on-premises Exchange Server or use an email address in another email system.

The journal email address might receive a large volume of email, especially if you're journaling all messages in your organization. You must make sure that the email address is highly available and has enough space to store all the messages it receives.

You can also specify an alternate journaling mailbox for your organization. As for the journal email address, this email must be outside Exchange Online. When the journal mailbox specified on a rule is unavailable, Non-Delivery Reports (NDRs) are sent to this email address with the journal reports as attachments. To check your alternate journaling mailbox, use this command:

```powershell
Get-TransportConfig | FL JournalingReportNdrTo*
```

If you want to change the alternate journaling mailbox, use this command:

```powershell
Set-TransportConfig   –JournalingReportNdrTo alternatejournal@contoso.com
```

## Diagnose why messages aren't journaled

If messages aren't reaching the journaling mailbox as expected, you can start your troubleshooting by listing all the journaling rules in your organization by using this command:

```powershell
Get-JournalRule | Format-Table
```

Use the following subsections to diagnose and fix the problem.

### Incorrect recipient address or scope

The journal rule won't fire as expected if the recipient address or scope are incorrectly configured. For example:

- You've made a spelling mistake in the recipient address.
- You've selected **Internal messages only** when you want to journal messages sent to or from external recipients.

Go through the list you obtained from the previous PowerShell command and check that the matching criteria are correct. If any are incorrect, you can use commands like the following to fix them:

```powershell
Set-JournalRule -Identity "Rule-For-Admins" -Recipient admins@contoso.com -Scope External
```

### Unavailable journal mailbox

If the journal email address for a journaling rule is not valid or doesn't exist, journal reports won't reach it and will remain in the transport queue.

Go through the list you obtained from the previous PowerShell command and make sure that the **JournalEmailAddress** value is a valid mailbox. You should also check that, in the external email system, the specified mailbox has enough space to receive many messages.

> [!IMPORTANT]
> Important: If the transport queue starts to grow because of an invalid journal email address, Microsoft might contact you to resolve the problem. If you haven't resolved the issue after two days, Microsoft will disable the journaling rule.

To fix incorrect journal email addresses, use the following command:

```powershell
Set-JournalRule -Identity "Rule-for-Admins" -JournalEmailAddress adminjournal@contoso.com
```

### Disabled journaling rules

If any of the journaling rules in the list are incorrectly disabled, you can enable them with this command:

```powershell
Enable-JournalRule -Identity "Rule-for-Admins"
```

## Duplicate journal reports

In certain situations, where you are using Exchange Online and Exchange Server in a hybrid configuration, a single message might result in two duplicate journaling entries. For example:

- Whenever a message is forked. Messages can be forked because there too many recipients for the message or because the message includes both internal and external recipients.
- When a message is sent from an on-premises mailbox to a cloud mailbox or in the other direction.

This behavior is by design and should not be considered a misconfiguration or bug. If you're using journaling in a hybrid Exchange organization, make sure that you have enough space in your journaling mailbox to accommodate some duplicated journal reports.

## Configure journaling for IRM-protected messages

In Exchange Information Rights Management (IRM) encrypts messages to control what recipients are permitted to do with them. For example, IRM can be used to prevent recipients from forwarded sensitive messages to other addresses. As you saw in Unit 2, Office Message Encryption (OME) is built on IRM and can encrypt sensitive messages automatically by using policies.

By default, Exchange Online decrypts any IRM- or OME-protected messages before they are attached to journal reports and sent to the journaling mailbox. This behavior might be what you want because it ensures that all messages, including protected messages, reach the journal mailbox. However, you should consider that the journal mailbox will store sensitive emails in plain text and so should be strongly protected.

To find out whether this decryption is currently enabled for your organization, use this command:

```powershell
Get-IRMConfiguration | FL JournalReportDecryptionEnabled
```

If you don't want encrypted messages to be journaled, reconfigure the IRM configuration by using this command :

```powershell
Set-IRMConfiguration -JournalReportDecryptionEnabled $False
```

Remember that encrypted messages will not be journaled with this setting, even when they match a journaling rule. To re-enable decryption, issue the same command with the value `$True`.

## Learn more

- [Journaling in Exchange Online](/exchange/security-and-compliance/journaling/journaling)
- [Manage journaling in Exchange Online](/exchange/security-and-compliance/journaling/manage-journaling)
- [Configure Journaling in Exchange Online](/exchange/security-and-compliance/journaling/configure-journaling)
