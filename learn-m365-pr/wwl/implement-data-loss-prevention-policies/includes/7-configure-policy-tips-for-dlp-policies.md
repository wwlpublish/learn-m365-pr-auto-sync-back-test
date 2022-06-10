For each rule in a DLP policy, an organization can configure policy tips to:

 -  **Notify the person the content conflicts with a DLP policy**. As such, they can take action to resolve the conflict. You can use the default text (see the tables below) or enter custom text about your organization's specific policies.
 -  **Allow the person to override the DLP policy**. You can optionally:
     -  **Require the person to enter a business justification for overriding the policy**. This information is logged. You can view it in the DLP reports in the **Reports** section of the portal.
     -  **Allow the person to report a false positive and override the DLP policy**. This information is also logged for reporting. You can use false positives to fine tune your rules.

For example, an organization may have a DLP policy applied to OneDrive for Business sites. The policy detects personal customer content. This policy has the following rules:

 -  **Rule 1.** If fewer than five instances of this sensitive information are detected in a document, and the document is shared with people inside the organization:
     -  The **Send a notification** action displays a policy tip. For policy tips, no override options are necessary because this rule just notifies people and doesn't block access.
 -  **Rule 2**. If greater than five instances of this sensitive information are detected in a document, and the document is shared with people inside the organization:
     -  The **Block access to content** action restricts the permissions for the file.
     -  The **Send a notification** action allows people to override the actions in this rule by providing a business justification. Your organization's business sometimes requires internal people to share personal information, and you don't want your DLP policy to block this work.
 -  **Rule 3**. If greater than five instances of this sensitive information are detected in a document, and the document is shared with people outside the organization:
     -  The **Block access to content** action restricts the permissions for the file.
     -  The **Send a notification** action doesn't allow people to override the actions in this rule because the information is shared externally. Under no circumstances should people in your organization be allowed to share personal data outside the organization.

### User Override support

The following list identifies important considerations to keep in mind when using a policy tip to override a rule:

 -  The option to override is per rule. It overrides all the actions in the rule, with one exception. The **Sending a notification** action can't be overridden.
 -  It's possible for content to match several rules in a DLP policy. However, only the policy tip from the most restrictive, highest-priority rule will be shown. For example, a policy tip from a rule that blocks access to content will be shown over a policy tip from a rule that just sends a notification. This design prevents people from seeing a cascade of policy tips.
 -  If the policy tips in the most restrictive rule allow people to override the rule, then overriding this rule also overrides any other rules that the content matched.
 -  If the **Notify + Allow Override** action is set with **Without Justification** or **With Justification or False Positives**, ensure **Block Access** is set to true and **Block Access Scope** has an appropriate value. Otherwise, the policy tip will be displayed, but the user won't see an option to override the email with justification.

Whether the Override option is available on a policy tip is dependent on the notification rule. The following table identifies the various rules that are available and whether each supports the ability to override the policy tip.

| **Notification Rule**                                                    | **Notify/Block action** | **Override available?** | **Require Justification?** |
| ------------------------------------------------------------------------ | ----------------------- | ----------------------- | -------------------------- |
| Notify only                                                              | Notify                  | No                      | No                         |
| Notify + Allow Override                                                  | Notify                  | No                      | No                         |
| Notify + Allow Override + False positive                                 | Notify                  | No                      | No                         |
| Notify + Allow Override + With justification                             | Notify                  | No                      | No                         |
| Notify + Allow Override + False positive + Without justification         | Notify                  | No                      | No                         |
| Notify + Allow Override + False positive + With justification            | Notify                  | No                      | No                         |
| Notify + Block                                                           | Block                   | No                      | No                         |
| Notify + Block + Allow Override                                          | Block                   | Yes                     | No                         |
| Notify + Block + Allow Override + False positive                         | Block                   | Yes                     | No                         |
| Notify + Block + Allow Override + With justification                     | Block                   | Yes                     | Yes                        |
| Notify + Block + Allow Override + False positive + Without justification | Block                   | Yes                     | No                         |
| Notify + Block + Allow Override + False positive + With justification    | Block                   | Yes                     | Yes                        |

### Policy tips on OneDrive for Business sites and SharePoint Online sites

When a document on a OneDrive for Business site or SharePoint Online site matches a rule in a DLP policy, and that rule uses policy tips, the policy tips display special icons on the document:

 -  If the rule sends a notification about the file, the **Warning** icon appears.
 -  If the rule blocks access to the document, the **Blocked** icon appears.

