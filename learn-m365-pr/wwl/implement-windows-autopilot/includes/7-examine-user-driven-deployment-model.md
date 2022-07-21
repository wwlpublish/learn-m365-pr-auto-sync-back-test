Windows Autopilot user-driven mode enables new Windows 10 devices to be transformed from their initial state directly from the factory into a ready-to-use state without requiring IT personnel to ever touch the device. The process is designed to be easy so that anyone can complete it. By doing so, devices can be shipped or distributed to the end user directly with basic instructions:

1.  Unbox the device, plug it in, and turn it on.
2.  Choose a language, locale, and keyboard.
3.  Connect it to a wireless or wired network with internet access.
4.  Specify your e-mail address and password for your organization account.

After an order completes these steps, the rest of the process is automated. The device does the following steps:

1.  Join the organization.
2.  Enroll in Microsoft Intune or another MDM service.
3.  Get configured as defined by the organization.

Any other prompts during the Out-of-Box Experience (OOBE) can be suppressed. For more information on the options that are available, see [Configuring Autopilot Profiles](/windows/deployment/windows-autopilot/profiles?azure-portal=true).

> [!WARNING]
> If an organization uses Active Directory Federation Services (ADFS), there's a [known issue](/mem/autopilot/known-issues?azure-portal=true) that can enable the end user to sign in with a different account than the one that's assigned to that device.

Windows Autopilot user-driven mode supports Azure Active Directory and Hybrid Azure Active Directory joined devices. For more information about these two join options, see [What is a device identity?](/azure/active-directory/devices/overview?azure-portal=true)

The steps of the user-driven process are as follows:

1.  After the device is connected to a network, it downloads a Windows Autopilot profile. The profile defines the settings used for the device. For example, define the prompts suppressed during OOBE.
2.  Windows checks for critical OOBE updates. If updates are available, they're automatically installed. If necessary, the device restarts.
3.  The user is prompted for Azure AD credentials. This customized user experience shows the Azure AD tenant name, logo, and sign-in text.
4.  The device joins Azure AD or Active Directory, depending on the Windows Autopilot profile settings.
5.  The device enrolls to Intune or another configured MDM service. Depending on organizational needs, this enrollment occurs either:
     -  During the Azure AD-join process using MDM auto-enrollment.
     -  Before the Active Directory-join process.
6.  If configured, it displays the **Enrollment status** page.
7.  After the device configuration tasks complete, the user is signed into Windows using the credentials they previously provided. If the device restarts during the device enrollment status page process, the user must reenter their credentials. These details don't persist after restart.
8.  After sign-in, the enrollment status page displays for user-targeted configuration tasks.

If any issues are found during this process, see [Windows Autopilot troubleshooting](/mem/autopilot/troubleshooting).

