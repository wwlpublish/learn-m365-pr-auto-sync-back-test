After you've created a device configuration profile, you may later want to find, modify, or monitor it. 

Intune includes some features to help monitor and manage your device configuration profiles. For example, you can check the status of a profile, see which devices are assigned, and update the properties of a profile.

## View existing device configuration profiles

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles**.

All of your profiles are shown. You also see the platform, the type of profile, and if the profile is assigned.

## View device configuration profile details

After you create your device configuration profile, Intune provides graphical charts. These charts display the status of a profile, such as it being successfully assigned to devices, or if the profile shows a conflict.

1. Select an existing profile. For example, select a iOS/iPadOS profile.
2. Select the **Overview** tab. In this view, the **Profile assignment** includes the following statuses:

    - **Completed**: Policy is applied successfully.
    - **Error**: The policy failed to apply. The message typically displays with an error code that links to an explanation.
    - **Conflict**: Two settings are applied to the same device, and Intune can't sort out the conflict. An administrator should review.
    - **Pending**: The device hasn't checked in with Intune to receive the policy yet.
    - **Not applicable**: The device can't receive the policy. For example, the policy updates a setting specific to iOS 11.1, but the device is using iOS 10.

3. The top graphical chart shows the number of devices assigned to the device profile. For example, if the configuration device profile applies to iOS/iPadOS devices, the chart lists the count of the iOS/iPadOS devices.

    When monitoring a Windows profile, the count in the **Profile assignment** status is per device per user. So, if two users sign in to the same device, then that device is counted twice.

    It can also show the number of devices for other platforms that are assigned the same device profile. For example, it shows the count of the non-iOS/iPadOS devices.

4. Select the top graphical chart. **Device status** opens.

    The devices assigned to the profile are listed, and it shows the deployment status. Also note that it only lists the devices with the specific platform (for example, iOS/iPadOS).

    Close the **Device status** details.

5. Select the circle in the bottom graphical chart. **User status** opens.

    The users assigned to the profile are listed, and it shows the deployment status. Also note that it only lists the users with the specific platform (for example, iOS/iPadOS).

    Close the **User status** details.

6. Back in the **Profiles** list, select a specific profile.

    - **Properties**: Change the name, or update any existing settings.
    - **Assignments**: Include or exclude devices that the policy should apply. Choose **Selected Groups** to choose specific groups.
    - **Device status**: The devices assigned to the profile are listed, and it shows if the profile is successfully deployed. You can select a specific device to get even more details, including the installed apps.
    - **User status**: Lists the user names with devices affected by this profile, and if the profile successfully deployed. You can select a specific user to get even more details.
    - **Per-setting status**: Filters the output by showing the individual settings within the profile, and shows if the setting is successfully applied.

> [!TIP]
> For additional information about all Intune reporting, see [Intune reports](/mem/intune/fundamentals/reports).
