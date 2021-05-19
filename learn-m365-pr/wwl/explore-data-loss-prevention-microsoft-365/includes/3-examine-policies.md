A DLP Policy combines different search patterns to look for, locations to protect or exclude, conditions, and actions.

 -  A condition may apply to content containing confidential information, such as credit card numbers, that's being shared with people outside the organization.
 -  An action may be to block access to the document and send both the user and the compliance officer an email notification or display a policy tip.

After creating DLP policies, you can activate them to examine different locations, such as:

 -  Exchange email
 -  SharePoint sites
 -  OneDrive accounts

You can also create a DLP policy and choose not to activate it, but instead run it in test mode. Test mode enables an organization to review the reports for any possible activity without interfering with the company's production environment. Test mode can also be configured to display policy tips for user training.

A DLP policy can find and protect sensitive information across Microsoft 365, whether that information is in Exchange, SharePoint, or OneDrive for Business. You can easily choose to protect all locations, exclude different services, or even exclude elements from services.

To monitor and audit your DLP Policies, there are two predefined reports available that show “DLP policy matches” and “DLP false positive and override”. You can also request those reports through email or create a custom schedule for recurring reports.

### Rules, conditions, and actions

Rules are what enforce an organization's business requirements on the information that it stores. A policy can contain one or more rules, and each rule consists of conditions and actions. When the conditions are met for a rule, the actions are automatically taken.

#### **Conditions**

Conditions focus not only on the content, such as the type of sensitive information you’re looking for, but also on the context, such as the person the document is shared with. You can use conditions to assign different actions to different risk levels. For example, sensitive content shared internally may have a lower risk and require fewer actions than sensitive content shared with people outside the organization.

Conditions can determine if:

 -  content contains any of the 80+ built-in types of sensitive information.
 -  content is shared with people outside or inside the organization.
 -  document properties contain specific values. For example, documents uploaded to Microsoft 365 from a Windows Server–based file server may have Files Classification Infrastructure (FCI) properties applied to them. For email, this condition works for documents attached to messages.

#### **Actions**

When content matches a condition in a rule, the actions assigned to the rule are automatically completed. The purpose of the actions is generally to protect the document or content. You can complete actions such as:

 -  **Block access to the content**. For site content, permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document. For email content, this action blocks the message from being sent. Depending on how the DLP rule is configured, the sender will see either a Non-Delivery Report (NDR), or if the rule uses the **Send a notification** action, a policy tip, and an email notification.
 -  **Send a notification.** Notifications can be sent to the person who shared, emailed, or last modified the content and, for site content, the site collection administrator and document owner. Besides sending an email notification, you can also display a policy tip:
    
     -  in Outlook 2013 and later and Outlook on the web.
     -  for the document on a SharePoint Online or OneDrive for Business site.
     -  in Excel 2016, PowerPoint 2016, and Word 2016, when the document is stored on a site included in a DLP policy.

Users can also be allowed to override the configured action to minimize the business impact of a possible false positive hit of the configured conditions. The override will then be logged with an optional override justification of the users.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”