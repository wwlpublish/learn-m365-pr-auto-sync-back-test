Windows Autopilot Self-deploying mode doesn't associate a user with a device. Instead, it's designed to deploy Windows 10 as a kiosk, digital signage device, or a shared device, all with little to no user interaction.

 -  For devices with an Ethernet connection, no user interaction is required.
 -  For devices connected through Wi-fi, no interaction is required after making the Wi-fi connection (choosing the language, locale, and keyboard, then making a network connection).<br>

Self-deploying mode consists of the following high-level steps:<br>

1.  Joins the device to Azure Active Directory.
2.  Enrolls the device in Intune (or another MDM service) using Azure AD for automatic MDM enrollment.
3.  Ensures that all policies, applications, certificates, and networking profiles are provisioned on the device.
4.  Uses the Enrollment Status Page to prevent access until the device is fully provisioned.

> [!NOTE]
> Self-deploying mode doesn't support Active Directory Join or Hybrid Azure AD Join. All devices will be joined to Azure Active Directory.

You can completely automate device configuration by combining self-deploying mode with MDM policies. The MDM policies can create a local account configured to automatically sign in.<br>

Optionally, you can use a [device-only subscription](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/microsoft-intune-announces-device-only-subscription-for-shared/ba-p/280817?azure-portal=true) service that helps manage devices that aren't affiliated with specific users. The Intune device SKU is licensed per device per month.

> [!IMPORTANT]
> Self-deploying mode doesn't associate a user with the device (since no user ID or password is specified as part of the process). As a result, some Azure AD and Intune capabilities (such as BitLocker recovery, installation of apps from the Company Portal, or Conditional Access) may not be available to a user that signs into the device. For more information, see [Windows Autopilot scenarios and capabilities](/mem/autopilot/windows-autopilot-scenarios) and [Setting the BitLocker encryption algorithm for Autopilot devices](/mem/autopilot/bitlocker).

### Requirements

Because self-deploying mode uses a device’s Trusted Platform Module (TPM) 2.0 hardware to authenticate the device into an organization’s Azure AD tenant, devices without TPM 2.0 can't be used with this mode.

The devices must also support TPM device attestation. With TPM device attestation, an administrator can define the set of devices that users can use to access corporate resources (for example, VPN or wireless access point) and have strong guarantees that no other devices can be used to access these resources. This access control model is strong because it's tied to a hardware-bound user identity, which is stronger than a software-based credential.

> [!NOTE]
> All newly manufactured Windows devices should meet these requirements.

> [!IMPORTANT]
> If you attempt a self-deploying mode deployment on a device that doesn't support TPM 2.0 or on a virtual machine, the process will fail when verifying the device. An 0x800705B4 timeout error (Hyper-V virtual TPMs aren't supported) will be displayed.<br><br>Window 10, version 1903 or later is required to use self-deploying mode because of issues with TPM device attestation in Windows 10, version 1809. Since Windows 10 Enterprise 2019 LTSC is based on Windows 10 version 1809, self-deploying mode isn't supported on Windows 10 Enterprise 2019 LTSC.

When setting up a kiosk, you can use Microsoft's Kiosk Browser. This browser is actually an app built on Microsoft Edge. It can be used to create a tailored, MDM-managed browsing experience.

You can display an organization-specific logo and organization name during the Autopilot process. To do so, Azure AD Company Branding must be configured with the images and text you want displayed.

**Additional reading.** For more information, see [Quickstart: Add company branding to your sign-in page in Azure AD](/azure/active-directory/fundamentals/customize-branding).

### Step-by-step

To complete a self-deploying mode deployment using Windows Autopilot, the following preparation steps must be completed:

1.  Create an Autopilot profile for self-deploying mode with the required settings. In Microsoft Intune, this mode is explicitly chosen when creating the profile.

    > [!NOTE]
    > You can't create a profile in the Microsoft Store for Business or Partner Center for self-deploying mode.

2.  If using Intune, create a device group in Azure Active Directory and assign the Autopilot profile to that group. Ensure the profile has been assigned to the device before attempting to deploy that device.
3.  Boot the device, connecting it to Wi-fi if necessary, then wait for the provisioning process to complete.

### Validation

When completing a self-deploying mode deployment using Windows Autopilot, the following end-user experience should be observed:

 -  Once connected to a network, the Autopilot profile will be downloaded.
 -  If the Autopilot profile has been configured to automatically configure the language, locale, and keyboard layout, these OOBE screens should be skipped as long as Ethernet connectivity is available. Otherwise, manual steps are required:
    
     -  If multiple languages are preinstalled in Windows 10, the user must select a language.
     -  The user must select a locale and a keyboard layout, and optionally a second keyboard layout.
 -  If connected using Ethernet, no network prompt is expected. If no Ethernet connection is available and Wi-fi is built in, the user must connect to a wireless network.
 -  Windows 10 will check for critical OOBE updates, and if any are available, they'll be automatically installed (rebooting if necessary).
 -  The device will join Azure Active Directory, after which the device will enroll in Intune (or other configured MDM services).
 -  The enrollment status page will be displayed.
 -  Depending on the device settings deployed, the device will either:
    
     -  Remain at the sign-in screen, where any member of the organization can sign in by specifying their Azure AD credentials.
     -  Automatically sign in as a local account for devices configured as a kiosk or digital signage.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”