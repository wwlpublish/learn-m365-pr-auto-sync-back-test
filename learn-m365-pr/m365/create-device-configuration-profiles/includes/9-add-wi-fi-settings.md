Wi-Fi is a wireless network that's used by many mobile devices to get network access. Microsoft Intune includes built-in Wi-Fi settings that can be deployed to users and devices in your organization. Once assigned, your users get access to your organization's Wi-Fi network without configuring it themselves.

You can use device configuration profiles to configure Wi-Fi settings for the following device platforms:
- **Android device administrator**
- **Android Enterprise**
- **iOS/iPadOS**
- **macOS**
- **Windows 10 and later**
- **Windows 8.1 and later**

Use the following steps to create a new iOS/iPadOS configuration profile.

## Step 1: Create a Wi-Fi device configuration profile for iOS/iPadOS devices
1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
   The **Create a profile** pane is displayed.
3. Select **iOS/iPadOS** from the dropdown box under **Platform**.
4. Select **Wi-Fi** from the dropdown box under **Profile type**.
5. Click **Create**.

## Step 2: Add basic profile values
1. Next to **Name**, add "Wi-Fi - iOS/iPadOS".
2. *[Optional]* Add a **Description** for your new profile.
3. Click **Next**.

## Step 3: Add configuration settings
1. Next to **Wif-Fi type**, select **Basic**.
2. Next to **Network name**, enter "iOS/iPadOS Wi-Fi settings". 
3. Next to **SSID**, enter the name of your organization.
   The Service Set Identifier (SSID) is the name of the Wi-Fi connection.
4. Select **Enable** next to **Connect automatically**.
5. Ensure **Disable** is selected next to **Hidden network**.
6. Select **WPA/WPA2-Personal** next to **Security type**.
   This setting is the security protocol to use for Wi-Fi authentication.
7. Enter a password as a **pre-shared key**.
   When your organization's network is set up or configured, a password or network key is also configured. Enter this password or network key for the pre-shared key (PSK) value.
8. Select **Manual** next to **Proxy settings**.
   Ensure that this proxy configuration is used by your organization.
9. Enter a **Proxy server address**.
   This is the IP address of the proxy server.
10. Enter a **Port number**.
If your proxy server uses a particular port, enter the port number.
11. Ensure that **Disable MAC address randomization** is set to **Not configured**.
12. Select **Next**.

## Step 4: Assign profile to group
For this device configuration profile, you can skip assigning this profile to any groups, users, or devices until you have created users and enrolled devices.
1. Click **Next**.

## Step 5: Review + create
1. Review the values and settings for this configuration profile.
2. Click **Create**.

> [!TIP]
> If you use certificate based authentication for your Wi-Fi profile, deploy the Wi-Fi profile, certificate profile, and trusted root profile to the same groups to ensure that each device can recognize the legitimacy of your certificate authority.  For more information, see [How to configure certificates with Microsoft Intune](/mem/intune/protect/certificates-configure).

You have now created a new device configuration profile named "Wi-Fi - iOS/iPadOS". You can see the new configuration profile in the list by selecting **Devices** > **Configuration profiles**. For more information about iOS/iPadOS Wi-Fi configuration settings in Intune, see [Add Wi-Fi settings for iOS and iPadOS devices in Microsoft Intune](/mem/intune//configuration/wi-fi-settings-ios).