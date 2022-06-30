Teams policies control how users can interact with teams and channels. For example, you can set whether users are allowed to create private or shared channels.

A user can only be assigned to one team policy at a time. If users are not assigned a custom policy, the default global policy applies to the users. 

> [!NOTE]
> Policy changes can take up to 24 hours to take effect.

## Create and manage Teams policies

### Use Teams admin center

To create a new Teams policy, use the following steps:

1. Go to **Teams admin center**, select **Teams** > **Teams Policies**.

2. Select **+ Add** from the top pane.

3. In the **New teams policy** window, enter the required fields and settings.

    |Policy settings|Description|
    |:-----|:----------|
    |**Create private channels**|When **On**, team owners and members can create private channels. (Team owners can control if members can create private channels in each team.)|
    |**Create shared channels**|When **On**, team owners can create shared channels. Teams apps that are available for your organization are also available in shared channels.|
    |**Invite external users to shared channels**|When **On**, owners and members of shared channels can invite external participants from organizations where a cross-organization trust has been configured. Teams policies for your organization apply to these channels.|
    |**Join external shared channels**|When **On**, users can participate in shared channels created by other organizations where a cross-organization trust has been configured. Teams policies for the other organization apply to these channels.|

4. Select **Apply** to save.

    :::image type="content" source="../media/teams-policy-user.png" alt-text=" Screenshot of managing users of Teams policies":::


You can then assign the policy directly to users, either individually or at scale through a batch assignment, or to a group that the users are members of. You can also edit the global policy or any custom policies that you create.

For the scenario that only allows a limited group of users to create private channels, use the following steps:

1. Create a custom Teams policy with creating private channels turned on.
2. Assign the custom policy to that group of users.
3. Turn off the private channel creation in the Global (org-wide default) policy.

### Use PowerShell

You can also use PowerShell to manage Teams policies.

- ```New-CsTeamsChannelsPolicy```
- ```Set-CsTeamsChannelsPolicy```
- ```Get-CsTeamsChannelsPolicy```
- ```Grant-CsTeamsChannelsPolicy```
- ```Remove-CsTeamsChannelsPolicy``` 

For example, the following command creates a new Teams policy that restricts the creation of private channels in Teams:

```powershell
New-CsTeamsChannelsPolicy -Identity "IT-Department" -Description "All members of the IT-Department" -AllowPrivateChannelCreation:$false
```

