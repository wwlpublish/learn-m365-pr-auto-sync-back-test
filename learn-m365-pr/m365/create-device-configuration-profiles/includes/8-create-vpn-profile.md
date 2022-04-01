Virtual private networks (VPNs) give users secure remote access to your organization's network. This type of security helps protect your organization's privacy by ensuring only authorized users are allowed access. Devices use a VPN connection profile (device configuration profile) to start a connection with the VPN server. VPN connection profiles in Microsoft Intune assign VPN settings to users and devices in your organization. You must assign these settings so users can easily and securely connect to your organizational network.

You can use device configuration profiles to configure VPN settings for the following devices:
- **Android device administrator**
- **Android Enterprise** > **Fully Managed, Dedicated, and Corporate-Owned Work Profile**
- **Android Enterprise** > **Personally-owned work profile**
- **iOS/iPadOS**
- **macOS**
- **Windows 10 and later**
- **Windows 8.1 and later**

Use the following steps to create a new Android Enterprise VPN configuration profile using Microsoft Tunnel.

> [!NOTE]
> Before completing the below steps, you must first follow the [prerequisites for Microsoft Tunnel in Intune](/mem/intune/protect/microsoft-tunnel-prerequisites).

## Step 1: Create a VPN device configuration profile

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
   The **Create a profile** pane is displayed.
3. Select **Android Enterprise** from the dropdown box under **Platform**.
4. Under the **Personally-Owned Work Profile** section, select **VPN**.
5. Click **Create**.

## Step 2: Add basic profile values
1. Next to **Name**, add "VPN settings - Android Enterprise - Personally-Owned Work Profile".
2. *[Optional]* Add a **Description** for your new profile.
3. Click **Next**.

## Step 3: Add configuration settings
1. Next to **Connection type**, select **Microsoft Tunnel**.
   For more information, see [Microsoft Tunnel overview](/mem/intune/protect/microsoft-tunnel-overview).
2. Under **Base VPN**, add a **Connection name**. For instance, include your organization's name as part of the connection name, such as "Contoso VPN".
   The connection name is a descriptive name for the VPN connection and will be displayed to end-users on their device.
3. Below **Microsoft Tunnel site**, click **Select a site** to display the **Microsoft Tunnel site** pane.
   The VPN client will connect to the public IP address or fully qualified domain name (FQDN) of the site.
4. Select an available site. 
   If you don't have an available site, create one by selecting **Tenant administration** > **Microsoft Tunnel Gateway**. For more information, see [Prerequisites for the Microsoft Tunnel in Intune](/mem/intune/protect/microsoft-tunnel-prerequisites).
5. Click **Next**.

## Step 4: Assign profile to group
For this device configuration profile, you can skip assigning this profile to any groups, users, or devices until you have created users and enrolled devices.
1. Click **Next**.

## Step 5: Set applicability Rules
For this device configuration profile, you can skip specifying how to apply this profile within an assigned group.
1. Click **Next**.

## Step 6: Review + create
1. Review the values and settings for this configuration profile.
2. Click **Create**.

You have now created a new device configuration profile named "VPN settings - Android Enterprise - Personally-Owned Work Profile". You can see the new configuration profile in the list by selecting **Devices** > **Configuration profiles**. For more information about Android Enterprise device configuration settings in Intune, see [Android Enterprise device settings to configure VPN in Intune](/mem/intune/configuration/vpn-settings-android-enterprise).

## VPN certificates

When you create the VPN profile, you choose a SCEP or PKCS certificate profile that you previously created in Intune. This profile is known as the identity certificate. It's used to authenticate against a trusted certificate profile (or *root certificate*) that you create to allow the user's device to connect. The trusted certificate is assigned to the computer that authenticates the VPN connection, typically, the VPN server.

If you use certificate-based authentication for your VPN profile, then deploy the VPN profile, certificate profile, and trusted root profile to the same groups. This assignment makes sure each device recognizes the legitimacy of your certificate authority.

For more information about how to create and use certificate profiles in Intune, see [How to configure certificates with Microsoft Intune](/mem/intune/protect/certificates-configure).