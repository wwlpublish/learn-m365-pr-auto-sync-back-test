Audio Conferencing settings allow you to enable or disable, set options such as default Conference Bridge numbers for users, and to perform tasks such as resetting a user's PIN.

Voice settings for users include the call sharing and group call pickup features of Microsoft Teams. These features enable users to share their incoming calls with colleagues so that the colleagues can answer calls that occur while the user is unavailable.

## Configure or manage audio conferencing bridge for a user

After assigning an Audio-Conferencing license to a user, you can edit an individual user's settings. You might want to do this if you want to set the default audio bridge number, conference ID, or PIN.

To edit the audio-conferencing settings, use the Teams Admin Center:

1. Navigate to the Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Sign into the Teams admin center with an account that has the Teams Administrator role.

1. In the left navigation, select **Users**, then select the user from the list of available users, then select **Edit.**

1. Under **Audio Conferencing**, modify any of the following:

| **Setting**| **Description**|
| :--- | :--- |
| **Audio conferencing**| To turn audio conferencing on or off for the user, select **Edit** next to **Audio Conferencing**, and then in the **Audio Conferencing** pane, toggle **Audio conferencing** On or Off.|
| **Send conference info in email**| Select this link only if you want to immediately send an email to the user with their conference ID and phone number. (This email does not include the PIN.)|
| **Conference ID**| Select **Reset conference ID** if you need to reset the conference ID for the user.|
| **PIN**| Select **Reset PIN** if you need to reset the PIN for the user.|
| **Default conferencing toll phone number** (required)| These will be numbers that are set on the audio conferencing bridge. Format the numbers as you want them to appear in Microsoft Teams meeting requests. To change the default toll number, select **Edit** next to **Audio Conferencing** and in the **Audio Conferencing** pane, select a number under **Toll number**.|
| **Invites from this user can include toll-free number**| To change this setting, select **Edit** next to **Audio Conferencing** and in the **Audio Conferencing** pane, toggle **Include toll-free numbers in meeting requests from this user** On or Off.|
| **Unauthenticated users can be the first person in the meeting**| To change this setting, toggle **Unauthenticated users can be the first person in the meeting** On or Off.|
| **Dial-out permissions**| To change this setting, click **Edit** next to **Audio Conferencing** and in the **Audio Conferencing** pane, choose an option under **Dial-out from meetings**.|

## Group call configuration

Call groups enable users to manage who they want notified when they get a call.

Group call pickup is less disruptive to recipients than other forms of call sharing, such as call forwarding or simultaneous ringing. Group call pickup is less invasive because users can configure how they want to be notified of an incoming shared call (through audio and visual notification, visual only, or through a banner in the Teams app), and they can decide whether to answer it.

To share calls with others, a user must create a call group and then add the users they want to share the calls with. The user can also configure simultaneous ring or forwarding.

Administrators don't have to configure these features for their users since the call group creation and notification settings are available for configuration on the user side.

However, administrators can use the Teams PowerShell module to modify the **AllowCallGroups** parameter in the **TeamsCallingPolicy** to enable or disable call groups:

To create a policy that prevents use of call groups, use the following cmdlet:

```powershell
New-CsTeamsCallingPolicy -Identity "AllowCallingPreventCallgroups" -AllowCallGroups $false

```

To assign the new policy it to a user, use the following cmdlet:

```powershell
Grant-CsTeamsCallingPolicy -Identity <User name> -PolicyName AllowCallingPreventCallgroups

```

A user can be enabled to use call groups by either changing their policy using the Set-CsTeamsCallingPolicy cmdlet or granting a different policy to the user.

You can use the Teams Client to add a call group by completing the following steps:

1. In the upper right corner of the Teams client, select **… > Settings** and then **Calls**.

1. Below **Call answering rules**, select **Forward my calls**, and open the dropdown menu by selecting **Voicemail**.

1. Select the call group to open a **Call group** new window.

1. Use the search field below **Add people** and select the users that you want to add to the call group.

1. In the **Ring order** menu, you can select to ring **All** at the same time simultaneously or **In the order above** to call people in order in 20-second intervals (just note that if your call group has six or more people, incoming calls will ring all of them at the same time).

> [!NOTE]
> All users added to a call group receive a notification in their Teams client.

When an admin turns off group calling for a user, after the user has already set up a call group, the call group relationships for the user in the Teams admin center must be cleaned up to avoid incorrect call routing.

To clean up or modify the call group for a user, complete the following steps:

1. Navigate to the Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Sign in to the Teams admin center with an account that has the Teams Administrator role.

1. In the left-hand navigation pane in the Teams Admin Center, select **Users** and then select the name of the user and then select **Edit**.

1. Select the **Voice** tab and navigate to the **Group call pickup** section.

1. In the list of users, select the users you want to remove from the **Call group** and select **Remove**.

If you want to add users to a call group, complete the following steps:

1. In the left-hand navigation pane in the Teams Admin Center, select **Users** and then select the name of the user who owns the call group you want to modify.

1. Select the **Voice** tab and navigate to the **Group call pickup** section.

1. Select **Add people** and then in the right-hand pane, search for the users you want to add.

1. Select **Apply** to add the selected users to the call group.

## Configuring Call Forwarding, Simultaneous Ring and Delegation

Like Group Call configuration, configuration for Call Forwarding, Simultaneous Ring, and Delegation is configured within the Teams client when logged in as the user the change affects.

You can use the Teams Client to make changes to these settings by following these steps:

1. Forwarding allows a user to forward their calls to voicemail, another user or to a call group. To configure Forwarding:

1. In the upper right corner of the client, select **Settings** and **Calls**.

1. Under **Call answering rules**, choose **Forward my calls**, and then select where you want your forwarded calls to go: **voicemail**, **another person**, or a **call group.**

1. With simultaneous ring, a call rings both in the user's Teams clients and also for another user or a call group. To configure simultaneous ring:

1. In the upper right corner of the client, select **Settings** and **Calls**.

1. Under Call answering rules, select **Calls ring me**. Then select **Also ring** and select where else you want your calls to ring: **another person**, **no one**, or a **call group**

1. Delegation allows another user to make or receive calls on the user who configures delegation's behalf. To configure delegation:

1. In the upper right corner of the client, select **Settings** and **General**.

1. Select **Manage delegates**.

1. Select **Your delegates** and type the person's name to assign delegate rights to.

1. Select the permissions to give them, and then select **Add**.

