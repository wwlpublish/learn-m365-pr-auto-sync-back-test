The Meeting Migration Service (MMS) is a service that updates a user’s existing meetings in the following scenarios:

- When a user is migrated from on-premises to the cloud

- When an admin makes a change to the user’s audio conferencing settings

- When an online user is upgraded to Teams only, or when a user's mode in TeamsUpgradePolicy is set to SfBwithTeamsCollabAndMeetings

- When you use PowerShell

MMS is automatically triggered in each of these cases. Admins can disable it at the tenant level. Admins can also use a PowerShell cmdlet to manually trigger meeting migration for a given user.

> [!NOTE]
> The meeting migration service can't be used if any of the following apply:

- The user’s mailbox is hosted in Exchange on-premises

- The user is being migrated from the cloud to Skype for Business Server on-premises

In these situations, end users can use the [Meeting Migration Tool](https://www.microsoft.com/download/details.aspx?id=51659&azure-portal=true) to migrate their own meetings instead.

## Meeting Migration Service

When the Meeting Migration Service has been triggered for a user, a migration request for that user is placed in a queue. Once the MMS processes the request, it will do these tasks:

1. It searches user’s mailbox for all existing future meetings organized by that user.

2. It updates or schedules new meetings in Teams for that user, depending on the information found in the user’s mailbox.

3. In the email message, it replaces the online meeting block in the meeting details.

4. It sends the updated version of that meeting to all meeting recipients on behalf of the meeting organizer. Meeting invitees will receive a meeting update with updated meeting coordinates in their email.

Once the Meetings Migration Service is triggered, the meetings migration process can take up to two hours until completed. It may take longer if the user has a large number of meetings.

> [!NOTE]
> If an error occurs during the migration process, MMS will periodically retry up to nine times during the 24 hours.

## Trigger MMS for a user

When the MMS is triggered for a user, the following scenarios are available:

- **User is migrated from on-premises to the cloud**. This scenario is the most common one where the MMS helps to ease the transition for users. Without meeting migration, once the user is moved online, the existing meetings organized by a user in Skype for Business Server on-premises will no longer work. Therefore, when you use the on-premises admin tools (either ```Move-CsUser``` or the **Admin Control Panel**) to move a user to the cloud, existing meetings are automatically moved to the cloud as follows:

  - If the ```MoveToTeams``` switch in ```Move-CsUser``` is specified, meetings are migrated directly to Teams and the user will be in TeamsOnly mode. Use of this switch requires Skype for Business Server 2015 with CU8 or later. These users can still join any Skype for Business meeting they may be invited to, using either the Skype for Business client or the Skype Meeting App.

  - Otherwise, meetings are migrated to Skype for Business Online.

- **Admin makes a change to the user’s audio-conferencing settings**. In this scenario, MMS will update existing Skype for Business and Microsoft Teams meetings to add, remove, or modify dial-in coordinates:

  - When you assign or remove a Microsoft Audio Conferencing service license to a user, and that user is not enabled for a third-party audio-conferencing provider.

  - When you change the audio provider

  - When you enable or disable audio conferencing for a user

  - When you move the user to a new audio-conferencing bridge

  - When a phone number from an audio-conferencing bridge is unassigned

  However, when you change meeting organizer’s SIP address, or when you change organization’s meeting URL, MMS will not be trying an update.

- **Updating meetings when assigning TeamsUpgradePolicy**: By default, meeting migration is automatically triggered when a user is granted an instance of ```TeamsUpgradePolicy``` with ```mode=TeamsOnly``` or ```mode= SfBWithTeamsCollabAndMeetings```. If you do not want to migrate meetings when granting either of these modes, then specify ```MigrateMeetingsToTeams $false``` in``` Grant-CsTeamsUpgradePolicy``` (if using PowerShell) or uncheck the box to migrate meetings when setting a user's coexistence mode (if using the Teams admin portal).

- **Admin uses PowerShell cmdlet**: Admins can manually trigger meeting migration for a user by running the cmdlet ```Start-CsExMeetingMigration```. This cmdlet queues a migration request for the specified user. In addition to the required Identity parameter, it takes two optional parameters, ```SourceMeetingType``` and ```TargetMeetingType```, which allow you to specify how to migrate meetings.

## Manage MMS

By using the PowerShell, admins can check the status of running migrations, manually trigger meeting migrations, and disable migrations altogether.

To check the status of meeting migrations, you can use the ```Get-CsMeetingMigrationStatus``` cmdlet. For example, to get a summary status of all MMS migrations, run the following cmdlet that provides a tabular view of all migration states:

```powershell
Get-CsMeetingMigrationStatus -SummaryOnly
```

:::image type="content" source="../media/manage-mms.png" alt-text="Meeting migration status":::

If you would like to check the status of migration for a user, you can use the ```Get-CsMeetingMigrationStatus``` cmdlet with the Identity parameter. For example, to check the status of migration for user JoniS@contoso.com, use the following cmdlet:

```powershell
Get-CsMeetingMigrationStatus -Identity JoniS@contoso.com
```

### Enable and disable MMS

MMS is enabled by default for all organizations, but it can also be disabled on different levels:

- Disable entirely for the tenant

- Disable only for changes related to audio conferencing (where MMS will still run when a user is migrated from on-premises to the cloud or when you grant TeamsOnly mode or SfBWithTeamsCollabAndMeetings mode in TeamsUpgradePolicy)

To check if MMS is enabled for your organization, run the following cmdlet. MMS is enabled if the ```MeetingMigrationEnabled``` parameter is ```$true```:

```powershell
Get-CsTenantMigrationConfiguration
```

To enable or disable MMS, use the ```Set-CsTenantMigrationConfiguration``` cmdlet. For example, to disable MMS, run the following cmdlet:

```powershell
Set-CsTenantMigrationConfiguration -MeetingMigrationEnabled $false
```

If MMS is enabled in the organization and you want to verify whether it's enabled for audio conferencing updates, check the value of the ```AutomaticallyMigrateUserMeetings``` parameter in the output from ```Get-CsOnlineDialInConferencingTenantSettings```. To enable or disable MMS for audio conferencing, use ```Set-CsOnlineDialInConferencingTenantSettings```.

For example, to disable MMS for audio conferencing, run the following cmdlet:

```powershell
Set-CsOnlineDialInConferencingTenantSettings -AutomaticallyMigrateUserMeetings $false
```

For more information, see [Using the Meeting Migration Service (MMS)](/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”