The following diagram identifies the steps required to run a staged migration in an Exchange 2003 or 2007 environment.

:::image type="content" source="../media/staged-migration-1afffb6c.png" alt-text="diagram shows the steps required to run a staged migration in an Exchange 2003 or 2007 environment.":::


The following list identifies each step in this diagram in greater detail:

1.  **Administrator runs synchronization, which creates users in Microsoft 365**. You must set up directory synchronization between your on-premises Active Directory and Microsoft 365 using Azure AD Connect. Directory synchronization synchronizes all objects including users, groups, and contacts to Microsoft 365 and provides a common global address list (GAL). Azure AD Connect creates the mail-enabled users in Microsoft 365, which will automatically be converted to mailboxes during the mailbox migration.
2.  **Create comma-separated value (CSV) file**. To start the migration batches, you need a CSV file that includes all users that will be migrated.
3.  **Administrator runs staged migration batch**. The Staged Migration wizard will start the migration by creating a migration batch for the CSV file. The wizard will create the Exchange Online mailbox and configure mail forwarding for each user in the CSV file.
4.  **Migration report sent to admin**. Exchange Online sends a status email message to the administrator once the migration batch is complete. This status message lists the number of mailboxes that were successfully migrated and how many couldn’t be migrated. The message also includes links to migration statistics and error reports that contain more detailed information.
5.  **All mailboxes of migration batch are migrated**. Once the migration batch starts a synchronization, copying all the items from the mailboxes that are in the migration batch will begin. Once the migration batch is finished, you must verify that all messages were successfully migrated. The migration batch will automatically run a delta-synchronization for all mailboxes every 24 hours to migrate any newly arrived messages to their respective Exchange Online mailboxes.
6.  **Administrator converts mailboxes**. After a migration batch is complete and you verified that all mailboxes in the batch are successfully migrated, you must convert the on-premises mailboxes to mail-enabled users. Once you complete this conversion, you can manage these users using your on-premises Exchange admin tools.
7.  **Users in the initial batch can connect to Exchange Online.** The users that are included in the initial migration batch can use their mailboxes once they've been migrated. You must also remember to convert the mailboxes in the source environment to mail-enabled users so that you can manage them in your on-premises Exchange environment.
8.  **Create comma-separated value (CSV) file for more batches of users**. Once you finish the first migration batch, you can create new migration batches using a CSV file that includes all users that should be migrated.
9.  **Run staged migration batches for more users**. Start migrating your other mailboxes using the Staged Migration wizard. Once these batches are finished, don’t forget that you must also convert the source mailboxes to mail-enabled users so that you can manage them in your on-premises Exchange environment (see step 6).
10. **Resolve any issue**. Resolve any issues that you see in the migration batches and continue to create new batches as needed.
11. **All users can connect to Exchange Online from Outlook**. At this step, you should verify that all users can connect and use their Exchange Online mailboxes.
12. **Complete the Microsoft 365 post-migration tasks**. To finish the transition to Exchange Online and Microsoft 365, you should complete the following post-configuration tasks:
    
    1.  Assign licenses to Microsoft 365 users (if not already done).
    2.  Configure the DNS MX record to point to your Microsoft 365 tenant so that email is delivered directly to the Exchange Online mailboxes. Allow up to 24 hours for DNS synchronization on the Internet.
    3.  Change the Autodiscover DNS record to point to your Microsoft 365 organization.
    4.  After you verify that all email is being routed to Microsoft 365, you should do a final delta-synchronization using your migration batches between your source email system and Microsoft 365.
    5.  Once the final delta-synchronization is complete, you can delete the migration batches to stop the synchronization.
13. **Complete the on-premises Exchange Server post-migration tasks.** Once there are no messages being sent in your source Exchange 2003 or 2007 environment, you can decommission all your servers but one. You must have one Exchange server available to complete any necessary management tasks. It's recommended that you keep one Exchange server on-premises to use the Exchange Admin Center and Exchange Management Shell to manage your users, groups and contacts. Having one Exchange Server available is necessary because you can't manage all user attributes in Exchange Online after enabling directory synchronization.
