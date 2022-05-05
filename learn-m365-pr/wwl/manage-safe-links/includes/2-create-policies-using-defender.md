Safe Links is a feature in Microsoft Defender for Office 365 that provides URL scanning of inbound email messages in mail flow. It also provides time of selection verification of URLs and links in email messages and in other locations. There's no built-in or default Safe Links policy. To get Safe Links scanning of URLs, you must create one or more Safe Links policies.

Safe Links scans incoming email for known malicious hyperlinks. Scanned URLs are rewritten using the Microsoft standard URL prefix: **https://nam01.safelinks.protection.outlook.com**. After the link is rewritten, it's analyzed for potentially malicious content.

After Safe Links rewrites a URL, the URL remains rewritten even if the message is *manually* forwarded or replied to (both to internal and external recipients). Other links that are added to the forwarded or replied-to message aren't rewritten. However, when *automatic* forwarding by Inbox rules or SMTP forwarding is employed, the URL won't be rewritten in the message that's intended for the final recipient *unless* that recipient is also protected by Safe Links, or the URL had already been rewritten in a previous communication.

As long as Safe Links is enabled, URLs are still scanned prior to delivery, regardless of whether they were rewritten or not. Unwrapped URLs will also still be checked by a client-side API call to Safe Links at the time of selection in Outlook for Desktop version 16.0.12513 or later.

You can configure Safe Links policies in the Microsoft 365 Defender portal or in PowerShell (Exchange Online PowerShell for eligible Microsoft 365 organizations with mailboxes in Exchange Online; standalone EOP PowerShell for organizations without Exchange Online mailboxes, but with Microsoft Defender for Office 365 add-on subscriptions).

The basic elements of a Safe Links policy are:

 -  **The Safe Links policy**. The options that can be configured within a Safe Links policy include:
    
     -  Turn on Safe Links protection.
     -  Turn on real-time URL scanning.
     -  Specify whether to wait for real-time scanning to complete before delivering the message.
     -  Turn on scanning for internal messages.
     -  Specify whether to track user selections on URLs.
     -  Specify whether to allow users to select trough to the original URL.
 -  **The Safe Links rule**. Specifies the priority and recipient filters (who the policy applies to).

The difference between these two elements isn't obvious when you manage Safe Links policies in Microsoft 365 Defender:

 -  When you create a Safe Links policy, you're actually creating a safe links rule and the associated safe links policy at the same time using the same name for both.
 -  When you modify a Safe Links policy, settings related to the name, priority, enabled or disabled, and recipient filters modify the safe links rule. All other settings modify the associated safe links policy.
 -  When you remove a Safe Links policy, the safe links rule and the associated safe links policy are removed.

> [!NOTE]
> In Exchange Online PowerShell or standalone EOP PowerShell, you manage the policy and the rule separately. This feature is discussed in the next unit.

To create, modify, and delete Safe Links policies, you must be a member of:

 -  The Organization Management or Security Administrator role groups in the Microsoft 365 Defender portal.
 -  The Organization Management role group in Exchange Online.

### Creating a custom Safe Links policy in Microsoft 365 Defender

Creating a custom Safe Links policy in Microsoft 365 Defender creates the safe links rule and the associated safe links policy at the same time using the same name for both.

1.  In the **Microsoft 365 admin center**, select **Show All** in the left-hand navigation pane, and then under **Admin centers**, select **Security**.
2.  In **Microsoft 365 Defender**, select **Policies and rules** in the left-hand navigation pane.
3.  On the **Policies and rules** page, select **Threat policies**.
4.  On the **Threat policies** page, under the **Policies** section, select **Safe Links.**
5.  On the **Safe Links** page, select **Create**.
6.  The **New Safe Links policy** wizard opens. On the **Name your policy** page, configure the following settings and then select **Next**:
    
     -  **Name.** Enter a unique, descriptive name for the policy.
     -  **Description.** Enter an optional description for the policy.
