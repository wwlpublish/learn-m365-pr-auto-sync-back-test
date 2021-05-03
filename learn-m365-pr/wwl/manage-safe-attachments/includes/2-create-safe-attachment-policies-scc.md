Safe Attachments is a feature in Microsoft Defender for Office 365. It uses a virtual environment to check attachments in inbound email messages after they've been scanned by anti-malware protection in Exchange Online Protection (EOP), but before delivery to recipients.

There's no built-in or default Safe Attachments policy. To get Safe Attachments scanning of email message attachments, you must create one or more Safe Attachments policies. You can configure Safe Attachments policies in the Security &amp; Compliance Center or in PowerShell.

The basic elements of a Safe Attachments policy are:

 -  **The safe attachment policy.** Specifies the actions for unknown malware detections, whether to send messages with malware attachments to a specified email address, and whether to deliver messages if Safe Attachments scanning can't complete.
 -  **The safe attachment rule.** Specifies the priority and recipient filters (who the policy applies to).

The difference between these two elements isn't obvious when you manage Safe Attachments policies in the Security &amp; Compliance Center:

 -  When you create a Safe Attachments policy, you're actually creating a safe attachment rule and the associated safe attachment policy at the same time using the same name for both.
 -  When you modify a Safe Attachments policy, settings related to the name, priority, enabled or disabled, and recipient filters modify the safe attachment rule. All other settings modify the associated safe attachment policy.
 -  When you remove a Safe Attachments policy, the safe attachment rule and the associated safe attachment policy are removed.

In Exchange Online PowerShell or standalone EOP PowerShell, you manage the policy and the rule separately. This feature is discussed in the next unit.

### Creating a custom Safe Attachments policy in the SCC

Creating a custom Safe Attachments policy in the Security &amp; Compliance Center creates the safe attachment rule and the associated safe attachment policy at the same time using the same name for both.

1.  In the Security &amp; Compliance Center, go to **Threat management &gt; Policy &gt; ATP Safe Attachments.**
2.  On the **Safe Attachments** page, select Create.
3.  The **New Safe Attachments policy** wizard opens. On the **Name your policy** page, configure the following settings:
    
     -  **Name.** Enter a unique, descriptive name for the policy.
     -  **Description.** Enter an optional description for the policy.
    
    When you're finished, select **Next**.
4.  On the **Settings** page that appears, configure the following settings:
    
     -  **Safe Attachments unknown malware response.** Select one of the following values:
        
         -  **Off.** Attachments aren't scanned for malware by Safe Attachments. Messages are still scanned for malware by [anti-malware protection in EOP](https://docs.microsoft.com/microsoft-365/security/office-365-security/anti-malware-protection?azure-portal=true). Typically, it's not recommended that you select this value.
         -  **Monitor.** Delivers messages with attachments and then tracks what happens with detected malware. Delivery of safe messages may be delayed because of Safe Attachments scanning.
         -  **Block.** Prevents messages with detected malware attachments from being delivered. Messages are quarantined where only admins (not end users) can review, release, or delete the messages. Automatically blocks future instances of the messages and attachments. Delivery of safe messages may be delayed because of Safe Attachments scanning. Block is the default and recommended value.
         -  **Replace.** Removes detected malware attachments and notifies recipients that attachments have been removed. Messages are quarantined where only admins (not end users) can review, release, or delete the messages. Delivery of safe messages may be delayed because of Safe Attachments scanning.
         -  **Dynamic Delivery (Preview Feature).** Delivers messages immediately, but replaces attachments with placeholders until Safe Attachments scanning is complete.
        
        These values are explained in greater detail in [Safe Attachments policy settings](https://docs.microsoft.com/microsoft-365/security/office-365-security/safe-attachments?view=o365-worldwide#safe-attachments-policy-settings?azure-portal=true).
     -  **Send the attachment to the following email address.** For the action values Block, Monitor, or Replace, you can select **Enable redirect** to send messages that contain malware attachments to the specified internal or external email address for analysis and investigation.
        
        The recommendation for Standard and Strict policy settings is to enable redirection. For more information, see [Safe Attachments settings](https://docs.microsoft.com/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?view=o365-worldwide#safe-attachments-settings?azure-portal=true).
     -  **Apply the above selection if malware scanning for attachments times out or error occurs.** The action specified by **Safe Attachments unknown malware response** is taken on messages even when Safe Attachments scanning can't complete. If you selected this option, always select **Enabled redirect**; otherwise, messages may be lost.
    
    When you're finished, select **Next**.
5.  On the **Applied to** page that appears, identify the internal recipients that the policy applies to.
    
    You can only use a condition or exception once, but you can specify multiple values for the condition or exception. Multiple values of the same condition or exception use OR logic (for example, *&lt;recipient1&gt;* or *&lt;recipient2&gt;*). Different conditions or exceptions use AND logic (for example, *&lt;recipient1&gt;* and *&lt;member of group 1&gt;*).
    
    Select **Add a condition**. In the dropdown that appears, select a condition under **Applied if**:
    
     -  **The recipient is.** Specifies one or more mailboxes, mail users, or mail contacts in your organization.
     -  **The recipient is a member of.** Specifies one or more groups in your organization.
     -  **The recipient domain is.** Specifies recipients in one or more of the configured accepted domains in your organization.
    
    After you select the condition, a corresponding dropdown appears with box titled **Any of these.**
    
     -  Select in the box and scroll through the list of values to select.
     -  Select in the box and start typing to filter the list and select a value.
     -  To add other values, select in an empty area in the box.
     -  To remove individual entries, select **Remove** on the value.
     -  To remove the whole condition, select **Remove** on the condition.
    
    To add another condition, select **Add a condition** and select a remaining value under "**Applied if"**.
    
    To add exceptions, select **Add a condition** and select an exception under **Except if.** The settings and behavior are exactly like the conditions.
    
    When you're finished, select **Next**.
6.  On the **Review your settings** page that appears, review your settings. You can select **Edit** on each setting to modify it.
    
    When you're done, select **Finish**.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”