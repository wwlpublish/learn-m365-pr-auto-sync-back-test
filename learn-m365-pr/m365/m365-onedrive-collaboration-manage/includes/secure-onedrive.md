To comply with business standards and industry regulations, organizations must protect sensitive items and prevent its inadvertent disclosure. Sensitive items can include financial data or personal information such as credit card numbers, social security numbers, or health records. You can secure content in OneDrive using Microsoft 365 solutions such as Data Loss Prevention (DLP) and sensitivity labels.

## Data Loss Prevention (DLP) for OneDrive

DLP policies are configured in the Microsoft 365 Compliance Center. When configured and applied correctly, DLP helps prevent the inadvertent sharing of sensitive items with people who shouldn't have access to them, both inside and outside of your org.  They cover locations such as Exchange, SharePoint, OneDrive, and Microsoft Teams. For example, you can set the DLP policy to identify any documents containing a credit card number that are stored in a OneDrive site or monitor the OneDrive sites of specific users to prevent the accidental sharing of sensitive items by automatically blocking the sharing of those files with people outside your organization. When a user tries to share a sensitive item, the DLP policy can both send them an email and display a policy tip that might allow them to override the policy if they have a business justification.
  
:::image type="content" source="../media/policy-tip.png" alt-text="Screenshot displays When a user tries to share a sensitive item, the DLP policy can both send them an email and display a policy tip" lightbox="../media/policy-tip.png":::

## How DLP policies work

DLP detects sensitive items by using deep content analysis (not just a simple text scan). This deep content analysis uses keyword matches, dictionary matches, the evaluation of regular expressions, internal functions, and other methods to detect content that matches your DLP policies. DLP continues to evaluate content it changes over time.

## Sensitivity labels in OneDrive

Sensitivity labels from the Microsoft Information Protection (MIP) framework let you classify and protect your organization's data, while making sure that user productivity and their ability to collaborate isn't hindered. Sensitivity labels enforce protection on files themselves regardless of where they are stored such as OneDrive, SharePoint, or on a local computer. They work differently from DLP in that they allow users to protect their own documents by applying functionality like encryption or watermarks. For example, when a user applies a Confidential label to a document or email, that label might encrypt the content and apply a "Confidential" watermark, depending on the label options that you configure. Sensitivity labels work across Microsoft 365 apps and different platforms and devices.

With a sensitivity label you can:

- Encrypt documents and choose which users or groups have permissions to perform which actions and for how long.
- Mark the content by adding watermarks, headers, or footers.

   :::image type="content" source="../media/sensitivity-label.png" alt-text="Screenshot displaying Sensitivity label." lightbox="../media/sensitivity-label.png":::

- Apply the label automatically in Office apps or recommend a label.  You can choose what types of sensitive information, such as SSN or CC, that you want a label to be applied for, and the label can either be applied automatically or you can prompt users to apply the label that you recommend.

To support sensitivity labels for Office on the web and for labels that apply encryption, make sure that your tenant is enabled for sensitivity labels for Office files in SharePoint and OneDrive.  

## Learn more

- [Overview of data loss prevention](/microsoft-365/compliance/data-loss-prevention-policies?azure-portal=true)
- [Learn about sensitivity labels](/microsoft-365/compliance/sensitivity-labels?azure-portal=true)
- [Create and configure sensitivity labels and their policies](/microsoft-365/compliance/create-sensitivity-labels?azure-portal=true)
- [Restrict access to content by using sensitivity labels to apply encryption](/microsoft-365/compliance/encryption-sensitivity-labels?azure-portal=true)
- [Enable sensitivity labels for Office files in SharePoint and OneDrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files?azure-portal=true)
