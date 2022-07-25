Windows Autopilot self-deploying mode enables an organization to deploy a device with little to no user interaction.

 -  For devices with an Ethernet connection, no user interaction is required.
 -  For devices connected through Wi-Fi, the user must only:
     -  Choose the language, locale, and keyboard.
     -  Make a network connection.

Self-deploying mode completes the following steps:

1.  Joins the device to Azure Active Directory.
2.  Enrolls the device in Intune (or another MDM service) using Azure AD for automatic MDM enrollment.
3.  Verifies that all policies, applications, certificates, and networking profiles are provisioned on the device.
4.  Uses the **Enrollment Status** page to prevent access until the device is fully provisioned.

> [!IMPORTANT]
> Self-deploying mode doesn't support Active Directory Join or Hybrid Azure AD Join. All devices will be joined to Azure Active Directory.

Self-deploying mode lets an organization deploy a Windows device as a kiosk, digital signage device, or a shared device. Autopilot now has a kiosk mode that supports Kiosk Browser, any UWP app, and specific versions of Microsoft Edge.

Organizations can use the Microsoft app titled [Kiosk Browser](https://www.microsoft.com/p/kiosk-browser/9ngb5s5xg2kp?rtc=1&amp;activetab=pivot:overviewtab?azure-portal=true) when setting up a kiosk device. This app is built on Microsoft Edge and can be used to create a tailored, MDM-managed browsing experience.

Organizations can completely automate device configuration by combining self-deploying mode with MDM policies. They can use the MDM policies to create a local account configured to automatically sign-in. For more information, see:

 -  [Simplifying kiosk management for IT with Windows 10](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/simplifying-kiosk-management-for-it-with-windows-10/ba-p/187691?azure-portal=true).
 -  [Set up a single app kiosk on Windows 10/11](/windows/configuration/setup-kiosk-digital-signage#set-up-a-kiosk-or-digital-sign-in-intune-or-other-mdm-service?azure-portal=true).

Organizations can optionally use a [device-only subscription](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/microsoft-intune-announces-device-only-subscription-for-shared/ba-p/280817?azure-portal=true) service that helps manage devices that aren't affiliated with specific users. The Intune device SKU is licensed per device per month.

> [!NOTE]
> Self-deploying mode doesn't currently associate a user with the device (since no user ID or password is specified as part of the process). As a result, some Azure AD and Intune capabilities (such as BitLocker recovery, installation of apps from the Company Portal, and Conditional Access) may not be available to a user who signs into the device. For more information, see [Windows Autopilot scenarios and capabilities](/mem/autopilot/windows-autopilot-scenarios?azure-portal=true) and [Setting the BitLocker encryption algorithm for Autopilot devices](/mem/autopilot/bitlocker?azure-portal=true).

### Requirements

> [!IMPORTANT]
> An organization can't automatically re-enroll a device through Autopilot after an initial deployment in self-deploying mode. Instead, it must delete the device record in the Microsoft Endpoint Manager admin center. From the admin center, the organization should select **Devices** &gt; **All devices**, then choose the devices it wants to delete, and then select **Delete**. For more information, see [Updates to the Windows Autopilot sign-in and deployment experience](https://techcommunity.microsoft.com/t5/intune-customer-success/updates-to-the-windows-autopilot-sign-in-and-deployment/ba-p/2848452?azure-portal=true).

Self-deploying mode uses a device's TPM 2.0 hardware to authenticate the device into an organization's Azure AD tenant. Therefore, devices without TPM 2.0 can't be used with this mode.

Devices must also support TPM device attestation. All new Windows devices should meet these requirements. The TPM attestation process also requires access to a set of HTTPS URLs that are unique for each TPM provider. For more information, see the entry for Autopilot self-Deploying mode and Autopilot pre-provisioning in [Networking requirements](/mem/autopilot/networking-requirements#tpm?azure-portal=true). For Windows Autopilot software requirements, see [Windows Autopilot software requirements](/mem/autopilot/software-requirements?azure-portal=true).

If an organization attempts a self-deploying mode deployment on a virtual machine or a device that doesn't support TPM 2.0, the process will fail with an 0x800705B4 timeout error (Hyper-V virtual TPMs aren't supported) when verifying the device. Also note that Windows 10, version 1903 or later is required to use self-deploying mode due to issues with TPM device attestation in Windows 10, version 1809. Since Windows 10 Enterprise 2019 LTSC is based on Windows 10 version 1809, self-deploying mode isn't supported on Windows 10 Enterprise 2019 LTSC.

See [Windows Autopilot known issues](/mem/autopilot/known-issues?azure-portal=true) and [Troubleshoot Autopilot device import and enrollment](/mem/autopilot/troubleshoot-device-enrollment?azure-portal=true) to review other known errors and solutions.

An organization-specific logo and organization name can be displayed during the Autopilot process. To do so, Azure AD Company Branding must be configured with the images and text an organization wants to display. See [Quickstart: Add company branding to your sign-in page in Azure AD](/azure/active-directory/fundamentals/customize-branding?azure-portal=true) for more details.

### How to deploy in Windows Autopilot self-deploying mode

To deploy in Windows Autopilot self-deploying mode, the following preparation steps must be completed:

1.  Create an Autopilot profile for self-deploying mode with the settings you want. In Microsoft Intune, this mode is explicitly chosen when creating the profile. It isn't possible to create a profile in the Microsoft Store for Business or Partner Center for self-deploying mode.
2.  If using Intune, create a device group in Azure Active Directory and assign the Autopilot profile to that group. Ensure that the profile has been assigned to the device before attempting to deploy that device.
3.  Boot the device, connecting it to Wi-Fi if necessary, and then wait for the provisioning process to complete.

### Validate self-deployment

When using Windows Autopilot to deploy in self-deploying mode, administrators can validate whether the deployment was successful by observing the following user experience:

 -  Once the device is connected to a network, the Autopilot profile will be downloaded.
 -  If using an Ethernet connection, and the Autopilot profile is configured to skip them, the following pages won't be displayed: language, locale, and keyboard layout. Otherwise, manual steps are required:
     -  If multiple languages are preinstalled in Windows, the user must select a language.
     -  The user must select a locale and a keyboard layout, and optionally a second keyboard layout.
 -  If using an Ethernet connection, no network prompt is expected. If no Ethernet connection is available and Wi-Fi is built in, the user needs to connect to a wireless network.
 -  Windows will check for critical OOBE updates, and if any are available they'll be automatically installed (rebooting if necessary).
 -  The device will join Azure Active Directory.
 -  After the device is joined Azure Active Directory, the device will enroll in Intune (or other configured MDM services).
 -  The **Enrollment status** page will be displayed.
 -  Depending on the device settings deployed, the device will either:
     -  Remain at the sign-in screen, where any member of the organization can sign on by specifying their Azure AD credentials.
     -  Automatically sign in as a local account, for devices configured as a kiosk or digital signage.

> [!CAUTION]
> Deploying Exchange ActiveSync (EAS) policies using self-deploying mode for kiosk deployments will cause auto-logon functionality to fail.

In case the observed results don't match these expectations, consult the [Windows Autopilot Troubleshooting](/mem/autopilot/troubleshooting) documentation.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”