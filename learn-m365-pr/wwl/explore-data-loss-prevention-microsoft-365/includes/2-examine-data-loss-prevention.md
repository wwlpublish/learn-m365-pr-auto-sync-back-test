Data loss prevention (DLP) in Microsoft 365 identifies, monitors, reports, and protects sensitive personal data such as Social Security and credit card numbers through deep content analysis. It also helps users understand and manage data risk. By using the Security &amp; Compliance Center, DLP can be configured to identify sensitive information in:

 -  email messages
 -  SharePoint and OneDrive for Business sites
 -  files created in Word, Excel, and PowerPoint

Administrators have a full range of controls and can customize the level of restrictions for their organization by creating DLP policies. DLP policies protect content by enforcing rules that include conditions and actions. DLP policies can be configured to:

 -  warn users when sensitive data is identified in email and documents.
 -  block users from sharing sensitive data to unauthorized users.
 -  block users from sharing sensitive data altogether.

The content search mechanisms of DLP are also used by more services than just Exchange, SharePoint, and OneDrive. They're also used by Azure Information Protection to find and protect sensitive data in a wide variety of elements.<br>

Policies are typically based on policy templates provided in the service. But in cases when your organization has its own specific requirements, you can also create a custom DLP policy from scratch.<br>

### Document fingerprinting

Information workers in your organization handle many kinds of sensitive information during a typical day. In the Security and Compliance Center, document fingerprinting makes it easier for you to protect this information by identifying standard forms that are used throughout your organization.

Document fingerprinting is a Data Loss Prevention feature that converts a standard form into a sensitive information type. These types can later be used in the rules of your DLP policies. For example, an organization can create a document fingerprint based on a blank patent template. It can then create a DLP policy that detects and blocks all outgoing patent templates with sensitive content filled in.

Optionally, you can set up policy tips to notify senders that they may be sending sensitive information, and the sender should verify that the recipients are qualified to receive the patents. This process works with any text-based forms used in your organization. Other examples of forms that you can upload include:<br>

 -  Government forms.
 -  Health Insurance Portability and Accountability Act (HIPAA) compliance forms.
 -  Employee information forms for Human Resources departments.
 -  Custom forms created specifically for your organization.

Ideally, your organization already has an established business practice of using certain forms to transmit sensitive information. After you upload an empty form to be converted to a document fingerprint and set up a corresponding policy, the DLP detects any documents in outbound mail that match that fingerprint.

The DLP content search mechanisms make it possible to not only search for keywords and patterns in content, but also for a whole Document Fingerprint. In fact, in can search for document fingerprint even if it has no further sensitive information inside or as a support to other search patterns.

#### How document fingerprinting works

You've probably already guessed that documents don't have actual fingerprints. However, the name helps explain the feature. In the same way that a person's fingerprints have unique patterns, documents have unique word patterns. When you upload a file, Microsoft 365 Data Loss Prevention:

 -  identifies the unique word pattern in the document.
 -  creates a document fingerprint based on that pattern.
 -  uses that document fingerprint to detect outbound documents containing the same pattern.

That's why uploading a form or template creates the most effective type of document fingerprint. Everyone who fills out a form uses the same original set of words and then adds their own words to the document. As long as the outbound document isn't password protected and contains all the text from the original form, DLP can determine if the document matches the document fingerprint.<br>

> [!IMPORTANT]
> For now, DLP can use document fingerprinting as a detection method in Exchange Online only.

### Sensitive information types in DLP

A sensitive information type is defined by a pattern that can be identified by a regular expression or a function. Data loss prevention in Microsoft 365 includes definitions for many common sensitive information types across many different regions that are ready for organizations to use. These types include credit card numbers, bank account numbers, national ID numbers, and passport numbers, to name but a few. Besides default information types, Microsoft 365 supports the customization and creation of new sensitive information types, such as company-specific health care numbers.

When a DLP policy looks for a sensitive information type such as a credit card number, it doesn't just look for a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

 -  Format
 -  Keywords
 -  Internal functions to validate checksums or composition
 -  Evaluation of regular expressions to find pattern matches
 -  Other content examination

This design helps DLP detection achieve a high degree of accuracy when examining content that may potentially violate organizational DLP policies.

**Additional reading.** For more information, see [What the sensitive information types look for](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”