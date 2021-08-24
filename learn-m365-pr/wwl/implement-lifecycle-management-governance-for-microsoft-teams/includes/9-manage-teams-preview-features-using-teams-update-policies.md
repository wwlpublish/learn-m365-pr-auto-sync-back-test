Public Preview for Microsoft Teams provides early access to unreleased features in Teams. Previews allow you to explore and test upcoming features. 

Public preview is enabled on a per-user basis, and the option to turn on public preview is controlled in an admin policy. Update policies are used to manage Teams and Office preview users who will see pre-release or preview features in the Teams app. 

You can use the Global (Org-wide default) policy and customize it, or create one or more custom policies for your users. The steps below is to enable public preview features for users. 

## Create a custom Update policy
1. Sign in to the Teams admin center.
2. Select **Teams**>**Update policies**.
3. Select **Add**.
4. Name the update policy, add a description, and select one of the following options:

   * **Follow Office Preview (default)** This new default option will automatically enable Teams Public Preview features for any user enrolled in Office Current Channel (Preview). There are no other actions required by the end user.
   
   * **Enabled** This option enables Teams Public Preview - regardless of whether a user is enrolled in Office Current Channel (Preview). The end user must also opt in to Teams public preview in their Teams app.
   
   * **Not enabled** Teams Public Preview features will not be available to end users.

      ‎:::image type="content" source="../media/update-policies.png" alt-text="Select the Update policies option":::

You can also set the policy using PowerShell using the ```Set-CsTeamsUpdateManagementPolicy``` cmdlet with the ```-AllowPreview``` boolean parameter.

## Assign the custom Update policy to users
Once you created the custom policy, you need to assign the policy to specific users because it doesn't over-write the global policy.

1. Go to **Teams admin center**>**Teams**>**Update policies**.
2. Select the custom Update policy. 
3. Select **Manage Users**.
4. Search and select **Add** next to the users.
5. Select **Apply**.

   ‎:::image type="content" source="../media/assign-update-policies.png" alt-text="Assign Update policy to users":::

You can also set the policy using PowerShell using the `Set-CsTeamsUpdateManagementPolicy` cmdlet.

## Enable public preview in Teams clients

Depends on the assigned policy, users will need to switch to public preview from their Teams clients. 

* Users who are assigned the update policy with **"Not enabled"** option will not see Teams preview features.

* Users who are assigned the update policy with **"Follow Office Preview (default)"** option and **not enrolled** in Office Current Channel (Preview) will also not see Teams preview features.

* Users who are assigned the update policy with **"Follow Office Preview (default)"** option and **enrolled** in Office Current Channel (Preview) will automatically see Teams Public Preview features. There is no action for them to take and it's not possible for them to opt-out of the Teams Public Preview.

* Users who are assigned the update policy with **"Enabled"** option will see an option in the Teams app that allows them to switch to Public Preview. 

   To see the public preview features, users will enable the public preview on a desktop or web client with the following tasks:

   1. Select your profile to display the Teams menu.
   2. Select **About** → **Public preview**.

      ‎:::image type="content" source="../media/public-peview-teams-client.png" alt-text="The public prepiew option in Teams client":::
   3. Select **Switch to Public preview**.
   
      ‎:::image type="content" source="../media/switch-to-public-preview.png" alt-text="Prompt for switching To Public Preview":::


For a list of what's available in the Teams public preview, see [Release Notes for Office Current Channel (Preview)](/officeupdates/current-channel-preview).
