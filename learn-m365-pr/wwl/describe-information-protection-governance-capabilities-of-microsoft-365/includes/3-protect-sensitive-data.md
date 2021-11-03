During its lifecycle, data will be created, shared, stored, and deleted. Data needs to be protected at all stages in its lifecycle, and wherever it's located.

## Protect your data with sensitivity labels

Sensitivity labels don’t just serve to classify your data. They also help protect your sensitive data.  As we learned in the previous module, after a sensitivity label is applied to an email or document, any configured protection settings for that label are enforced on the content.

**Automatically apply a sensitivity label to content**.  When you create a sensitivity label, you can automatically assign that label to content when it matches conditions that you specify. As a result, the protection associated with that label is automatically applied.

The ability to apply sensitivity labels to content automatically is important because you don’t need to:

- Train your users when to use each of your classifications.
- Rely on users to classify all content correctly.
- Ensure users know about your policies. Instead, they can focus on their work.

To learn more, visit [Apply a sensitivity label to content automatically](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically).

**Use sensitivity labels to apply encryption**.  You can restrict access to content to which a sensitivity label is applied. For example, with the encryption settings for a sensitivity label, you can protect content so that:

- Only users within your organization can open a confidential document or email.
- Only users in a specific department can edit and print a document or email, while all other users in your organization can only read it.
- Users cannot forward or copy information from an email.
- Users cannot open a document after a specified date.

When a document or email is encrypted, access to the content is restricted, so that:

- It can be decrypted only by users authorized by the label's encryption settings.
- Remains encrypted no matter where it resides, inside or outside your organization, even if the file's renamed.
- It is encrypted both at rest (for example, in a OneDrive account) and in transit (for example, email as it traverses the internet).

The encryption settings are available when you [create a sensitivity label](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels) in the Microsoft 365 compliance center or the Microsoft 365 Defender portal.

## Office 365 Message Encryption (OME)

People often use email to exchange sensitive information, such as financial data, legal contracts, patient health information, etc. As a result, mailboxes can become repositories for large amounts of potentially sensitive information, and information leakage can become a serious threat to your organization.

With **Office 365 Message Encryption**, your organization can send and receive encrypted email messages between people inside and outside your organization. Office 365 Message Encryption works with Outlook.com, Yahoo!, Gmail, and other email services. Email message encryption helps ensure that only intended recipients can view the message content.

Office 365 Message Encryption is an online service that's built on **Microsoft Azure Rights Management (Azure RMS)**, which is used by Azure Information Protection (AIP).  OME includes encryption, identity, and authorization policies to help secure your email.

With OME, users can then encrypt email messages and a variety of attachments. For more information, visit [How Office 365 Message Encryption works](https://docs.microsoft.com/microsoft-365/compliance/ome).

## Data loss prevention (DLP)

Data Loss Prevention (DLP) is designed to protect sensitive information and prevent its inadvertent disclosure and is implemented through policies.  With DLP policies, you can identify, monitor, and automatically protect sensitive information across Office 365. Data loss prevention policies can use sensitivity labels and [sensitive information types](https://docs.microsoft.com/microsoft-365/compliance/sensitive-information-type-entity-definitions) to identify sensitive information.

With a DLP policy, you can:

- **Identify sensitive information** across many services, such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams.  For example, you can identify any document containing a credit card number that's stored in any OneDrive for Business site, or you can monitor just the OneDrive sites of specific people.
- **Prevent the accidental sharing of sensitive information**. For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document or block the email from being sent.
- **Monitor and protect sensitive information** in the desktop versions of Excel, PowerPoint, and Word. Just like in Exchange Online, SharePoint Online, and OneDrive for Business, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.
- **Help users learn how to stay compliant** without interrupting their workflow. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip.
- **View DLP reports** showing content that matches your organization's DLP policies.  To assess how your organization is complying with a DLP policy, you can see how many matches each policy and rule has over time. 

DLP detects sensitive information by using deep content analysis and not just a simple text scan. This deep content analysis uses keyword matches, dictionary matches, the evaluation of regular expressions, internal functions, and other methods to detect content that matches your DLP policies. Potentially only a small percentage of your data is considered sensitive. A DLP policy can identify, monitor, and automatically protect just that data, without impeding or affecting people who work with the rest of your content.

For more information, visit [Overview of data loss prevention](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies).

## Windows Information Protection

Windows Information Protection (WIP) is a set of technologies that protect your organization from accidental or malicious data leaks, without significant changes to your enterprise environment or apps. It provides this protection to both enterprise-owned devices and BYOD devices, and it does so without interfering with employees’ regular workflows.

For more information, visit [Protect your enterprise data using Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
