Microsoft 365 provides a range of migration options that organizations must consider before moving their email data to Exchange Online. These options involve both migration and coexistence strategies. It's important to understand the difference between them.

 -  **Migration.** Migration is the process of moving user data from a source messaging system to Exchange Online. In a migration scenario, an organization wants to move its existing mailboxes to Exchange Online as quickly as possible, without the need to maintain a long-term coexistence.
 -  **Coexistence.** Coexistence is another term for a fully hybrid environment. It's the process of maintaining an organization's existing on-premises messaging system and Exchange Online at the same time, for a short or long-term period. Unlike migration, coexistence enables an organization to move mailboxes between its on-premises mail servers and Exchange Online, without its users noticing a difference. As such, coexistence provides the smoothest way to move mailboxes from the user perspective, but it also requires the most work for mail administrators.<br><br>With coexistence, on-premises server products are synchronized or integrated to cloud enterprise services. In this state, an organization can either pool resources to one location or have a mixed bag of resources located on-premises and in the cloud. For example, an organization could integrate its on-premises Exchange environment with Exchange Online. In doing so, it may need to keep some mailboxes local to its environment for proprietary purposes. However, it may have many of the mailboxes housed in the cloud for ease of use and backup purposes.

The following table summarizes when to use migration and coexistence. Keep in mind, however, that there may be other contributing factors, depending on an organization's business needs.

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
    

If an organization can migrate all data within an acceptable time, such as over a day or weekend.


If an organization has fewer than 2000 users.


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
    

When an organization:

 -  uses hybrid only for migration.
 -  plans to move to Exchange Online and don't need a full hybrid configuration.
    
 -  must move users between its on-premises Exchange Server deployment and Microsoft 365.
    
 -  needs Exchange on-premises for recipient administration purposes.


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


Full-featured Exchange federation between on-premises Exchange Server deployment and Exchange Online organization.


Automatic Outlook profile updates.


  :::column-end:::
  :::column:::
    

If an organization:

 -  requires long-term coexistence between its on-premises Exchange Server deployment and Microsoft 365.
    
 -  must move users between its on-premises Exchange Server deployment and Microsoft 365.


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
    

If an organization:

 -  only needs to migrate its user’s emails and its folder structure.
    
 -  is migrating from a third-party mail system providing IMAP access.


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

 -  Network upload
 -  Drive shipping


  :::column-end:::
  :::column:::
    

If an organization:

 -  has a large amount of mailbox data that needs to be migrated to Microsoft 365.
    
 -  runs IMAP/POP3 servers and its clients can export PST files (for example, using Microsoft Outlook).
    
 -  doesn't want to overutilize its Internet connectivity during migration.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Third-party migration (for example, IBM Domino and Novell Group wise)


  :::column-end:::
  :::column:::
    

Any other email server


  :::column-end:::
  :::column:::
    

Third-party migration tool for migration.


  :::column-end:::
  :::column:::
    

If none of the previously mentioned options work for an organization, and it wants to migrate its user’s mailboxes to Microsoft 365.


  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”