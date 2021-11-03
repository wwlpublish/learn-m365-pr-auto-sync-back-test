Safe Links is a feature in Microsoft Defender for Office 365 that protects users from malicious URLs. These URLs are commonly used in phishing attacks to extract sensitive information from a user.

When an email with an embedded URL is delivered to a recipient, the web page or attachment on the other side of the link may be safe to view at the time of delivery. However, it may not be safe when the user opens the email and selects the link. Safe Links protects the user by rewriting the link in the message body so that the link is checked at the time it’s selected, instead of when the message is delivered.

When a user selects a link in a message or document, Safe Links checks to see if the link is malicious. It does so by redirecting the URL to a secure server in the Microsoft 365 environment that checks the URL against a blocklist of known malicious web sites.

 -  If the site is safe, the browser is redirected to the original destination web site.
 -  If the site is on the blocklist, the user is blocked from continuing to the site, and the browser displays a warning page like the image below.

:::image type="content" source="../media/warning-message-malicious-website-ca2920ef.png" alt-text="screenshot of warning message saying website is classified as malicious":::


Safe Links is selective enough to remove only malicious links. Even within a single email, only the malicious links will be removed. If there are other links that are safe, the user can select them and navigate to the target websites without interference.

Like Safe Attachments, Safe Links protects your organization according to policies that are created by your security administrators. You can create and configure policies and apply them to specific people, groups, or domains.

The following graphic shows how malicious links are rewritten while in transport by Microsoft Defender for Office 365. If a recipient opens a dangerous link, they connect to Defender for Cloud and aren't redirected to the original target.

:::image type="content" source="../media/rewrite-malicious-links-31eef935.jpg" alt-text="graphic depicts the fact that malicious links are rewritten while in transport, and if a recipient opens a dangerous link, they connect to Defender for Office 365 and are not redirected to the original target":::


### URL detonation

URL detonation is a capability that combines elements of Safe Links and Safe Attachments into a single feature. This feature protects users in the event a link points to a malicious file on a web server. When a user selects a link to a file on a web server, the file is downloaded into the Safe Attachments sandbox environment and run (or "detonated").

As the content is being analyzed, a web page is presented to the user explaining that a scan is in process. If the file is ultimately determined to be malicious, then the user is redirected to a warning page advising the user that the site is malicious.

:::image type="content" source="../media/link-being-scanned-warning-message-4f608043.png" alt-text="screenshot of warning message saying this link is being scanned":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”
