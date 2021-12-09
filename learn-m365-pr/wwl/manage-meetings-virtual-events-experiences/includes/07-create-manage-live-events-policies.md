With the help of Microsoft Teams Live events policies, an administrator can control which users in the company can hold live events, and which features will be available in the events they create. Microsoft Teams provides a default Live events policy that organizations can use. The Teams administrator can also create one or more custom Live events policies that can be tailored specifically to their organization's needs. After a custom policy is created, it must be assigned to a user or groups of users within the organization.

## Default Live events policy

If a custom policy isn't created and assigned, then the users will receive the default Live events policy. In the default Live events policy, the following settings are defined:

- Live event scheduling is enabled for Teams users.
- Live captions and subtitles are turned off.
- Everyone in the organization can join Live events.
- The recording setting is set to always record.

## Create or edit a Live events policy

In **Microsoft Teams admin center**, under the **Meetings** group in the left-hand navigation pane, select **Live events policies**. When creating and editing Live event policies, the following options can be selected:

- **Global policy**: This organization-wide policy is the existing default policy. Select the **Edit** button to change this policy.
- **New policy**: This option is used to create a new custom policy.
- **Choose existing policy**: By selecting an existing policy and the **Edit** button, you can change the policy.
‎
	:::image type="content" source="../media/live-event-policies.png" alt-text="Screenshot of the Create a Live events policy window":::
 
The Teams administrator should complete the following steps to create a Live events policy:

1. In the **Microsoft Teams admin center**, in the left-hand navigation pane, select **Meetings** and then select **Live events policies**.
2. In the **Live events policies** window, select **+Add** on the menu bar that appears above the list of policies.
3. In the **Live event policies \ Add** window, enter a name for your policy and optionally enter a description.
4. Customize the following settings according to your preferences for this new policy:

	- **Live events scheduling** - Select the toggle to turn this option **On** or **Off**.
	- **Transcription for attendees** - Select the toggle to turn this option **On** or **Off**.
	- **Who can join scheduled Live events** - Choose from **Everyone**, **Everyone in the organization**, and **Specific users or groups**.
	- **Who can record an event** - Choose from **Always record**, **Never record,** and **Organizer can record**.

5. Select **Save** to save your new policy.  
‎
## Assign a Live events policy to users

Once a custom Live events policy is created, it must be assigned to users in order for the policy to become active. Complete the following steps in the Microsoft Teams admin center to assign the policy:

1. In the **Microsoft Teams admin center**, in the left-hand navigation pane, select **Users** > **Manage users**.
2. In the **Manage users** window, select the user(s) who will be assigned the policy (select the check mark to the left of each user's Display name; don't select on the Display name itself).
3. After selecting all the required users, select **Edit settings** on the menu bar.
4. In the **Edit settings** pane that appears, select the drop-down arrow for the **Live events policy** field. In the menu that appears, select the policy that will be applied to the selected users.
5. Select **Apply**.

A Live events policy can also be assigned to one or more users in the Microsoft Teams admin center under the **Meetings** section.

1. In the **Microsoft Teams admin center**, in the left-hand navigation pane, select **Meetings** and then select **Live events policies**. 
2. In the **Live events policies** window, select the name of the policy to be assigned and then select **Manage users** on the menu bar. 
3. In the **Manage users** pane that appears, search for and select the appropriate user and then select the **Add** button next to the user's name. This step must be repeated for every user that will be assigned this policy.
4. When you've finished, select **Apply**.

## Manage Live event policies using PowerShell

Live event policies can also be managed by using the following Windows PowerShell cmdlets:

- ```Get-CsTeamsMeetingBroadcastPolicy```
- ```Set-CsTeamsMeetingBroadcastPolicy```
- ```New-CsTeamsMeetingBroadcastPolicy```
- ```Grant-CsTeamsMeetingBroadcastPolicy```

When a user has been assigned the global policy, the **AllowBroadcastScheduling** parameter will indicate whether the user can schedule a Live event. To determine whether this parameter is set to True, run the following command:  

```powershell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```

To disable Live events scheduling across your organization, run the following command:

```powershell
Set-CsTeamsMeetingBroadcastPolicy -identity Global   
‎-AllowBroadcastScheduling $false
```

To identify who can join Live events, the global policy must be set to allow users to create events that everyone, including anonymous users, can attend. To update the global policy, run the following command:  

```powershell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastAttendeeVisibility Everyone
```

The recording option for Live events only applies to Live events that are produced in Teams. For example, to set the global policy to disable recording for Live events, run the following command:

```powershell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastRecordingMode AlwaysDisabled
```


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”