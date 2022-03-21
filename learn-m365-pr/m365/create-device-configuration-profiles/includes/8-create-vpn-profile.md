Virtual private networks (VPNs) give users secure remote access to your organization network. Devices use a VPN connection profile to start a connection with the VPN server. VPN profiles in Microsoft Intune assign VPN settings to users and devices in your organization. Use these settings so users can easily and securely connect to your organizational network.

## Create a VPN device configuration profile

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
3. Enter the following properties:

    - **Platform**: Choose the platform of your devices. Your options:
      - **Android device administrator**
      - **Android Enterprise** > **Fully Managed, Dedicated, and Corporate-Owned Work Profile**
      - **Android Enterprise** > **Personally-owned work profile**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows 10 and later**
      - **Windows 8.1 and later**
    - **Profile**: Select **VPN**. Or, select **Templates** > **VPN**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **VPN profile for entire company**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. 

8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](/mem/intune/configuration/scope-tags).

    Select **Next**.

10. In **Assignments**, select the user or groups that will receive your profile. For more information on assigning profiles, see [Assign user and device profiles](/mem/intune/configuration/device-profile-assign).

    Select **Next**.

11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

## Secure your VPN profiles

VPN profiles can use many different connection types and protocols from different manufacturers. These connections are typically secured through the following methods.

### Certificates

When you create the VPN profile, you choose a SCEP or PKCS certificate profile that you previously created in Intune. This profile is known as the identity certificate. It's used to authenticate against a trusted certificate profile (or *root certificate*) that you create to allow the user's device to connect. The trusted certificate is assigned to the computer that authenticates the VPN connection, typically, the VPN server.

If you use certificate-based authentication for your VPN profile, then deploy the VPN profile, certificate profile, and trusted root profile to the same groups. This assignment makes sure each device recognizes the legitimacy of your certificate authority.

For more information about how to create and use certificate profiles in Intune, see [How to configure certificates with Microsoft Intune](/mem/intune/protect/certificates-configure).

> [!NOTE]
> Certificates added using the **PKCS imported certificate** profile aren't supported for VPN authentication. Certificates added using the **PKCS certificates** profile are supported for VPN authentication.

### User name and password

The user authenticates to the VPN server by providing a user name and password, or [derived credentials](/mem/intune/protect/derived-credentials).