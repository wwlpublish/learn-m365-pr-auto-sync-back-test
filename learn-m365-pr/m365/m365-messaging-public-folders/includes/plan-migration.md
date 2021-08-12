Using Exchange Online in an organization that has existing on-premises Exchange servers gives companies the option to run a hybrid configuration. In a hybrid configuration, you'll need to decide where your public folders reside. Only one version of a public folder can exist, and it must be on the on-premises Exchange server or in Exchange Online.

## Understand the limits of public folders in Microsoft 365

Before you start to plan the migration, you need to survey current public folder usage. With your business users, you have to decide which folders to migrate. You can do this manually or use Exchange PowerShell commands to return the details for every folder:

```powershell
Get-PublicFolder "\" -Recurse | Get-PublicFolderStatistics | `
Select FolderPath, ItemCount, TotalAssociatedItemSize, TotalDeletedItemSize, TotalItemSize | fl
```

This command recursively returns the size and number of items in each public folder. With this information, you can compare your company's requirements against what is supported by Microsoft 365 Exchange Online.

- Maximum number of public folders you can migrate in one batch: 250,000
- Maximum number of public folders you can create in Exchange Online: 500,000
- Maximum number of subfolders per public folder: 10,000
- Maximum size of a public folder mailbox: 50 GB but, for E3 or E5 plans, you can have 100 GB
- Maximum number of public folder mailboxes: 1,000
- Maximum total size of all public folder mailboxes: 50 TB

You'll also need to identify what kinds of public folders your organization is using.

- Public folders on Exchange server 2010 SP3 RU8 are called **legacy** public folders.
- Newer versions of Exchange server public folders are called **modern** public folders.

> [!NOTE]
> If your version of Exchange server is older than 2010 SP3 RU8, you'll need to upgrade to at least this version before you can migrate public folders to Exchange Online.
>

## Using PST files to migrate public folders

Use this approach if you have very few folders, or they are small, and their permissions are simple. Using PST files isn't the best approach because you'll lose any permissions granted to public folders. Exchange Online manages public folders and mailboxes automatically. Exchange Online auto-splits mailboxes when they exceed their size quotas. This process might take up to two weeks to catch up, if the mailboxes are large.

If your organization decides that this is the right approach, take these steps to make the migration as successful as possible:

1. Note the permissions on your existing public folders, as these aren't migrated.
2. Download the **ModernPublicFolderToMailboxMapGenerator.ps1** script from the Exchange 2013/2016/2019 Public Folders Migration Scripts website (link in **Learn more** section below).
3. Run the script to create a .csv file that maps source public folders to public folder mailboxes in your Exchange Online destination. This file is used to calculate the correct number of public folder mailboxes in Exchange Online.
4. Create the public folder mailboxes that you'll need, based on the contents of the mapping file.
5. Use the **New-PublicFolder** cmdlet (link in **Learn more** section below) to create the uppermost public folder in each of the public folder mailboxes, using the Mailbox parameter.
6. Export and import the PST files using Outlook.
7. Assign permissions to the migrated public folders.

## Migrate public folders to Exchange Online

The steps you need to take to complete a batch migration of public folders are detailed and complex. You'll need to follow the steps for either a legacy or modern batch migration as set out below. At a high level, you'll need to complete the same kinds of steps for either folder.

1. Download and save migration scripts.
2. Prepare your environments for the migration.
3. Generate the required .csv files.
4. Create the new public folder mailboxes in Exchange Online.
5. Start the migration request.
6. Lock down on-premises public folders—your users should expect a minimum 48 hours of downtime.
7. Finalize the migration.
8. Test and, if successful, unlock the public folders.
9. Remove the on-premises public folders.

## Learn more

- [Exchange 2013/2016/2019 Public Folders Migration Scripts download](https://www.microsoft.com/download/details.aspx?id=54855&azure-portal=true)
- [Use batch migration to migrate legacy public folders to Office 365 and Exchange Online](/exchange/collaboration-exo/public-folders/batch-migration-of-legacy-public-folders?azure-portal=true)
- [Use batch migration to migrate Exchange Server public folders to Exchange Online](/Exchange/collaboration/public-folders/migrate-to-exchange-online?azure-portal=true)
- [New-PublicFolder PowerShell cmdlet](/powershell/module/exchange/sharing-and-collaboration/new-publicfolder?azure-portal=true)
