Microsoft 365 Data Loss Prevention (DLP) policies can use classification properties or item properties to identify sensitive items in a document. For example, organizations can use:

 -  Windows Server File Classification infrastructure (FCI) properties
 -  SharePoint document properties
 -  third-party system document properties

For example, an organization may use Windows Server FCI to identify items that contain personal data. It then classifies the document by setting the **Personally Identifiable Information** property to **High**, **Moderate**, **Low**, **Public**, or **Not PII**. The type and number of occurrences of personal data found in the document determines the value entered in this property.

A DLP policy can identify documents that have a property set to specific values, such as High or Medium. When this condition is true, the policy will take an action such as blocking access to those files. The same policy can have another rule that takes a different action if the property is set to Low, such as sending an email notification. These examples show how DLP integrates with Windows Server FCI. The goal of this integration is to protect Office documents uploaded or shared to Microsoft 365 from Windows Server-based file servers.

This module examines how to create a DLP policy that uses an FCI classification property. You'll step through the process of creating the managed property in SharePoint Online. You'll then review the process of creating the actual policy with a Security and Compliance Center PowerShell session.

After completing this module, you'll be able to:

 -  Describe how to work with managed properties for DLP policies.
 -  Explain how SharePoint Online creates crawled properties from documents.
 -  Describe how to create a managed property from a crawled property in SharePoint Online.
 -  Explain how to use Windows PowerShell to create a DLP policy with rules that apply to managed properties.
