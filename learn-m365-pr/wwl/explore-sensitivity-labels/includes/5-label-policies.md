After an organization creates its sensitivity labels, it must publish them to make them available to their users and services. The sensitivity labels can then be applied to Office documents and emails, and other items that support sensitivity labels.

Unlike retention labels, which are published to locations such as all Exchange mailboxes, sensitivity labels are published to users or groups. Apps that support sensitivity labels can then display them to those users and groups as applied labels, or as labels that they can apply.

When an organization configures a label policy, it can:

 -  **Choose which users and groups see the labels.** Labels can be published to any specific user or email-enabled security group, distribution group, or Microsoft 365 group (which can have dynamic membership) in Azure AD.
 -  **Apply a default label to documents and emails.** A default label can be applied to all new documents and unlabeled emails created by the users and groups included in the label policy. The same or different default label can be applied to containers if you've enabled sensitivity labels for Microsoft Teams, Microsoft 365 groups, and SharePoint sites. With this setting, the Azure Information Protection unified labeling client also applies the default label to existing documents that are unlabeled. Users can always change the default label if it's not the right label for their document or email.
    
    An organization should consider using a default label to set a base level of protection settings for its content. However, without user training and other controls, this setting can also result in inaccurate labeling. It's not a good idea to select a label that applies encryption as a default label to documents. For example, many organizations need to send and share documents with external users who may not have apps that support the encryption. Or, they may not use an account that can be authorized. For more information about this scenario, see [Sharing encrypted documents with external users](/microsoft-365/compliance/sensitivity-labels-office-apps?azure-portal=true).
 -  **Require a justification for changing a label.** If a user tries to remove a label or replace it with a label that has a lower-order number, you can require the user provides a justification to complete this action. For example, a user opens a document labeled Confidential (order number 3) and replaces that label with one named Public (order number 1). Administrators can read the justification reason along with the label change in [activity explorer](/microsoft-365/compliance/data-classification-activity-explorer?azure-portal=true).
    
    :::image type="content" source="../media/sensitivity-label-justification-required-9506ae33.png" alt-text="screenshot of sensitivity label window showing justification required option":::
    

 -  **Require users to apply a label with one option for email and documents, and another for containers.** Also known as mandatory labeling, these options ensure a label must be applied before users can save documents and send emails, and create new groups or sites.
    
     -  For containers, a label must be assigned at the time the group or site is created.
     -  For documents and emails, a label can be assigned:
        
         -  manually by the user.
         -  automatically because of a condition that you configure.
         -  assigned by default (the default label option previously described).
    
        The following image displays an example of a prompt shown in Outlook when a user is required to assign a label.
    
    :::image type="content" source="../media/sensitivity-labels-mandatory-prompt-aip-outlook-e1aeec1c.png" alt-text="screenshot displays an example of a prompt shown in Outlook when a user is required to assign a label":::
    

    Organizations should consider using this option to help increase their labeling coverage. However, without user training, these settings can result in inaccurate labeling and frustrated users. For example, unless you also set a corresponding default label, mandatory labeling can frustrate your users with the frequent prompts.

    > [!NOTE]
    > Mandatory labeling for documents and emails isn't available for all apps or all platforms. For more information, see [Require users to apply a label to their email and documents](/microsoft-365/compliance/sensitivity-labels-office-apps?azure-portal=true).

 -  **Provide help link to a custom help page.** If your users aren't sure what your sensitivity labels mean or how they should be used, you can provide a **Learn More** URL. This URL will appear at the bottom of the Sensitivity label menu in the Office apps.
    
    :::image type="content" source="../media/sensitivity-label-learn-more-0cbae756.png" alt-text="screenshot showing Learn More option at the bottom of the sensitivity label menu in Office apps":::
    

After you create a label policy that assigns new sensitivity labels to users and groups, users start to see those labels in their Office apps. Allow up to 24 hours for the latest changes to replicate throughout your organization.

There's no limit to the number of sensitivity labels that an organization can create and publish-with one exception: If the label applies encryption, the maximum number of labels that you can create is 500.

> [!WARNING]
> As a best practice to lower administrative overheads and reduce complexity for your users, try to keep the number of labels to a minimum. Real-world deployments have proved that effectiveness can be noticeably reduced when users have more than five main labels or more than five sublabels per main label.

### Label policy priority (order matters)

An organization makes its sensitivity labels available to users by publishing them in a sensitivity label policy. These policies appear in a list on the **Sensitivity policies** tab on the **Label policies** page. Just like sensitivity labels, the order of the sensitivity label policies is important because it reflects their priority. The label policy with the lowest priority is shown at the top, and the label policy with the highest priority is shown at the bottom.

A label policy consists of:

 -  A set of labels.
 -  The users and groups that will be assigned the policy with labels.
 -  The scope of the policy and policy settings for that scope (such as default label for files and emails).

A user can be included in multiple label policies, and the user will get all the sensitivity labels and settings from those policies. If there's a conflict in settings from multiple policies, the settings from the policy with the highest priority (lowest position) is applied. In other words, the highest priority wins for each setting.

> [!TIP]
> If you're not seeing the label or label policy setting behavior that you expect for a user or group, check the order of the sensitivity label policies. You may need to move the policy down. To reorder the label policies, select a sensitivity label policy, choose the ellipsis to the right of it, and then select **Move up** or **Move down**.

:::image type="content" source="../media/sensitivity-label-policy-priority-49fc072c.png" alt-text="screenshot showing policy priority window with option to move policies up or down":::


> [!NOTE]
> When there's a conflict of settings for a user who has multiple policies assigned, the setting from the policy with the highest priority (lowest position) is applied.

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Create a sensitivity label](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-101/M7-L7-E1-T2/index.html?azure-portal=true).

This simulation guides you through the steps to create a sensitivity label and a sensitivity label policy for the fictitious company known as Adatum Corporation.
