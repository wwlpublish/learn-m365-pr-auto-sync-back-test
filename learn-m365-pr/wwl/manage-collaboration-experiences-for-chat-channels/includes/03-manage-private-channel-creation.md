Teams policies control how users can interact with teams and channels. For example, whether private teams are discovered in the search results, and whether users can create private teams.

A user can only be assigned to one team policy at a time. If users are not assigned a custom policy, the default global policy applies to the users. 

> [!NOTE]
> Policy changes can take up to 24 hours to take effect.

## Manage private channel creation for users (Teams policies)

### Use Teams admin center

For the scenario that only allow a limited group of users to create private channels, you'll do the following steps:

1. Create a custom Teams policy with creating private channels tuned on.
2. Assign the custom policy to that group of users.
3. Turn off the private channel creation in the Global (org-wide default) policy. 

To create a new Teams policy, you'll do the following steps:

1. Go to **Teams admin center**, select **Teams**> **Teams Policies**.

2. Select **+ Add** from the top pane.

3. In the **New teams policy** window, enter the required fields and settings.

4. Select **Save**.

    :::image type="content" source="../media/teams-policy-user.png" alt-text="Screenshot of managing users of Teams policies":::


You can then assign the policy directly to users, either individually or at scale through a batch assignment, or to a group that the users are members of. You can also edit the global policy or any custom policies that you create.


### Use PowerShell

You can also use PowerShell to manage Teams policies.

- New-CsTeamsChannelsPolicy
- Set-CsTeamsChannelsPolicy
- Get-CsTeamsChannelsPolicy
- Grant-CsTeamsChannelsPolicy
- Remove-CsTeamsChannelsPolicy 

For example, the following command creates a new Teams policy that restricts the creation of private channels in Teams:

```powershell
New-CsTeamsChannelsPolicy -Identity "IT-Department" -Description "All members of the IT-Department" -AllowPrivateChannelCreation:$false
```

## Manage private channel creation for a team

One way to restrict the creation of private channels is to let an administrator create a Team policy that restricts private channel creation. But team owners can also restrict the private channel creation on a per team level basis themselves. This can be handy when team owners want to retain full control of their team activity, which includes restricting members from creating private channels, which team owners in turn cannot control.

To restrict team members from creating private channels, a team owner must open the team from one of the Microsoft Team clients and manage the team. A team owner should perform the following steps to restrict his or her team members from creating private channels:

1. Log in to one of the Microsoft Teams clients.

2. Select the ellipsis icon (the three dots) to the right of the team and select **Manage team**.

3. Open the **Settings** tab and the **Member permissions** dropdown menu.

4. Select or deselect **Allow members to create private channels**.

By doing these steps, you will restrict private channel creation to team owners only.

:::image type="content" source="../media/team-private-channel-creation-restriction.png" alt-text="Screenshot of managing member permissions":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”