7.  On the **Users and domains** page, enter **onmicrosoft** in the **Domains** field. In the drop-down list that appears, select the xxxxxZZZZZZ.onmicrosoft.com domain for your organization (where xxxxxZZZZZZ is your tenant prefix), and then select **Next**.
8.  On the **Protection Settings** page that appears, configure the following settings:
    
     -  **On: Safe Links checks a list of known, malicious links when users click links in email.** Enables or disables Safe Links scanning in email messages. The recommended value is selected (On), which results in the following actions:
        
         -  Safe Links scanning is enabled in Outlook (C2R) on Windows.
         -  URLs are rewritten and users are routed through Safe Links protection when they select URLs in messages.
         -  When selected, URLs are checked against a list of known malicious URLs and the ["Block the following URLs" list](/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
         -  URLs that don't have a valid reputation are detonated asynchronously in the background.
        
        The following settings are available only if Safe Links scanning is on in email messages:
        
         -  **Apply Safe Links to email messages sent within the organization**. Enables or disables Safe Links scanning on messages sent between internal senders and internal recipients within the same Exchange Online organization. The recommended value is selected (on).
         -  **Apply real-time URL scanning for suspicious links and links that point to files**. Enables real-time scanning of links, including links in email messages that point to downloadable content. The recommended value is selected (on).
         -  **Wait for URL scanning to complete before delivering the message**:
            
             -  **Selected (On)**. Messages that contain URLs are held until scanning is finished. Messages are delivered only after the URLs are confirmed to be safe. This option is the recommended value.
             -  **Not selected (Off)**. If URL scanning can't complete, deliver the message anyway.
         -  **Do not rewrite URLs, do checks via SafeLinks API only**. If this setting is enabled, no URL wrapping takes place. Safe Links is called exclusively throughAPIs at the time of URL selection by Outlook clients that support it. The recommend value is **Disabled**.
     -  **Track user clicks**. Enables or disables storing Safe Links selection data for URLs that are selected in email messages. The recommend value is to leave this setting selected (track user clicks).
        
        URL selection tracking for links in email messages sent between internal senders and internal recipients is currently not supported.
     -  **Let users click through to the original URL**. Allows or blocks users from clicking through the [warning page](/microsoft-365/security/office-365-security/safe-links?azure-portal=true) to the original URL. The recommend value is disabled.
     -  **Display the organization branding on notification and warning pages**. This option shows your organization's branding on warning pages. Branding helps users identify legitimate warnings, because default Microsoft warning pages are often used by attackers. For more information about customized branding, see [Customize the Microsoft 365 theme for your organization](/microsoft-365/admin/setup/customize-your-organization-theme?azure-portal=true).
        
        For more information about the recommended values for Standard and Strict policy settings for Safe Links policies, see [Safe Links policy settings](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?azure-portal=true).
     -  **Recipient filters**. You need to specify the recipient conditions and exceptions that determine who the policy applies to. You can use these properties for conditions and exceptions:
        
         -  **The recipient is.**
         -  **The recipient domain is.**
         -  **The recipient is a member of.**
        
        You can only use a condition or exception once, but the condition or exception can contain multiple values. Multiple values of the same condition or exception use OR logic (for example, \[recipient1\] or \[recipient2\]). Different conditions or exceptions use AND logic (for example, \[recipient1\] and \[member of group1\]).
     -  **Priority**. If you create multiple policies, you can specify the order that they're applied. No two policies can have the same priority, and policy processing stops after the first policy is applied.
        
        For more information about the order of precedence and how multiple policies are evaluated and applied, see [Order and precedence of email protection](/microsoft-365/security/office-365-security/how-policies-and-protections-are-combined?azure-portal=true).
    
    When you're finished, select **Next.**
9.  On the **Notification** page, configure how you would like to notify your users by selecting from the following options, and then select **Next**:
    
     -  **Use the default notification text.**
     -  **Use custom notification text**. If you select this option, a field will appear in which you can enter **Custom notification text**.
10. On the **Review** page that appears, review your settings. You can select **Edit** in each section to modify the settings within the section. Or you can select **Back** or select the specific page in the wizard.
    
    When you're finished, select **Submit**.
11. On the **New Safe Links policy created** page, select **Done**.

## **Exercise – Interactive demonstrations**

Select the following links to complete these interactive demonstrations:

 -  [Create a Safe Links policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M2-L2-E2-T1/index.html?azure-portal=true).
 -  [Validate the Safe Links policy](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M2-L2-E2-T2/index.html?azure-portal=true).

The first simulation guides you through the steps to create a Safe Links policy for the fictitious Adatum Corporation. Because there's no built-in or default Safe Links policy in Microsoft 365, you must create at least one Safe Links policy for Adatum's global Safe Links settings to be active. After creating a Safe Links policy, you'll be shown where to define a company-wide list of blocked URLs in the Safe Links global settings. The blocked URLs and other options defined in the Safe Links global settings are only applied to users who are included in active Safe Links policies.

The second simulation validates a Safe Links policy that prevents users from selecting blocked URLs that appear in email messages. In this simulation, the blocked URL defined in Adatum's Safe Links policy is http://tailspintoys.com. You'll validate that this policy prevents Holly Dickson from navigating to this URL when it appears in an email that Holly receives.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”