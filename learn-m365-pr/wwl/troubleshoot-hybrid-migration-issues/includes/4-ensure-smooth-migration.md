When you migrate from Exchange Server on-premises to Exchange Online there are many components that must interact correctly for the migration to complete successfully. Usually, these components are created by Exchange migration tools and don't cause problems, but occasionally you might need to investigate and reconfigure them.

In your digital camera manufacturing company, you have set up a hybrid deployment and you intend to migrate all your mailboxes to Exchange Online over the next six months. You will migrate users in small batches of 10 to 30 according to their team membership. You've started the first mailbox move operations but you've experienced errors. You need to resolve these problems and migrate the remaining mailboxes smoothly.

Here, you'll learn how to ensure that all migration components are configured correctly and working well and how to resolve common migration errors.

## Migration types

You can migrate to Exchange Online from many different email systems including on-premises Exchange Server, IMAP servers, Google Workspace, and Lotus Notes. There are several different approaches to migration and the one you choose depends on the source system, the size of your organization, and your operational requirements.

> [!NOTE]
> It's not within the scope of this troubleshooting course to cover all aspects of migration planning and execution, which is a large and complicated subject. However, because the type of migration influences the problems that you might have to troubleshoot, this unit starts with a review of migration types. For more information about migration techniques, see the links in the Learn more section below.

These are the approaches you can use to migrate from on-premises Exchange Server systems to Exchange Online:

- **Cutover migration.** In cutover migration, you use the migration tools in Exchange Admin Center to migrate all your mailboxes in a single action. Use this method if you want to migrate quickly and you have fewer than 150 mailboxes.
- **Minimal hybrid migration.** In minimal hybrid migration, you use the Hybrid Migration Wizard (HCW) to migrate all your recipients over a couple of weeks or less. Use this method if you want to migrate over a few days and have fewer than 150 mailboxes. This method is not supported for Exchange Server 2003 or Exchange Server 2007 organizations. It's also referred to as **express migration**.
- **Staged migration.** In staged migration, you use migration tools in Exchange Admin Center to migrate mailboxes in batches over a prolonged period. Use this method if you have Exchange Server 2003 or Exchange Server 2007 and more than 150 mailboxes.
- **Exchange hybrid migration.** In hybrid migration, you use the HCW to create a stable hybrid deployment of Exchange and then migrate mailboxes to Exchange Online. Use this method if you have Exchange Server 2010 or later and more than 150 mailboxes, or if you want to migrate users in small batches over time.

## Troubleshoot endpoints

In all these migration types, migration endpoints are a critical object and must be created successfully for a smooth operation. The migration endpoint is an object in Exchange Online that stores:

- The type of endpoint. For example, this endpoint might be an Exchange remote move endpoint or an IMAP endpoint.
- The full-qualified domain name of the on-premises server to migrate from.
- The credentials of an administrative account in the on-premises system.

Endpoints are usually created by the migration tools in Exchange Admin Center or the HCW. These tools try connecting to the endpoint to ensure that the details you have entered are correct. If you receive an error at this stage in the migration wizard, check the values you entered.

:::image type="content" source="../media/04-endpoint-creation-error.png" alt-text="Screenshot showing an endpoint creation error in the Exchange Admin Center migration tool.":::

Firewalls commonly prevent the creation of endpoints, resulting in similar errors. To avoid these, make sure that your firewalls allow incoming connections on TCP port 443.

Endpoints can also cause migration problems if they are out of date. For example, if the administrator's credentials change, then Exchange Online will not be able to connect to the on-premises server.

To investigate these issues, use Exchange Online PowerShell to list your endpoints and their properties:

```powershell
Get-MigrationEndpoint | FL
```

To make corrections, you can use the `Set-MigrationEndpoint` cmdlet. For example, to update the administrator's credentials:

``` powershell
$Credentials = Get-Credential

Set-MigrationEndpoint -Name ContosoExchServerEndpoint -Credentials $Credentials
```

## Troubleshoot the Mailbox Replication Service

When you're performing a migration from an on-premises Exchange Server system, you need an Exchange remote move endpoint in the Exchange Online system that identifies a server in the Exchange on-premises organization. The server you identify is:

- In Exchange 2010, the server that runs client access services.
- In Exchange 2013 and later, the server has the mailbox role.

This server must have the Mailbox Replication Service proxy enabled for migrations to work.

To check the location of the proxy and whether it is enabled, run this command on an on-premises Exchange Server:

```powershell
Get-WebServicesVirtualDirectory | Select Identity, MRSProxyEnabled
```

If the proxy is not enabled, correct the problem by using this command:

```powershell
Set-WebServicesVirtualDirectory "EXCHSERVER\EWS (Default Web Site)" -MRSProxyEnabled $True
```

In the above command, replace `EXCHSERVER\EWS (Default Web Site)` with the identity value you retrieved from the previous command.

PowerShell on the on-premises Exchange Server includes the `Test-MRSHealth` cmdlet, which you can use to ping the components of the Mailbox Replication Service and obtain additional status information:

```powershell
Test-MRSHealth
```

You can also test whether a connection can be made from Exchange Online to the proxy by using the `Test-MigrationServerAvailability` cmdlet. In the Exchange Online PowerShell, run these commands:

```powershell
$Credentials = Get-Credential

Test-MigrationServerAvailability -ExchangeRemoteMove -Autodiscover -EmailAddress admin@contoso.com -Credentials $Credentials
```

Enter the credentials of an administrator in the Exchange on-premises organization and specify an on-premises email address for the `-EmailAddress` property. If the test passes, then you should be able to create Exchange on-premises endpoints in the migration tools.

## Use the data consistency score to assess a migration

When you run a migration to Exchange Online, you hope that data in migrated mailboxes is moved over with no changes. However, in most situations, there will be some level of inconsistency between the original items in the on-premises mailbox and the migrated items in the cloud mailbox. Exchange Online checks for any inconsistencies and records a score. If data consistency scores are poor, it can prevent a migration from being completed.

For each migrated mailbox, Exchange Online records one of four grades:

- Perfect. There was no inconsistency in the migrated mailbox.
- Good. One or more inconsistencies were detected, but the data loss was not impactful.
- Investigate. A small amount of noticeable data loss was detected.
- Poor. Major data loss was detected.

If the grade is Perfect or Good, the mailbox will migrate with no approval required. If the grade is Investigate or Poor, you will be prompted to approve the skipped items and the migration can't complete until you do so.

After you complete a migration, you can check the grade for a migrated mailbox by using the following command in Exchange Online PowerShell:

```powershell
Get-MigrationUser -identity serena.davis@contoso.com | FL DataConsistencyScore
```

If the grade is Investigate or Poor, some items were not migrated. You can identify these items by using this command in Exchange Online PowerShell:

```powershell
$userStats = Get-MigrationUserStatistics -Identity serena.davis@contoso.com -IncludeSkippedItems

$userStats.SkippedItems | FT -a Subject, Sender, DateSent, ScoringClassifications
```

This report enables you to assess the importance of the lost items and whether to re-execute the migration for that mailbox.

## Troubleshoot slow migrations

The duration of a migration operation depends on many factors, such as:

- The number of mailboxes you are migrating in a batch.
- The average size of those mailboxes.
- The performance of the target server identified in the migration endpoint.
- The network bandwidth available between the target server and Exchange Online.

It's therefore difficult to define what constitutes a slow migration. However, by observing migration tests and real-world customer migrations, Microsoft has defined broad expectations for durations. For example:

- If you're migrating up to 1,000 mailboxes, 90% of mailboxes should migrate within 5 to 14 days.
- If you're migrating between 5,000 and 10,000 mailboxes, 90% of mailboxes should migrate within 20 to 45 days.

If your migration appears to be significantly slower than these expectations, you can consider these changes:

