There are many methods you can use to import mail, calendar, and contact information into Exchange Online. The strategy you choose depends on what email system you run on-premises, how large your organization is, and how long you want to take to complete your migration.

## Migrating from Exchange Server

In complex, real-world business environments, Exchange Server provides critical communication and collaboration tools. It's likely to impact your bottom line if email functionality goes wrong. If migrations are performed carelessly, problems often arise and can prevent users from doing their jobs. 
Microsoft provides the mail migration advisor to help you execute trouble-free migrations from your current mail system to Exchange Server in Microsoft 365. This tool asks you questions about your current environment and proposes the most appropriate migration path. The migration strategies you'll learn about in this section are all included in the migration advisor.

### Migrating in a hybrid environment

The most flexible method for migrating to Exchange Online from an Exchange Server on-premises system is to create a hybrid environment. You extend your on-premises organization into the cloud by creating a Microsoft 365 tenant and synchronizing it with your Exchange servers.

The mail migration advisor might suggest one of these three hybrid environment migration strategies:

- **Full hybrid migrations**. Consider a full hybrid migration if you have a large company, with thousands of mailboxes. A complete, integrated hybrid environment is set up and remains in place for a sustained period. There is a seamless experience for users during the migration. For example, there's a single global address list and free/busy information is shared both on-premises and in the cloud. You can migrate mailboxes in small batches to Exchange Online, troubleshooting as you go, and taking your time to make the transition as smooth as possible.
- **Minimal hybrid migrations**. Consider a minimal hybrid migration if you have several hundred to 2,000 mailboxes and want to complete your migration in a few weeks. In a minimal hybrid migration, there's a single global address list but enhanced functionality, such as synchronized free/busy information, is not implemented. This is a good option to consider if you want to minimize the administrative effort associated with the migration, and don't mind limiting functionality slightly during the migration project.
- **Express hybrid migrations**. Consider an express hybrid migration if you have a small Exchange Server system, with fewer than 500 mailboxes, and you want to complete your move within two weeks. In this strategy, there's a one-time synchronization of user accounts from the on-premises system to the cloud. You can then move mailboxes into Exchange Online with minimal disruption.

All these hybrid migration strategies have the following features:

- Usernames and passwords will synchronize from on-premises to the cloud.
- Users don't have to recreate their Outlook profile to start using the new system.
- Mail flows smoothly between all users during the migration.
- Each user experiences almost no email downtime.

### Migrating all mailboxes at once

In a cutover migration, all your mailboxes are moved to Exchange Online at once, in a single operation. You don't need to configure a hybrid environment because the two systems don't coexist for long. Consider this type of migration when:

- Your on-premises email system is Exchange Server 2003 or later.
- You have fewer than 150 mailboxes to migrate; cutover migration supports up to 2,000 mailboxes but such migrations take a long time and are difficult to manage.
- You want to complete the migration as fast as possible.

A cutover migration is simple to execute and quick, but users must recreate their Outlook profile and need new credentials after the migration has completed. There might be an interruption in email service during the migration so consider executing it over the weekend or another period of low demand.

### Migrating in batches

In a staged migration, you move mailboxes from the on-premises Exchange servers to Exchange Online in batches. No hybrid environment is required so this form of migration can be used for older versions of Exchange Server.

Consider this type of migration when:

- You have more than 2,000 mailboxes.
- Your on-premises email system is Exchange 2003 or Exchange 2007.

As for cutover migrations, there is some disruption during the migration. Users must, for example, recreate their Outlook profiles.

## Migrating from other email systems

If your on-premises email system is something other than Exchange, or if it's a version of Exchange earlier that 2003, you can still import emails from clients into Exchange Online. Use IMAP or Personal Storage Table (.pst) files.

### Migrating from IMAP-enabled email systems

In the Exchange Online admin center, there's a tool you can use to migrate email from any set of mailboxes that supports IMAP4. This protocol is widely used but bear in mind that it only supports access to emails. You can't use this protocol to migrate calendar or contact information from systems outside Exchange Online.

Consider using this migration strategy when you have Exchange Server 2000 or earlier on-premises or when you have some other email system that supports IMAP4. To complete the import process, you must first create a comma-separated text file that lists the email addresses and security credentials for each mailbox that you want to import. Exchange Online connects to all those mailboxes and copies all the emails it finds into the corresponding mailbox in Exchange Online.

### Using the Microsoft 365 Import service

Microsoft email clients, including Outlook, can use .pst files to save emails, calendar events, and contacts on local hard drives or network shared folders. You can import the content of .pst files into Exchange Online by using the Microsoft 365 Import service.

There are two ways to send .pst files to Microsoft for import:

- **Network upload**. Upload the .pst files to an Azure Storage account by using the AzCopy.exe command-line tool.
- **Drive shipping**. Copy the .pst files to a physical hard drive, which you post to Microsoft. You use the **WAImportExport.exe** tool to execute this copy, so that the files are encrypted with BitLocker. Azure staff copy the data to an Azure Storage account in your subscription.

When the .pst files are present in Azure Storage, you can create a PST import job to get the data into the correct mailboxes in Exchange Online. You must supply a comma-separated file that maps each .pst file to a mailbox that already exists in Exchange Online.

> [!NOTE]
> Any user who has a .pst file from an old email system can import that data into their inbox by using the tools in Outlook. If you need to support a small number of these users, direct them to Outlook and show them how to add the .pst file to their profile. They can then copy all the data they wish to keep into the correct folders in their mailbox.
>

## Learn more

- [Ways to migrate multiple email accounts to Office 365](/exchange/mailbox-migration/mailbox-migration?azure-portal=true)
- [Use the Office 365 mail migration advisor](/exchange/mail-migration-jump?azure-portal=true)
- [Exchange Server hybrid deployments](/exchange/exchange-hybrid?azure-portal=true)
- [New Exchange Online migration options](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-exchange-online-migration-options/ba-p/606109?azure-portal=true)
