After a sensitivity label is applied to an email or document, any configured protection settings for that label are enforced on the content. You can configure a sensitivity label to:

 -  **Encrypt emails and documents to prevent unauthorized people from accessing this data.** Organizations can also choose which users or groups have permissions to complete which actions and for how long. For example, you can choose to allow all users in your organization to modify a document while a specific group in another organization can only view it. Or, instead of administrator-defined permissions, you can allow your users to assign permissions to the content when they apply the label.
    
    For more information about the Encryption settings when you create or edit a sensitivity label, see [Restrict access to content by using encryption in sensitivity labels](/microsoft-365/compliance/encryption-sensitivity-labels?azure-portal=true).
 -  **Mark the content when you use Office apps.** Content can be marked by adding watermarks, headers, or footers to email or documents that have the label applied. Watermarks can be applied to documents but not email. The following example shows a Word document with a sensitivity label in the header and in a watermark.
    
    :::image type="content" source="../media/sensitivity-label-watermark-header-a6ed7114.png" alt-text="screenshot shows a Word document with a sensitivity label in the header and in a watermark":::
    
    
    Some, but not all apps support dynamic markings by using variables. For example, insert the label name or document name into the header, footer, or watermark. For more information, see [Dynamic markings with variables](/microsoft-365/compliance/sensitivity-labels-office-apps?azure-portal=true).

> [!NOTE]
> Watermarks are limited to 255 characters. Headers and footers are limited to 1024 characters, except in Excel. Excel has a total limit of 255 characters for headers and footers but this limit includes characters that aren't visible, such as formatting codes. If that limit is reached, the string you enter isn't displayed in Excel.

 -  **Protect content in containers.** Content in containers, such as sites and groups, can be protected when you enable the capability to [use sensitivity labels with Microsoft Teams, Microsoft 365 groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites?azure-portal=true).<br><br>You can't configure protection settings for groups and sites until you enable this capability. This label configuration doesn't result in documents or emails being automatically labeled. Instead, the label settings protect content by controlling access to the container where content can be stored. These settings include privacy settings, external user access and external sharing, and access from unmanaged devices.

 -  **Apply the label automatically to files and emails, or recommend a label.** Organizations can choose how to identify sensitive information they want labeled. The label can either be applied automatically, or you can prompt users to apply the label that you recommend. If you recommend a label, the prompt displays whatever text you choose, as seen in the following example.
    
    :::image type="content" source="../media/sensitivity-label-prompt-for-required-label-3d7cb90c.png" alt-text="screenshot showing prompt to apply the recommended label":::
    
    
    For more information about the Autolabeling for files and emails settings when you create or edit a sensitivity label, see: [Apply a sensitivity label to content automatically](/microsoft-365/compliance/apply-sensitivity-label-automatically?azure-portal=true) for Office apps, and [Automatically label your data in Azure Purview](/azure/purview/create-sensitivity-label?azure-portal=true).

### When Office apps apply content marking and encryption

Office apps apply content marking and encryption with a sensitivity label differently, depending on the app you use.

:::row:::
  :::column:::
    **App**
  :::column-end:::
  :::column:::
    **Content marking with a sensitivity label**
  :::column-end:::
  :::column:::
    **Encryption**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Word, Excel, PowerPoint on all platforms
  :::column-end:::
  :::column:::
    Immediately
  :::column-end:::
  :::column:::
    Immediately
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outlook for PC and Mac
  :::column-end:::
  :::column:::
    After Exchange Online sends the email
  :::column-end:::
  :::column:::
    Immediately
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outlook on the web, iOS, and Android
  :::column-end:::
  :::column:::
    After Exchange Online sends the email
  :::column-end:::
  :::column:::
    After Exchange Online sends the email
  :::column-end:::
:::row-end:::


Solutions that apply sensitivity labels to files outside Office apps do so by applying labeling metadata to the file. In this scenario, content marking from the label's configuration isn't inserted into the file but encryption is applied.

When those files are opened in an Office desktop app, the content markings are automatically applied by the Azure Information Protection unified labeling client when the file is first saved. The content markings aren't automatically applied when you use built-in labeling for desktop, mobile, or web apps.

Scenarios that include applying a sensitivity label outside Office apps include:

 -  The scanner, File Explorer, and PowerShell from the Azure Information Protection unified labeling client.<br>
 -  Autolabeling policies for SharePoint and OneDrive.<br>
 -  Exported labeled and encrypted data from Power BI.<br>
 -  Microsoft Defender for Cloud Apps.<br>

For these scenarios, using their Office apps, a user with built-in labeling can apply the label's content markings by temporarily removing or replacing the current label and then reapplying the original label.
