When planning your transition from Skype for Business to Teams, you can choose appropriate upgrade path and coexistence modes based on users' readiness. 

Setting transitional coexistence mode enables a smoother transition to Microsoft Teams. You can choose the same coexistence mode for all users or different coexistence modes for different groups of users.

## Set upgrade options for all users from Teams Admin Center

The following steps configure upgrade for all users within your organization:

1. Sign in to **Microsoft Teams admin center**, and under **Teams** > select **Teams upgrade settings**.

:::image type="content" source="../media/teams-org-wide-upgrade.png" alt-text="Upgrade options for all users from Teams Admin Center":::

2. On the **Teams upgrade** page, from **Coexistence mode** options, choose one of the following options for your organization:

   - **Islands**

   - **Skype for Business only**

   - **Skype for Business with Teams collaboration**

   - **Skype for Business with Teams collaboration and meetings**

   - **Teams only**

   :::image type="content" source="../media/coexistence-mode.png" alt-text="Coexistence modes":::

3. You can enable **Notify Skype for Business users that an upgrade to Teams is available** while not selecting **Teams only** mode.

4. On the **Teams upgrade** page, you can select the **Preferred app for users to join Skype for Business meetings**.

   - Skype Meetings app

   - Skype for Business

5. You can also enable **Download the Teams app in the background for Skype for Business users**.

6. Select the **Save** button to save your changes.

## Set upgrade options for a single user from Teams Admin Center

In some scenarios, you may want to set different coexistence modes for different users. The following steps set the upgrade options for a single user:

1. Sign in to **Microsoft Teams admin center**.

2. Under the **Users** section, find the user that you would like to set the upgrade options.

3. On the user page, on the **Account** tab, under **Teams upgrade** section, select **Edit**.

4. On the **Teams Upgrade** page, choose one of the following options for the selected user:

   - **Use** **Org-wide settings**

   - **Islands**

   - **Skype for Business only**

   - **Skype for Business with Teams collaboration**

   - **Skype for Business with Teams collaboration and meetings**

   - **Teams only**

5. Select **Apply**.

6. If you select any **Coexistence mode** (except **Use Org-wide settings)**, you will have the option to enable notifications in the user's Skype for Business app, which will inform the user that the upgrade to Teams is coming soon. Enabling this for the user is done by turning on the **Notify the Skype for Business user** option.

   :::image type="content" source="../media/islands-mode.png" alt-text="Upgrade options for a single user from Teams Admin Center":::

7. At the end, select **Apply** to apply your changes.

## Set upgrade options from PowerShell

PowerShell is a good option for automation. In order to allow administrators to use PowerShell to manage the transition from Skype for Business to Teams, you can use ```Grant-CsTeamsUpgradePolicy``` cmdlet. This cmdlet enables admins to apply ```TeamsUpgradePolicy``` to either individual users or to configure the default settings for an entire organization.

For example, to configure the user AlexW@contoso.com to Teams in **Islands mode** and to notify the user, run the following cmdlet:

```powershell
Grant-CsTeamsUpgradePolicy -PolicyName IslandsWithNotify -Identity "AlexW@contoso.com"
```

Or, for configuring a TeamsOnly policy for the whole organization, run the following cmdlet:

```powershell
Grant-CsTeamsUpgradePolicy -PolicyName TeamsOnly -Global
```
