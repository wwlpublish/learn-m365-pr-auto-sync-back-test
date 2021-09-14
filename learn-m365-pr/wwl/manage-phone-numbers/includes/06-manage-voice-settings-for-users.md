Voice settings for users include the call sharing and group call pickup features of Microsoft Teams. These features enable users to share their incoming calls with colleagues so that the colleagues can answer calls that occur while the user is unavailable.

Group call pickup is less disruptive to recipients than other forms of call sharing, such as call forwarding or simultaneous ringing. Group call pickup is less invasive because users can configure how they want to be notified of an incoming shared call (through audio and visual notification, visual only, or through a banner in the Teams app), and they can decide whether to answer it. To share calls with others, a user creates a call group and adds the users who they want to share their calls with to the group. Then they choose a simultaneous ring or forward setting. As for licensing requirements, the users must be Enterprise Voice enabled to set up and use call sharing and group call pickup.

To share calls with others, a user must create a call group and then add the users they want to share the calls with. The user can also configure simultaneous ring or forwarding.

> [!NOTE]
> The call group owner and members of the call group must all be in Teams Only deployment mode. The maximum number of users in each call group is 25.

## Group call configuration

Call groups enable users to manage who they want notified when they get a call.

Administrators don't have to configure these features for their users since the call group creation and notification settings are available for configuration on the user side. However, administrators can use the Skype for Business Online PowerShell module to modify the **AllowCallGroups** parameter in the **TeamsCallingPolicy** to enable or disable call groups:

```powershell
New-CsTeamsCallingPolicy -Identity "AllowCallingPreventCallgroups" -AllowCallGroups $false
```

The ```Grant-CsTeamsCallingPolicy``` cmdlet can be used to grant the policy to a user:

```powershell
Grant-CsTeamsCallingPolicy -Identity alex.wilber@contoso.com -PolicyName AllowCallingPreventCallgroups
```

A user can be enabled to use call groups by either changing their policy using the ```Set-CsTeamsCallingPolicy``` cmdlet, or granting a different policy to the user.

> [!NOTE]
> Before creating a new policy, you should always verify that no policy already exists that covers your exact scenario.
 
You can use the Microsoft Teams Client to add a call group by completing the following steps:

1. In the upper-right corner of the client, select **Settings** and **Calls**.
2. Below **Call answering rules**, select **Forward my calls**, and open the dropdown menu by selecting **Voicemail**.
3. Select the **call group** to open a **Call group** new window.
4. Use the search field below **Add people** and select the  users that you want to add to the call group.
5. In the **Ring order** menu, you can select to ring **All at the same time** simultaneously or **In the order above** to call people in order in 20-second intervals (just note that if your call group has six or more people, incoming calls will ring all of them at the same time).

> [!NOTE]
> All users added to a call group receive a notification in their Teams client.

When an admin turns off group calling for a user after the user has already set up a call group, the call group relationships for the user in the Teams admin center must be cleaned up to avoid incorrect call routing.
 
To clean up or modify the call group for a user, sign into the Teams Admin Center and complete the following steps:

1. In the left-hand navigation pane in the **Teams Admin Center**, select **Users** and then select the name of the user you want to edit.
2. Select the **Voice** tab and navigate to the **Group call pickup** section.
3. In the list of users, select the users you want to remove from the Call group and select **Remove**.

If you want to add users to a call group, complete the following steps:

1. In the left-hand navigation pane in the **Teams Admin Center**, select **Users** and then select the name of the user who owns the call group you want to modify.
2. Select the **Voice** tab and navigate to the **Group call pickup** section.
3. Select **Add people** and then in the right-hand pane, search for the users you want to add.
4. Select **Apply** to add the selected users to the call group.

‎:::image type="content" source="../media/user-voice-setting.png" alt-text="Voice settings for users":::

**Additional reading.** For more information, see [Call forwarding, call groups, and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-call-groups-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”