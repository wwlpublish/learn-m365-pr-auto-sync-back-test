Safe Attachments is a feature in Microsoft Defender for Office 365. It uses a virtual environment to check attachments in inbound email messages after they've been scanned by anti-malware protection in Exchange Online Protection (EOP), but before delivery to recipients.

There's no built-in or default Safe Attachments policy. To get Safe Attachments scanning of email message attachments, you must create one or more Safe Attachments policies. You can configure Safe Attachments policies in Microsoft 365 Defender or in Windows PowerShell.

The basic elements of a Safe Attachments policy are:

 -  **The safe attachment policy.** Specifies the actions for unknown malware detections, whether to send messages with malware attachments to a specified email address, and whether to deliver messages if Safe Attachments scanning can't complete.
 -  **The safe attachment rule.** Specifies the priority and recipient filters (who the policy applies to).

The difference between these two elements isn't obvious when you manage Safe Attachments policies in Microsoft 365 Defender:

 -  When you create a Safe Attachments policy, you're actually creating a safe attachment rule and the associated safe attachment policy at the same time using the same name for both.
 -  When you modify a Safe Attachments policy, settings related to the name, priority, enabled or disabled, and recipient filters modify the safe attachment rule. All other settings modify the associated safe attachment policy.
 -  When you remove a Safe Attachments policy, the safe attachment rule and the associated safe attachment policy are removed.

In Exchange Online PowerShell or standalone EOP PowerShell, you manage the policy and the rule separately. This feature is discussed in the next unit.

### Creating a custom Safe Attachments policy in Microsoft 365 Defender

Creating a custom Safe Attachments policy in Microsoft 365 Defender creates the safe attachment rule and the associated safe attachment policy at the same time using the same name for both.

1.  In the **Microsoft 365 admin center**, select **Show All** in the left-hand navigation pane, and then under **Admin centers**, select **Security**.<br>
2.  In **Microsoft 365 Defender**, select **Policies & rules** in the left-hand navigation pane.<br>
3.  On the **Policies & rules** page, select **Threat policies**.<br>
4.  On the **Threat policies** page, under the **Policies** section, select **Safe Attachments.**
5.  On the **Safe Attachments** page, select **Create**.
6.  The **New Safe Attachments policy** wizard opens. On the **Name your policy** page, configure the following settings:
    
     -  **Name.** Enter a unique, descriptive name for the policy.
     -  **Description.** Enter an optional description for the policy.
7.  On the **Users and domains** page, enter **onmicrosoft** in the **Domains** field. In the drop-down list that appears, select the xxxxxZZZZZZ.onmicrosoft.com domain for your organization (where xxxxxZZZZZZ is your tenant prefix), and then select **Next**.
8.  On the **Settings** page that appears, configure the following settings and then select **Next**:
    
     -  **Safe Attachments unknown malware response.** Select one of the following values:
        
         -  **Off.** Attachments aren't scanned for malware by Safe Attachments. Messages are still scanned for malware by [anti-malware protection in EOP](/microsoft-365/security/office-365-security/anti-malware-protection?azure-portal=true). Typically, it's not recommended that you select this value.
         -  **Monitor.** Delivers messages with attachments and then tracks what happens with detected malware. Delivery of safe messages may be delayed because of Safe Attachments scanning.
         -  **Block.** Prevents messages with detected malware attachments from being delivered. Messages are quarantined where only admins (not end users) can review, release, or delete the messages. Automatically blocks future instances of the messages and attachments. Delivery of safe messages may be delayed because of Safe Attachments scanning. Block is the default and recommended value.
         -  **Replace.** Removes detected malware attachments and notifies recipients that attachments have been removed. Messages are quarantined where only admins (not end users) can review, release, or delete the messages. Delivery of safe messages may be delayed because of Safe Attachments scanning.
         -  **Dynamic Delivery (Preview Feature).** Delivers messages immediately, but replaces attachments with placeholders until Safe Attachments scanning is complete.
        
        These values are explained in greater detail in [Safe Attachments policy settings](/microsoft-365/security/office-365-security/safe-attachments?azure-portal=true).
     -  **Redirect messages with detected attachments.** If you select Enable redirect, you can specify an email address in the Send messages that contain blocked, monitored, or replaced attachments to the specified email address box to send messages that contain malware attachments for analysis and investigation.<br><br>The recommendation for Standard and Strict policy settings is to enable redirection. For more information, see [Safe Attachments settings](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?azure-portal=true).
     -  **Apply the Safe Attachments detection response if scanning can't complete (timeout or errors).** The action specified by Safe Attachments unknown malware response is taken on messages even when Safe Attachments scanning can't complete. If you select this option, always select **Enable redirect** and specify an email address to send messages that contain malware attachments; otherwise, messages may be lost.
9.  On the **Review** page that appears, review your settings. You can select **Edit** in each section to modify the settings within the section. Or you can select **Back** or select the specific page in the wizard. When you're finished, select **Submit**.
10. On the **New Safe Attachments policy created** page, select **Done**.

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Create a Safe Attachment policy and turn on advanced threat protection for SharePoint, OneDrive, and Microsoft Teams](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M2-L2-E1-T1/index.html?azure-portal=true).

This simulation guides you through the steps to turn on Windows Defender for Office 365 for the fictitious Adatum Corporation. Windows Defender for Office 365 provides advanced threat protection (ATP) for SharePoint, OneDrive, and Microsoft Teams. This simulation also instructs you on how to create a Safe Attachments policy that tests email attachments for malware that are sent to recipients within Adatum's onmicrosoft.com domain. You'll configure the policy so that if an attachment is blocked, it will be removed from the email that's sent to the recipient, and a copy of the email will be redirected to Joni Sherman for additional review.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”