- Change the endpoint to use an on-premises Exchange Server with a higher specification.
- Upgrade the hardware for any on-premises network appliances, such as firewalls.

> [!NOTE]
> Microsoft have also provided the **AnalyzeMoveRequestStats.ps1** PowerShell script to help diagnose problems with slow migrations. To download this script and for more information about it see the **Mailbox Migration Performance Analysis** link in the Learn more section below.

## Troubleshoot hybrid deployment migrations

If you have a hybrid deployment of Exchange, and you are moving mailboxes into Exchange Online singly or in batches, there are two specific errors that you might encounter:

### Troubleshoot an exception thrown by the target

If you were previously able to move mailboxes, but you have upgraded the on-premises Exchange Servers and now you receive an error such as the following:

**Exception has been thrown by the target of an invocation.**

This problem can arise when you upgrade an on-premises server from Exchange Server 2010 SP 1 and is caused when the web.config file is overwritten during the upgrade.

To resolve the problem, first check that the MRSProxyEnabled parameter is set to false on the upgraded server:

```powershell
Get-WebServicesVirtualDirectory | Select Identity, MRSProxyEnabled
```

Then, re-enable the MRSProxy service:

```powershell
Set-WebServicesVirtualDirectory -Identity "EXCHSERVER\EWS (Default Web Site)" –MRSProxyEnabled $true
```

### Troubleshoot a 403 forbidden error

This problem causes an error such as the following when you try to move mailboxes into Exchange Online:

**The connection to the server 'mail.contoso.com' could not be completed.**

If you used the PowerShell New-MoveRequest cmdlet to start the move, you might receive an error like this one:

```
The call to 'https://mail.contoso.com/EWS/mrsproxy.svc' failed. Error details: The HTTP request was forbidden with client authentication scheme 'Negotiate'.

The remote server returned an error: (403) Forbidden..

+ CategoryInfo : NotSpecified: (:) [New-MoveRequest], RemoteTransientException

+ FullyQualifiedErrorId : [Server=xxxxxxxxxxxx,RequestId=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx,TimeStamp=4/21/2015 2:07:09 PM] [FailureCategory=Cmdlet-RemoteTransien tException] 284A32E1,Microsoft.Exchange.Management.RecipientTasks.NewMoveRequest

+ PSComputerName : outlook.office365.com
```

This problem arises when the Mailbox Replication Service proxy is disabled. You can check its status by running this command on the Exchange on-premises server:

```powershell
Get-WebServicesVirtualDirectory | Select Identity, MRSProxyEnabled
```

To resolve the problem, re-enable the proxy:

```powershell
Set-WebServicesVirtualDirectory -Identity "EXCHSERVER\EWS (Default Web Site)" –MRSProxyEnabled $true
```

## Learn more

- [Ways to migrate multiple email accounts to Microsoft 365 or Office 365](/exchange/mailbox-migration/mailbox-migration)
- [Enable the MRS Proxy endpoint for remote moves in Exchange Server](/exchange/architecture/mailbox-servers/mrs-proxy-endpoint)
- [Track and prevent migration data loss in Exchange Online](/exchange/mailbox-migration/track-prevent-data-loss-dcs)
- [Microsoft 365 and Office 365 email migration performance and best practices](/exchange/mailbox-migration/office-365-migration-best-practices)
- [(Exception has been thrown by the target) error when moving mailboxes to or from Office 365 in a hybrid deployment](/exchange/troubleshoot/move-mailboxes/error-move-mailboxes-to-from-o365)
- [The remote server returned an error (403) Forbidden error when moving mailboxes to Exchange Online](/exchange/troubleshoot/move-mailboxes/remote-server-returned-error-403-forbidden)
- [Exchange Hybrid Migrations: More Than Just a Pretty Face](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-hybrid-migrations-more-than-just-a-pretty-face/ba-p/1623109)
- [Mailbox Migration Performance Analysis](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)