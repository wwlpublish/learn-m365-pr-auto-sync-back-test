Files attached to emails can cause two problems. Very large files are blocked to prevent single messages from monopolizing server resources. Attachments may also be blocked because they contain malicious code or content. You might need to help users access attachments that have been blocked.

In the marketing company where you work, video files are sometimes exchanged as email attachments. Also, partner organizations may send materials they’re working on in Office document attachments. Sometimes, your users cannot open the files they have been sent, or the emails do not arrive. You must find out what causes these problems and reconfigure the system if attachments are blocked inappropriately.

Here, you’ll learn why Exchange Online may block an attachment, and how to configure the system to ensure security while enabling users to receive data.

## Message and attachment size limits

Email systems were originally designed to transmit messages with relatively small quantities of plain text. When clients and protocols evolved to permit users to attach files to emails, the size of emails grew – but email is still not the best method to transfer large files. When users attach large files to emails, it can cause unnecessary load on email servers and impact on the prompt delivery of other email.

Users should be encouraged to upload large files to a dedicated transfer application, such as One Drive, and then email a link to their colleagues, instead of using an attachment. However, end users may be unaware of the size of a file they want to send, and you can’t train users outside of your organization. Therefore, you should expect large email attachments to cause problems for users occasionally.

Exchange Online imposes system limits on the size of messages. These limits include:

- Message size limit for plain text messages: 150MB.
- Message size limit for encrypted messages: 25MB.
- Number of attachments: 250.
- File attachment size limit: 150MB.

Any messages that exceed these limits will not be delivered and the sender will receive a Non-Delivery Report (NDR).

> [!NOTE]
> For full information about email and attachment size limits, see **Message limits** in **Learn More** below.

## Safe Attachments policies

If you’re using Microsoft Defender for Office 365, you have extra protection against attacks contained in email attachments: the Safe Attachments feature. All emails in Exchange Online are scanned by Exchange Online Protection (EOP) before they’re delivered to inboxes. After that scan, Defender for Office 365 has a virtual environment where it can execute attachments to test their actions. This process is known as **detonation**. Mails with attachments that pass this test will be delivered to their destination.

Safe Attachments can prevent email with problematic attachments from reaching the user. You might need to troubleshoot an attachment that isn’t delivered, or configure the Safe Attachment policies that govern this process.

In the default Defender for Office 365 configuration, there is no extant Safe Attachments policy but the built-in protection preset security includes Safe Attachments protection. This protection is always present as a back stop. For example, if you create a new Safe Attachment policy and apply it only to administrators, other users continue to receive the built-in protection.

If you create a Safe Attachments policy, you can filter it to apply to specific users, groups, or domains. You can also specify a priority that determines the policy that applies if there’s more than one for a given user.

A key setting for a Safe Attachments policy is the response. You can choose from:

- **Off.** Attachments are not detonated, and Safe Attachments is not applied.
- **Monitor.** Messages are delivered with their attachments. Defender for Office monitors what happens with the detected malware.
- **Block.** Messages with malware attachments are quarantined. Future emails with the same attachments are immediately quarantined without testing.
- **Replace.** Malware attachments are replaced before the message is delivered. The recipient is told about the replacement. The original message and its attachment is quarantined.
- **Dynamic Delivery.** Messages are delivered immediately but attachments are swapped with placeholders until Safe Attachments testing is complete.

### Use the Microsoft 365 Defender portal to investigate and modify Safe Attachments policies

If messages with attachments are not reaching their intended destination, the problem might be the configuration of Safe Attachments. You will need the following permissions:

- To edit Safe Attachments policies, you must be a member of the **Organization Management**, or **Security Administrator** role groups.
- To view Safe Attachments policies, you must be a member of the **Global Reader** or **Security Reader** role groups.

You can view the Safe Attachments policies in the Microsoft 365 Defender portal:

1.  In the [Microsoft 365 Defender portal](https://security.microsoft.com), log on and go to **Email & Collaboration \> Policies & Rules \> Threat policies \> Safe Attachments**.
1.  All Safe Attachments policies in your organization are displayed in the list. When you select a policy, full details are displayed.
1.  To make changes to a policy, select **Edit** in the appropriate section.
1.  To disable a policy, select **Turn off**.
1.  To change the order in which policies are applied, select **Increase priority** or **Decrease priority**.
1.  When your changes are complete, select **Close**.

### Use PowerShell to investigate and modify Safe Attachments policies

In PowerShell, Safe Attachments policies are presented as separate objects from Safe Attachments rules, which determine who the policy applies to.

To list Safe Attachment policies in PowerShell, use this command:

``` powershell
Get-SafeAttachmentPolicy
```

Then, you can obtain full details of each policy and its corresponding rule using its name:

``` powershell
Get-SafeAttachmentPolicy -Identity "Sales Staff Attachments"
Get-SafeAttachmentRule -Identity "Sales Staff Attachments"
```

When you’ve identified the policy that is causing the problem, you can delete it. Ensure that you delete both the policy and its corresponding rule:

``` powershell
Remove-SafeAttachmentPolicy -Identity "Sales Staff Attachments"
Remove-SafeAttachmentRule -Identity "Sales Staff Attachments"
```

## Access to attachments in Outlook on the web

Outlook on the web is an application that enables users to access their email from a browser. Users can check their inbox from almost any computer with an internet connection and a web browser. This can be helpful if you’re on a client’s site, in an internet cafe, or some other location without access to your computer or devices.

As an administrator, you can control what users can do with attachments when they log in to Outlook on the web. For example, when they log in from a computer on a public network, such as an internet cafe, you might want to prevent them from saving attachments locally, in case these files contain sensitive information and remain on the cafe computer after the session. You can control attachment access by using public attachment handling.

Public attachment handling settings can confuse users, who may be surprised that they can’t access an attachment and request support. If this behavior is what you want, you can troubleshoot the problem by advising the user to access their mailbox from their own device or computer using Outlook. You should explain why attachments are blocked in Outlook on the web.

If the behavior is not what you want, and users of Outlook on the web should have access to attachments, you can the `Get-OwaMailboxPolicy` cmdlet to investigate the configuration. Use the following command to list the policies:

``` powershell
Get-OwaMailboxPolicy | Format-Table Name
```

Then, to view the details of a policy, use this command:

``` powershell
Get-OwaMailboxPolicy -Identity default-owa-policy
```

## Learn more

- [Message limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits)
- [Safe Attachments in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/safe-attachments)
- [Set up Safe Attachments policies in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/set-up-safe-attachments-policies)
- [Public attachment handling in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/public-attachment-handling)
