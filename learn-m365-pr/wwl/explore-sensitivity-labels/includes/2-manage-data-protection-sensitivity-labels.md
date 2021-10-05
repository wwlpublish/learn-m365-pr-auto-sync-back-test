Sensitivity labels are definitions that you can apply to documents and emails in your Office apps. For example, you can publish sensitivity labels within your Office environment that classify documents as "Classified", "Confidential", "Internal", "Draft", "Sensitive", and so on.

From there, an organization can build upon the sensitivity labels within its Microsoft 365 environment by automatically encrypting confidential information in documents and emails that are assigned specific labels, such as "Highly Confidential". Other actions can also be assigned to sensitivity labels. For example, you can prohibit sensitive documents from being sent in emails, restrict the use of files for various reasons, and even archive files after a certain period of time.

Sensitivity labels can be used to:<br>

 -  **Provide protection settings that include encryption and content markings.** Organizations can tie sensitivity labels with other actions on a document. For example, an organization can configure a label, such as a "Confidential" label, so that when it's applied to a document or email, the content is automatically encrypted and a "Confidential" watermark is applied to the content. Content markings can be displayed in headers, footers, and watermarks. Encryption can also restrict what actions authorized people can take on the content.
 -  **Protect content in Office apps across different platforms and devices.** This feature is supported by Word, Excel, PowerPoint, and Outlook on the Office desktop apps and Office on the web. It's also supported on Windows, macOS, iOS, and Android.
 -  **Protect content in third-party apps and services by using Microsoft Cloud App Security.** With Cloud App Security, organizations can detect, classify, label, and protect content in third-party apps and services, such as SalesForce, Box, or DropBox. They can do so even if the third-party app or service doesn't read or support sensitivity labels.
 -  **Protect containers that include Teams, Microsoft 365 Groups, and SharePoint sites.** This feature enables organizations to set privacy settings, external user access and external sharing, and access from unmanaged devices.
 -  **Extend sensitivity labels to Power BI.** When organizations turn on this capability, they can apply and view labels in Power BI. They can also protect data when it's saved outside the service.
 -  **Extend sensitivity labels to assets in Azure Purview.** When organizations turn on this capability, currently in preview, they can apply their sensitivity labels to assets such as SQL columns, files in Azure Blob Storage, and more.
 -  **Extend sensitivity labels to third-party apps and services.** Using the Microsoft Information Protection SDK, third-party apps can read sensitivity labels and apply protection settings.
 -  **Classify content without using any protection settings.** In its simplest design, sensitivity labels are used when organizations just want to classify their content. They have no plans on tying labels with protection settings. This design provides users with a visual mapping of classification to their organization's label names. Organizations can also use the labels to generate usage reports and see activity data for its sensitive content. Based on this information, organizations can always choose to apply protection settings later.

In all these cases, sensitivity labels in Microsoft 365 can help organizations take the right actions on the right content. With sensitivity labels, you can classify data across your organization, and enforce protection settings based on that classification.

The following image shows available sensitivity labels in Excel, from the Home tab on the Ribbon. In this example, the applied label displays on the status bar.

:::image type="content" source="../media/sensitivity-label-in-excel-254e8a24.png" alt-text="screenshot shows available sensitivity labels in Excel, from the Home tab on the ribbon":::


For more information about these and other scenarios that are supported by sensitivity labels, see [Common scenarios for sensitivity labels](/microsoft-365/compliance/get-started-with-sensitivity-labels?azure-portal=true). New features are being developed all the time that support sensitivity labels, so you might also find it useful to reference the [Microsoft 365 roadmap](https://www.microsoft.com/microsoft-365/roadmap?azure-portal=true).

### What a sensitivity label is

When you assign a sensitivity label to content, it's like a stamp that's attached to a document. Sensitivity labels are:

 -  **Customizable.** Customizable labels are specific to your organization and business needs. You can create categories for different levels of sensitive content in your organization. For example, Personal, Public, General, Confidential, and Highly Confidential.
 -  **Clear text.** Because a label is stored in clear text in the metadata for files and emails, third-party apps and services can read it and then apply their own protective actions, if necessary.
 -  **Persistent.** Because a label is stored in metadata for files and emails, the label roams with the content, no matter where it's saved or stored. The unique label identification becomes the basis for applying and enforcing the policies that you configure.

When viewed by users, a sensitivity label appears like a tag on apps that they use. This design enables sensitivity labels to be easily integrated into an organization's existing workflows.

Each item that supports sensitivity labels can have a single sensitivity label applied to it. Documents and emails can have both a sensitivity label and a retention label applied to them.

:::image type="content" source="../media/sensitivity-label-on-email-2751eaea.png" alt-text="screenshot showing sensitivity label on an email":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers."