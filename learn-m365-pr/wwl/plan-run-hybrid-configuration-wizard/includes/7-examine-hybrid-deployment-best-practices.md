Messaging administrators should consider the following best practices when implementing a hybrid deployment:

 -  **Use the Hybrid Configuration Wizard (HCW) app**. You configure a hybrid deployment in two ways: either manually or by using the HCW app. It's highly recommended that you use the HCW app because the wizard automatically handles all necessary configuration settings for you.
 -  **Understand the requirements of Minimal Hybrid, Exchange Classic, and Exchange Modern Hybrid**. To test the Exchange Server on-premises environment from the Internet, use the [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365?azure-portal=true).
 -  **Understand why your organization wants to implement a hybrid deployment**. Don't try to use “everything” if your organization only wants to move archive mailboxes to Exchange Online.
 -  **Start slowly, and then speed up when everything works**. At the beginning, move mailboxes only for people who can acceptably work with a short outage. After you gain confidence that the hybrid deployment works reliably, move the other mailboxes. Always move test mailboxes first and then consider moving production mailboxes.
 -  **Don't change the MX resource record at first.** Change it only after you've verified the hybrid deployment works.
 -  **Use multiple MRS Proxy endpoints where possible.** The Mailbox Replication service (MRS) has a proxy endpoint that is required for cross-forest mailbox moves and remote move migrations between your on-premises Exchange organization and Microsoft 365. Depending on your organization’s Internet connection, it's wise to have multiple MRS proxy endpoints if you also have multiple Internet inbound connections and certificates.

**Additional reading.** For more information, see [Office 365 Mail Flow best practices](/exchange/mail-flow-best-practices/mail-flow-best-practices?azure-portal=true).
