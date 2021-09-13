Safe Links is a feature in Microsoft Defender for Office 365 that provides URL scanning of inbound email messages in mail flow, and time of selection verification of URLs and links in email messages and in other locations. There's no built-in or default Safe Links policy. To get Safe Links scanning of URLs, you must create one or more Safe Links policies. You can configure Safe Links policies in Microsoft 365 Defender or in Windows PowerShell.

The basic elements of a Safe Links policy are:

 -  **The safe links policy**. Turn on Safe Links protection, turn on real-time URL scanning, specify whether to wait for real-time scanning to complete before delivering the message, turn on scanning for internal messages, specify whether to track user selections on URLs, and specify whether to allow users to select trough to the original URL.
 -  **The safe links rule**. Specifies the priority and recipient filters (who the policy applies to).

The difference between these two elements isn't obvious when you manage Safe Links policies in Microsoft 365 Defender:

 -  When you create a Safe Links policy, you're actually creating a safe links rule and the associated safe links policy at the same time using the same name for both.
 -  When you modify a Safe Links policy, settings related to the name, priority, enabled or disabled, and recipient filters modify the safe links rule. All other settings modify the associated safe links policy.
 -  When you remove a Safe Links policy, the safe links rule and the associated safe links policy are removed.

> [!NOTE]
> In Exchange Online PowerShell or standalone EOP PowerShell, you manage the policy and the rule separately. This feature is discussed in the next unit.

### Creating a custom Safe Links policy in Microsoft 365 Defender

Creating a custom Safe Links policy in Microsoft 365 Defender creates the safe links rule and the associated safe links policy at the same time using the same name for both.

1.  In the **Microsoft 365 admin center**, select **Show All** in the left-hand navigation pane, and then under **Admin centers**, select **Security**.<br>
2.  In **Microsoft 365 Defender**, select **Policies & rules** in the left-hand navigation pane.<br>
3.  On the **Policies & rules** page, select **Threat policies**.<br>
4.  On the **Threat policies** page, under the **Policies** section, select **Safe Links.**
5.  On the **Safe Links** page, select **Create**.
6.  The **New Safe Links policy** wizard opens. On the **Name your policy** page, configure the following settings and then select **Next**:
    
     -  **Name.** Enter a unique, descriptive name for the policy.
     -  **Description.** Enter an optional description for the policy.
7.  On the **Users and domains** page, enter **onmicrosoft** in the **Domains** field. In the drop-down list that appears, select the xxxxxZZZZZZ.onmicrosoft.com domain for your organization (where xxxxxZZZZZZ is your tenant prefix), and then select **Next**.
8.  On the **Protection Settings** page that appears, configure the following settings:
    
     -  **Select the action for unknown potentially malicious URLs in messages.** Select **On** to enable Safe Links protection for links in email messages.
     -  **Select the action for unknown or potentially malicious URLs within Microsoft Teams.** Select **On** to enable Safe Links protection for links in Teams.
     -  **Apply real-time URL scanning for suspicious links and links that point to files.** Select this setting to enable real-time scanning of links in email messages.
     -  **Wait for URL scanning to complete before delivering the message.** Select this setting to wait for real-time URL scanning to complete before delivering the message.
     -  **Apply Safe Links to email messages sent within the organization.** Select this setting to apply the Safe Links policy to messages between internal senders and internal recipients.
     -  **Do not track user clicks.** Leave this setting unselected to enable the tracking user selections on URLs in email messages.
     -  **Do not let users click through to the original URL.** Select this setting to block users from selecting through to the original URL in [warning pages](/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
     -  **Display the organization branding on notification and warning pages.** Select this setting to display the organization branding on notification and warning pages. This should help users identify that it’s a legitimate warning they’re seeing, as default Microsoft warning pages are often used by malicious actors to look legitimate themselves.
     -  **Do not rewrite the following URLs.** Allows access the specified URLs that would otherwise be blocked by Safe Links.
        
        In the box, type the URL or value that you want, and then select the **Add** button.
        
        To remove an existing entry, select it and then select the trash can (delete) icon.
        
        For entry syntax, see [Entry syntax for the "Do not rewrite the following URLs" list](/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
    
    For detailed information about these settings, see [Safe Links settings for email messages](/microsoft-365/security/office-365-security/safe-links?azure-portal=true) and [Safe Links settings for Microsoft Teams](/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
    
    For more the recommended values for Standard and Strict policy settings, see [Safe Links policy settings](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?azure-portal=true).
    
    When you're finished, select **Next.**
9.  On the **Notification** page, configure how you would like to notify your users by selecting from the following options, and then select **Next**:
    
     -  **Use the default notification text**
     -  **Use custom notification text**. If you select this option, a field will appear in which you can enter **Custom notification text**.
10. On the **Review** page that appears, review your settings. You can select **Edit** in each section to modify the settings within the section. Or you can select **Back** or select the specific page in the wizard.
    
    When you're finished, select **Submit**.
11. On the **New Safe Links policy created** page, select **Done**.

## **Exercise – Interactive demonstrations**

Select the following links to complete these interactive demonstrations:

 -  [Create a Safe Links policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M2-L2-E2-T1/index.html?azure-portal=true)
 -  [Validate the Safe Links policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M2-L2-E2-T2/index.html?azure-portal=true)

The first simulation guides you through the steps to create a Safe Links policy for the fictitious Adatum Corporation. Because there's no built-in or default Safe Links policy in Microsoft 365, you must create at least one Safe Links policy for Adatum's global Safe Links settings to be active. After creating a Safe Links policy, you'll be shown where to define a company-wide list of blocked URLs in the Safe Links global settings. The blocked URLs and other options defined in the Safe Links global settings are only applied to users who are included in active Safe Links policies.

The second simulation validates a Safe Links policy that prevents users from selecting blocked URLs that appear in email messages. In this simulation, the blocked URL defined in Adatum's Safe Links policy is http://tailspintoys.com. You'll validate that this policy prevents Holly Dickson from navigating to this URL when it appears in an email that Holly receives.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”