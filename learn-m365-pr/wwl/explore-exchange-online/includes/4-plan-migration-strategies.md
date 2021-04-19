Microsoft 365 provides a range of migration options that organizations must consider before moving their email data to Exchange Online. These options involve both migration and coexistence strategies. It's important to understand the difference between them.

 *  **Migration.** Migration is the process of moving user data from a source messaging system to Exchange Online. In a migration scenario, you want to move your existing mailboxes to Exchange Online as quickly as possible, without the need to maintain a long-term coexistence.
 *  **Coexistence.** Coexistence is another term for a fully hybrid environment. It's the process of maintaining your existing on-premises messaging system and Exchange Online at the same time, for a short or long-term period. Unlike migration, coexistence enables you to move mailboxes between your on-premises mail servers and Exchange Online, without your users noticing a difference. As such, coexistence provides the smoothest way to move mailboxes from the user perspective, but it also requires the most work for mail administrators.
    
    With coexistence, you sync or integrate on-premises server products to cloud enterprise services. In this state, you can either pool resources to one location or have a mixed bag of resources located on-premises and in the cloud. For example, you could integrate your on-premises Exchange environment with Exchange Online. In doing so, you may need to keep some mailboxes local to your environment for proprietary purposes; however, you may have many of the mailboxes housed in the cloud for ease of use and backup purposes.

The following table summarizes when to use migration and coexistence. Keep in mind, however, that there may be other contributing factors, depending on your business needs.

:::row:::
  :::column:::
    

**Migration approach**


  :::column-end:::
  :::column:::
    

**Source email server**


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
    

Cutover Exchange Migration


  :::column-end:::
  :::column:::
    

Exchange 2010 or later


  :::column-end:::
  :::column:::
    

Migrates all mailboxes at one time.


Uses Outlook Anywhere connection to mailboxes.


Requires manual Outlook profile updates.


  :::column-end:::
  :::column:::
    

If you can migrate all data within an acceptable time, such as over a day or weekend).


If your organization has fewer than 2000 users.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Minimal (Express) Hybrid Configuration


  :::column-end:::
  :::column:::
    

Exchange 2010 or later


  :::column-end:::
  :::column:::
    

Requires Azure AD Connect for directory synchronization.


Configures hybrid but without federation functionality.


Automatic Outlook profile updates.


  :::column-end:::
  :::column:::
    

When you:

 *  use hybrid only for migration.
 *  plan to move to Exchange Online and don't need a full hybrid configuration.
    
 *  must move users between your on-premises Exchange and Microsoft 365.
    
 *  need Exchange on-premises for recipient administration purposes.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Full Hybrid Configuration (coexistence)


  :::column-end:::
  :::column:::
    

Exchange 2010 or later


  :::column-end:::
  :::column:::
    

Requires Azure AD Connect for directory synchronization.


Full-featured Exchange federation between on-premises and Exchange Online organization.


Automatic Outlook profile updates.


  :::column-end:::
  :::column:::
    

If you:

 *  require long-term coexistence between your on-premises Exchange and Microsoft 365.
    
 *  must move users between your on-premises Exchange and Microsoft 365.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

IMAP Migration


  :::column-end:::
  :::column:::
    

Any IMAP-accessible email server


  :::column-end:::
  :::column:::
    

IMAP connection to user mailboxes.


Needs manual Outlook profile updates.


  :::column-end:::
  :::column:::
    

If you:

 *  only need to migrate your user’s emails and its folder structure.
    
 *  are migrating from a third-party mail system providing IMAP access.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

PST migration


  :::column-end:::
  :::column:::
    

Any mail server that can store PST files


  :::column-end:::
  :::column:::
    

Migration tool to connect to PST files.


PST files are transferred to Microsoft 365 using either:

 *  Network upload
 *  Drive shipping


  :::column-end:::
  :::column:::
    

If you:

 *  have a large amount of mailbox data that needs to be migrated to Microsoft 365.
    
 *  run IMAP/POP3 servers and your clients can export PST files (for example, using Microsoft Outlook).
    
 *  don't want to overutilize your Internet connectivity during migration.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Third-party migration (for example, IBM Domino and Novell Groupwise)


  :::column-end:::
  :::column:::
    

Any other email server


  :::column-end:::
  :::column:::
    

Third-party migration tool for migration.


  :::column-end:::
  :::column:::
    

If none of the previously mentioned options work for you and you want to migrate your user’s mailboxes to Microsoft365.


  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”