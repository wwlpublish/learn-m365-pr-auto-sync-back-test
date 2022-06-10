Organizations can use a Microsoft Purview Data Loss Prevention (DLP) policy to identify, monitor, and protect sensitive information across Microsoft 365. An organization wants its users who work with sensitive information to stay compliant with its DLP policies. However, it doesn't want to unnecessarily block them from getting their work done. Email notifications and policy tips can help with this situation.

:::image type="content" source="../media/excel-spreadsheet-with-social-security-number-41387521.png" alt-text="Screenshot of an Excel spreadsheet with a social security number that displays a policy tip message with an Override button.":::


When an organization creates a DLP policy, it can configure the user notifications to:

 -  Send an email notification that describes the issue to the people it chooses.
 -  Display a policy tip for content that conflicts with the DLP policy:
     -  For email in Outlook on the web and Outlook 2013 and later, the policy tip appears at the top of a message above the recipients. It's also displayed while the message is being composed.
     -  For documents in a OneDrive for Business account or SharePoint Online site, the policy tip is indicated by a warning icon that appears on the item. To view more information, you can select an item and then choose Information in the upper-right corner of the page to open the details pane.
     -  For Excel, PowerPoint, and Word documents that are stored on a OneDrive for Business site or SharePoint Online site that's included in the DLP policy, the policy tip appears on the Message Bar and the Backstage view **(File menu &gt; Info**).

### Add user notifications to a DLP policy

When an organization creates a DLP policy, it can enable **User notifications**. When this setting is enabled, Microsoft 365 sends out both email notifications and policy tips. You can customize who notification emails are sent to, the email text and the policy tip text.

1.  In the **Microsoft Purview compliance portal**, select **Data loss prevention** in the navigation pane.
2.  On the **Data loss prevention** page, select the **Policies** tab.
3.  On the **Policies** tab, select the **+Create policy** option on the menu bar. Selecting this option initiates the **Create policy** wizard.
    
    :::image type="content" source="../media/policy-tab-data-loss-prevention-page-ac62222e.png" alt-text="Screenshot of the Policy tab on the Data Loss Prevention page showing the Create policy option.":::
    
4.  On the **Choose the information to protect** page, select the DLP policy template that protects the types of sensitive information you want to protect. Select the category, select the template within that category, and then select **Next**. To start with an empty template, select **Custom** as the category and **Custom policy** as the template.
5.  On the **Name your policy** page, enter a **Name** for the policy. If you selected a template, the template name will be displayed in the **Name** field. You must modify the name or enter a new one. You'll receive an error if you don't change the template name. Select **Next**.
6.  On the **Choose locations to apply the policy** page, set the **Status** toggle switch to **On** for each location that you want the DLP policy to protect. Then select **Next**.
    
    To include or exclude an entire location, such as all Exchange email or all OneDrive accounts, switch the **Status** of that location to **On** or **Off**, respectively.
    
    To include only specific SharePoint sites or OneDrive accounts, switch the **Status** to **On**. Then select the link under the **Included** or **Excluded** column to choose specific sites or accounts.
7.  On the **Define policy settings** page, select **Create or customize advanced DLP rules**, and then select **Next**.
8.  On the **Customize advanced DLP rules** page, select **+Create rule** on the menu bar.
9.  On the **Create rule** page, enter a name for the rule in the **Name** field.
10. Under the **User notifications** section, set the toggle switch to **On**. Setting this option to **On** enables two more options.
     -  Under the **Endpoint devices** section, you can select the option to **Show users a policy tip notification when an activity is restricted**.
     -  Under the **Microsoft 365 services** section, you can select an option to **Notify users in Office 365 service with a policy tip**.
        
        :::image type="content" source="../media/user-notification-window-f14fefc3.png" alt-text="Screenshot of the user notifications window that appears in the rule editor.":::
        
11. Update any other settings that are applicable to this policy, and then select **Save**. The **Send email alerts to these people** option is examined in the next section.

> [!NOTE]
> Notification emails are sent unprotected.

### Options for configuring email notifications

For each rule in a DLP policy, you can:

 -  **Send the notification to the people you choose**. These people can include the owner of the content, the person who last modified the content, the owner of the site where the content is stored, or a specific user.
 -  **Customize the text that's included in the notification by using HTML or tokens**. For more information, see the following section.

When configuring email notifications, keep in mind the following items:

 -  Email notifications can only be sent to individual recipients. Notifications can't be sent to groups or distribution lists.
 -  Only new content will trigger an email notification. Editing existing content will trigger policy tips, but not email notifications.
 -  External senders don't receive notifications. Notifications go only to internal users.

:::image type="content" source="../media/email-notification-options-371dadff.png" alt-text="Screenshot of the email notifications window with the Notify these people option selected.":::


### Default email notification

Default email notifications have a Subject line that begins with the action taken. For example:

 -  "Notification"
 -  "Message Blocked" for email
 -  "Access Blocked" for documents

If the notification is about a document, the notification message body includes a link that takes the user to the site where the document is stored. It also opens the policy tip for the document. By doing so, the user can resolve any issues (see the next unit on policy tips). If the notification is about a message, the notification includes as an attachment the message that matches a DLP policy.

:::image type="content" source="../media/default-email-notification-705db2c8.png" alt-text="Screenshot of the default email notification window with a link to the site to fix the issues.":::


By default, notifications display text similar to the following for an item on a site. The notification text is configured separately for each rule. As a result, the text that's displayed differs depending on which rule is matched.

| **If the DLP policy rule does this...**                   | **Then the default notification for SharePoint or OneDrive for Business documents says this...**                                                                                    | **Then the default notification for Outlook messages says this...**                                              |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Sends a notification but doesn't allow override.          | This item conflicts with a policy in your organization.                                                                                                                             | Your email message conflicts with a policy in your organization.                                                 |
| Blocks access, sends a notification, and allows override. | This item conflicts with a policy in your organization. If you don't resolve this conflict, access to this file might be blocked.                                                   | Your email message conflicts with a policy in your organization. The message wasn't delivered to all recipients. |
| Blocks access and sends a notification.                   | This item conflicts with a policy in your organization. Access to this item is blocked for everyone except its owner, last modifier, and the primary site collection administrator. | Your email message conflicts with a policy in your organization. The message wasn't delivered to all recipients. |

### Custom email notification

An organization can create a custom email notification instead of sending the default email notification to its end users or administrators. The custom email notification supports HTML and has a 5,000-character limit. HTML can be used to include images, formatting, and other branding in the notification.

An organization can also use the following tokens to help customize the email notification. These tokens are variables that are replaced by specific information in the notification that's sent.

| **Token**             | **Description**                                                                                                       |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| %%AppliedActions%%    | The actions applied to the content.                                                                                   |
| %%ContentURL%%        | The URL of the document on the SharePoint Online site or OneDrive for Business site.                                  |
| %%MatchedConditions%% | The conditions that were matched by the content. Use this token to inform people of possible issues with the content. |

:::image type="content" source="../media/custom-email-notification-936f223c.png" alt-text="Screenshot of the custom email notification window with all the tokens highlighted.":::


## 

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”