Safe Links is a feature in Defender for Office 365 that provides URL scanning and rewriting of inbound email messages in mail flow, and time-of-click verification of URLs and links in email messages and other locations. Safe Links scanning can help protect your organization from malicious links that are used in phishing and other attacks.

Safe Links protection is available in the following locations:

- **Email messages** - Safe Links protection for links in email messages is controlled by Safe Links policies. There is no default Safe Links policy, so to get the protection of Safe Links in email messages, you need to create one or more **Safe Links policies**.

- **Microsoft Teams (currently in TAP Preview)** - Safe Links protection for links in Teams conversations, group chats, or from channels is also controlled by Safe Links policies. There is no default Safe Links policy, so to get the protection of Safe Links in Teams, you need to create one or more **Safe Links policies**.
  
- **Office 365 apps** - Safe Links protection for Office 365 apps is available in supported desktop, mobile, and web apps. You configure Safe Links protection for Office 365 apps in the **global setting**, which is applied to all users in the organization who are licensed for Defender for Office 365.

## How Safe Links works in Teams

At a high level, here's how Safe Links protection works for URLs in Microsoft Teams:

1. A user starts the Teams app.

2. Microsoft 365 verifies that the user's organization includes Microsoft Defender for Office 365, and that the user is included in an active Safe Links policy where protection for Microsoft Teams is enabled.

3. URLs are validated at the time of click for the user in chats, group chats, channels, and tabs.

After you turn on Safe Links protection for Microsoft Teams, URLs in Teams are checked against a list of known malicious links when the protected user clicks the link (time-of-click protection). URLs are not rewritten. If a link is found to be malicious, users will have the following experiences:

- If the link was clicked in a Teams conversation, group chat, or from channels, the warning page as shown in the following screenshot will appear in the default web browser.

- If the link was clicked from a pinned tab, the warning page will appear in the Teams interface within that tab. The option to open the link in a web browser is disabled for security reasons.

- Depending on how the **Do not allow users to click through to original URL** setting in the policy is configured, the user will or will not be allowed to click through to the original URL (**Continue anyway (not recommended)** in the screenshot). It is recommended that you enable the **Do not allow users to click through to original URL** setting so users can't click through to the original URL.

If the user who sent the link isn't included in a Safe Links policy where Teams protection is enabled, the user is free to click through to the original URL on their computer or device.

:::image type="content" source="../media/safe-links-for-teams-malicious-message.png" alt-text="A Safe Links for Teams page reporting a malicious link":::

Clicking the **Go Back** button on the warning page will return the user to their original context or URL location. However, clicking on the original link again will cause Safe Links to rescan the URL, so the warning page will reappear.

## Enable Safe Links for Microsoft Teams

You can configure Safe Links policies in the Microsoft 365 Defender portal or in PowerShell (Exchange Online PowerShell for eligible Microsoft 365 organizations with mailboxes in Exchange Online; standalone EOP PowerShell for organizations without Exchange Online mailboxes, but with Microsoft Defender for Office 365 add-on subscriptions).

### Use Microsoft 365 Defender portal

You enable or disable Safe Links protection for Microsoft Teams in Safe Links policies.

1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com?azure-portal=true) as a global administrator or security administrator.

2. In the left navigation bar, select **Policies & rules** \> **Threat policies** \> **Policies** section \> **Safe Links**.

3. Select **+ Create** to create new Safe Links policies.

The following settings in Safe Links policies apply to links in Teams:

- **Select the action for unknown or potentially malicious URLs within Microsoft Teams** setting. The recommended value is **On**.

- **Apply real-time URL scanning for suspicious links and links that point to files**: Enables real-time scanning of links, including links in email messages that point to downloadable content. The recommended value is enabled.
  - **Wait for URL scanning to complete before delivering the message**
    - **Enabled** - Messages that contain URLs are held until scanning is finished. Messages are delivered only after the URLs are confirmed to be safe. This setting is the recommended value.
    - **Disabled** - If URL scanning can't complete, deliver the message anyway.

- **Do not track user clicks**: Enables or disables storing Safe Links click data for URLs clicked in email messages. The recommend value is to leave this setting unselected (to track user clicks).

  URL click tracking for links in email messages sent between internal senders and internal recipients is currently not supported.

- **Do not allow users to click through to original URL**: Allows or blocks users from clicking through the warning page to the original URL. The recommend value is enabled.

    :::image type="content" source="../media/safe-links-policy-settings.png" alt-text="A Safe Links protection settings page":::

The following table shows the recommended settings for two  security levels: **Standard** and **Strict**.

| Protection settings | Default | Standard | Strict |
|---|---|---|---|
|Wait for URL scanning to complete before delivering the message  |Not selected  |Selected  |Selected  |
|Do not track user clicks  |Not selected  |Not selected  |Not selected  |
|Do not let users click through to the original URL  |Not selected  |Selected  |Selected  |

### Use Exchange Online PowerShell

You can also configure safe links policies by using the *-SafeLinksPolicy:

- `New-SafeLinksPolicy`

- `Set-SafeLinksPolicy`

For more information, see:

- [Safe Links settings for Microsoft Teams](/microsoft-365/security/office-365-security/safe-links?azure-portal=true#safe-links-settings-for-microsoft-teams)

- [Set up Safe Links policies in Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/set-up-safe-links-policies?azure-portal=true)

- [Safe Links policy settings](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?azure-portal=true#safe-links-policy-settings)

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”