You know from experience that users can become frustrated with the update process if it negatively affects their day-to-day work. You want to ensure that your users have a positive experience with all updates. You can control which options you want to give to users so they can decide when to install an update. You can choose whether you want to allow users to pause updates, specify active hours for auto restarts, download updates over metered connections, and more.

In this unit, you'll learn about how to control the user experience after a user's device receives an update.

## Control the Windows Update settings page

The Windows Update Settings page is where users can control things like active hours, see their update history, and more. You can control which options are visible to users on this page.

:::image type="content" source="../media/5-windows-update-settings-expanded.png" lightbox="../media/5-windows-update-settings-inline.png" alt-text="Figure 16. Windows Update Settings page.":::

The following controls are available to control update options for users:

- **Pause**
- **Remove access to windows update features**

Configuring the following will affect user Group Policy controls on the Windows Update Settings page as follows:

- **Specify active hours range for auto restarts**; this will remove the user's ability to configure active hours from the Windows Update Settings page.
- **Allow download automatically over a metered network** will make **Receive updates for other Microsoft products when you update Windows** unavailable.

### Group Policy: Remove access to "Pause updates" feature

You can use the **Remove access to "Pause updates" feature** Group Policy to prevent users from being able to pause updates:

:::image type="content" source="../media/5-gp-prevent-users-pause-updates-expanded.png" lightbox="../media/5-gp-prevent-users-pause-updates-inline.png" alt-text="Figure 17. Prevent users from pausing updates using a Group Policy.":::

### Use an MDM to prevent users from pausing updates

Alternatively, you can use set the **Option to pause Windows updates** to **Disable** in Microsoft Intune to prevent users from pausing updates:

:::image type="content" source="../media/5-mdm-prevent-users-pause-updates-expanded.png" lightbox="../media/5-mdm-prevent-users-pause-updates-inline.png" alt-text="Figure 18. Prevent users from pausing updates in Microsoft Intune.":::

### Microsoft recommendation

For the best experience, Microsoft recommends that you don't remove the user's ability to use Windows Update Settings features.

## Try it – Restrict access

In your pursuit of ensuring that all devices receive updates according to a set schedule, you might be tempted to prevent user from checking for Windows updates. However, in the click-through demonstration below, you'll see that this can negatively affect the user experience.

For the purpose of this demonstration, we'll configure the setting in Local Group Policy, to mirror the effect of what would result if you had set this configuration with your preferred management tooling.

Click on the image below to get started.

[![Interactive guide](../media/7-interactive-guide.png)](https://edxinteractivepage.blob.core.windows.net/edxpages/cloud-managed-devices-learning-module/Restrict-access-to-Windows-Update-features-through-Group-Policy/index.html)
