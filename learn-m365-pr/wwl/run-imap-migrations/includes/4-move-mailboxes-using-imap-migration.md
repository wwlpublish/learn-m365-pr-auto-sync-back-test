Once an organization has finished planning its IMAP migration, it's ready to move its user mailboxes. Completing an IMAP migration involves:

1.  Satisfying the migration prerequisites, such as:
    
     -  Registering any SMTP domains in Microsoft 365.
     -  Creating all the target mailboxes in Exchange Online.
     -  Create a migration endpoint to connect Microsoft 365 to your email system.
2.  Creating an IMAP migration batch.
3.  Running the IMAP migration wizard.

Complete the following steps to run an IMAP migration in the Exchange Admin Center (EAC):

1.  Create a migration endpoint to connect Microsoft 365 to your email system by completing the following steps:
    
    1.  In the Microsoft 365 admin center, select **Show all**, and then under **Admin centers** select **Exchange**. This step will open the Exchange admin center (EAC) for Exchange Online.
    2.  In the classic **Exchange admin center**, navigate to **recipients** &gt; **migration**.
    3.  On the menu bar, select the **More (ellipsis)** icon and then select **Migration endpoints**.
    4.  On the **migration endpoints** window, select the **+ (New)** icon to create a new migration endpoint.
    5.  On the **Select the migration endpoint type** page (as seen in the following screenshot), select **IMAP** and then select **Next**.
    6.  On the **IMAP migration configuration** page, enter your source IMAP server name and configure the required access settings such as authentication, encryption, and port. Then select **Next**. The migration service uses the settings to test the connection to your email server.
    7.  On the **Enter general information** page, type a Migration endpoint name, such as **IMAP-endpoint**. Leave the other two boxes blank to use the default values. Select **New**.

:::image type="content" source="../media/migration-endpoint-wizard-623e3efe.png" alt-text="screenshot of page to create new migration endpoint in the Migration Endpoint Wizard":::


2.  Create your migration batch and migrate your mailboxes by completing the following steps:
    
    1.  In the EAC, navigate to **recipients &gt; migration**.
    2.  In the menu bar, select the **plus (+) sign** icon and then select **Migrate to Exchange Online**.
    3.  On the **Select a migration type** page, select the **IMAP migration** option, and then select **Next**.
    4.  On the **Select the users** page, select **Browse** to specify the migration CSV file that you previously prepared. Once you select the file, Microsoft 365 validates it and displays the number of users listed in the file as the number of mailboxes to migrate. If the number displayed from the file doesn’t match the number of users you planned to migrate, check your CSV file for any issues.
    5.  On the **IMAP migration configuration** page, select **Next** and select the migration endpoint you created.
    6.  On the **Move configuration** page, type the name of the migration batch. You can also optionally enter the names of the folders you want to exclude from migrating, such as Shared, Junk Email, and Deleted. Then select **Next**.
    7.  On the **Start the batch** page, select **automatically start the batch**. The migration starts as soon as you save the new migration batch. The batch status is first created and changes to syncing after the migration starts. As soon as the initial move is completed, the status will change to "**synced"**.
    8.  If any issues occur during the migration, you can use the [IMAP Migration Troubleshooter](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration?azure-portal=true) to investigate the problems.

3.  Stop the email synchronization. After your sync is completed, you must change the DNS MX record of all your domains to point to Microsoft 365. This step can take up to a day to synchronize to all other DNS servers on the Internet. You can verify the change since no new messages should be sent to your old IMAP server.
4.  To finish the migration, allow either 72 hours for the final delta-synchronization to complete or manually start the migration batch again. Once you're sure that all messages are migrated, you should remove the migration batch.

**Additional reading.** For more information, see [Migrate other types of IMAP mailboxes to Microsoft 365](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-other-types-of-imap-mailboxes?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.