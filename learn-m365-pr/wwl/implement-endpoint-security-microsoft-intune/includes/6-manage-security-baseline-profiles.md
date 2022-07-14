Organizations should manage profiles for security baselines. Doing so helps to secure and protect their users and their Windows 10 and later devices. Security baselines are pre-configured groups of Windows settings that represent the recommended security posture from the relevant security teams. An organization can deploy a default (unmodified) baseline or create a customized profile to enforce the settings it requires for its environment.

When an organization creates a security baseline profile in Intune, it's creating a template that consists of multiple device configuration settings. Common tasks performed by organizations when working with security baselines include:

 -  **Create a profile**. Configure the settings you want to use and assign the baseline to groups.
 -  **Change the baseline version for a profile**. Change the baseline version in use by a profile.
 -  **Remove a security baseline assignment**. Stop managing settings with a security baseline.

Each of these tasks is examined in the following sections in this unit.

### Prerequisites

To manage baselines in Intune, your account must have the [Policy and Profile Manager](/mem/intune/fundamentals/role-based-access-control#built-in-roles?azure-portal=true) built-in role. Some baselines may also require you to have an active subscription to other services, such as Microsoft Defender for Endpoint.

### Create a profile

Organizations must perform the following steps to create a profile:

1.  In the **Microsoft Endpoint Manager admin center**, select **Endpoint security** in the navigation pane.
2.  On the **Endpoint security** page, select **Security baselines** on the navigation pane. Doing so will display the list of available baselines.
    
    :::image type="content" source="../media/available-baselines-1cd55c97.png" alt-text="Screenshot of the Endpoint security node showing the Security baseline page and the list of available baselines.":::
    
3.  Select the baseline you'd like to use.
4.  On the **Profiles** page for the selected baseline, select **+Create profile** on the menu bar.
5.  On the **Create profile** page, each of the steps in the **Create profile** process is displayed as a tab at the top of the page. The first step is the **Basics** tab. Enter the following fields on this tab:
     -  **Name**. Enter a name for your security baselines profile. For example, enter **Standard profile for Defender for Endpoint**.
     -  **Description**. Enter some text that describes what this baseline does. The description is optional, but recommended.
6.  Select **Next** to proceed to the **Configuration settings** tab. After you advanced to a new tab, you can select the tab name to return to a previously viewed tab if you need to make any changes.
7.  On the **Configuration settings** tab, view the groups of **Settings** that are available in the baseline you selected. You can expand a group to view the settings in that group, and the default values for those settings in the baseline. To find specific settings:
     -  Select a group to expand and review the available settings.
     -  Use the **Search** bar and specify keywords that filter the view to display only those groups that contain your search criteria.Each setting in a baseline has a default configuration for that baseline version. Reconfigure the default settings to meet your business needs. Different baselines may contain the same setting, and use different default values for the setting, depending on the intent of the baseline.
    
    :::image type="content" source="../media/sample-list-of-settings-67a17db6.png" alt-text="Screenshot of the Create profile page showing the Configuration settings tab with the application management settings highlighted.":::
    
8.  When you're finished customizing the settings, select **Next** to proceed to the **Scope tags** tab.
9.  On the **Scope tags** tab, select **+Select scope tags** to open the **Select tags** pane.
10. In the **Select tags** pane, select the scope tags that you want to assign to the profile, and then select the **Select** button at the bottom of the pane.
11. When you're finished selecting tags, select **Next** to proceed to the **Assignments** tab.
12. On the **Assignments** tab, under the Included groups section, select **Add groups** to include and then assign the baseline to one or more groups.
    
    :::image type="content" source="../media/assignments-tab-create-profile-194852d4.png" alt-text="Screenshot of the Create profile page showing the Assignments tab.":::
    
13. On the **Select groups to include** pane that appears, select the groups that you want to include in the profile. Then select the **Select** button.
    
    :::image type="content" source="../media/select-groups-to-include-pane-ea41c90f.png" alt-text="Screenshot of the Select groups to include pane showing the groups you can choose from to include in the profile.":::
    
14. If you want to exclude groups from the profile, repeat the prior steps, but this time you should select **+Add groups** under the **Excluded groups** section.
15. On the **Select groups to exclude** pane that appears, select the groups that you want to exclude from the profile. Then select the **Select** button.
16. Select **Next** to proceed to the **Review + create** tab. Review the details for the baseline. If any settings must be updated or corrected, select **Previous** to navigate back to the appropriate page to make your changes. When all settings are correct, select **Create** to save and deploy the profile.
17. As soon as you create the profile, it's pushed to the assigned group. It may also be immediately applied.
    
    > [!TIP]
    > If you save a profile without first assigning it to groups, you can later edit the profile to do so.

After you create a profile, you can edit it by performing the following steps:

1.  In the **Microsoft Endpoint Manager admin center**, select **Endpoint security** in the navigation pane.
2.  On the **Endpoint security** page, select **Security baselines** on the navigation pane.
3.  Select the baseline you'd like to use.
4.  On the **Profiles** page for the selected baseline, select the profile from the list of available profiles.
5.  On the **Overview** page for the selected profile, under the **Manage** section in the navigation pane, select **Properties**.
6.  On the **Properties** page, the tabs that you entered when creating the profile are now displayed as sections. Select the **Edit** option for the section that you want to update, then make your necessary changes. Repeat for each section (tab) that requires updating for the profile.
7.  When you're finished making your changes, select **Review+save** to commit your changes.

### Change the baseline version for a profile

When a new version for a baseline is released, organizations should plan to update their existing profiles to the new version:

 -  Existing profiles don’t upgrade to new versions automatically.
 -  Settings in baseline profiles that don’t use the latest version become read-only. Organizations can continue using those older profiles, including editing their name, description and assignments. However, they won't be able to edit settings for them or create new profiles based on the older versions.

> [!TIP]
> It's recommended that organizations [test the version update](/mem/intune/protect/security-baselines-configure#test-the-conversion-and-updated-baseline?azure-portal=true) on a copy of their existing profiles before they update their live profiles.

When an organization changes the profile version:

 -  It should select the latest instance of the same baseline. It can't change between two different baseline types, such as changing a profile from using a baseline for Defender for Endpoint to using the MDM security baseline.
 -  It can download a CSV file that lists the changes between the two baseline versions involved.
 -  It must choose how to update the profile:
     -  It can keep all its customizations from the original baseline version.
     -  It can choose to use the default values for all settings in the new baseline version.
    
    > [!NOTE]
    > An organization can't change only some settings in a profile during the update.

During conversion:

 -  New settings that weren't in the older version an organization was using are added. Any new settings from the new version will use their default values.
 -  Settings that aren't in the new baseline version that was selected are removed and no longer enforced by this security baseline profile. When a setting is no longer managed by a baseline profile, that setting doesn't reset on the device. Instead, the setting on the device remains set to its last configuration until some other process manages the setting to change it. Examples of processes that can change a setting after an organization stops managing it include:
     -  A different baseline profile.
     -  A group policy setting.
     -  Manual configuration that's made on the device.

After the conversion to the new baseline version is complete:

 -  The baseline immediately redeploys to assigned groups.
 -  An organization can edit the baseline to change individual settings.

### Test the conversion and updated baseline

Before an organization updates a baseline profile to a new version, it should create a copy of it so that it can test the new version of the profile on a group of devices.

 -  When an organization creates a copy, group assignments aren't included. This design means the organization's baseline copy won’t deploy to any devices at the time it makes a copy, or at the time it updates it to a new version.
 -  After an organization updates the profile to the latest version, it can edit its settings. The organization can assign the updated copy to a group of devices and edit it to introduce changes to individual settings in the profile.

### To change the baseline version for a profile

Before an organization updates the version of a profile that's assigned to groups, it should test the version update on a copy of the profile. Doing so enables the organization to validate the new baselines settings on a test group of devices.

Perform the following steps to change the baseline version for a profile:

1.  In the **Microsoft Endpoint Manager admin center**, select **Endpoint security** in the navigation pane.
2.  On the **Endpoint security** page, select **Security baselines** on the navigation pane. Doing so will display the list of available baselines.
3.  Select the baseline you'd like to use.
4.  On the **Profiles** page for the selected baseline, select the check box for the profile you want to edit, and then select the **Change Version** option that appears on the menu bar.
    
    :::image type="content" source="../media/select-baseline-2fb2ca1d.png" alt-text="Screenshot showing the Profiles page, with both a selected profile and the Change version option on the menu bar highlighted.":::
    
5.  On the **Change Version** pane that appears, use the **Select a security baseline to update to** dropdown, and select the version instance you want to use.
    
    :::image type="content" source="../media/select-instance-d5c0f3fe.png" alt-text="Screenshot showing the Change version pane for a selected profile, with a Select a security baseline to update version highlighted style=":::
    
6.  Select **Review update** to download a CSV file that displays the difference between the profiles current instance version and the new version you've selected. Review this file so that you understand which settings are new or removed, and what the default values for these settings are in the updated profile. When ready, continue to the next step.
7.  Choose one of the two options for **Select a method to update the profile**:
     -  **Accept baseline changes but keep my existing setting customizations**. This option keeps the customizations you made to the baseline profile and applies them to the new version you've selected to use.
     -  **Accept baseline changes and discard existing setting customizations**. This option overwrites your original profile completely. The updated profile will use the default values for all settings.
8.  Select **Submit**. The profile updates to the selected baseline version. After the conversion is complete, the baseline immediately redeploys to assigned groups.

### Remove a security baseline assignment

When a security baseline setting no longer applies to a device, or settings in a baseline are set to **Not configured**, those settings on a device may not revert to a pre-managed configuration depending on the settings in the security baseline. The settings are based on CSPs. Each CSP can handle the change removal differently.

Other processes that may later change settings on the device include:

 -  a different or new security baseline
 -  device configuration profile
 -  Group Policy configurations
 -  manual edit of the setting on the device

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”