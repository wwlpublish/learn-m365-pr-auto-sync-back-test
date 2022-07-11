
Safe Links is a feature in Defender for Office 365 that provides URL scanning and rewriting of inbound email messages in mail flow, and time-of-click verification of URLs and links in email messages and other locations. Safe Links scanning can help protect your organization from malicious links that are used in phishing and other attacks.

Safe Links protection is available in the following locations:

- **Email messages** - Safe Links protection for links in email messages is controlled by Safe Links policies. There is no default Safe Links policy, so to get the protection of Safe Links in email messages, you need to create one or more **Safe Links policies**.

- **Microsoft Teams** - Safe Links protection for links in Teams conversations, group chats, or from channels is also controlled by Safe Links policies. There is no default Safe Links policy, so to get the protection of Safe Links in Teams, you need to create one or more **Safe Links policies**.
  
- **Office 365 apps** - Safe Links protection for Office 365 apps is available in supported desktop, mobile, and web apps. You configure Safe Links protection for Office 365 apps in the **global setting**, which is applied to all users in the organization who are licensed for Defender for Office 365.

## How Safe Links works in Teams

At a high level, here's how Safe Links protection works for URLs in Microsoft Teams:

1. A user starts the Teams app.

2. Microsoft 365 verifies that the user's organization includes Microsoft Defender for Office 365, and that the user is included in an active Safe Links policy where protection for Microsoft Teams is enabled.

3. URLs are validated at the time of click for the user in chats, group chats, channels, and tabs.

After you turn on Safe Links protection for Microsoft Teams, URLs in Teams are checked against a list of known malicious links when the protected user clicks the link (time-of-click protection). URLs are not rewritten. If a link is found to be malicious, users will have the following experiences:

- If the link was clicked in a Teams conversation, group chat, or from channels, the warning page as shown in the following screenshot will appear in the default web browser.

- If the link was clicked from a pinned tab, the warning page will appear in the Teams interface within that tab. The option to open the link in a web browser is disabled for security reasons.

- Depending on how the **Click protection settings** in the policy is configured, the user will or will not be allowed to click through to the original URL. 

If the user who sent the link isn't included in a Safe Links policy where Teams protection is enabled, the user is free to click through to the original URL on their computer or device.

:::image type="icon" source="../media/safe-links-for-teams-malicious-message.png" alt-text="Screenshot of a Safe Links for Teams page reporting a malicious link.":::

Clicking the **Go Back** button on the warning page will return the user to their original context or URL location. However, clicking on the original link again will cause Safe Links to rescan the URL, so the warning page will reappear.

## Enable Safe Links for Microsoft Teams

You can configure Safe Links policies in the Microsoft 365 Defender portal or in PowerShell (Exchange Online PowerShell for eligible Microsoft 365 organizations with mailboxes in Exchange Online; standalone EOP PowerShell for organizations without Exchange Online mailboxes, but with Microsoft Defender for Office 365 add-on subscriptions).

### Use Microsoft 365 Defender portal

You enable or disable Safe Links protection for Microsoft Teams in Safe Links policies.

1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com?azure-portal=true) as a global administrator or security administrator.

2. In the left navigation bar, select **Policies & rules** \> **Threat policies** \> **Policies** section \> **Safe Links**.

3. Select **+ Create** to create new Safe Links policies.

4. On the **Name your policy** page, enter the **Name** and **Description** for the policy.

5. On the **Users and domains** page that appears, identify the internal recipients that the policy applies to. You can specify by **Users**, **Groups**, or **Domains**. 

6. On the **Protection settings** page that appears, configure the following settings:

    * **Action on potentially malicious URLs within Emails**. The recommended value is **On** with the following settings:
        
      |Setting|Recommendation| 
      |--|--|
      |On: Safe Links checks a list of known, malicious links when users click links in email|Selected|
      |Apply Safe Links to email messages sent within the organization| Selected|
      |Apply real-time URL scanning for suspicious links and links that point to files| Selected|
      |Wait for URL scanning to complete before delivering the message| Selected|
      |Do not rewrite URLs, do checks via Safe Links API only| Not selected|
      |Do not rewrite the following URLs in email|No recommendation |

    * **Action for potentially malicious URLs in Microsoft Teams**. The recommended value is **On** with the following settings:
        
      |Setting|Recommendation| 
      |--|--|
      |On: Safe Links checks a list of known, malicious links when users click links at Microsoft Teams|Selected|

    * **Action for potentially malicious URLs in Microsoft Office apps**. The recommended value is **On** with the following settings:
        
      |Setting|Recommendation| 
      |--|--|
      |On: Safe Links checks a list of known, malicious links when users click links in Microsoft Office apps|Selected|

    * **Click protection settings**

      |Setting|Recommendation| 
      |--|--|
      |Track user click|Selected|
      |Let users click through to the original URL|Not selected|
      |Display the organization branding on notification and warning pages|No recommendation|

      :::image type="icon" source="../media/safe-links-policy-settings.png" alt-text="Screenshot of a Safe Links protection settings page.":::

7. On the **Notification** page that appears, select one of the following values for **How would you like to notify your users?**:
   - **Use the default notification text**
   - **Use custom notification text**: If you select this value (the length cannot exceed 200 characters), the following settings appear:
     - **Use Microsoft Translator for automatic localization**
     - **Custom notification text**: Enter the custom notification text in this box.

8. On the **Review** page that appears, review your settings and select **Submit**.


### Use Exchange Online PowerShell

You can also configure safe links policies by using the *-SafeLinksPolicy:

- `New-SafeLinksPolicy`

- `Set-SafeLinksPolicy`

For more information, see:

- [Safe Links settings for Microsoft Teams](/microsoft-365/security/office-365-security/safe-links?azure-portal=true#safe-links-settings-for-microsoft-teams)

- [Set up Safe Links policies in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/set-up-safe-links-policies?azure-portal=true)

- [Safe Links policy settings](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?azure-portal=true#safe-links-policy-settings)

