In organizations that use Microsoft Exchange Server, their users may also use public folders. In a migration scenario, once an organization migrates its mailboxes to Exchange Online, it can then configure public folder coexistence if it's running in a hybrid configuration, whether its users are in Exchange Online or on-premises. However, if an organization wants to remove its on-premises Exchange servers, it must migrate its public folders to Exchange Online.

Organizations should consider the following limitations when planning a public folder migration to Exchange Online:

 -  Maximum number of public folders that can be migrated: 250,000
 -  Maximum number of public folders that can be created in Exchange Online: 500,000
 -  Maximum number of subfolders per public folder: 10,000
 -  Maximum size of a public folder mailbox: 50 GB (for Microsoft 365 E3 and E5 plans, you can have 100 GB)
 -  Maximum number of public folder mailboxes: 1000
 -  Maximum total size of all public folder mailboxes: 50 TB

There are two types of public folders:

 -  **Legacy public folders**. Public folders that are in a public folder database on Exchange Server 2010 or earlier.
 -  **Modern public folders**. Public folders that are in a public folder mailbox on Exchange Server 2013 or later.

‎This distinction is important because the requirements are different for each public folder type. The following options are available for migrating public folders:

 -  Migrate legacy public folders to Exchange Online.
 -  Migrate modern public folders to Exchange Online.
 -  Migrate public folders to Microsoft 365 Groups.

### Migrate legacy public folder requirements

Legacy public folders are public folders stored on Exchange 2010 or earlier. To migrate legacy public folders to Exchange Online, your on-premises Exchange servers must meet the following requirements:

 -  The on-premises Exchange Servers must run at least:
    
     -  Exchange 2007 SP3 RU15 or later
     -  Exchange 2010 SP3 RU8 or later
 -  It's recommended that you move all your mailboxes to Exchange Online before migrating legacy public folders.
 -  You don't need to configure a hybrid deployment to migrate legacy public folders.

### Migrate modern public folders requirements

Modern public folders are public folders stored on Exchange Server 2013 or later. To migrate modern public folders to Exchange Online, your on-premises Exchange Servers must meet the following requirements:

 -  If you intend to migrate users to Microsoft 365, you should complete your user migration before migrating your public folders.
 -  You must prepare your Active Directory with Exchange Server 2016 CU4 or later.
 -  Your Exchange Servers must run at least:
    
     -  Exchange Server 2013 CU15 (only in a mixed environment with Exchange Server 2016 or 2019)
     -  Exchange Server 2016 CU4 or later
     -  Exchange Server 2019
 -  You don't need to configure a hybrid deployment to migrate modern public folders.

**Additional reading.** For more information, see [Use batch migration to migrate Exchange Server public folders to Exchange Online](/exchange/collaboration-exo/public-folders/batch-migration-of-legacy-public-folders?azure-portal=true).

### Migrate legacy and modern public folders to Exchange Online

The steps to migrate legacy and modern public folders to Exchange Online are identical; only the requirements are different.

Complete the following steps to migrate legacy and modern public folders to Exchange Online:

1.  **Download the migration scripts**. You must download the Public Folders Migration Scripts package that consists of the following three PowerShell scripts:
    
     -  Export-PublicFolderStatistics.ps1
     -  PublicFolderToMailboxMapGenerator.ps1
     -  Create-PublicFolderMailboxesForMigration.ps1
2.  **Prepare for the migration**. You must prepare your existing Exchange servers and Microsoft 365 for the migration. For example, you must ensure that your existing public folder names don't include special characters like the “\\” (backslash).
3.  **Generate the CSV files**. You use the Export-PublicFolderStatistics.ps1 and PublicFolderToMailboxMapGenerator.ps1 scripts to create the mapping CSV file that includes the required public folder mailboxes and their name.
4.  **Create the public folder mailboxes in Exchange Online**. Use the Create-PublicFolderMailboxesForMigration.ps1 script together with your CSV mapping file to create all required public folder mailboxes in Exchange Online.
5.  **Create and start the migration request**. Create a new Public Migration Batch using your CSV mapping file. Then start the migration batch to begin synchronizing the public folder content to Exchange Online.
6.  **Lock down the public folders on the Exchange server for final migration**. Once the initial synchronization is finished, you must lock down your legacy or modern public folder environment for the final synchronization. During this lock-down, your users can't access the public folders until you unlock them. You should take this step into consideration when planning your migration schedule.
7.  **Complete the public folder migration**. This step includes the final delta-synchronization and completes the public folder migration batch. At this point, the on-premises public folders and the public folders in Exchange Online are identical.
8.  **Test and unlock the public folder migration**. After you complete the migration, you must run tests to ensure the migration was successful. Once that step is complete, unlock the public folders so all mailboxes in Exchange Online can access those folders.

**Additional reading.** The public folder migration steps were simplified for this unit. However, for detailed information, see [Use batch migration to migrate legacy public folders to Office 365 and Exchange Online](/exchange/collaboration-exo/public-folders/batch-migration-of-legacy-public-folders?azure-portal=true).

### Migrate public folders to Microsoft 365 Groups

An organization can optionally move its public folder data to Microsoft 365 Groups in either of two scenarios:

 -  Once it migrated its on-premises public folders to Exchange Online.
 -  It plans to remove its on-premises public folders.

Microsoft 365 Groups is the latest collaboration offering from Microsoft. As such, there are many reasons why they're a preferable solution over public folders, which is a much older technology. In Outlook, for example, Groups can replace mail-enabled public folders altogether.

Public folders can be migrated to Microsoft 365 Groups from the following environments:

 -  Exchange Online
 -  Exchange on-premises
 -  Exchange 2010 SP3 RU8 or later
 -  Exchange 2013 CU15 or later
 -  Exchange 2016 CU4 or later
 -  Exchange 2019

> [!NOTE]
> If your public folders are on-premises, you must have an Exchange hybrid environment set up before you can migrate the public folder data to Microsoft Groups.

Migrating public folder data to Microsoft 365 Groups consists of the following steps:

1.  **Select source.** Choose the public folders that you want to migrate. You can choose any folder containing mail or calendar content.
2.  **Create target.** Create corresponding groups for your folders. Groups can be based on the required configuration, such as members, privacy settings, and data classification.
3.  **Copy data.** Use the migration batch cmdlets to copy data from public folders to Groups.
4.  **Lock source.** Lock the public folders once you've verified the data in Groups.
5.  **Cutover.** Copy any new data that has been created between steps 3 and 4.

An organization's public folders and their corresponding groups will remain online for users during steps 1 through 3. After copying data from public folder to Groups in step 3, the organization can evaluate whether to continue with the rest of the migration. This decision can be based on the Groups experience and whether it suits the organization and its users. For example:

 -  If you’re not satisfied with the Groups experience, you can roll back your migration and resume using public folders at that point.
 -  If you’re satisfied with the Groups experience, then continue with the migration. It's recommended that you back up your original public folders following step 5.
    
     -  If you decide to go back to public folders following the migration, you can still roll back to public folders, provided you saved your backup files from the migration process and you haven't deleted your original public folders.
     -  If you decide to continue using Groups, you can delete the original public folders after completing step 5. However, once the original public folders are removed, you can't roll back to them even if you saved your backup files.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.