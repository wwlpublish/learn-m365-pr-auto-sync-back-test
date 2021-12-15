Before examining the mailbox migration options, it’s important that you understand the difference between migration and coexistence.

 -  **Migration**. Migration is the process of moving user data from a source messaging system to Exchange Online. When migrating your email data, you want to move the mailboxes from your existing messaging system to Exchange Online as quickly as possible. You want to avoid maintaining mailboxes in both systems for a long period of time. There are various types of migrations, each of which has different requirements.
 -  **Coexistence.** Also known as a hybrid configuration, coexistence is the process of maintaining mailboxes simultaneously in both your existing Exchange environment and Exchange Online. While this option is limited to Exchange environments, it typically deals with upgrades from on-premises deployments to hybrid deployments. Coexistence doesn't require that you move your mailboxes all at once from your existing system to Exchange Online, as is the case with a migration. In fact, most organizations who implement a hybrid deployment don't plan on moving completely to the cloud in the short term. In a coexistence, you can move mailboxes between your on-premises mail servers and Exchange Online as your business allows, and without the users noticing a difference. As such, coexistence provides the smoothest way to move mailboxes from the user perspective, but it also requires the greatest effort for messaging administrators.

The following table summarizes when to use migration and coexistence. There may be other contributing factors, depending on your business needs.

:::row:::
  :::column:::
    **Migration Approach**
  :::column-end:::
  :::column:::
    **Source Email Server**
  :::column-end:::
  :::column:::
    **Mechanism**
  :::column-end:::
  :::column:::
    **When to use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cutover migration
  :::column-end:::
  :::column:::
    Exchange 2007 or later
  :::column-end:::
  :::column:::
    Migrates all mailboxes at one time.
Uses Outlook Anywhere connection to mailboxes.
Requires manual Outlook profile updates.
  :::column-end:::
  :::column:::
    When you can migrate all data within an acceptable time (for example, over a day or weekend).
Your organization has fewer than 2000 users.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Staged migration
  :::column-end:::
  :::column:::
    Exchange 2007
  :::column-end:::
  :::column:::
    Requires Azure AD Connect for directory synchronization.
Uses Outlook Anywhere connection to mailboxes.
Requires manual Outlook profile updates.
  :::column-end:::
  :::column:::
    Your organization has more than 2000 users.
When you want to move your entire email organization to Exchange Online and manage user accounts in Microsoft 365, but the cutover option isn't suitable for you.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Minimal Hybrid Configuration / Express Migration
  :::column-end:::
  :::column:::
    Exchange 2010 or later
  :::column-end:::
  :::column:::
    Requires Azure AD Connect for directory synchronization.
Configures hybrid but without federation-related features like free/busy.
Automatic Outlook profile updates.
  :::column-end:::
  :::column:::
    You use hybrid-only for migration.
You plan to move to Exchange online and don't need a full hybrid configuration.
You need to move users between your on-premises Exchange and Microsoft 365.
You need Exchange on-premises for recipient administration purposes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Full Hybrid Configuration
  :::column-end:::
  :::column:::
    Exchange 2010 or later
  :::column-end:::
  :::column:::
    Requires Azure AD Connect for directory synchronization.
Full featured Exchange federation between on-premises and Exchange Online organization.
Automatic Outlook profile updates.
  :::column-end:::
  :::column:::
    You have the needs for a long-term coexistence between your on-premises Exchange and Microsoft 365.
You need to move users between your on-premises Exchange and Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    IMAP migration
  :::column-end:::
  :::column:::
    Any IMAP-accessible email server
  :::column-end:::
  :::column:::
    IMAP connection to user mailboxes.
Needs manual Outlook profile updates.
  :::column-end:::
  :::column:::
    You only need to migrate your user’s emails and its folder structure.
You're migrating from a third-party mail system providing IMAP access.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PST migration
  :::column-end:::
  :::column:::
    Any mail server that can store PST files.
  :::column-end:::
  :::column:::
    Migration tool to connect to PST files.
PST files are transferred to Microsoft 365 using either Network upload or Drive shipping.
  :::column-end:::
  :::column:::
    You have a large amount of mailbox data that needs to be migrated to Microsoft 365.
You run IMAP/POP3 servers and your clients can export PST files (for example, use Microsoft Outlook).
You don't want to overutilize your Internet connectivity during migration.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cross-tenant migration
  :::column-end:::
  :::column:::
    Any mailbox from one tenant to another Microsoft 365 tenant.
  :::column-end:::
  :::column:::
    Implement an organizational relationship.
Configure the Move Mailbox application in Azure, EXO Migration Endpoint, and the EXO Organization Relationship.
  :::column-end:::
  :::column:::
    For tenants in hybrid or cloud only deployments, or any combination of the two.When combining multiple Microsoft 365 tenants.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Third-party migration (for example, IBM Domino, Novell Groupwise, and so on)
  :::column-end:::
  :::column:::
    Any other email server
  :::column-end:::
  :::column:::
    Third-party migration tool for migration.
  :::column-end:::
  :::column:::
    When none of the previously mentioned options work for you, and you want to migrate your user’s mailboxes to Microsoft 365.
  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.