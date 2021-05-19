A policy tip is a notification or warning that appears when someone is working with content that conflicts with a DLP policy. For example, content like an Excel workbook on a OneDrive for Business site that contains personal information and is shared with an external user.

You can use email notifications and policy tips to increase awareness and help educate people about your organization's policies. You can also give people the option to override the policy, so that they're not blocked if they have a valid business need or if the policy is detecting a false positive.

### Options for configuring email notifications

An organization can enable User notifications when it creates a DLP policy. When user notifications are enabled, Microsoft 365 sends out both email notifications and policy tips. Organizations can customize which users will receive notification emails, the email text, and the policy tip text.

> [!NOTE]
> Email notifications can only be sent to individual recipients. They can't be sent to groups or distribution lists. Only new content will trigger an email notification. Editing existing content will trigger policy tips, but not an email notification.<br>

:::image type="content" source="../media/email-notification-window-fd1a488c.png" alt-text="screenshot of the email notification window":::


#### Default email notification

Notifications have a Subject line that begins with the action taken, such as "Notification", "Message Blocked" for email, or "Access Blocked" for documents.

 -  If the notification is about a document:
    
     -  The notification message body includes a link that takes the sender to the site where the document's stored.
     -  It opens the policy tip for the document, where you can resolve any issues (see the section below about policy tips).
 -  If the notification is about a message:
    
     -  The notification includes an attachment that contains the message that matches a DLP policy.

:::image type="content" source="../media/email-notification-message-ae7d6870.png" alt-text="screenshot showing the default email notification message indicating access to the attached document is blocked":::


By default, email notifications display text similar to the notifications in the following table for an item on a site. The notification text is configured separately for each rule, so the text that's displayed differs depending on which rule is matched.<br>

:::row:::
  :::column:::
    **If the DLP policy rule does this action:**
  :::column-end:::
  :::column:::
    **Then the default notification for SharePoint or OneDrive for Business documents displays this message:**
  :::column-end:::
  :::column:::
    **Then the default notification for Outlook messages displays this message:**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Sends a notification but doesn't allow override.

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
    This item conflicts with a policy in your organization. If you don't resolve this conflict, access to this file might be blocked.

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


#### Custom email notification

You can create a custom email notification instead of sending the default email notification to your end users or administrators. The custom email notification supports HTML and has a 5,000-character limit. HTML can be used to include images, formatting, and other branding in the notification.

The following tokens can also be used to help customize the email notification. These tokens are variables that are replaced by specific information in the notification that's sent.

:::row:::
  :::column:::
    **Token**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    %%AppliedActions%%

  :::column-end:::
  :::column:::
    The actions applied to the content.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    %%ContentURL%%

  :::column-end:::
  :::column:::
    The URL of the document on the SharePoint Online site or OneDrive for Business site.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    %%MatchedConditions%%

  :::column-end:::
  :::column:::
    The conditions that were matched by the content. This token is used to inform people of possible issues with the content.

  :::column-end:::
:::row-end:::


The following screenshot of a **Block access to content** email notification displays where each token appears in the message.<br><br>

:::image type="content" source="../media/access-blocked-notification-0679ddb3.png" alt-text="screenshot showing a custom email notification where access is blocked to an attached document, and it highlights the fields that can be updated in the notification":::


### Policy tips in Outlook

When you compose a new email in Outlook on the web and Outlook 2013 and later, you'll see a policy tip if you add content that matches a rule in a DLP policy, and that rule uses policy tips. The policy tip appears at the top of the message, above the recipients, while the message is being composed.

:::image type="content" source="../media/policy-tip-in-an-email-message-868f0f94.png" alt-text="screenshot of an email message with a policy tip displayed":::


Policy tips work whether the sensitive information appears in the message body, subject line, or even a message attachment as shown here.

If the policy tips are configured to allow override, you can choose Show Details &gt; Override &gt; enter a business justification or report a false positive &gt; Override.<br>

:::image type="content" source="../media/policy-tip-with-override-f930b4b1.png" alt-text="screenshot of a policy tip on an email message that displays the Override option":::


:::image type="content" source="../media/policy-tip-override-message-f2fa477f.png" alt-text="screenshot of window where you can enter a reason for overriding a DLP policy":::


> [!NOTE]
> When you add sensitive information to an email, there may be latency between when the sensitive information is added and when the policy tip appears.

### Outlook supports showing policy tips for only some conditions

Currently, Outlook 2013 and later supports showing policy tips only for these conditions:

 -  Content contains
 -  Content is shared

> [!NOTE]
> Exceptions are considered conditions. All of these conditions work in Outlook, where they will match content and enforce protective actions on content. But showing policy tips to users is not yet supported.

### Policy tips in the Exchange admin center vs. the Security &amp; Compliance Center

DLP policies and mail flow rules can be created in the Exchange admin center. DLP policies can also be created in the Security and Compliance Center. However, policy tips can work with only one of these method, but not both. This restriction is because the policies created in the Exchange admin center are stored in different location fronm the policies created in the SCC, and policy tips can draw only from a single location.

If you've configured policy tips in the Exchange admin center, any policy tips that you configure in the Security &amp; Compliance Center won't appear to users in Outlook on the web and Outlook 2013 and later until you turn off the tips in the Exchange admin center. This ensures that your current Exchange mail flow rules (also known as transport rules) will continue to work until you choose to switch over to the Security &amp; Compliance Center.

> [!IMPORTANT]
> While policy tips can draw only from a single location, email notifications are always sent, even if you're using DLP policies in both the Security &amp; Compliance Center and the Exchange admin center.
