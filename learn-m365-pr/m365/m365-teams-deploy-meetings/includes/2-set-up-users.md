Teams offers a great deal of functionality that can be customized by each customer. Your company will have to decide which features it's appropriate to deploy.

In our scenario of a software development company, audio and video conferences are used for daily stand-up meetings, customer communication, and other parts of the Agile software development process. You want to start planning for Microsoft Teams meetings by learning how you can manage user access.

Here, you learn how to set users up on Teams meetings by using the Microsoft 365 admin center, PowerShell, or Teams meetings policies.

## Manage user access to Teams

You manage access to Teams at the user level by assigning or removing a Microsoft Teams product license. You complete this operation by using either the Microsoft 365 admin center or PowerShell.

> [!NOTE]
> By default, when a licensing plan (for example, Microsoft 365 Enterprise E3 or Microsoft 365 Business Premium) is assigned to a user, a Teams license is automatically assigned. The user is then enabled for Teams. You can disable or enable Teams for a user by removing or assigning a license at any time.

### Using the Microsoft 365 admin center

Teams user-level licenses are managed directly through the Microsoft 365 admin center user management interfaces. An administrator can assign licenses to new users when those accounts are created or to users with existing accounts.
The steps are different depending on whether you use the Licenses page or Active Users page. For step-by-step instructions, see **Assign licenses to users** in the **Learn more** section below.

:::image type="content" border="false" source="../media/2-office-365.png" alt-text="Assign licenses":::

### Using PowerShell

Run the following command to display all available licensing plans in your organization:

```powershell
Get-MsolAccountSku
```

Run the following commands to disable Teams, where **CompanyName:License** is your organization name and the identifier for the licensing plan that you retrieved in the earlier step. For example, **ContosoSchool:ENTERPRISEPACK_STUDENT**:

```powershell
$acctSKU="<CompanyName:License>
$x = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans "TEAMS1"
```

## Manage user meeting policies and settings in Teams

Meeting policies are used to control the features that are available to participants for meetings scheduled by users in your organization. You can use the global, organization-wide, default policy that's automatically produced or create and assign custom policies. You manage meeting policies in the Microsoft Teams admin center or by using PowerShell.

### Let anonymous people start a meeting

This policy is per-organizer and allows for leaderless dial-in conferencing meetings. This setting controls whether dial-in users can join the meeting without an authenticated user from the organization in attendance. The default value is **False**, which means dial-in users will wait in the lobby until an authenticated user joins the meeting.

:::image type="content" source="../media/2-waiting-in-lobby.png" alt-text="User waiting in lobby":::

### Automatically admit people

This policy is per-organizer. The setting controls whether people join a meeting directly or wait in the lobby until they're admitted by an authenticated user. This setting doesn't apply to dial-in users.

### Allow dial-in users to bypass the lobby

This policy is per-organizer. The setting controls whether people who dial in by phone join the meeting directly or wait in the lobby, whatever the **Automatically admit people** setting fixes. The default value is **False**. When it's **False**, dial-in users will wait in the lobby until an organization user joins the meeting with a Teams client and admits them. If it's **True**, dial-in users will automatically join the meeting when an organization user arrives.

### Configure desktop sharing in Microsoft Teams

Desktop sharing lets users present a screen or app during a meeting or chat. Administrators configure screen sharing in Microsoft Teams to let users share an entire screen, an app, or a file. You let users give or request control, allow PowerPoint sharing, add a whiteboard, and allow shared notes. You also configure whether anonymous or external users can request control of the shared screen.

To configure screen sharing, you create a new meetings policy, and then assign it to the users you want to manage.

1. Sign into the [Microsoft Teams admin center](https://admin.teams.microsoft.com/).

1. Select **Meetings** > **Meeting policies**.

    :::image type="content" source="../media/2-meeting-policies.png" alt-text="Meeting policies":::

1. On the **Meeting policies** page, select **+ Add**.

    :::image type="content" border="false"  source="../media/2-new-policy.png" alt-text="New policy link":::

1. Give your policy a unique title and enter a brief description.
1. Under **Content sharing**, choose a screen sharing mode from the drop-down list:

    - **Entire screen**: lets users share their entire desktop.
    - **Single application**: lets users limit screen sharing to a single active application.
    - **Disabled**: turns off screen sharing.

    :::image type="content" source="../media/2-content-sharing.png" alt-text="Content sharing":::

1. Turn the following settings on or off:

    - **Allow a participant to give or request control**. Lets members of the team give or request control of the presenter's desktop or application.
    - **Allow an external participant to give or request control**. This policy is per-user. Whether an organization has this policy set for a user doesn't control what external participants can do, whatever the meeting organizer has set. This parameter controls whether external participants can be given control or request control of the sharer's screen, depending on what the sharer has set within their organization's meeting policies.
    - **Allow PowerPoint sharing**. Lets users create meetings that allow PowerPoint presentations to be uploaded and shared.
    - **Allow whiteboard**. Lets users share a whiteboard.
    - **Allow shared notes**. Lets users take shared notes.

1. Select **Save**.

### Use PowerShell to configure shared desktop

You can also use the **Set-CsTeamsMeetingPolicy** cmdlet to control desktop sharing.

### Customize meeting invitations

You can customize Teams meeting invitations to satisfy your organization's needs. Add your organization's logo and include helpful information, such as links to your support website and legal disclaimer, and a text-only footer.

1. Sign into the [Microsoft Teams admin center](https://admin.teams.microsoft.com/).
1. In the left navigation, go to **Meetings** > **Meeting settings**.
1. Under **Email invitation**, do the following:

    :::image type="content" source="../media/2-email-invitation.png" alt-text="Configure the email invitation":::

    - **Logo URL**. Enter the URL where your logo is stored. The URL must be reachable inside and outside your organization.
    - **Legal URL**. If your organization has a website where you want people to go for any legal concerns, enter the URL here.
    - **Help URL**. If your organization has a support website where you want people to go if they run into issues, enter the URL here.
    - **Footer**. Enter text that you want to include as a footer.

1. Select **Preview invite** to see a preview of your meeting invitation.
1. When you're done, select **Save**.
1. Wait an hour or so for the changes to propagate. Then schedule a Teams meeting to see what the invitation looks like.

## Learn more

- [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users)
- [Manage meeting settings in Microsoft Teams](/microsoftteams/meeting-settings-in-teams)