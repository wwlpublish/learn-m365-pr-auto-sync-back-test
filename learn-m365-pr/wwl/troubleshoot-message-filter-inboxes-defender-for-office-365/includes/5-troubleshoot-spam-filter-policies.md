Out-of-the-box, Exchange Online is configured to quarantine malicious emails and mark bulk emails as spam. You can also use custom spam filter policies to influence the actions it takes. If these actions are wrongly applied to legitimate email, you might need to diagnose and fix the cause.

In the marketing company where you work, large volumes of spam and malicious email are received to public-facing addresses. Exchange administrators have created and tuned several different anti-spam policies that filter out most of this material while delivering legitimate email. However, sometimes emails are quarantined or marked incorrectly, and you have to find the policy that caused the problem and release the quarantined items.

Here, you’ll learn how to release quarantined email and fix problems with anti-spam policies.

## Finding and releasing quarantined messages

If a message has been moved to quarantine, it’s likely to be either because it contains malware, or a spam filter policy has moved it there. Anti-malware policies quarantine a message if any attachment is found to contain malware. In the default configuration, anti-spam policies quarantine phishing messages but deliver spam and bulk email to the user’s **Junk Email** folder. You can alter policies if this behavior is not what you want.

Both users and administrators can investigate quarantined messages and, if they’re incorrectly quarantined, move them to the inbox. This action is also called “releasing a message from quarantine”:

1. In the [Microsoft 365 Defender portal](https://security.microsoft.com), log on and go to **Email & collaboration \> Review \> Quarantine**.
1. Browse through the messages in the list. You can change the order of the mail by selecting a column heading.
1. If there are many quarantined messages, you can filter them by selecting **Filter**, completing some properties to filter by, and then selecting **Apply**. Alternatively, use the **Search** tool.
1. To view more details about a quarantined message, select it in the list. The **Details** pane shows several properties of the message including the **Quarantine reason**.
1. To release the message from quarantine, select **Release email**.

> [!NOTE]
> If you are unable to release a message from the quarantine, it may be because the quarantine policy is configured to prevent you. In this case, contact an administrator to release the message for you.

In the above procedure, Exchange users see messages that were quarantined from their own inbox in the list. Administrators with correct permissions can see messages that were quarantined from any inbox in the Exchange Online organization. Specifically, you must be a member of the **Organization Management**, **Security Administrator**, or **Quarantine Administrator** role groups.

## Troubleshoot anti-spam policies

Exchange Online Protection (EOP) applies anti-spam filter policies to incoming mail to help protect against unsolicited and nuisance emails. There is a default anti-spam policy, which administrators can edit but not remove. You can also add your own extra anti-spam policies and apply them to specific users, group, or domains in your organization. If items are moved to quarantine in error, you might need to investigate the anti-spam filter policies that are in place and determine which one is incorrectly configured.

If you’re using custom policies, they always take precedence over the default policy. You can also configure the priority of custom policies. Create and edit policies by using the Microsoft 365 Defender portal or PowerShell.

Anti-spam policies have two components:

- **Spam filter policy.** This component specifies the actions that the filter takes for different spam verdicts and notifications.
- **Spam filter rule.** This component specifies the policy priority and who the policy applies to.

In the portal, these objects are managed as a single entity but, if you edit them in PowerShell, you must obtain and change them separately.

### Use the Microsoft 365 Defender portal to investigate and modify anti-spam policies

To view and edit anti-spam policies in the Microsoft 365 Defender portal, you will need the following permissions:

- To edit anti-spam policies, you must be a member of the **Organization Management**, or **Security Administrator** role groups.
- To view anti-spam policies, you must be a member of the **Global Reader** or **Security Reader** role groups.

1.  In the [Microsoft 365 Defender portal](https://security.microsoft.com), log on and go to **Email & Collaboration \> Policies & Rules \> Threat policies \> Anti-spam**.
1.  All anti-spam policies in your organization are displayed in the list. When you select a policy, full details are displayed.
1.  To make changes to a policy, select **Edit** in the appropriate section.
1.  To disable a policy, select **Turn off**.
1.  To change the order in which policies are applied, select **Increase priority** or **Decrease priority**.
1.  When your changes are complete, select **Close**.

### Use PowerShell to investigate and modify anti-spam policies

To list the anti-spam filter policies in PowerShell, use this command:

``` powershell
Get-HostedContentFilterPolicy
```

Then, to obtain full details of each policy, use this command:

``` powershell
Get-HostedContentFilterPolicy -Identity "ExecutivesGroupSpamPol"
```

From the filter policies, you can see the actions that the policy will take but not who it will apply to. To find out that information, list the spam filter rules. There should be one rule for each spam filter policy:

``` powershell
Get-HostedContentFilterRule
```

Then, to obtain the list of users and priority for a specific rule, use this command:

``` powershell
Get-HostedContentFilterRule -Identity "ExecutivesGroupSpamPol"
```

When you’ve identified the policy that’s causing the problem, you can delete it. Ensure that you delete both the policy and its corresponding rule:

``` powershell
Remove-HostedContentFilterPolicy -Identity "ExecutiveGroupSpamPol"
Remove-HostedContentFilterRule -Identity "ExecutiveGroupSpamPol"
```

## Learn more

- [Anti-spam protection in EOP](/microsoft-365/security/office-365-security/anti-spam-protection)
- [Configure anti-spam policies in EOP](/microsoft-365/security/office-365-security/configure-your-spam-filter-policies)
- [Quarantined email messages in EOP and Defender for Office 365](/microsoft-365/security/office-365-security/quarantine-email-messages)
- [Find and release quarantined messages as a user in EOP](/microsoft-365/security/office-365-security/find-and-release-quarantined-messages-as-a-user)
- [Manage quarantined messages and files as an admin in EOP](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files)
- [Protect against threats](/microsoft-365/security/office-365-security/protect-against-threats)
