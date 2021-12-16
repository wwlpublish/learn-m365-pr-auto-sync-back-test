As is the case with any type of deployment or installation process, an organization should spend enough time planning its cutover or staged migration. By doing so, it will be ready almost every contingency that may occur. Organizations should consider the cutover or staged migration planning factors, system requirements, and limitations that were covered previously, plus their business requirements. Once an organization has finished its migration plan, it's ready to complete a cutover or staged migration using the Exchange Admin Center (EAC) or Windows PowerShell.

This unit examines how to create and manage migration batches in the Exchange Admin Center.

### Create a migration endpoint for a cutover or staged migration

Creating a migration endpoint to connect Microsoft 365 to your on-premises Exchange server is a prerequisite to creating a migration batch for a cutover or staged migration. Once the batch is created, you must verify this connection. The connection can be verified as a separate task in the EAC or during creation of the migration batch.

The following steps explain how to create a migration endpoint:

1.  In the EAC, navigate to **recipients** &gt; **migration**.
2.  On the menu bar, select the **More (…)** icon and select **Migration endpoints**.
3.  On the **Select the migration endpoint type** page, select **Outlook Anywhere,** and then select **Next**.
4.  On the **Enter on-premises account credentials** page, enter the e-mail address of an on-premises user, the sign-in information of an on-premises Exchange administrator, and then select **Next**.
5.  Microsoft 365 tests the connection to the source server and displays the connection settings. If Microsoft 365 was unable to detect your settings, you need to type an Exchange server name that you plan to use for migration, the RPC proxy server name, authentication, and your mailbox permission. Then select **Next**.
6.  On the **Enter general information** page, enter a Migration endpoint name, the maximum concurrent migrations (max. 300), and the maximum incremental syncs (max. 300). Then select **New** to create the migration endpoint.

    :::image type="content" source="../media/migration-endpoint-c7e032f8.png" alt-text="screenshot of new migration endpoint page to enter general information":::


### Move mailboxes using a cutover migration

The following steps describe how to create a migration batch and migrate mailboxes using a cutover migration in the EAC: ‎

1.  In the EAC, navigate to **recipients** &gt; **migration**.
2.  On the menu bar, select the **plus (+) sign** icon and then select **Migrate to Exchange Online**.
3.  On **new migration batch** page, select **Cutover migration**, and then select **Next**.

‎    :::image type="content" source="../media/new-migration-batch-f8d564a3.png" alt-text="screenshot of new migration endpoint page to select the migration type":::


4.  On the next page, you can either select a migration endpoint if you previously created one, or you can have the wizard create a new one for you. Then select **Next**.
5.  On the **Confirm the migration endpoint** page, verify that the migration endpoint settings are correct, and then select **Next**.
6.  On the **Move configuration** page, type the name of the migration batch, and then select **Next**. The batch name is displayed in the list of migration batches on the Migration page after you create the migration batch.
7.  On the **Start the batch** page, select the recipient(s) that receive a report migration report once the migration is completed, and then choose one of the following options:
    
     -  **Automatically start the batch**. The migration batch is started as soon as you save the new migration batch with a status of Syncing.
     -  **Manually start the batch later**. The migration batch is created but isn't started. The status of the batch is set to Created.
8.  Select **New** to create the migration batch. The new migration batch is displayed on the migration dashboard.

Once the migration batch is created, you must complete the following tasks to finish the cutover migration:‎.

1.  **Verify the migration is working.** While the migration is in progress, you can follow the batch’s synchronization status on the migration dashboard. If there are errors, you can view a log file that provides more information about each error. You can also verify whether the users were created in the Office 365 admin center as the migration proceeds. After the migration is done, the sync status is set to **Synced**.
2.  **Delete the migration batch.** After you change the MX record and verify that all email is being routed to Microsoft 365 mailboxes, notify the users that their mail is going to Microsoft 365. At this point, you can delete the cutover migration batch. When you delete a cutover migration batch, the migration service cleans up any records related to the migration batch and then deletes the migration batch. Complete the following steps to delete a cutover migration batch from the list of migration batches on the migration dashboard:
    
    1.  In the EAC, navigate to **recipients** &gt; **migration**.
    2.  On the migration dashboard, select the batch and then select **Delete**.
    3.  Verify that the migration batch is no longer listed on the migration dashboard.

