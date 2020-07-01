Data is held in more places and on more devices than ever before. Before you can protect sensitive data, you need to know your data.

Knowing your data, is about being able to discover and identify important information across your environment.  You may also need to clarify what sensitive data means for your organization because it is not the same for everyone.  Knowing your data starts with being able to identify what sensitive data you have today so that you can classify it appropriately.

## Sensitivity labels

Sensitivity labels from Microsoft Information Protection let you classify and protect your organization's data while ensuring that user productivity and collaboration aren't hindered.

When you assign a sensitivity label to a group, document, or email, it's like a stamp that's applied to content.  That label is:

- **Customizable**. You can create categories for different levels of sensitive content in your organization, such as Personal, Public, General, Confidential, and Highly Confidential.
- **Clear text**. Because the label is stored in clear text in the content's metadata, third-party apps and services can read it and then apply their own protective actions, if necessary.
- **Persistent**. After you apply a sensitivity label to content, the label is stored in the metadata of that email or document. Which means the label roams with the content, including the protection settings, and this data becomes the basis for applying and enforcing policies.

After a sensitivity label is applied to an email or document, any configured protection settings for that label are enforced on the content. With a sensitivity label, you can:

- **Encrypt** email only or both email and documents. You can choose which users or group have permissions to perform which actions and for how long. For more information about the encryption settings when you create or edit a sensitivity label, see [Restrict access to content by using encryption sensitivity](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide).
- **Mark the content** when you use Office apps, by adding watermarks, headers, or footers to email or documents that have the label applied. Watermarks can be applied to documents but not email.  For more information on when content markings are applied, see [When Office apps apply content marking and encryption](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#whe).
- **Apply the label automatically** in Office apps or recommend a label. You can choose what types of sensitive information that you want to be labeled. The label can be applied automatically, or you can prompt users to apply the label that you recommend.
- **Protect content in containers such as sites and groups** when you opt in to the preview to [use sensitivity labels with Microsoft Teams, Microsoft 365 groups, and SharePoint sites (public preview)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites?view=o365-worldwide). This label configuration doesn't result in documents being automatically labeled. Instead, the label settings protect content by controlling access to the container where documents are stored.

After you create your sensitivity labels, you need to publish them and make them available to people and services in your organization. The sensitivity labels can then be applied to documents and emails. Sensitivity labels are published to users or groups.  Once published, sensitivity labels will appear in Office apps for those users and groups.

Sensitivity labels use Azure Information Protection.

## Azure Information Protection

Azure Information Protection (sometimes referred to as AIP) is a cloud-based solution that helps an organization classify and optionally, protect its documents and emails by applying labels. Labels can be applied automatically by administrators who define rules and conditions, manually by users, or a combination where users are given recommendations.

You use Azure Information Protection labels to apply classification to documents and emails. When you do, the classification is identifiable regardless of where the data is stored or with whom it’s shared. The labels can include visual markings such as a header, footer, or watermark. Metadata is added to files and email headers in cleartext. The clear text ensures that other services, such as data loss prevention solutions, can identify the classification and take appropriate action.

For example, the following email message has been classified as "General". The label has added a footer of "Sensitivity: General" to the email message. This footer is a visual indicator for all recipients that it's intended for general business data that shouldn't be sent outside the organization. The label is embedded in the email headers so that email services can inspect this value and create an audit entry or prevent it from being sent outside the organization.

:::image type="content" source="../media/2-report-reminder.png" alt-text="Report reminder":::

## Data classification

After applying retention labels and sensitivity labels, organizations will want to see how the labels are being used across the tenant and what is being done with those items. The data classification portal, accessed from the Microsoft 365 Compliance center, provides snapshots of how sensitive info and labels are being used across your organization's locations.

Watch this video to learn more about data classification:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

To learn more about data classification, visit [Know your data - data classification overview](https://docs.microsoft.com/microsoft-365/compliance/data-classification-overview?view=o365-worldwide).
