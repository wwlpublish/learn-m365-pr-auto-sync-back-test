Voice settings for users include the outbound calling and call answering rules in Microsoft Teams. You might want to change these settings, for example, if:

* A user is out on sick leave, and you need to ensure that incoming calls to the user are forwarded to a colleague.
* You need to inspect the call forward settings for all users in a department and potentially correct them as appropriate.
* A new assistant has been employed and you need to add the assistant as a delegate for a group of employees.


## Voice settings
There are two sections for users' voice settings.

* **Outbound calling**. Outbound call controls to restrict the type of calls that can be made by users in your organization.

* **Call answer rules**. The call answering rules enable users to share their incoming calls with colleagues so that the colleagues can answer calls that occur while the user is unavailable. The settings include:

    * Forwarding settings
    * Group call pickup
    * Call delegation
    * Simultaneous ringing

    Group call pickup is less disruptive to recipients than other forms of call sharing, such as call forwarding or simultaneous ringing. Group call pickup is less invasive because users can configure how they want to be notified of an incoming shared call (through audio and visual notification, visual only, or through a banner in the Teams app), and they can decide whether to answer it.

## Configure voice settings

As for licensing requirements, the users must be Enterprise Voice enabled to set up and use call sharing and group call pickup. Call sharing and group call pickup can be configured from Teams admin center or Teams client. 

### Use Teams admin

Admins can also use the Teams admin center to configure call forward and unanswered settings, group call pickup, and call delegation for your users.

To configure immediate call forward settings:

1. In the Teams admin center, go to **Users** > **Manage users** and select a user.

2. On the user details page, go to the **Voice** tab.

3. Under **Outbound calling**, select one of the following options:

    * Any destination
    * In the same country or region as the organizer
    * Don't allow

4. Under **Call answering rules**, select the appropriate call forward type and destination.

    * Select **Be immediately forwarded**, and select the appropriate call forward type and destination.

    * To configure simultaneous ringing, select **Ring the user's devices**. In the **Also allow** drop-down, select the appropriate simultaneous ringing setting.

    * To configure unanswered settings, select the appropriate setting in the **If unanswered** drop-down. In the **Ring for this many seconds before redirecting** drop-down, specify the number of seconds to wait.

The configuration of call delegation and group call pickup are integrated into the call forward and unanswered settings by selecting the appropriate type. For example, to configure that calls should also ring the user's delegates, on the same page select **Call delegation** under **Also allow**. Then add the appropriate delegates by selecting **Add people** and clicking **Save**.

‎:::image type="content" source="../media/user-voice-setting.png" alt-text="Screenshot of Voice settings for users.":::

### Use PowerShell

You can use PowerShell to configure call forward and delegation settings for your users.  You'll use the following cmdlets, which are available in Teams PowerShell module version 4.0 or later:

- [Get-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings) - shows call forwarding settings, delegates, and delegator information for a user.
- [Set-CsUserCallingSettings](/powershell/module/teams/set-csusercallingsettings) - sets call forwarding settings for a user.
- [New-CsUserCallingDelegate](/powershell/module/teams/new-csusercallingdelegate) - adds a new delegate with permissions for a user.
- [Set-CsUserCallingDelegate](/powershell/module/teams/set-csusercallingdelegate) - changes permissions for an existing delegate.
- [Remove-CsUserCallingDelegate](/powershell/module/teams/remove-csusercallingdelegate) - removes a delegate from a user.


### Use Teams Client

Call groups enable users to manage who they want notified when they get a call.

Users can also create a call group and adds the users who they want to share their calls with to the group. For more information, see [Call forwarding, call groups, and simultaneous ring in Teams](https://support.office.com/article/call-forwarding-call-groups-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e?azure-portal=true).

