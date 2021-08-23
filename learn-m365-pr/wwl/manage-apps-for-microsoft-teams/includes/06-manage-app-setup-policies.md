As an admin, you can use app setup policies to customize Microsoft Teams to highlight the apps that are most important for your users. You choose the apps to pin to the apps bar and set the order that they appear. App setup policies let you showcase apps that users in your organization need, including apps built by third-parties or by developers in your organization. You can also use app setup policies to manage how built-in features appear.

Apps are pinned to the app bar. This is the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients (iOS and Android). 

|Teams desktop client  |Teams mobile client |
|---------|---------|
|:::image type="content" source="../media/app-setup-policies-mobile-app-bar.png" alt-text="Screenshot showing Teams desktop client](../media/app-setup-policies-desktop-app-bar.png)<br>  |   ![Screenshot showing Teams mobile client":::      |


You manage app setup policies in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create custom policies and assign them to users. Users in your organization will automatically get the global policy unless you create and assign a custom policy. 

You can edit the settings in the global policy to include the apps that you want. If you want to customize Teams for different groups of users in your organization, create and assign one or more custom policies. If a user is assigned a custom policy, that policy applies to the user. If a user is not assigned a custom policy, the global policy applies to the user. 

:::image type="content" source="../media/app-setup-policies.png" alt-text="Screenshot of app setup policies":::


> [!NOTE]
> If you have Teams for Education, it is important to know that the Assignments app is pinned by default in the global policy even though you do not currently see it listed in the global policy. It will be the fourth app in the list of pinned apps on Teams clients.
 

## Create a custom app setup policy

You can use the Microsoft Teams admin center to create a custom policy:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Setup policies**.
2. Select **Add**.
    :::image type="content" source="../media/app-setup-policies-add.png" alt-text="Screenshot showing the Add app setup policies page":::
3. Enter a name and description for the policy.
4. Turn on or turn off **Upload custom apps**, depending on whether you want to let users upload custom apps to Teams. You won't be able to change this setting if **Allow third-party apps** is turned off in **org-wide app settings**.
5. Turn on or turn off **Allow user pinning**, depending on whether you want to let users personalize their app bar by pinning apps to it.
6. To install apps for users:

    1. Under **Installed apps**, select **Add apps**.
    2. In the **Add installed apps** pane, search for the apps you want to automatically install for users when they start Teams. You can also filter apps by app permission policy. When you've chosen your list of apps, select **Add**.

        :::image type="content" source="../media/app-setup-policies-add-installed-apps.png" alt-text="Screenshot showing the Add installed apps pane":::

7. To pin apps:

    1. Under **Pinned apps**, select **Add apps**.
    2. In the **Add pinned apps** pane, search for the apps you want to add, and then select **Add**. You can also filter apps by app permission policy. When you've chosen your list of apps to pin, select **Add**.

         :::image type="content" source="../media/app-setup-policies-add-apps.png" alt-text="Screenshot showing the Add pinned apps pane":::

    3. Arrange the apps in the order that you want them to appear in Teams, and then select **Save**.

        :::image type="content" source="../media/app-setup-policies-new-policy-setup.png" alt-text="Screenshot showing the Pinned apps section":::   

## Edit a custom app setup policy

You can use the Microsoft Teams admin center to edit a policy, including the global (Org-wide default) policy and custom policies that you create.

 

1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Teams apps** > **Setup policies**.

2. Select the policy by selecting to the left of the policy name, and then select **Edit**.

3. From here, make the changes that you want. You can add, remove, and change the order of apps.

4. Select **Save**.

 

## Assign a custom app setup policy to users

You can use the Microsoft Teams admin center to assign a custom app setup policy to individual users, or you can use the Skype for Business PowerShell module to assign a custom policy to groups of users, such as a security group or distribution group.

 

### Assign a custom app setup policy to users from Teams admin center

There are multiple ways to assign an app setup policy to your users in the admin center. You can assign users either in Setup policies or in Users in Teams admin center.

Perform the following steps if you want to assign users in setup policies:

1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Teams apps** > **Setup policies**.

2. Select the policy by selecting to the left of the policy name.

3. Select **Manage users**.

4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.  
‎
5. When you're finished adding users, select **Save**.
 

You can also perform the following steps if you want to assign users within the Users pane:

1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Users**, and then select the user.

2. Select the user by selecting to the left of the username, and then select **Edit settings**.

3. Under **App setup policy**, select the app setup policy you want to assign, and then select **Apply**.

 

### Assign a custom app setup policy to users in a group using PowerShell

You may want to assign an app setup policy to multiple users that you have already identified. For example, you may want to assign a policy to all users in a security group. You can do this by connecting to the Azure Active Directory PowerShell for Graph module and the Skype for Business PowerShell module. 

For example, to assign an app setup policy called **HR App Setup Policy** to all users in the **Contoso HR Project** group, you would perform the following PowerShell commands:

 
```powershell

## Get the GroupObjectId of the particular group: ##
$group = Get-AzureADGroup -SearchString "Contoso HR Project"

## Get the members of the specified group: ##
$members = Get-AzureADGroupMember -ObjectId $group.ObjectId -All $true | Where-Object {$_.ObjectType -eq "User"}

## Assign all users in the group to a particular app setup policy: ##
$members | ForEach-Object { Grant-CsTeamsAppSetupPolicy -PolicyName "HR App Setup Policy" -Identity $_.EmailAddress}
```

Depending on the number of members in the group, this command may take several minutes to execute.

 
