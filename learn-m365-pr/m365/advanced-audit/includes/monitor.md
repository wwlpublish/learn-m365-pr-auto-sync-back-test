The new *MailItemsAccessed* auditing action helps you narrow the scope of user account compromises to specific mail items. It's the first audit activity referred to as a crucial event. The goal of using this new auditing action is forensics defensibility. It helps you assert a specific piece of mail data wasn't compromised. The *MailItemsAccessed* mailbox auditing action covers all mail protocols: POP, IMAP, MAPI, EWS, Exchange ActiveSync, and REST. It logs both mail sync and mail bind activities. The access type is recorded in the *OperationProperties* field of the audit record.

Mailbox auditing generates audit records for access to email messages so you can be confident they have not been compromised. In circumstances where it is not certain whether an email was accessed, the assumption is made that it was. Using *MailItemsAccessed* audit records for forensics purposes is typically performed after a data breach has been resolved and the attacker has been removed. To begin your investigation, you should identify the mailboxes that may have been compromised and determine the time frame when the attacker had access to those mailboxes.

## Auditing sync access
Sync operations are recorded when a mailbox is accessed by a desktop version of the Outlook client for Windows or Mac. A significant number of mail items are typically downloaded from Exchange Online to the local computer during the sync operation, so the audit volume generated can be substantial. Instead of generating an audit record for each synced email, Advanced Audit generates an audit event for the mail folder containing the synced items. The assumption should be made that all mail items in the synced folder have been compromised. 

## Auditing bind access
A bind operation occurs when a user accesses an individual email message. For bind access, the *InternetMessageId* of individual messages will be recorded in the audit record. All bind operations that occur within a 2-minute interval are aggregated in a single audit record in the *Folders* field within the *AuditData* property. Each message accessed is identified by its *InternetMessageId*. The number of bind operations aggregated in the record is displayed in the *OperationCount* field in the *AuditData* property.

## Audit records throttling
If more than 1,000 *MailItemsAccessed* audit records are generated in less than 24 hours, Exchange Online will stop generating auditing records for *MailItemsAccessed* activity. This is referred to as “throttling”. *MailItemsAccessed* activity will not be logged for 24 hours after throttling is initiated. If this occurs, there is a chance the mailbox could be accessed during this period without an audit record being generated. The recording of *MailItemsAccessed* activity will be resumed following a 24-hour period. Here are some key considerations: 
- Less than 1 percent of all mailboxes in Exchange Online are throttled.
- When a mailbox is throttling, only audit records for *MailItemsAccessed* activity are not audited. Other mailbox auditing actions are not affected.
- Mailboxes are throttled only for bind operations. Audit records for sync operations are not throttled.
- You should assume *MailItemsAccessed* activity was not recorded in the audit logs if a mailbox is throttled.

## Learn more
- [The MailItemsAccessed mailbox auditing action](https://docs.microsoft.com/microsoft-365/compliance/mailitemsaccessed-forensics-investigations?view=o365-worldwide#the-mailitemsaccessed-mailbox-auditing-action?azure-portal=true)
