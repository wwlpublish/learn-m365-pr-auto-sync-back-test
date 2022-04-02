After you've created a device configuration profile, you may later want to find, modify, or monitor it. 

Intune includes some features to help monitor and manage your device configuration profiles. For example, you can check the status of a profile, see which devices are assigned, and update the properties of a profile.

## View existing device configuration profiles

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles**.

All of your profiles are shown. You also see the related platform, the type of profile, and the last time the profile was modified.

## View device configuration profile details

After you create your device configuration profile, Intune provides status details about how the configuration profile.

1. Select an existing configuration profile.<br>
   In this view, you can view a profile report, the profile assignment status, and the per setting profile status. In addition, you can modify the properties settings of the profile.

2. Select **View Report**.<br>
   This report shows all the devices and users that have checked in to receive the policy. Devices may show up multiple times based on the user that had checked in. This report does not include devices in a pending policy assignment state. To see the devices in a pending policy assignment state, select the “Device assignment status” report
3. Click the name of the device configuration profile at the top to return to the profile details.

4. Select **Device assignment status** > **Generate report**.<p>
   The generated report provides the following details:
    - **Success**: Policy is applied successfully.
    - **Conflict**: Two settings are applied to the same device, and Intune can't sort out the conflict. An administrator should review.
    - **Error**: The policy failed to apply. The message typically displays with an error code that links to an explanation.
    - **Pending**: The device hasn't checked in with Intune to receive the policy yet.
    - **Not applicable**: The device can't receive the policy. For example, the policy updates a setting specific to iOS 11.1, but the device is using iOS 10.

5. Click the name of the device configuration profile at the top again to return to the profile details.

6. You can also edit specific settings within the profile.<p>

   The following profile sections allow you to modify the profile:
    - **Properties**: Change the name, or update any existing settings.
    - **Assignments**: Include or exclude devices that the policy should apply. Choose **Selected Groups** to choose specific groups.
    - **Scope tags**: Configure or update the admin access and visibility of the device configuration profile.
    - **Configuration settings**: Update the configuration settings for the device configuration profile.
    - **Applicability Rules**: Specify how to apply this profile within an assigned group. Intune will only apply the profile to devices that meet the combined criteria of these rules.

For additional information about all Intune reporting, see [Intune reports](/mem/intune/fundamentals/reports).
