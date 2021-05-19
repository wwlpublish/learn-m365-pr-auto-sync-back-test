When you create a DLP policy in the Security &amp; Compliance Center, you can configure a user notification action to inform users and educate them when they are in violation of an organization’s policy. Users can be notified through email notifications and policy tips.

Email notifications have a Subject line that begins with the action taken, such as “Notification”, “Message Blocked” for email, or “Access Blocked” for documents. If the notification is about a document, the notification message body includes a link that takes you to the site where the document is stored. It then opens the policy tip for the document, where you can resolve any issues (policy tips are examined in the next unit). If the notification is about a message, the notification includes an attachment that contains the message that matches a DLP policy.

:::image type="content" source="../media/email-notification-item-conflict-c12fc8e9.png" alt-text="screenshot of email notification message saying the item conflicts with a policy in the organization":::


By default, notifications display text similar to the statements in the following chart for an item on a site. The notification text is configured separately for each rule. By doing so, the text that's displayed differs depending on which rule is matched.

:::row:::
  :::column:::
    

**If the DLP policy rule does this action:**


  :::column-end:::
  :::column:::
    

**Then the default notification for SharePoint or OneDrive for Business documents displays this message:**


  :::column-end:::
  :::column:::
    

**Then the default notification for Outlook email displays this message:**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Sends a notification but doesn’t allow override.


  :::column-end:::
  :::column:::
    

This item conflicts with a policy in your organization.


  :::column-end:::
  :::column:::
    

Your email message conflicts with a policy in your organization.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Blocks access, sends a notification, and allows override.


  :::column-end:::
  :::column:::
    

This item conflicts with a policy in your organization. If you don’t resolve this conflict, access to this file might be blocked.


  :::column-end:::
  :::column:::
    

Your email message conflicts with a policy in your organization. The message wasn't delivered to all recipients.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Blocks access and sends a notification.


  :::column-end:::
  :::column:::
    

This item conflicts with a policy in your organization. Access to this item is blocked for everyone except its owner, last modifier, and the primary site collection administrator.


  :::column-end:::
  :::column:::
    

Your email message conflicts with a policy in your organization. The message wasn't delivered to all recipients.


  :::column-end:::
:::row-end:::
