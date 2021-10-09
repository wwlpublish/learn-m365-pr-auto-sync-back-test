Once you decide to move to Configuration Manager or extend your existing Configuration Manager solution, there are two main paths to reach co-management of your Windows 10 or later devices:

- **[Enable co-management for existing Windows 10 or later Configuration Manager clients](#enable-co-management-for-existing-window-10-or-later-configuration-manager-clients)**
- **[Enable co-management for new internet-based Windows 10 or later devices](#enable-co-management-for-new-internet-based-windows-10-or-later-devices)**

Each path requires some combination of Azure Active Directory (Azure AD), Configuration Manager, Microsoft Intune, and Windows 10 or later. The Windows 10 or later is the operating system of the users device, which is the Configuration Manager client. These paths to co-management do not apply to Windows Server or macOS.

> [!NOTE]
> A Configuration Manager client is a Windows 10 or later device that has the Configuration Manager client application installed on it.  

Based on the following paths to enable co-management, choose which path is right for you and your organization.

## Enable co-management for existing Windows 10 or later Configuration Manager clients

With co-management, you can keep your well-established processes for using Configuration Manager to manage your organization's PCs. At the same time, you're investing in the cloud through the use of Intune for security and modern provisioning. When you enable this path to co-management, you do the following steps:

- Set up [hybrid Azure AD](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
- Configure Configuration Manager client agents to register with Azure AD
- Configure Intune to auto-enroll devices
- Enable co-management in Configuration Manager

In this co-management path, you already have Windows 10 or later devices that are Configuration Manager clients. In addition, you have an on-premises Active Directory that you can connect to Azure Active Directory (Azure AD) in a hybrid Azure AD configuration.

> [!IMPORTANT]
> If you can't deploy a hybrid Azure Active Directory (AD) that joins your on-premises AD with Azure AD, we recommend you [Enable co-management for new internet-based Windows 10 or later devices](#enable-co-management-for-new-internet-based-windows-10-or-later-devices).

To enable this co-management path, see [Tutorial: Enable co-management for existing Configuration Manager clients](/mem/configmgr/comanage/tutorial-co-manage-clients).

## Enable co-management for new internet-based Windows 10 or later devices

Just as mentioned above, co-management allows you to keep your well-established processes for using Configuration Manager to manage PCs in your organization. You gain cloud-based security and modern provisioning by using Microsoft Intune. When you enable this path to support co-management, you do the following steps:

- Deploy and configure a [cloud management gateway (CMG)](/mem/configmgr/core/clients/manage/cmg/overview)
    - Request a public [Secure Sockets Layer (SSL)](/windows/win32/http/ssl-certificates) certificate for the CMG
    - Enable [Azure cloud services](/mem/configmgr/core/servers/deploy/configure/azure-services-wizard) in Configuration Manager
    - Configure the management point (site system server) and clients to use the cloud management gateway
- Enable co-management in Configuration Manager
- Configure Intune to install the [Configuration Manager client](/mem/configmgr/core/understand/fundamentals-of-client-management-tasks#configuration-manager-client-application)

This path to co-management involves having Windows 10 or later devices that must join Azure AD and be automatically enrolled into Intune. Also, you must install the Configuration Manager client to reach a co-management state. When you do this, you set up co-management of Windows 10/11 devices in an environment where you use both Azure Active Directory (AD) and an on-premises AD but don't have a hybrid Azure Active Directory (AD). The Configuration Manager environment includes a single primary site with all site system roles located on the same server, the site server. 

This path to co-management begins with the premise that your Windows 10 or later devices are already enrolled with Intune. If you are not using Microsoft Intune, you can quickly sign up for the [Intune free trial](/mem/intune/fundamentals/free-trial-sign-up). Or for a complete overview of Intune, see [Set up Microsoft Intune](/learn/modules/set-up-microsoft-intune?azure-portal=true).

> [!IMPORTANT]
> If you have a hybrid Azure AD that joins your on-premises AD with Azure AD, we recommend you [enable co-management for existing Windows 10 or later Configuration Manager clients](#enable-co-management-for-existing-window-10-or-later-configuration-manager-clients).

To enable this co-management path, see [Tutorial: Enable co-management for new internet-based devices](/mem/configmgr/comanage/tutorial-co-manage-new-devices).
