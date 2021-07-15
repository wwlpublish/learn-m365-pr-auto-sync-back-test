You can upgrade users from Skype for Business Online selectively or all-in by assigning the appropriate coexistence and upgrade mode to your users.

Skype for Business Online customers recommended path is to start with the default Islands mode, drive Teams adoption saturation in the organization, and then move to TeamsOnly mode rapidly.

## Assign the coexistence and upgrade mode

You can upgrade your users to TeamsOnly mode by assigning the UpgradeToTeams instance of TeamsUpgradePolicy, which can be performed by using the Microsoft Teams admin center or a Skype for Business remote Windows PowerShell session. You can do this either on a per-user basis, or on a tenant-wide basis if you want to upgrade the entire tenant in one step.

## Upgrade all users to Teams at one time

### Step 1: Notify the users of the change (optional)

1. In the Microsoft Teams admin center, select **Org-wide settings > Teams upgrade**.
1. Under **Coexistence mode**, change the **Notify Skype for Business users that an upgrade to Teams is available** switch to **On**.

### Step 2: Set the coexistence mode to TeamsOnly for the organization

1. In the Microsoft Teams admin center, select **Org-wide settings**.
1. Select **TeamsOnly** mode from the **Coexistence mode** drop-down list.

## Upgrade users in stages

### Step 1: Identify groups of users for upgrade

Often organizations choose to upgrade their organizations in waves of users. You'll want to identify these users first so you can easily search for them in the Microsoft Teams admin center. Alternatively, you may want to use PowerShell to more efficiently do this.

### Step 2: Set notification for the users in the current upgrade wave (optional)

If using the Microsoft Teams admin center, you can configure TeamsUpgradePolicy for up to 20 users at once:

1. In the Microsoft Teams admin center, select **Users**, and find and multi-select the checkbox for up to 20 users who should be upgraded.
1. Select **Edit settings** in the upper left corner of the listview.
1. In the **Edit settings** pane on the right, under **Teams upgrade**, change the **Notify the Skype for Business user** switch to **On**.

   >[!NOTE]
   > If the value of coexistence mode is **Use Org-wide settings,** you won't see this switch, so you'll need to first explicitly set the Coexistence mode for these users to whatever the default value is for the org.

### Step 3: Set the coexistence mode for users to TeamsOnly

When you are ready to upgrade the users in the current wave to use Teams as their only application, set the Coexistence mode for the users to TeamsOnly.

If using the Microsoft Teams admin center, you can configure TeamsUpgradePolicy for up to 20 users at once:

1. In the Microsoft Teams admin center, select **Users**, and then select the checkbox for up to 20 users.
1. Select **Edit settings** in the upper left corner of the listview.
1. In the **Edit settings** pane on the right, under **Teams upgrade** section, set the coexistence mode to **TeamsOnly** in the drop-down list.

### Step 4: Repeat steps 1-3 for successive waves of users

As you validate your upgrade to TeamsOnly mode and are ready to expand, repeat the previous steps to apply TeamsOnly mode to more users. Alternatively, you may find it easier to upgrade groups of users at once using PowerShell.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Upgrade from Skype for Business Online to Teams](/MicrosoftTeams/upgrade-to-teams-execute-skypeforbusinessonline)
