Safe Links is a feature in Microsoft Defender for Office 365 that provides:

 -  URL scanning and rewriting of inbound email messages in mail flow.
 -  Time-of-click verification of URLs and links in email messages and other locations.

Safe Links scanning occurs in addition to the regular anti-spam and anti-malware protection in inbound email messages in Exchange Online Protection (EOP). Safe Links scanning can help protect your organization from malicious links that are used in phishing and other attacks.

When an email with an embedded URL is delivered to a recipient, the web page or attachment on the other side of the link may be safe to view at the time of delivery. However, it may not be safe when the user opens the email and selects the link. Safe Links protects the user by rewriting the link in the message body. By doing so, the link is checked at the time it’s selected, rather than when the message is delivered.

When a user selects a link in a message or document, Safe Links checks to see if the link is malicious. It does so by redirecting the URL to a secure server in the Microsoft 365 environment that checks the URL against a blocklist of known malicious web sites.

 -  If the site is safe, the browser is redirected to the original destination web site.
 -  If the site is on the blocklist, the user is blocked from continuing to the site, and the browser displays a warning page like the image below.

:::image type="content" source="../media/malicious-website-warning-cc2435da.png" alt-text="Screenshot of the warning message saying the website is classified as malicious.":::


Safe Links is selective enough to remove only malicious links. Even within a single email, only the malicious links will be removed. If there are other links that are safe, the user can select them and navigate to the target websites without interference.

Like Safe Attachments, Safe Links protects your organization according to policies that are created by your security administrators. You can create and configure policies and apply them to specific people, groups, or domains.

The following graphic shows how malicious links are rewritten while in transport by Microsoft Defender for Office 365. If a recipient opens a dangerous link, they connect to Defender and aren't redirected to the original target.

:::image type="content" source="../media/rewrite-malicious-links-31eef935.jpg" alt-text="Diagram showing the fact that malicious links are rewritten while in transport, and if a recipient opens a dangerous link, they connect to Defender for Office 365 and aren't redirected to the original target.":::


Safe Links protection is available in the following locations:

 -  **Email messages**. Similar to Safe Attachments, there's no default Safe Links policy. However, the **Built-in protection** preset security policy provides Safe Links protection to all recipients (users who aren't defined in custom Safe Links policies). Organizations can also create Safe Links policies that apply to specific users, group, or domains.
 -  **Microsoft Teams**. Safe Links protection for links in Teams conversations, group chats, or from channels also controlled by Safe Links policies.
 -  **Office 365 apps**. Safe Links protection for Office 365 apps is available in supported desktop, mobile, and web apps. You configure Safe Links protection for Office 365 apps in the global setting that are outside of Safe Links policies. Safe Links protection for Office 365 apps is applied to all users in the organization who are licensed for Microsoft Defender for Office 365. This protection applies even if the users aren't included in active Safe Links policies.

### URL detonation

URL detonation is a capability that combines elements of Safe Links and Safe Attachments into a single feature. This feature protects users in the event a link points to a malicious file on a web server. When a user selects a link to a file on a web server, the file is downloaded into the Safe Attachments sandbox environment and run (or "detonated").

As the content is being analyzed, a web page is presented to the user explaining that a scan is in process. If the file is ultimately determined to be malicious, then the user is redirected to a warning page advising the user that the site is malicious.

:::image type="content" source="../media/warning-message-link-being-scanned-6f246446.png" alt-text="Screenshot of the warning message saying this link is being scanned.":::


### Suspicious message warning

When a user selects a URL in an email message that's similar to other suspicious messages, Safe Links displays the following warning message. Users should be instructed to double-check the email message before proceeding to the site.

:::image type="content" source="../media/warning-message-suspicious-message-5b659036.png" alt-text="Screenshot of the warning message saying a link was selected from a suspicious message.":::


### Safe Links scenarios

The following table describes common scenarios for Safe Links in Microsoft 365 and Office 365 organizations that include Microsoft Defender for Office 365.

:::row:::
  :::column:::
    **Scenario**
  :::column-end:::
  :::column:::
    **Result**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Jean is a member of the Marketing department. Safe Links protection for Office 365 apps is turned on in the global settings for Safe Links. A Safe Links policy that applies to members of the Marketing department also exists. Jean opens a PowerPoint presentation in an email message, and then selects a URL in the presentation.
  :::column-end:::
  :::column:::
    Jean is protected by Safe Links.

Jean is included in a Safe Links policy. Safe Links protection for Office 365 apps is also turned on.For more information about the requirements for Safe Links protection in Office 365 apps, see [Safe Links settings for Office 365 apps](/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Chris' Microsoft 365 E5 organization has no Safe Links policies configured. Chris receives an email from an external sender that contains a URL to a malicious website that he ultimately selects.
  :::column-end:::
  :::column:::
    Chris isn't protected by Safe Links. At least one Safe Links policy must be created for anyone to get Safe Links protection in inbound email messages. Chris must be included in the conditions of a policy to get Safe Links protection.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    In Pat's organization, no admins have created any Safe Links policies. However, Safe Links protection for Office 365 apps is turned on. Pat opens a Word document and selects a URL in the file.
  :::column-end:::
  :::column:::
    Pat isn't protected by Safe Links. Safe Links protection for Office 365 apps is turned on globally. However, at least one Safe Links policy must be created for anyone to get Safe Links protection. Since no Safe Links policies have been created, Pat isn't eligible for Safe Links protection.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    In Lee's organization, https://tailspintoys.com is configured in the **Block the following URLs** list in the global settings for Safe Links. A Safe Links policy that includes Lee already exists. Lee receives an email message that contains the URL https://tailspintoys.com/aboutus/trythispage. Lee selects the URL.
  :::column-end:::
  :::column:::
    The URL may be automatically blocked for Lee; it depends on the URL entry in the list and the email client Lee used. For more information, see ["Block the following URLs" list for Safe Links](/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Jamie and Julia both work for contoso.com. A long time ago, admins configured Safe Links policies that apply to both Jamie and Julia. Jamie sends an email to Julia, not knowing the email contains a malicious URL.
  :::column-end:::
  :::column:::
    Julia is protected by Safe Links if the Safe Links policy that applies to her is configured to apply to messages between internal recipients. For more information, see [Safe Links settings for email messages](/microsoft-365/security/office-365-security/safe-links?azure-portal=true).
  :::column-end:::
:::row-end:::


## Knowledge check<br>

Choose the best response for the following question. Then select “Check your answers.”