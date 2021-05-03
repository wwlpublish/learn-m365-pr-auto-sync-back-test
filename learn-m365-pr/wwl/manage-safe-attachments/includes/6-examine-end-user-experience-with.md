The goal of Safe Attachments is to protect users from opening unsafe attachments. Some administrators choose to create policies that block or replace attachments. However, most admins select the dynamic delivery option to avoid message delivery delays.

When a Safe Attachments policy is applied with the action to Block, the entire message is prevented from being delivered. Instead, the user instead receives a notification message. This notification indicates that a message with a malicious attachment was received. It also states that both the message body and the attachment were blocked.

When a Safe Attachments policy is applied with the action to Replace, the attachment provides a better user experience. In this scenario, if a malicious attachment is detected, it's replaced with an icon with a red warning sign. If the user hovers over the icon, a message appears that indicates malware was detected, and the attachment was blocked.

The user still has access to the original message body, but the malware threat was removed. This process enables the user to at least read and respond to the message if needed.

:::image type="content" source="../media/warning-message-blocked-attachment-682e0e0a.png" alt-text="screenshot of warning message saying access to attachment is blocked":::


One of the caveats to any sandboxing solution for file attachments is the latency involved in completing the scan and analysis. Policies configured to block or replace attachments often result in delivery delays that may annoy end users and impact their productivity. That's why the dynamic delivery option provides the best user experience. It eliminates any delays in receiving the message body.

While ensuring the user is protected, dynamic delivery enables the user to remain productive. It does so by allowing the user to read and respond to the email while the attachment is being scanned. The user receives the email, but in place of the attachment that was originally sent, the user receives a placeholder attachment. This placeholder notifies the user the original attachment is currently being scanned.

What happens next depends on the outcome of the scanning process:

 -  If the scanned attachment is considered clean, it's automatically attached to the original message in the user’s inbox.
 -  If the scanned attachment is considered infected, the message is updated with a new attachment. This attachment tells the recipient the original attachment was infected with malware.

:::image type="content" source="../media/email-with-atp-scan-in-progress-message-60acf3de.png" alt-text="screenshot of email message with attachment highlighted showing message that ATP scan is in progress":::
