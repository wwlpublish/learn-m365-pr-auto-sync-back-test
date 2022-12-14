The following diagram identifies the steps required to complete a cutover migration.

:::image type="content" source="../media/cutover-migration-fa2c1135.png" alt-text="diagram shows the steps required to complete a cutover migration":::


The following list describes each numbered step in this diagram in greater detail:

1.  **Communicate changes to users and verify your domains in Microsoft 365.** An organization must let its users know about the migration and how it impacts them. It should provide them with instruction as to the tasks that must be completed before, during, and after migration. As a best practice, companies should ask their users to reduce their mailbox size as much as possible and empty their **Deleted Items** folder. They must also verify all the existing SMTP domains in their Microsoft 365 tenants; otherwise, these SMTP addresses can't be used in Exchange Online.

2.  **Prepare your servers and optionally create empty mail-enabled security groups**. An organization should prepare its on-premises Exchange servers to allow Outlook Anywhere communication for Microsoft 365. Outlook Anywhere requires a third-party trusted TLS/SSL certificate with a principal name that matches the external host name of the published service. Self-signed certificates can't be used. The [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365?azure-portal=true) tool can verify the connectivity. In preparing for the cutover migration, an organization can optionally create empty mail-enabled security groups. Because the migration service can't detect whether on-premises Active Directory groups are security groups, it can't configure any migrated groups as security groups in Microsoft 365. If an organization wants to have security groups in Microsoft 365, it must first configure an empty mail-enabled security group in Microsoft 365 before starting the cutover migration.

3.  **Connect Microsoft 365 to the source email system**. As a preparatory task, an organization can create a migration endpoint in Microsoft 365 that connects to its source email system. If it doesn't create a migration endpoint, the migration wizard will create one when it creates a migration batch.

4.  **Migrate mailboxes**. To start migrating its mailboxes, an organization must use the Cutover Migration wizard to create a migration batch. This process will start a synchronization. Once the migration batch is finished, verify that all messages were successfully migrated. The migration batch will automatically run a delta-synchronization every 24 hours on all mailboxes to migrate any newly arrived messages to their respective Exchange Online mailboxes.

5.  **Change Autodiscover and MX record to Microsoft 365**. An organization must change its Autodiscover DNS record and DNS MX record of all its SMTP domains. Doing so will enable new email to be delivered to Microsoft 365. As a best practice, an organization should wait a day or two to ensure the DNS settings are propagated to all the other SMTP servers on the Internet so that no messages are transferred to its old mail server.

6.  **Verify routing**. After an organization verifies that all email is being routed to Microsoft 365, it should run a final delta-synchronization using its migration batch between its source email system and Microsoft 365. Once this task is complete, the organization can delete the migration batch to stop the synchronization.

7.  **Assign Exchange licenses and optionally Decommission Exchange servers**. In this first post-migration task, an organization must grant Exchange licenses to its migrated users in Microsoft 365. If it fails to do so, the users will be soft-deleted after 30 days. Once there are no messages being sent in the organization's source Exchange environment, it can optionally decommission the servers since they're no longer needed.

8.  **Send a welcome message to users**. Once an organization completed the migration, it should send a Welcome message to its users. This message should let them know about Microsoft 365 and how to sign into their new mailboxes in Exchange Online.
