Information workers in an organization handle many kinds of sensitive information during a typical day. In the Microsoft Purview compliance portal, Document Fingerprinting makes it easier for an organization to protect this information. It does so by identifying standard forms that are used throughout the organization. This unit examines the concepts behind Document Fingerprinting and how to create one by using Windows PowerShell.

### Basic scenario for Document Fingerprinting

Document Fingerprinting is a Microsoft Purview Data Loss Prevention (DLP) feature. It converts a standard form into a sensitive information type. This type can then be used in the rules of an organization's DLP policies. For example, an organization can:

1.  Create a document fingerprint based on a blank patent template.
2.  Create a DLP policy that detects and blocks all outgoing patent templates with sensitive content filled in.
3.  Optionally set up policy tips to notify senders they may be sending sensitive information. Any sender receiving the policy tip should verify the recipients are qualified to receive the patents.

This process works with any text-based forms used in an organization. Other examples of forms that an organization can upload include:

 -  Government forms
 -  Health Insurance Portability and Accountability Act (HIPAA) compliance forms
 -  Employee information forms for Human Resources departments
 -  Custom forms created specifically for an organization

Let's consider the following example. Contoso already has an established business practice of using certain forms to transmit sensitive information. Contoso will begin by uploading an empty form to be converted to a document fingerprint. Once it's created the document fingerprint, Contoso will create a new data classification rule. This rule will use the document fingerprint that it previously created. Contoso will then set up a corresponding DLP policy, and it will add the rule to the policy. With the document fingerprint now assigned to a DLP policy, the DLP service will detect any documents in outbound mail that match that fingerprint.

### How Document Fingerprinting works

We all know that documents don't have actual fingerprints. However, the "document fingerprinting" name helps explain the feature. In the same way that a person's fingerprints have unique patterns, documents have unique word patterns. When an organization uploads a file, Microsoft Purview DLP:

1.  Identifies the unique word pattern in the document.
2.  Creates a document fingerprint based on that pattern.
3.  Uses that document fingerprint to detect outbound documents containing the same pattern.

This process shows why uploading a form or template creates the most effective type of document fingerprint. Everyone who fills out a form uses the same original set of words. They then add their own words to the document. As long as the outbound document isn't password protected and contains all the text from the original form, DLP can determine if the document matches the document fingerprint.

> [!IMPORTANT]
> For now, DLP can only use document fingerprinting as a detection method in Exchange Online.

Organizations can use any form as the basis for creating a document fingerprint. The following example shows what happens if you create a document fingerprint based on a patent template.

:::image type="content" source="../media/document-fingerprinting-d2167213.png" alt-text="Diagram showing a patent document being compared to the document fingerprint of a patent template.":::


The patent template contains the blank fields "Patent title," "Inventors," and "Description" and descriptions for each of those fields—**that's the word pattern**. The original patent template should be in one of the supported file types and in plain text. When the organization uploads the patent template:

1.  DLP converts this word pattern into a document fingerprint. The fingerprint is a small Unicode XML file containing a unique hash value representing the original text.
2.  The patent fingerprint is saved as a data classification in Active Directory.
    
    > [!NOTE]
    > As a security measure, the original document itself isn't stored on the service; only the hash value is stored. The original document can't be reconstructed from the hash value.
3.  The patent fingerprint then becomes a sensitive information type the organization can associate with a DLP policy.
4.  After the organization associates the fingerprint with a DLP policy, DLP detects any outbound emails containing documents that match the patent fingerprint. It then deals with them according to the organization's policy.

For example, assume you want to set up a DLP policy that prevents regular employees from sending outgoing messages containing patents. DLP will use the patent fingerprint to detect patents and block those emails. Alternatively, you may want to allow your legal department to send patents to other organizations because it has a business need for doing so. You can allow specific departments to send sensitive information by creating exceptions for those departments in your DLP policy. Or, you can allow them to override a policy tip with a business justification.

### Supported file types

Document Fingerprinting supports the same file types that are supported in mail flow rules (also known as transport rules). For a list of supported file types, see [Supported file types for mail flow rule content inspection](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection?azure-portal=true).

> [!NOTE]
> Mail flow rules and Document Fingerprinting don't support the .dotx file type. This situation can be confusing because .dotx is a template file in Word. When you see the word "template" in this unit, it refers to a document that an organization has established as a standard form, and not the template file type.

Document Fingerprinting won't detect sensitive information in the following cases:

 -  Password protected files.
 -  Files that contain only images.
 -  Documents that don't contain all the text from the original form used to create the document fingerprint.
 -  Files greater than 10 MB.

### Use PowerShell to create a classification rule package based on Document Fingerprinting

Currently, you can only create a document fingerprint using the Security &amp; Compliance PowerShell module.

DLP uses classification rule packages to detect sensitive content. To create a classification rule package based on a document fingerprint, use the **New-DlpFingerprint** and **New-DlpSensitiveInformationType** cmdlets.

> [!NOTE]
> Because the results of **New-DlpFingerprint** aren't stored outside the data classification rule, you must always run **New-DlpFingerprint** and **New-DlpSensitiveInformationType** or **Set-DlpSensitiveInformationType** in the same PowerShell session.

Let's walk through an example that shows how to create a classification rule package based on document fingerprinting.

1.  In this example, you'll create a new document fingerprint based on the file **C:\\My Documents\\Contoso Employee Template.docx**. You'll store the new fingerprint as a variable so that you can use it with the **New-DlpSensitiveInformationType** cmdlet in the same PowerShell session.
    
    ```powershell
    $Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
    
    $Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
    ```
2.  Now that you've created the document fingerprint, you should create a new data classification rule. For this example, let's name it **Contoso Employee Confidential**. This rule will use the document fingerprint of the file **C:\\My Documents\\Contoso Customer Information Form.docx**.
    
    ```powershell
    $Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
    
    $Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
    
    New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
    ```
3.  You can now use the **Get-DlpSensitiveInformationType** cmdlet to find all DLP data classification rule packages. In this example, **Contoso Customer Confidential** is part of the data classification rule packages list. You'll then add the **Contoso Customer Confidential** data classification rule package to a DLP policy. While you can complete this step in the Microsoft Purview compliance portal, this example adds a rule to an existing DLP policy named **ConfidentialPolicy**.
    
    ```powershell
    New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
    ```
4.  You can also use the data classification rule package in mail flow rules in Exchange Online. To run this command, you must first connect to Exchange Online PowerShell. Keep in mind that it takes time for the rule package to sync from the Microsoft Purview compliance portal to the Exchange admin center.
    
    ```powershell
    New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
    ```

Microsoft Purview Data Loss Prevention now detects documents that match the **Contoso Customer Form.docx** document fingerprint.