### Move mailboxes using a staged migration

Before you can create a migration batch and begin moving mailboxes using a staged migration, you must first create a CSV file that includes a user batch. Each record in the CSV file must include the following information (in this order), each of which is separated by a comma:

 -  **EmailAddress** (required). This field is the email address for a user’s on-premises mailbox.
 -  **Password** (optional). This field is the password that will be set on the user’s new Exchange Online mailbox. A password must have a minimum length of eight characters.
 -  **ForceChangePassword** (optional). When a user logs in to their new Exchange Online mailbox for the first time, this option specifies whether the user must change the password. Use either True or False for the value of this parameter. Other values are invalid.

The following example is a CSV file that would migrate two users from contoso.com to Exchange Online using staged migration. The first record is the heading line that displays the sequence of fields in each record.

**EmailAddress,Password,ForceChangePassword**

SaraD@contoso.com,Pa$$w0rd,False

RobY@contoso.com,Pa$$w0rd,False

Once the CSV batch file is created, you must complete following steps to create a migration batch and migrate mailboxes using a staged migration in the EAC:‎.

1.  In the EAC, navigate to **recipients** &gt; **migration**.
2.  On the menu bar, select the **plus (+) sign** icon and then select **Migrate to Exchange Online**.
3.  On the **new migration batch** page, select **Staged migration**, and then select **Next**.
4.  On the **Select the users** page, select **Browse,** select the CSV file to use for this migration batch, and then select **Next**.
5.  On the next page, you can either select a migration endpoint if you previously created one, or you can have the wizard create a new one for you. Then select **Next**.
6.  On the **Confirm the migration endpoint** page, verify that the migration endpoint settings are correct, and then select **Next**.
7.  On the **Move configuration** page, type the name of the migration batch and then select **Next**. The batch name is displayed in the list of migration batches on the Migration page after you create the migration batch.
8.  On the **Start the batch** page, select the recipient(s) that should receive a migration report once the migration is completed, and then choose one of the following options:
    
     -  **Automatically start the batch**. The migration batch is started as soon as you save the new migration batch with a status of Syncing.
     -  **Manually start the batch later**. The migration batch is created but isn't started. The status of the batch is set to Created.
9.  Select **New** to create the migration batch. The new migration batch is displayed on the migration dashboard.

Once the migration batch is created, you must complete the following tasks to finish the staged migration:

1.  **Verify the migration is working.** While the migration is in progress, you can follow the batch’s synchronization status on the migration dashboard. If there are errors, you can view a log file that provides more information about each error. You can also verify whether the users were created in the Microsoft 365 admin center as the migration proceeds. After the migration is done, the sync status is set to Synced.
2.  **Delete the migration batch.** After the migration batch is synchronized and the users in the batch are connected to their Exchange Online mailboxes, you should wait at least another 72 hours and then delete the migration batch. Complete the following steps to remove the batch from the list of migration batches on the migration dashboard:
    
    1.  In the EAC, navigate to **recipients** &gt; **migration**.
    2.  On the migration dashboard, select the batch and then select **Delete**.
    3.  Verify that the migration batch is no longer listed on the migration dashboard.
3.  **Repeat the process until all your users are moved to Exchange Online.** If you have more users whose mailboxes must be migrated to Exchange Online, create a new CSV file and start a new migration batch.

> [!NOTE]
> ‎You can run batches simultaneously or one at a time. Remember, each migration batch has a limit of 2,000 mailboxes.

Once all mailboxes have been moved to Exchange Online, you must:

 -  Change the DNS MX records of your SMTP domain to point to Microsoft 365.
 -  Plan the decommissioning of your source Exchange servers.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.