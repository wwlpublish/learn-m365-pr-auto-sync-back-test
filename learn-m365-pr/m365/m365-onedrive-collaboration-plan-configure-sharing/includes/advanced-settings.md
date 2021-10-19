
## Limit external sharing by domain

You can specify a list of allowed or blocked domains for external sharing. When specified, sharing invitations can only be sent to allowed domains. Denied domains cannot be sent sharing invitations.

1. Navigate to SharePoint Admin Center.
1. Select **Policies > Sharing**.
1. Expand **More external sharing settings**.
1. Select or deselect the **Limit external sharing by domain** checkbox.
1. Select **Add domains**.
1. Add the domains that you want your company users to be able to access.

:::image type="content" source="../media/external-sharing-settings.png" alt-text="Screen shot showing the external sharing settings.":::

:::image type="content" source="../media/add-domains.png" alt-text="Screen shot showing where domains can be added.":::

## Limit the sharing options for a user

After you have set the organization level sharing options, you can also further limit sharing options for an individual OneDrive user.

1. In the Admin Center, select **Users > Active Users**.
1. Select the user from the list.
1. In the pop up panel on the left, select **OneDrive**.
1. Select **Manage external sharing**.

:::image type="content" source="../media/onedrive-external-sharinga.png" alt-text="Screen shot showing how to limit sharing access for an individual OneDrive.":::

- Select the required option

:::image type="content" source="../media/onedrive-external-sharing.png" alt-text="Screen shot showing how to limit sharing access for an individual OneDrive.":::

## Allow only users in specific security groups to share externally

To limit who can share with guests in SharePoint and OneDrive, you can limit sharing to people in specified security groups. These sharing settings affect files and folders stored in OneDrive and SharePoint and not adding members to SharePoint sites, Microsoft Teams, and other Microsoft 365 group resources.

People in the security group can be given the ability to share with unauthenticated users only or with both unauthenticated and authenticated users.

1. In the SharePoint Admin Center, select **Policies > Sharing**.
1. Expand **More external sharing settings**.
1. Select **Allow only users in specific security groups to share externally**.
1. The **Manage security groups** button appears.

    :::image type="content" source="../media/security-groups.png" alt-text="Screen shot showing how to add a security group.":::

1. Select the options to amend.

    :::image type="content" source="../media/manage-security-zones.png" alt-text="Screen shot showing how to add a security group.":::

## Allow guests to share items they don't own

This setting is turned on by default and guests must have full control permission to share items externally. This allows a guest to share a file with other people once shared with them.

## Sharing notifications

External sharing notifications allow users to monitor through email and mobile devices which external users have access to their files and what they are doing with them.

File and folder owners will be emailed when:

- Another user invites external users to shared files.
- An external user accepts an invitation to access their files.
- An anonymous link is created or changed.

If external sharing is enabled in your organization, these notifications are enabled by default.

## Learn more

- [Restrict sharing of SharePoint and OneDrive content by domain](/sharepoint/restricted-domains-sharing?azure-portal=true)
- [Manage guest access in Microsoft 365 groups](/microsoft-365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide?azure-portal=true)
