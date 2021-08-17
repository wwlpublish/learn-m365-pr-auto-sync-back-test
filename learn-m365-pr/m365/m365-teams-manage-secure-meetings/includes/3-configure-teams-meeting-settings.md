Microsoft Teams allows you to configure whether guests can join meetings and whether another organization can have access to your Teams environment.

## What is guest access?

Guest access is a way to allow third-party individuals or organizations to collaborate with project teams or members of your organization. It allows anyone with a personal or business email account to participate and access all your existing teams and channels. As a Teams administrator, you have full control over which features and services a guest can or can't have access to.
Guest access is an organization-wide setting in Teams and is turned off by default.

## What is external access?

External access is subtly different to guest access as it allows another organization's users access to your Teams environment. Through external access, they can call, message, and find anyone in your organization. However, they won't have access to your teams or channels, or any other Teams resources. By default, external access is enabled.

If you need a third party to access your teams and channels, you may want to consider guest access, since external access won't permit this.

## Compare guest access with external access

Both guest and external access can be used at the same time in Teams meetings. If for compliance and security reasons, you want to limit access to Teams resources, you should consider using external access. With guest access, you do have the capability to specify the level of restrictions to meet your compliance and security obligations.

These include:

- Deciding which teams a guest can be added to.
- Assessing the guest and grant access to a team based on the domain they're coming from.
- Deciding if the guest can access your teams and channels associated SharePoint site.

## Enable guest access

Before you enable guest access, you first of all need to assess what level of access they need. Teams provides guest access to features and capabilities using four levels of authorization. Each authorization level controls the guest experience when using Teams:

- **Azure Active Directory** - This authorization level controls the guest experience at the directory, tenant, and application level.
- **Microsoft Teams** - Controls the guest experience at a Teams level only.
- **Microsoft 365 Groups** - Controls the guest experience in Microsoft Teams and Microsoft 365 Groups.
- **SharePoint Online and OneDrive for Business** - Controls the guest experience in SharePoint Online, OneDrive for Business, Teams, and Microsoft 365 Groups.

Each level gives you the flexibility to decide how a guest will interact with your organization through Teams.

### Configure guest access using Teams admin center

To provision guest access, you'll need to use the Teams admin center. When you enable guest access, you'll also need to define what a guest can do, including:

- Make private peer-to-peer calls.
- Use IP-based video.
- See or use screen sharing mode.
- Send, edit, or delete messages.
- Use Teams meetings chat.
- Use Giphys, memes or stickers in chat conversations.

Follow these steps to enable guest access in your Teams environment:

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com/).
1. Select **Org-wide settings** > **Guest access**.
1. Set **Allow guest access in Microsoft Teams** to **On**.

    :::image type="content" source="../media/2-set-up-guests-image1.png" alt-text="Screenshot showing how to turn on the allow guest access in  Teams":::

1. Under **Calling**, **Meeting**, and **Messaging**, select **On** or **Off** for each capability, depending on what you want to allow for guest users.

    - **Make private calls** - Turn **On** to allow guests to make peer-to-peer calls.
    - **Allow IP video** - Turn **On** to allow guests to use video in their calls and meetings.
    - Screen sharing mode - Controls the availability of screen sharing for guest users.
        - Select **Disabled** to remove the ability for guests to share their screens in Teams.
        - Select **Single application** to allow sharing of individual applications.
        - Select **Entire screen** to allow complete screen sharing.
    - **Allow Meet Now** - Turn **On** to allow guests to use the Meet Now feature in Microsoft Teams.
    - **Edit sent messages** - Turn **On** to allow guests to edit messages they previously sent.
    - **Guests can delete sent messages** - Turn **On** to allow guests to delete messages they previously sent.
    - **Chat** - Turn **On** to give guests the ability to use chat in Teams.
    - **Use Giphys in conversations** - Turn **On** to allow guests to use Giphys in conversations. Giphy is an online database and search engine that allows users to search for and share animated GIF files. Each Giphy is assigned a content rating.
    - Giphy content rating - Select a rating from the drop-down list:
        - **Allow all content** - Guests can insert all Giphys in chats, regardless of the content rating.
        - **Moderate** - Guests can insert Giphys in chats, but will be moderately restricted from adult content.
        - **Strict** - Guests can insert Giphys in chats, but will be restricted from inserting adult content.
    - **Use memes in conversations** - Turn **On** to allow guests to use Memes in conversations.
    - **Use Stickers in conversations** - Turn **On** to allow guests to use stickers in conversations.

1. Select **Save**.

## Enable anonymous users in meeting in Teams

In Teams, an anonymous user is one that hasn't been authenticated against your Active Directory. There's a built-in policy called **RestrictedAnonymousAccess**, which contains setting that will prevent an anonymous user from starting or joining a meeting.

By default, anonymous users can't start a meeting, but they can be invited by participants of a meeting if you've enabled them.

You'll need to use Teams PowerShell to make changes to policies.

Run the following to get the Teams meeting policy assignments for your organization.

```powershell
Get-CsOnlineUser | Select-Object objectid, TeamsMeetingPolicy | Group-Object TeamsMeetingPolicy
```

If you have a small number of users, you can remove the **RestrictedAnonymousAccess** meeting policy using the **Grant-CSTeamsMeetingPolicy** cmdlet.

Run the following to remove the **RestrictedAnonymousAccess** meeting policy from users.

```powershell
Get-CsOnlineUser |? TeamsMeetingPolicy -eq "RestrictedAnonymousAccess" | Select-Object objectid | foreach {Grant-CsTeamsMeetingPolicy -Identity $_.ObjectId -PolicyName $null}
```

If you have a large number of users, it's more efficient to use the **New-CsBatchPolicyAssignmentOperation** cmdlet to submit a batch operation.

Run the following commands to remove the **RestrictedAnonymousAccess** meeting policy from a batch of users.

```powershell
$restrictedAnonymousUsers = @(Get-CsOnlineUser |? TeamsMeetingPolicy -eq "RestrictedAnonymousAccess" | %{ $_.ObjectId })
```

```powershell
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMeetingPolicy -PolicyName $null -Identity $restrictedAnonymousUsers -OperationName "Batch unassign meeting policy"
```

### Learn more

- [Grant-CSTeamsMeetingPolicy](/powershell/module/skype/grant-csteamsmeetingpolicy)
- [New-CsBatchPolicyAssignmentOperation](/powershell/module/teams/new-csbatchpolicyassignmentoperation?)
