Microsoft Teams allows you to collaborate with people both inside and outside your organization. The people outside your organization must have **guest access**. Many organizations find this guest access vital, but you must take care to ensure that it doesn't introduce vulnerabilities into your system.

## How to secure guest access

There are seven steps. You'll find a link to a troubleshooting guide in the **Learn more** section.

1. Enable **Guest access in Teams**.
1. Configure **Azure AD** to allow guests in Teams.
1. Configure **Microsoft 365 groups**.
1. Configure **Sharing in Microsoft 365**.
1. Verify **Sharing settings in SharePoint**.
1. Set up **Guest permissions in Teams**.
1. Turn on **Anonymous users can join a meeting** if necessary.

Let's examine these steps in more detail.

## Enable guest access in Teams

To allow or disallow guest access for the whole organization, you must be a Teams service administrator.

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com/).
1. Select **Org-Wide settings** > **Guest access**.
1. Set the **Allow guest access in Microsoft Teams** switch to **On**.
1. On the same page, you enable or disable guests, or turn off **Calling**, **Meeting**, and **Messaging** settings for guests.
1. Select **Save**. Each Team can then choose whether to allow guess access.

:::image type="content" source="../media/6-guest-access.png" alt-text="Screenshot of the Guest access screen in the admin center":::

## Configure Azure AD

Before you collaborate with guests in Teams, you must configure your Azure AD settings.

1. Sign into the [Azure portal](https://portal.azure.com) as a tenant administrator.
1. Select **Azure Active Directory** > **Users** > **User settings**.
1. Under **External users**, select **Manage external collaboration settings**. You can also access the same settings from **Manage** > **Organizational relationships** > **Settings**.
1. On the **External collaboration settings** page, choose the policies you want to enable.

The following table gives details of these settings:

|Policy  |What it does  |
|---------|---------|
|Guest user permissions are limited    | Determines permissions for guests in your directory. Select **Yes** to block guests from certain directory tasks, like enumerating users, groups, or other directory resources. Select **No** to give guests the same access to directory data as regular users in your directory.      |
|Admins and users in the guest inviter role can invite    |  To allow admins and users in the "guest inviter" role to invite guests, set this policy to **Yes**.       |
|Members can invite    |   To allow non-admin members of your directory to invite guests, set this policy to **Yes** (recommended). If you want only admins to add guests, set this policy to **No**. This action will limit the guest experience for non-admin teams owners. They'll only be able to add guests in Teams that have already been added in Azure AD by the admin.      |
|Guests can invite     |    To allow guests to invite other guests, set this policy to **Yes**.  However, this option isn't currently supported, so guests can't invite others even when it's set to **Yes**.   |
|Enable email one-time passcode for guests    |  Currently in preview.       |
|Collaboration restrictions     |    Allows or blocks invitations to specific domains.  |
| | |

## Configure Microsoft 365 Groups

If you want guest users to access group content, you must specifically enable them.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to **Settings** > **Org Settings**.
1. Select **Services**, and then select **Microsoft 365 Groups**.
1. Select the check box **Let group members outside the organization access group content** to allow guests to access group content.
1. Select the check box **Let group owners add people outside the organization to groups** to allow team owners to add new guests. This setting must be turned on to support guest access.

## Configure sharing in Microsoft 365

You can enable ordinary users to add guests:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to **Settings** > **Org Settings**.
1. Select **Security & privacy** > **Sharing**.
1. Select the check box **Let users add new guests to this organization** > **Save changes**.

## Verify sharing setting in SharePoint

Because Teams uses SharePoint sites for storage, verify the guest settings for those sites:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), under **Admin centers**, select **SharePoint**.
1. Under **Sites**, select **Active sites**.
1. Select the site, select **Sharing**, and then select either **Anyone** or **New and existing guests**.

## Set guest permissions in Teams

In the Teams application, at the individual team level, configure guest permissions that control whether guests can create, update, or delete channels. Teams administrators and team owners can configure these settings.

:::image type="content" source="../media/6-teams-guest-permissions.png" alt-text="Screenshot of the Teams guest permissions options":::

## Anonymous users can join a meeting

If you want guests to join meetings, you must turn on the **Anonymous users can join a meeting** setting in Microsoft Teams.

1. In the [Teams admin center](https://admin.teams.microsoft.com/), go to **Meetings** > **Meeting settings**.
1. Under **Participants**, select **Anonymous users can join a meeting**.

## Learn more

- [Allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/external-identities/allow-deny-list)
- [Use Teams administrator roles to manage Teams](https://docs.microsoft.com/microsoftteams/using-admin-roles)
- [Manage guest access in Microsoft 365 Groups](https://docs.microsoft.com/microsoft-365/admin/create-groups/manage-guest-access-in-groups)
- [Control guest access in Microsoft 365 Groups](https://docs.microsoft.com/microsoftteams/teams-dependencies)
- [Manage meeting settings in Teams](https://docs.microsoft.com/microsoftteams/meeting-settings-in-teams)
- [Troubleshoot problems with guest access in Microsoft Teams](https://docs.microsoft.com/microsoftteams/troubleshoot-guest-access)