To take action on a document, you should first select an item. Then select the **Information** icon in the upper-right corner of the page to open the details pane and select the option to **View the policy tip**.

:::image type="content" source="../media/view-the-policy-tip-screen-0ecbb775.png" alt-text="Screenshot of the information pane showing a policy tip with its various options.":::


The policy tip lists the issues with the content. If a policy tip is configured with these options, you can select **Resolve**. You can then select either **Override the policy tip** or **Report a false positive**.

:::image type="content" source="../media/policy-tip-screen-with-resolve-and-override-options-7f18c6c2.png" alt-text="Screenshot of the policy tip screen with the resolve and override options.":::


DLP policies are synced to sites and contented is evaluated against them periodically and asynchronously. As a result, there may be a short delay between the time a DLP policy is created and the time that policy tips begin to appear. There may be a similar delay from when you resolve or override a policy tip to when the icon on the document on the site goes away.

#### Default text for policy tips on sites

By default, policy tips display text similar to the following messages for an item on a site. The notification text is configured separately for each rule. As a result, the text that's displayed differs depending on which rule is matched.

| **If the DLP policy rule does this action:**              | **Then the default policy tip displays this message:**                                                                                                                              |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sends a notification but doesn't allow override.          | This item conflicts with a policy in your organization.                                                                                                                             |
| Blocks access, sends a notification, and allows override. | This item conflicts with a policy in your organization. If you don't resolve this conflict, access to this file may be blocked.                                                     |
| Blocks access and sends a notification.                   | This item conflicts with a policy in your organization. Access to this item is blocked for everyone except its owner, last modifier, and the primary site collection administrator. |

#### Custom text for policy tips on sites

An organization can customize the text for policy tips separately from the email notification. Unlike custom text for email notifications, custom text for policy tips doesn't accept HTML or tokens. Instead, custom text for policy tips is plain text only with a 256-character limit.

### Policy tips in Outlook on the web and Outlook 2013 and later

When you compose a new email in Outlook on the web or Outlook 2013 and later, you'll see a policy tip if:

 -  You add content that matches a rule in a DLP policy.
 -  That rule uses policy tips.

The policy tip appears at the top of the message, above the recipients, while the message is being composed.

:::image type="content" source="../media/outlook-email-message-with-policy-tip-8b8a2825.png" alt-text="Screenshot of an email in Outlook that's displaying a sensitive data policy tip that's been highlighted.":::


Policy tips work whether the sensitive information appears in the message body or subject line. They also work when the sensitive information appears in a message attachment, as shown in the following screenshot.

:::image type="content" source="../media/outlook-email-message-with-policy-tip-and-message-attachment-c8226139.png" alt-text="Screenshot of an email in Outlook that's displaying a sensitive data policy tip showing that an attachment conflicts with a DLP policy.":::


If the policy tips are configured to allow override, you can select **Show Details** and then **Override.** 

:::image type="content" source="../media/outlook-email-message-with-policy-tip-and-override-option-e6d54ec8.png" alt-text="Screenshot of an email in Outlook that's displaying a sensitive data policy tip and an override button.":::


If you select the **Override** option in the policy tip, a dialog window appears. In this window, you can enter a business justification for overriding the policy tip, or you can report a false positive. Then select the **Override** button.

:::image type="content" source="../media/policy-tip-override-justification-1902bfea.png" alt-text="Screenshot of a policy tip override dialog window where you can enter a justification for overriding the policy tip.":::


> [!NOTE]
> When you add sensitive information to an email, there may be latency between when the sensitive information is added and when the policy tip appears. Policy tips won't appear when emails are encrypted with Microsoft Purview Message Encryption and the policy that's used to detect them uses the detect encryption condition.

#### Default text for policy tips in email

By default, policy tips display text similar to the following messages for email.

| **If the DLP policy rule does this action:**              | **Then the default policy tip displays this message:**   |
| --------------------------------------------------------- | -------------------------------------------------------- |
| Sends a notification but doesn't allow override.          | Your email conflicts with a policy in your organization. |
| Blocks access, sends a notification, and allows override. | Your email conflicts with a policy in your organization. |
| Blocks access and sends a notification.                   | Your email conflicts with a policy in your organization. |

