When users are migrated from Skype for Business Server to Microsoft Teams, by default, existing meetings will be upgraded to Microsoft Teams meetings. Therefore, you should consider upgrading Meeting Room devices to support Microsoft Teams as you migrate users and migrating Meeting Room accounts to Teams.

Before you begin your migration, you should assess your existing Skype for Business enabled Meeting Rooms for compatibility with Microsoft Teams.

Skype Room System v2 (SRS v2) provide native compatibility with Microsoft Teams. When running up-to-date software, SRS v2 devices become Microsoft Teams Room systems. Your existing devices should therefore already have the correct updates.

Older Lync Room Systems with Skype Room System v1 (SRS v1) are not supported with Microsoft Teams and reached end-of-life in October 2018. Microsoft recommends replacing these devices with native Microsoft Teams Rooms.

Other Skype for Business Server compatible room systems can use various different technologies to integrate. This means you need to validate with each vendor the compatibility of their solution and what functionality will be available after migration to Microsoft Teams. In some cases, this can mean that reduced functionality will be available on the meeting room device after migration. In other cases, you may need to deploy new third-party gateway software to allow integration.

If you will lose functionality or need to deploy additional solutions to integrate existing meeting room solutions with Microsoft Teams, perform a comparison against the end solution versus deploying new devices that support Microsoft Teams Rooms. In some cases, peripheral hardware such as conference audio and video equipment is compatible with Microsoft Teams Rooms and only requires the controller unit to be replaced.

## Migrate Skype for Business Server Meeting Room accounts to Teams

By performing the prerequisites for implementing Skype for Business Server with Hybrid, on-premises Active Directory accounts were synchronized to Azure AD and can therefore be migrated to Microsoft Teams. This includes Meeting Room accounts.

Meeting Room accounts include Exchange-related configuration to support validation of meeting room available, choosing meeting rooms based on locations and policies to allow bookings.

You can Migrate a Meeting room account using a similar method to migrating users, shown earlier in this module. Instead of the Move-CsUser cmdlet, the Move-CsMeetingRoom cmdlet is used on-premises.

Before you migrate, a Meeting Room account, you should assign the appropriate licensing to the account, and plan for management of Microsoft Teams Rooms devices. You will learn about this later in the module Configure, deploy, and manage Teams devices.

To migrate a Meeting Room account, use the same accounts and PowerShell environment used to migrate users to Teams, described in unit 5 of this module. Then, use the following PowerShell cmdlets:

```powershell
$cred=Get-Credential

$url="https://admin1a.online.lync.com/HostedMigration/hostedmigrationService.svc"

Move-CsMeetingRoom -Identity meetingroom@contoso.com -Target sipfed.online.lync.com -Credential $cred -HostedMigrationOverrideUrl $url -Verbose

```

With Microsoft Teams Rooms devices, you may need to sign-out of the meeting room device and sign-in again in to register the device with Microsoft Teams.

