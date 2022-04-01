After you have created a device configuration profile and enrolled your organization's devices into Intune, you can assign the profile to your user or device groups. When the device configuration profile is assigned, the users and devices receive the profile, and the settings you entered are applied.

> [!NOTE]
> This modules explains how to create device configuration profiles before enrolling devices into Microsoft Intune.

## Assign a device profile

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles**. All the profiles are listed.
3. Select the profile you want to assign > **Properties** > **Assignments** > **Edit**.

4. Select **Included groups** or **Excluded groups**, and then choose **Select groups to include**. When you select your groups, you're choosing an Azure AD group. To select multiple groups, hold down the **Ctrl** key, and select your groups.

5. Select **Review + Save**. This step doesn't assign your profile.
6. Select **Save**. When you save, your profile is assigned. Your groups will receive your profile settings when the devices check in with the Intune service.

For more information, see [Assign user and device profiles in Microsoft Intune](/mem/intune/configuration/device-profile-assign).