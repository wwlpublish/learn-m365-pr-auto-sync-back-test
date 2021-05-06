Safe Links is a feature in Microsoft Defender for Office 365 that provides URL scanning of inbound email messages in mail flow, and time of selection verification of URLs and links in email messages and in other locations. You can configure Safe Links policies in the Security &amp; Compliance Center or in PowerShell.

There's no built-in or default Safe Links policy. To get Safe Links scanning of URLs, you must create one or more Safe Links policies. You can configure Safe Links policies in the Security &amp; Compliance Center or in PowerShell.

The basic elements of a Safe Links policy are:

 -  **The safe links policy**. Turn on Safe Links protection, turn on real-time URL scanning, specify whether to wait for real-time scanning to complete before delivering the message, turn on scanning for internal messages, specify whether to track user selections on URLs, and specify whether to allow users to select trough to the original URL.
 -  **The safe links rule**. Specifies the priority and recipient filters (who the policy applies to).

The difference between these two elements isn't obvious when you manage Safe Links policies in the Security &amp; Compliance Center:

 -  When you create a Safe Links policy, you're actually creating a safe links rule and the associated safe links policy at the same time using the same name for both.
 -  When you modify a Safe Links policy, settings related to the name, priority, enabled or disabled, and recipient filters modify the safe links rule. All other settings modify the associated safe links policy.
 -  When you remove a Safe Links policy, the safe links rule and the associated safe links policy are removed.

> [!NOTE]
> In Exchange Online PowerShell or standalone EOP PowerShell, you manage the policy and the rule separately. This feature is discussed in the next unit.

### Creating a custom Safe Links policy in the SCC

Creating a custom Safe Links policy in the Security &amp; Compliance Center creates the safe links rule and the associated safe links policy at the same time using the same name for both.

1.  In the Security &amp; Compliance Center, go to **Threat management &gt; Policy &gt; ATP Safe Links**.<br>
2.  On the **Safe Links** page, select **Create**.
3.  When you're finished, select **Next**.
4.  The **New Safe Links policy** wizard opens. On the **Name your policy** page, configure the following settings:
    
     -  **Name.** Enter a unique, descriptive name for the policy.
     -  **Description.** Enter an optional description for the policy.
5.  On the **Settings** page that appears, configure the following settings:
    
     -  **Select the action for unknown potentially malicious URLs in messages.** Select On to enable Safe Links protection for links in email messages.
     -  **Select the action for unknown or potentially malicious URLs within Microsoft Teams.** Select On to enable Safe Links protection for links in Teams.
     -  **Apply real-time URL scanning for suspicious links and links that point to files.** Select this setting to enable real-time scanning of links in email messages.
     -  **Wait for URL scanning to complete before delivering the message.** Select this setting to wait for real-time URL scanning to complete before delivering the message.
     -  **Apply Safe Links to email messages sent within the organization.** Select this setting to apply the Safe Links policy to messages between internal senders and internal recipients.
     -  **Do not track user clicks.** Leave this setting unselected to enable the tracking user selections on URLs in email messages.
     -  **Do not allow users to click through to original URL.** Select this setting to block users from selecting through to the original URL in [warning pages](https://docs.microsoft.com/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
     -  **Do not rewrite the following URLs.** Allows access the specified URLs that would otherwise be blocked by Safe Links.
        
        In the box, type the URL or value that you want, and then select the plus sign (+).
        
        To remove an existing entry, select it and then select the trash can (delete) icon.
        
        For entry syntax, see [Entry syntax for the "Do not rewrite the following URLs" list](https://docs.microsoft.com/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
    
    For detailed information about these settings, see [Safe Links settings for email messages](https://docs.microsoft.com/microsoft-365/security/office-365-security/safe-links?azure-portal=true) and [Safe Links settings for Microsoft Teams](https://docs.microsoft.com/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
    
    For more the recommended values for Standard and Strict policy settings, see [Safe Links policy settings](https://docs.microsoft.com/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?azure-portal=true).
    
    When you're finished, select **Next.**
6.  On the **Applied to** page that appears, identify the internal recipients that the policy applies to.
    
    You can only use a condition or exception once, but you can specify multiple values for the condition or exception. Multiple values of the same condition or exception use OR logic (for example, *&lt;recipient1&gt;* or *&lt;recipient2&gt;*). Different conditions or exceptions use AND logic (for example, *&lt;recipient1&gt;* and *&lt;member of group 1&gt;*).
    
    Select **Add a condition**. In the dropdown that appears, select a condition under **Applied if**:
    
     -  **The recipient is.** Specifies one or more mailboxes, mail users, or mail contacts in your organization.
     -  **The recipient is a member of.** Specifies one or more groups in your organization.
     -  **The recipient domain is.** Specifies recipients in one or more of the configured accepted domains in your organization.
    
    After you select the condition, a corresponding dropdown appears with a box titled **Any of these.**
    
     -  Select in the box and scroll through the list of values to select.
     -  Select in the box and start typing to filter the list and select a value.
     -  To add other values, select in an empty area in the box.
     -  To remove individual entries, select **Remove** on the value.
     -  To remove the whole condition, select **Remove** on the condition.
    
    To add another condition, select **Add a condition** and select a remaining value under **Applied if**.
    
    To add exceptions, select **Add a condition** and select an exception under **Except if**. The settings and behavior are exactly like the conditions.
    
    When you're done, select **Next**.
7.  On the **Review your settings** page that appears, review your settings. You can select **Edit** on each setting to modify it. When you're finished, select **Finish**.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”