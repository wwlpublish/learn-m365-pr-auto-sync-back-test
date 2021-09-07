As an admin, you can use app permission policies to control what apps are available to Microsoft Teams users in your organization. You can allow or block all apps or specific apps published by Microsoft, third-parties, and your organization. When you block an app, users who have the policy are unable to install it from the Teams app store. You must be a global admin or Teams service admin to manage these policies.

You manage app permission policies in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies to individual users or users in a group.

:::image type="content" source="../media/app-permissions-policies.png" alt-text="Screenshot of app permission policy":::

By default, all apps are allowed in the **global policy**. This includes apps published by Microsoft, third parties, and your organization. Users in your organization will automatically get the global policy unless you create and assign a custom policy. **Organization-wide app settings** on the **Manage apps** page override the global policy and any custom policies that you create and assign to users.

For example, you want to block all third-party apps and allow specific apps from Microsoft for the HR team in your organization. First, you would go to the Manage apps page and make sure that the apps that you want to allow for the HR team are allowed at the org level. Then, create a custom policy named HR App Permission Policy, set it to block and allow the apps that you want, and assign it to users on the HR team.

## Create a custom app permission policy

If you want to control the apps that are available for different groups of users in your organization, create and assign one or more custom app permission policies. You can create and assign separate custom policies based on whether apps are published by Microsoft, third-parties, or your organization. It's important to know that after you create a custom policy, you can't change it if third-party apps are disabled in org-wide settings.  
‎
1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Teams apps** > **Permission policies**.

2. Select **Add**.  ‎  
‎:::image type="content" source="../media/app-permission-policies-new-policy.png" alt-text="Screenshot of settings for a new app permission policiy":::  

3. Enter a name and description for the policy.

4. Under **Microsoft apps**, **Third-party apps**, and **Tenant apps**, select one of the following options that is listed in the following graphic:

	:::image type="content" source="../media/choose-teams-apps-published-dialog-box.png" alt-text="Screenshot of options to manage app permissions":::

5. If you selected **Allow specific apps and block all others**, add the apps that you want to allow:
	- Select **Allow apps**.
	- Search for the app(s) that you want to allow, and then select **Add**. The search results are filtered to the app publisher (Microsoft apps, Third-party apps, or Tenant apps).
	- Once you have chosen the list of apps, select **Allow**.

6. Similarly, if you selected **Block specific apps and allow all others**, search for and add the apps that you want to block.
7. Select **Save**.


## Edit an app permission policy

You can use the Microsoft Teams admin center to edit a policy, including the global policy and custom policies that you create.

1. In the left-hand navigation pane of the **Microsoft Teams admin center**, go to **Teams apps** > **Permission policies**.

2. Select the policy by selecting to the left of the policy name, and then select **Edit**.

3. Make the changes that you want. You can manage settings based on the app publisher and add and remove apps based on the allow/block setting.

4. Select **Save**.

## Assign a custom app permission policy to users
You can use the Microsoft Teams admin center to assign a custom policy to one or more users. Alternatively, you can use the Skype for Business PowerShell module to assign a custom policy to groups of users, such as all users in a security group or distribution group.

### Assign a custom app permission policy to a user
To assign users to app permission policies, you can either assign users to a policy, or you can assign policies to a user.
 
You should perform the following steps to assign users to a policy:  
‎
1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Teams apps** > **Permission policies**.
2. Select the custom policy by selecting to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.  ‎  
5. When you're finished adding users, select **Apply**. 

Alternatively, you can also perform the following steps to assign a policy to a user:  
‎
1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Users**.
2. Select the user by selecting to the left of the username, and then select **Edit settings**.
3. Under **App permission policy**, select the app permission policy you want to assign, and then select **Apply**.
 
### Assign a custom app permission policy using PowerShell

You may want to assign a custom app permission policy to multiple users with PowerShell for automation. For example, you may want to assign a policy to all users in a security group. You can do this by connecting to the Azure Active Directory PowerShell module and the Skype for Business PowerShell module and using the ```Grant-CsTeamsAppPermissionPolicy``` cmdlet. 
 
For example, if you want to assign a custom app permission policy called HR App Permission Policy to all users in the Contoso HR Project group, you would run the following command: 

```powershell
$group = Get-AzureADGroup -SearchString "Contoso HR Project"

$members = Get-AzureADGroupMember -ObjectId $group.ObjectId -All $true | Where-Object {$_.ObjectType -eq "User"}

$members | ForEach-Object { Grant-CsTeamsAppPermissionPolicy -PolicyName "HR App Permission Policy" -Identity $_.EmailAddress}
```

Depending on the number of members in the group, this command may take several minutes to execute.
