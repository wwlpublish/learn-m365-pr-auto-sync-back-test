## Register devices

Before deploying a device using Windows Autopilot, the device must be registered with the Windows Autopilot deployment service. Ideally, registration would be performed by the OEM, reseller, or distributor from which the devices were purchased, but it can also be done by the organization by collecting the hardware identity and uploading it manually.

- **OEM registration** - When you purchase devices directly from an OEM, that OEM can automatically register the devices with the Windows Autopilot deployment service.
- **Reseller, distributor, or partner registration** - When you purchase a device from your reseller, distributor, or partner, they can automatically register the devices with the Windows Autopilot deployment service.
- **Automatic registration** - If an existing device is already running Windows 10 version 1703 or later and enrolled in an MDM service such an Intune, that MDM service can ask the device for the hardware ID or hardware hash.
- **Manual registration** - To perform manual registration of a device, you must first capture its hardware ID or hardware hash. Once this process has completed, the resulting hardware ID can be uploaded to the Windows Autopilot service.
- **Device identification** - To define a device to the Windows Autopilot deployment service, a unique hardware ID for the device is captured and uploaded to the service through a harvesting process that collects the device from within a running Windows 10 version 1703 or later installation.

Once the hardware IDs have been captured from existing devices, they can be uploaded through a variety of means, such as:

- Microsoft Intune
- Partner Center
- Microsoft 365 Admin Center
- Microsoft Store for Business

## Configure device profiles

For each device that has been defined to the Windows Autopilot deployment service, a profile of settings needs to be applied that specifies the exact behavior of that device when it is deployed.

The following profile settings are available:

- **Skip Cortana, OneDrive, and OEM registration setup pages:** All devices registered with Autopilot will automatically skip these pages during the out-of-box experience (OOBE) process.
- **Automatically set up for work or school**: All devices registered with Autopilot will automatically be considered work or school devices, so this question will not be asked during the OOBE process.
- **Sign in experience with company branding:** Instead of presenting a generic Azure Active Directory sign-in page, all devices registered with Autopilot will automatically present a customized sign-in page with the organization's name, logon, and additional help text, as configured in Azure Active Directory.
- **Skip privacy settings**: This optional Autopilot profile setting enables organizations to not ask about privacy settings during the OOBE process. This setting is typically desirable so that the organization can configure these settings via Intune or other management tool.
- **Disable local admin account creation on the device**: Organizations can decide whether the user setting up the device should have administrator access once the process is complete.
- **Skip End User License Agreement (EULA)**: Starting in Windows 10 version 1709, organizations can decide to skip the EULA page presented during the OOBE process. This setting means that organizations accept the EULA terms on behalf of their users.
- **Disable Windows consumer features**: Starting in Windows 10 version 1803, organizations can disable Windows consumer features so that the device does not automatically install any additional Microsoft Store apps when the user first signs into the device.
- **BitLocker encryption:** BitLocker encryption settings can be applied before automatic encryption is started. This setting ensures that the default encryption algorithm is not applied automatically when it is not the desired setting.

## Enrollment status page

The **Enrollment Status Page (ESP)** displays the status of the complete device configuration process when an MDM-managed user signs into a device for the first time. The ESP will help users understand the progress of device provisioning and ensures the device has met the organizations desired state before the user can access the desktop for the first time.

The ESP will track the installation of applications, security policies, certificates, and network connections. Within Intune, an administrator can deploy ESP profiles to a licensed Intune user and configure specific settings within the ESP profile; a few of these settings are:

- Force the installation of specified applications.
- Allow users to collect troubleshooting logs.
- Specify what a user can do if device setup fails.

## Application Management

Autopilot supports multiple ways of delivering applications to users and devices via Intune. With these methods, you can fully recreate your baseline image in a more modern seamless way by installing these types of apps:

- **Microsoft Store Apps** - Apps that are configured in conjunction with the Microsoft Store for Business.
- **Line of Business Apps** - In-house or purchased applications that are installed with msi/msix/msixbundle or appx/appxbundle installation files.
- **Windows (Win32) Apps** - Typical Win32 apps that are deployed through Intune and packaged using the Win32 Content Prep Tool.
- **Microsoft 365 Apps** - All of the apps that are included in the Office suite including Word, Excel, PowerPoint, OneDrive, Access, Outlook, Publisher, Skype for Business, Teams, Project, and Visio.

## Learn more

- [Create and assign deployment profile](/intune/enrollment/enrollment-autopilot?azure-portal=true)
- [Extract device hardware information to CSV](/windows/deployment/windows-autopilot/add-devices#device-identification?azure-portal=true)
- [Import device hardware information to cloud service](/intune/enrollment/enrollment-autopilot?azure-portal=true)
- [Troubleshoot deployment](/windows/deployment/windows-autopilot/troubleshooting?azure-portal=true)
