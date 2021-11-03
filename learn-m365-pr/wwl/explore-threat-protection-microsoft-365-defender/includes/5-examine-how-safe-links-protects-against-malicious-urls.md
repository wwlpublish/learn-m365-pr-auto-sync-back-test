Safe Links is a feature in Microsoft Defender for Office 365 that protects users from malicious URLs that are commonly used in phishing attacks. Phishing attacks are typically designed to:

 -  Extract sensitive information from a user.
 -  Deliver malicious code to end-user machines.
 -  Trick users into actions that cause financial damages.

The Safe Links feature works by replacing embedded URLs from incoming messages and testing the URLs before a user can use them.

 -  If a URL isn't harmful, the user can select it in the message and get redirected to the target without any interruption.
 -  If a URL is considered to be potentially dangerous or malicious, a warning message is displayed, and the user isn't automatically redirected to the target. However, the user can optionally choose to either skip or visit the target.

### Considerations for implementing Safe Links

It’s important that you complete the following prerequisite tasks before deploying Safe Links in your environment:

 -  Verify that your organization has Microsoft Defender for Office 365 licensed.
 -  Verify that you have the necessary permissions to define or edit Microsoft Defender for Cloud's advanced threat protection policies. This action requires you to be a member of the Company administrators or Security admins role group.
 -  Review your policies to ensure they’re defined in the proper sequence. Policies are enforced in the order they're listed in the Microsoft 365 Defender portal.
 -  Verify that Office clients are configured to use Modern Authentication (this consideration is for Safe Links protection in Office documents).
 -  Allow up to 30 minutes for your new or updated policies to be propagated to all Microsoft 365 datacenters.
 -  Verify that a default policy is in place that applies to everyone. Other policies can be defined for specific recipients.

When deploying Safe Links, you should begin by checking the default policy. You can then configure other policies according to your organization’s needs. For example, your default policy may block users from overriding blocked URLs, while other policies block specific URLs automatically and skip rewriting for specific URLs.

### Default policy options

Default policy options apply to everyone in your organization.

:::row:::
  :::column:::
    **Default policy option**
  :::column-end:::
  :::column:::
    **Effect**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Block the following URLs
  :::column-end:::
  :::column:::
    Enables your organization to have a custom list of URLs that are automatically blocked. When users select a URL in this list, they'll be taken to a warning page that explains why the URL is blocked.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft 365 Apps for enterprise (formerly Office 365 ProPlus), Office for iOS and Android
  :::column-end:::
  :::column:::
    When this option is selected, Safe Links protection is applied to URLs in documents that are open in Microsoft 365 Apps for enterprise (Word, Excel, and PowerPoint on Windows or macOS), Office documents on iOS, or Android devices, Visio 2016 on Windows, and Office Online (Word Online, PowerPoint Online, Excel Online, and OneNote Online), provided the user has signed into Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Don't track when users click Safe Links
  :::column-end:::
  :::column:::
    When this option is selected, data isn't stored for selected URLs in Word, Excel, PowerPoint, and Visio documents.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Don't let users click through Safe Links to original URL
  :::column-end:::
  :::column:::
    When this option is selected, users can't continue past a warning page to a URL that's determined to be malicious.
  :::column-end:::
:::row-end:::


### Other recipient-based policies

The following table identifies the policy options that apply to specific email recipients.

:::row:::
  :::column:::
    **Custom policy option**
  :::column-end:::
  :::column:::
    **Effect**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Off
  :::column-end:::
  :::column:::
    

Doesn't scan URLs in email messages.


Enables you to define an exception rule, such as a rule that doesn't scan URLs in email messages for a specific group of recipients.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    On
  :::column-end:::
  :::column:::
    

Rewrites URLs to route users through Safe Links protection when the users select URLs in email messages.


Compares a selected URL against a list of blocked or malicious URLs.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Use Safe Attachments to scan downloadable content
  :::column-end:::
  :::column:::
    When this option is selected, URLs that point to downloadable content are scanned.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Apply Safe Links to messages sent within the organization
  :::column-end:::
  :::column:::
    When this option is available and selected, Safe Links protection is applied to email messages sent between people in your organization, provided the email accounts are hosted in Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Do not track user clicks
  :::column-end:::
  :::column:::
    When this option is selected, click data for URLs in email from external senders isn't stored. URL click tracking for links within email messages sent within the organization is currently not supported.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Do not allow users to click through to original URL
  :::column-end:::
  :::column:::
    When this option is selected, users can't continue past a warning page to a URL that's determined to be malicious.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Do not rewrite the following URLs
  :::column-end:::
  :::column:::
    Leaves URLs as they are. Keeps a custom list of safe URLs that don't need scanning for a specific group of email recipients in your organization.
  :::column-end:::
:::row-end:::


### URL detonation

URL detonation combines elements of Safe Links and Safe Attachments into a single feature, whose purpose is to protect users in the event a link points to a malicious file on a web server. When a user selects a link to a file on a web server, the file is downloaded into the Safe Attachments sandbox environment and detonated. As the content is being analyzed, a web page is presented to the user explaining that a scan is in process. If the file is ultimately determined to be malicious, the user is redirected to a warning page advising the user the site is malicious.

:::image type="content" source="../media/safe-links-warning-8a245198.png" alt-text="screenshot of warning message indicating the website is classified as malicious":::


> [!TIP]
> This option can only be configured in a custom policy you create. The option isn't available in the default policy.

### Safe Links in Microsoft 365 Apps for enterprise

Safe Links can also validate URLs in documents that are opened in Microsoft 365 Apps for enterprise (formerly Office 365 ProPlus). These apps include Word, Excel, PowerPoint, and Visio running on Windows.

> [!NOTE]
> This option can only be configured in the default, organization-wide policy.
