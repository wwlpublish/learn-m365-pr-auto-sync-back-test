A DLP policy combines different search patterns to look for, locations to protect or exclude, conditions, and actions.

 -  A condition may apply to content containing confidential information that's being shared with people outside the organization. Such information may include a credit card number, social security number, health ID, and so on.
 -  An action may be to block access to the document and then display a policy tip or send both the user and the compliance officer an email notification.

After an organization creates DLP policies, it can activate them to examine different locations, such as:

 -  Exchange email
 -  SharePoint sites
 -  OneDrive accounts

An organization can also create a DLP policy and choose not to activate it. Instead, it may choose to run it in test mode. Test mode enables an organization to review the reports for any possible activity without interfering with the company's production environment. Test mode can also be configured to display policy tips for user training.

A DLP policy can find and protect sensitive information across Microsoft 365. It doesn't matter if the information is in Exchange Online, SharePoint Online, or OneDrive for Business. You can easily choose to protect all locations, exclude different services, or even exclude elements from services.

For organizations to monitor and audit their DLP policies, there are two predefined reports available that show “DLP policy matches” and “DLP false positive and override”. Organizations can also request those reports through email, or they can create custom schedules for recurring reports.

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
     -  in Excel, PowerPoint, and Word (2016 or later), when the document is stored on a site that's included in a DLP policy.

Users can also be allowed to override the configured action to minimize the business impact of a possible false positive hit of the configured conditions. The override will then be logged with an optional override justification of the users.

### DLP policy configuration overview

Organizations have flexibility in how they create and configure their DLP policies. They can start from a predefined template and create a policy in just a few clicks. Or, they can design their own custom policy from the ground up. No matter which method they choose, all DLP policies require the same information.

1.  **Choose what you want to monitor**. DLP comes with many predefined policy templates to help you get started. You can also create a custom policy.
     -  Predefined policy templates include financial data, medical and health data, and privacy data. All templates are for various countries and regions.
     -  A custom policy uses the available sensitive information types, retention labels, and sensitivity labels.
2.  **Choose where you want to monitor**. Organizations can pick one or more locations they want DLP to monitor for sensitive information. The following table displays the list of locations that can be monitored.
    
    :::row:::
      :::column:::
        **Location**
      :::column-end:::
      :::column:::
        **Include/Exclude by:**
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        Exchange email
      :::column-end:::
      :::column:::
        distribution groups
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        SharePoint sites
      :::column-end:::
      :::column:::
        sites
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        OneDrive accounts
      :::column-end:::
      :::column:::
        accounts or distribution groups
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        Teams chat and channel messages
      :::column-end:::
      :::column:::
        account or distribution group
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        Windows 10, Windows 11, and macOS (Catalina 10.15 and higher) devices
      :::column-end:::
      :::column:::
        user or group
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        Microsoft Cloud App Security
      :::column-end:::
      :::column:::
        instance
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        On-premises repositories
      :::column-end:::
      :::column:::
        repository file path
      :::column-end:::
    :::row-end:::
    
3.  **Choose the conditions that must be matched for a policy to be applied to an item**. Organizations can accept pre-configured conditions or define custom conditions. Some examples are:
     -  The Item contains a specified kind of sensitive information that is being used in a certain context. For example, 95 social security numbers being emailed to a recipient outside the organization.
     -  The item has a specified sensitivity label.
     -  The item with sensitive information is shared either internally or externally.
4.  **Choose the action to take when the policy conditions are met**. The actions depend on the location where the activity is happening. Some examples are:
     -  **SharePoint/Exchange/OneDrive**. Block people who are outside your organization from accessing the content. Show the user a tip and send them an email notification that indicates they're taking an action that's prohibited by the DLP policy.
     -  **Teams Chat and Channel**. Block sensitive information from being shared in the chat or channel.
     -  **Windows 10, Windows 11, and macOS (Catalina 10.15 and higher) devices**. Audit or restrict copying a sensitive item to a removeable USB device.
     -  **Office apps**. Show a popup message notifying the user they're engaging in a risky behavior. Then block the action, or block the action but allow the user to override the block.
     -  **On-premises file shares**. Move the file from where it's stored to a quarantine folder.

> [!NOTE]
> The conditions and the actions to take are defined in an object called a Rule.

A DLP policy that's created in the Microsoft Purview compliance portal is stored in a central policy store. It's then synced to the various content sources, including:

 -  Exchange Online, and from there to Outlook on the web and Outlook.
 -  OneDrive for Business sites.
 -  SharePoint Online sites.
 -  Office desktop programs (Excel, PowerPoint, and Word).
 -  Microsoft Teams channels and chat messages.

After the policy is synced to the right locations, it starts to evaluate content and enforce actions.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”