#### Policy tips in the Exchange admin center vs. the Microsoft Purview compliance portal

Policy tips can work either with DLP policies and mail flow rules created in the Exchange admin center, or with DLP policies created in the Microsoft Purview compliance portal, but not both. The reason for this condition is that policies are stored in different locations, but policy tips can draw only from a single location.

If you've configured policy tips in the Exchange admin center, any policy tips that you configure in the Microsoft Purview compliance portal won't appear to users in Outlook on the web and Outlook 2013 and later until you turn off the tips in the Exchange admin center. This design ensures that your current Exchange mail flow rules will continue to work until you choose to switch over to the Microsoft Purview compliance portal.

While policy tips can draw only from a single location, email notifications are always sent. In fact, they're sent even if you're using DLP policies in both the Microsoft Purview compliance portal and the Exchange admin center.

### Policy tips in Excel, PowerPoint, and Word

When people work with sensitive content in the desktop versions of Excel, PowerPoint, and Word, policy tips can notify them in real time that the content conflicts with a DLP policy. This design requires that:

 -  The Office document is stored on a OneDrive for Business site or SharePoint Online site.
 -  The site is included in a DLP policy that's configured to use policy tips.

Office desktop programs automatically sync DLP policies directly from Office 365. They then scan your documents to ensure:

 -  They don't conflict with your DLP policies.
 -  They display policy tips in real time.

> [!NOTE]
> Office desktop apps scan documents themselves to determine if DLP policy tips should be shown. They don't show policy tips that SharePoint Online sites or OneDrive for Business sites have already determined should be shown on a file. As a result, you may not always see a DLP policy tip in the desktop apps that you see in the SharePoint Online sites or OneDrive for Business sites. In contrast, the Office applications on the web only show DLP policy tips that SharePoint Online sites or OneDrive for Business sites have already determined should be shown.

Depending on how an organization configures the policy tips in the DLP policy, its users can choose to:

 -  Ignore the policy tip.
 -  Override the policy with or without a business justification.
 -  Report a false positive.

Policy tips appear on the Message Bar.

:::image type="content" source="../media/excel-spreadsheet-with-social-security-number-41387521.png" alt-text="Screenshot of an Excel spreadsheet displaying a policy tip with an override option.":::


And policy tips also appear in the **Backstage** view (on the **File** tab).

:::image type="content" source="../media/excel-spreadsheet-info-screen-with-policy-tip-2b91fd6a.png" alt-text="Screenshot of an Excel spreadsheet Info page showing a policy tip.":::


If policy tips in the DLP policy are configured with the option to Override or Report a false positive, you can do so by selecting the **Resolve** button. In the dialog box that appears, you can select to **Override** a policy tip or **Report** a false positive.

:::image type="content" source="../media/excel-spreadsheet-info-screen-with-policy-tip-override-option-675e807e.png" alt-text="Screenshot of an Excel spreadsheet Info page showing a policy tip and the override option.":::


In each of these Office desktop programs, users can choose to turn off policy tips. If turned off, policy tips that are just notifications won't appear on the Message Bar or Backstage view. However, policy tips about blocking and overriding will still appear. Users will also receive the email notification. In addition, turning off policy tips doesn't exempt the document from any DLP policies that were applied to it.

#### Default text for policy tips in Excel, PowerPoint, and Word

By default, policy tips display text similar to the following messages on the Message Bar and Backstage view of an open document. The notification text is configured separately for each rule. As such, the text that's displayed differs depending on which rule is matched.

| **If the DLP policy rule does this action:**              | **Then the default policy tip displays this message:**                                                                                                                          |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sends a notification but doesn't allow override.          | This file conflicts with a policy in your organization. Go to the **File** menu for more information.                                                                           |
| Blocks access, sends a notification, and allows override. | This file conflicts with a policy in your organization. If you don't resolve this conflict, access to this file might be blocked. Go to the **File** menu for more information. |
| Blocks access and sends a notification.                   | This file conflicts with a policy in your organization. If you don't resolve this conflict, access to this file might be blocked. Go to the **File** menu for more information. |

#### Custom text for policy tips in Excel, PowerPoint, and Word

You can customize the text for policy tips separately from the email notification. Unlike custom text for email notifications, custom text for policy tips doesn't accept HTML or tokens. Instead, custom text for policy tips is plain text only with a 256-character limit.
