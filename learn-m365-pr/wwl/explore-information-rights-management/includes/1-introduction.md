Leakage of potentially sensitive information can not only be costly for an organization, but it can also have wide-ranging impact on the organization and its business, employees, customers, and partners. Local and industry regulations increasingly govern how certain types of information are stored, transmitted, and secured. To avoid violating applicable regulations, organizations must protect themselves against intentional, inadvertent, or accidental information leakage. The consequences of violating these regulations include financial damages, damages to image and credibility, or loss of competitive advantage.

Traditional solutions, such as email encryption and file permissions, often lack the necessary enforcement tools that apply uniform policies to prevent information leakage. For example, a user sends an email containing sensitive information that's **Company Confidential** and shouldn't be **Forwarded**. After the message is delivered to the recipient, the sender or the organization no longer has technical control over the information. The recipient can willfully or inadvertently forward the message to external email accounts using features such as automatic forwarding rules. By doing so, your organization will be subjected to serious information leakage risks.

In Microsoft 365, you can use Information Rights Management (IRM) features to apply persistent protection to email and attachments sent from Outlook and Outlook on the web, and Office documents created in Word, Excel, and PowerPoint by the use of user restrictions. In Microsoft 365, IRM uses Azure Rights Management Services (RMS) as part of Azure Information Protection (AIP) to provide a complete IRM solution.

Azure Information Protection is subscription-based. It enables administrators to set up specific labels that can be used to lock down, restrict access, or encrypt emails or documents depending on the label configuration the Microsoft 365 Enterprise Administrator defines. These options are all applied from the end-user perspective on either the Office document or the email they're creating.

With effective use of RMS, organizations can:

 -  reduce security risks from wire-tapping and man-in-the-middle attacks.
 -  prevent unwarranted access of data, such as emails and files, that's in-transit or at rest by an unauthorized user who doesn't have appropriate permissions.

These actions are accomplished by encrypting the data and applying policies on the data to limit or allow the actions by the consumer of the data.

RMS uses extensible rights markup language (XrML)-based certificates and licenses to certify computers and users, and to protect content. When content such as a document or a message is protected using RMS, an XrML license containing the rights that authorized users have to the content is attached. To access IRM-protected content, Microsoft-enabled applications must get a use license for the authorized user from the RMS cluster.

In this module, you'll examine the features of Information Rights Management. This exploration begins with an analysis of the encryption options that are available in Microsoft 365. You'll then explore how IRM protects email in Exchange and documents in SharePoint. The module concludes with a comparison of IRM protection and AIP classification.

After completing this module, you'll be able to:

 -  Identify the different Microsoft 365 encryption options.
 -  Explain how Information Rights Management (IRM) can be used in Exchange.
 -  Configure IRM protection for Exchange mails.
 -  Explain how IRM can be used in SharePoint.
 -  Apply IRM protection to SharePoint documents.
 -  Compare IRM protection and AIP classification.
