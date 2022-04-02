As mentioned previously, device configuration profiles are groups of settings that enable or disable different device capabilities or restrictions. You determine the specific capabilities or restrictions and apply the settings across the devices connected to your organization. You also determine the groups of users and devices that require these capabilities and settings. 

Device restrictions control security, hardware, data sharing, and more settings on the devices. For example, you can create a device restriction profile that manages access to the App store, restricts certain apps from being installed on the device, prevents device users from using the device camera, or requires an access password for the device.

Device restrictions are supported for devices running the following operating systems:
- Android device administrator
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 11
- Windows 10
- Windows 10 Team

> [!NOTE]
> This modules explains how to create device configuration profiles before enrolling devices into Microsoft Intune.

Use the following steps to create a new iOS/iPadOS device configuration profile to require a password.

## Step 1: Create a new iOS/iPadOS password profile
1. Sign in to [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.<br>
   The **Create a profile** pane is displayed.
3. Select **iOS/iPadOS** from the dropdown box under **Platform**.
4. Select **Device restrictions** from the dropdown box under **Profile type**.
5. Click **Create**.

## Step 2: Add basic profile values
1. Next to **Name**, add "Require device password".
2. *[Optional]* Add a **Description** for your new profile.
3. Click **Next**.

## Step 3: Add configuration settings
1. Click **Password** from the list to display password related settings.
2. Select **Yes** next to **Require password**.
3. Select **Yes** next to **Block simple passwords**.

    :::image type="content" source="../media/create-device-configuration-profiles-01.png" alt-text="Device configuration profile password settings":::

4. Click **Next**.

## Step 4: Assign profile to group
For this device configuration profile, you can skip assigning this profile to any groups, users, or devices until you have created users and enrolled devices.
1. Click **Next**.

## Step 5: Review + create
1. Review the values and settings for this configuration profile.
2. Click **Create**.

You have now created a new device configuration profile named "Require device password". You can see the new configuration profile in the list by selecting **Devices** > **Configuration profiles**. For related information, see [iOS and iPadOS device settings to allow or restrict features using Intune](/mem/intune/configuration/device-restrictions-ios).