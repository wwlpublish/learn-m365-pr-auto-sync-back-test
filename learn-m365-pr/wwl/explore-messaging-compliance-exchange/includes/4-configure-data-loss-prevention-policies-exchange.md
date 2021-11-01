Data loss prevention (DLP) policies are simple packages that are collections of mail flow rules (also known as transport rules). These rules contain specific conditions, actions, and exceptions that filter messages and attachments based on their content.

DLP policies can use the full power of mail flow rules to detect and then act on messages in transit. For example, a mail flow rule can detect content that violates an organization's DLP policies by conducting deep content analysis through:

 -  Keyword matches.
 -  Dictionary matches.
 -  Text pattern matches through regular expressions.
 -  Other content examination techniques.

Document fingerprinting is also an available feature of DLP for Exchange to detect sensitive information in standard forms.

DLP policies that you create in the Exchange admin center (EAC) for your on-premises Exchange Server work similar to data loss prevention in the Microsoft 365 Compliance center, except that they're unable to protect as many different locations. Data loss prevention in Exchange Server includes the following considerations:

 -  DLP is a premium feature that requires an Exchange Enterprise Client Access License (CAL).
 -  In hybrid environments where some mailboxes are in on-premises Exchange and some are in Exchange Online, DLP policies are only applied in Exchange Online. Messages that are sent between on-premises users don't have DLP policies applied because the messages don't leave the on-premises environment.
 -  Document fingerprinting is no longer available in Exchange Online, but it's still available for Exchange Server deployments.

### Sensitive information types in DLP policies

Data loss prevention includes 80 sensitive information types that are ready for you to use in your DLP policies. A sensitive information type is defined by a pattern that can be identified by a regular expression or a function. Corroborative evidence such as keywords and checksums can also be used to identify a sensitive information type. Confidence level and proximity are also used in the evaluation process.

**Additional reading**. For more information, see [Sensitive information types in Exchange Server](/exchange/policy-and-compliance/data-loss-prevention/sensitive-information-types?azure-portal=true).

### Document fingerprinting

Document fingerprinting can identify a document format that should be monitored. If your organization has a standard form for an information type such as a customer record or financial reports, document fingerprinting can allow DLP to recognize that information type. Documents that match the fingerprint can then be prevented from being sent outside the organization.

> [!NOTE]
> Document fingerprinting doesn't detect sensitive information if the file is password protected, contains only images, or doesn't contain all the text that was in the original fingerprinted document.

### DLP policies in Exchange hybrid

In Exchange hybrid, DLP policies work through mail flow rules. As a result, they can only act on messages that are routed through the organization’s transport servers.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.