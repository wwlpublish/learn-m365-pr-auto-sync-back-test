Windows Autopilot enables organizations to easily provision new devices by using the preinstalled OEM image and drivers. This process is known as the pre-provisioned (formerly white glove) deployment model. It can be completed by the end user to help make their device business-ready.

:::image type="content" source="../media/autopilot-preprovision-oem-end-user-6306c478.png" alt-text="graphic showing the steps that are completed by the OEM and the end user":::


Windows Autopilot can also provide a *pre-provisioning* service that helps partners or IT staff pre-provision a fully configured and business-ready Windows 10 PC. From the end user’s perspective, the Windows Autopilot user-driven experience is unchanged, but getting their device to a fully provisioned state is faster.

In a **Windows Autopilot for pre-provisioned deployment**, the provisioning process is split. The time-consuming portions are performed by IT, partners, or OEMs. The end user simply completes a few necessary settings and policies, and then they can begin using their device.

:::image type="content" source="../media/autopilot-preprovision-oem-partner-end-user-0f9b0897.png" alt-text="graphic showing the steps completed by the OEM, then the OEM, partner, or IT person, and then the end user":::


Pre-provisioned deployments use Microsoft Intune in Windows 10, version 1903 and later. Such deployments build on existing Windows Autopilot [user-driven scenarios](/mem/autopilot/user-driven?azure-portal=true). They support user-driven mode scenarios for both Azure Active Directory joined and Hybrid Azure Active Directory joined devices.

### Prerequisites

Besides the Windows Autopilot requirements, Windows Autopilot for pre-provisioned deployment has the following prerequisites:

 -  Windows 10, version 1903 or later is required.
 -  An Intune subscription.
 -  Physical devices that support TPM 2.0 and device attestation. Virtual machines aren't supported. The pre-provisioning process uses Windows Autopilot self-deploying capabilities, so TPM 2.0 is required. The TPM attestation process also requires access to a set of HTTPS URLs that are unique for each TPM provider.
 -  Physical devices with Ethernet connectivity are required to complete pre-provisioning. Wi-fi connectivity isn't supported because of the requirement to choose a language, locale, and keyboard to make that Wi-fi connection. Enforcing this requirement in a pre-provisioning process could prevent the user from choosing their own language, locale, and keyboard when they receive the device.

> [!IMPORTANT]
> Because the OEM or vendor completes the pre-provisioning process, it doesn’t require access to an end user's on-premises domain infrastructure. This requirement is unlike a typical hybrid Azure AD-joined scenario because rebooting the device is postponed. The device is resealed before the time when connectivity to a domain controller is expected. The domain network is then contacted when the device is unboxed on-premises by the end user.

### Preparation

Devices slated for pre-provisioning are registered for Autopilot through the normal registration process.

To be ready to try out Windows Autopilot for pre-provisioned deployment, make sure that you can first successfully use existing Windows Autopilot user-driven scenarios:

 -  **User-driven Azure AD join.** Devices can be deployed using Windows Autopilot and joined to an Azure Active Directory tenant.
 -  **User-driven with Hybrid Azure AD join.** Devices can be deployed using Windows Autopilot and joined to an on-premises Active Directory domain, then registered with Azure Active Directory to enable the Hybrid Azure AD join features.

If these scenarios can't be completed, Windows Autopilot for pre-provisioned deployment will fail since it builds on top of these scenarios.

Before starting the pre-provisioning process in the provisioning service facility, you must configure another Autopilot profile setting by using your Intune account:

:::image type="content" source="../media/allow-pre-provisoned-oobe-5ce71570.png" alt-text="screenshot of the Out of box experience page (OOBE)":::


The Windows Autopilot for pre-provisioned deployment pre-provisioning process applies all device-targeted policies from Intune. That includes certificates, security templates, settings, apps, and more – anything targeting the device. Additionally, any Win32 or LOB apps will be installed if they meet these two conditions:

 -  Configured to install in the device context.
 -  Targeted to the user pre-assigned to the Autopilot device.

Make sure not to target both win32 and LOB apps to the same device.

> [!NOTE]
> Select the language mode as **User specified** in Autopilot profiles to ensure easy access into pre-provisioning mode. The pre-provisioning technician phase will install all device-targeted apps and any user-targeted, device-context apps that are targeted to the assigned user. If there's no assigned user, then it will only install the device-targeted apps. Other user-targeted policies won't apply until the user signs into the device. To verify these behaviors, be sure to create appropriate apps and policies targeted to devices and users.

### Scenarios

Windows Autopilot for pre-provisioned deployment supports two distinct scenarios:

 -  **User-driven deployments with Azure AD Join.** The device will be joined to an Azure AD tenant.
 -  **User-driven deployments with Hybrid Azure AD Join.** The device will be joined to an on-premises Active Directory domain, and separately registered with Azure AD.

Each of these scenarios consists of two parts - a technician flow and a user flow. At a high level, these parts are the same for Azure AD Join and Hybrid Azure AD join. The differences are primarily seen by the end user in the authentication steps.

#### Technician flow

After the customer or IT Admin has targeted all the apps and settings they want for their devices through Intune, the pre-provision technician can begin the pre-provisioned process. The technician could be a member of the IT staff, a services partner, or an OEM – each organization can decide who should complete these activities. Whatever the scenario, the process to be performed by the technician is the same:

1.  Boot the device (running Windows 10 Pro, Enterprise, or Education SKUs, version 1903 or later).
2.  From the first OOBE screen (which could be a language selection or locale selection screen), don't select **Next**. Instead, press the Windows key five times to view another options dialog. From that screen, choose the **Windows Autopilot provisioning** option and then select **Continue**.
3.  On the **Windows Autopilot Configuration** screen, the following information will be displayed about the device:
     -  The Autopilot profile assigned to the device.
     -  The organization name for the device.
     -  The user assigned to the device (if there's a user).
     -  A QR code containing a unique identifier for the device. You can use this code to look up the device in Intune. You may need to look up the device in Intune to make configuration changes, like assigning a user or adding the device to groups needed for app or policy targeting.
4.  Validate the information displayed. If any changes are needed, make the changes, and then select **Refresh** to redownload the updated Autopilot profile details.
5.  Select **Provision** to begin the provisioning process.
6.  If the pre-provisioning process completes successfully, a green status screen appears with information about the device, including the same details presented previously.
7.  Select **Reseal** to shut down the device. At that point, the device can be shipped to the end user.

If the pre-provisioning process fails:

 -  A red status screen appears with information about the device, including the same details presented previously.
 -  Diagnostic logs can be gathered from the device. It can then be reset to start the process over again.

#### User flow

If the pre-provisioning process completed successfully and the device was resealed, it can be delivered to the end user to complete the normal Windows Autopilot user-driven process. The user must then complete a standard set of steps:

1.  Power on the device.
2.  Select the appropriate language, locale, and keyboard layout.
3.  Connect to a network (if using Wi-Fi). If using Hybrid Azure AD Join, there must be connectivity to a domain controller; if using Azure AD Join, internet connectivity is required.
4.  On the branded sign-on screen, enter the user’s Azure Active Directory credentials.
5.  If using Hybrid Azure AD Join, the device will reboot. After the reboot, enter the user’s Active Directory credentials.
6.  Other policies and apps will be delivered to the device, as tracked by the Enrollment Status Page (ESP). Once complete, the user can access the desktop.