**Additional reading**. For more information on the available join options, see the following sections:

 -  [Azure AD join](/mem/autopilot/user-driven#user-driven-mode-for-azure-ad-join) is available if devices don't need to join an on-premises Active Directory domain.
 -  [Hybrid Azure AD join](/mem/autopilot/user-driven#user-driven-mode-for-hybrid-azure-ad-join) is available for devices that need to join both Azure AD and your on-premises Active Directory domain.

### Available user-driven modes

The following options are available for user-driven deployment:

 -  **Azure Active Directory join.** This option is available if devices don't need to be joined to an on-premises Active Directory domain.
 -  **Hybrid Azure Active Directory join.** This option is available for devices that must be joined to both Azure Active Directory and an on-premises Active Directory domain.

The following sections provide a summary of user-driven mode for Azure AD join and Hybrid Azure AD join. For more detailed information on these two options, see [Windows Autopilot user-driven mode](/mem/autopilot/user-driven?azure-portal=true).

### User-driven mode for Azure Active Directory join

To complete a user-driven deployment using Windows Autopilot, the following preparation steps must be completed:

1.  Ensure the users who will be performing user-driven mode deployments can join devices to Azure Active Directory.
2.  Create an Autopilot profile for user-driven mode with the required settings. In Microsoft Intune, this mode is explicitly chosen when creating the profile. With Microsoft Store for Business and Partner Center, user-driven mode is the default and doesn't need to be selected.
3.  If using Intune, create a device group in Azure Active Directory and assign the Autopilot profile to that group.

For each device that will be deployed using user-driven deployment, these extra steps are needed:

4.  Ensure that the device has been added to Windows Autopilot. Adding a device to Windows Autopilot can be done in two ways:
     -  Automatically by an OEM or partner at the time the device is purchased.
     -  Manual harvesting as described in [Adding devices to Windows Autopilot](/mem/autopilot/add-devices?azure-portal=true).
5.  Ensure an Autopilot profile has been assigned to the device:
     -  If using Intune and Azure Active Directory dynamic device groups, the profile can be assigned to the device automatically.
     -  If using Intune and Azure Active Directory static device groups, manually add the device to the device group.
     -  If using other methods (such as Microsoft Store for Business or Partner Center), manually assign an Autopilot profile to the device.

> [!TIP]
> If the intended end-state of the device is co-management, an organization can configure device enrollment in Intune to enable co-management, which happens during the Autopilot process. This behavior directs the workload authority in an orchestrated manner between Configuration Manager and Intune. For more information, see [How to enroll with Autopilot](/mem/configmgr/comanage/autopilot-enrollment?azure-portal=true).

### User-driven mode for hybrid Azure Active Directory join

Windows Autopilot requires that devices be Azure Active Directory joined. If you have an on-premises Active Directory environment, you can join devices to your on-premises domain. To join the devices, you must configure Autopilot devices to be hybrid-joined to Azure Active Directory (Azure AD).

> [!TIP]
> As Microsoft talks with its customers that are using Microsoft Endpoint Manager to deploy, manage, and secure their client devices, it often receives questions regarding co-managing devices and hybrid Azure AD-joined devices. Many customers confuse these two issues. Co-management is a management option, while Azure AD is an identity option. For more information, see [Understanding hybrid Azure AD and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201?azure-portal=true). This blog post aims to clarify hybrid Azure AD join and co-management, how they work together, but aren't the same thing. Organizations can't deploy the Configuration Manager client while provisioning a new computer in Windows Autopilot user-driven mode for hybrid Azure AD join. This limitation is due to the identity change of the device during the Azure AD-join process. Deploy the Configuration Manager client after the Autopilot process. See [Client installation methods in Configuration Manager](/mem/configmgr/core/clients/deploy/plan/client-installation-methods?azure-portal=true) for alternative options for installing the client.

### Prerequisites

To implement user-driven, hybrid Azure AD-joined deployments using Windows Autopilot, organizations must complete the following prerequisites:

 -  A Windows Autopilot profile for user-driven mode must be created and **Hybrid Azure AD joined** must be specified as the selected option under **Join to Azure AD as** in the Autopilot profile.
 -  If using Intune, a device group in Azure Active Directory must exist with the Windows Autopilot profile assigned to that group.
 -  If using Intune, create and assign a Domain Join profile. A Domain Join configuration profile includes on-premises Active Directory domain information.
 -  The device must access the Internet.
 -  The Intune Connector for Active Directory must be installed.
    
    > [!NOTE]
    > The Intune Connector will complete an on-premises AD join. As a result, users don't need on-premises AD-join permission, assuming the Connector is [configured to perform this action](/intune/windows-autopilot-hybrid#increase-the-computer-account-limit-in-the-organizational-unit?azure-portal=true) on the user's behalf.
 -  If using Proxy, the WPAD Proxy settings option must be enabled and configured.

The hybrid Azure AD join process uses the system context to complete device Azure AD join. By doing so, it’s not affected by user-based Azure AD join permission settings. All users are enabled to join devices to Azure AD by default.

Besides the core requirements for a user-driven Hybrid Azure AD Join deployment mentioned above, the following extra requirements apply in an on-premises scenario:

 -  The device must be running Windows 10, version 1809 or later.
 -  The device must have access to an Active Directory domain controller.
     -  It must be connected to the organization's network.
     -  It must resolve the DNS records for the AD domain and the AD domain controller.
     -  It must communicate with the domain controller to authenticate the user.

### Step-by-step instructions

The step-by-step deployment instructions are too detailed for this training. However, for more information, see [Deploy hybrid Azure AD joined devices using Intune and Windows Autopilot](/intune/windows-autopilot-hybrid?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”