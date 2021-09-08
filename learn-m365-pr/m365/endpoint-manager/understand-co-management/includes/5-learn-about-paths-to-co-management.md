Once you decide to move to Configuration Manager or extend your existing Configuration Manager solution, there are two main paths to reach co-management of your Windows 10 devices:

- **[Enable co-management for existing Windows 10 Configuration Manager clients](#enable-co-management-for-existing-configuration-manager-clients)**
- **[Enable co-management for new internet-based Windows 10 devices](#enable-co-management-for-new-internet-based-windows-10-devices)**

Each path requires some combination of Azure Active Directory (Azure AD), Configuration Manager, Microsoft Intune, and Windows 10.

> [!NOTE]
> A Configuration Manager client is a Windows 10 device that has the Configuration Manager client software and client application installed on the devices. The Configuration Manager client application is designed for your help desk rather than for the end user.

## Enable co-management for existing Configuration Manager clients

With co-management, you can keep your well-established processes for using Configuration Manager to manage your organization's PCs. At the same time, you're investing in the cloud through the use of Intune for security and modern provisioning. When you enable this path to co-management, you do the following steps:

- Set up [hybrid Azure AD](#hybrid-azure-ad)
- Configure Configuration Manager client agents to register with Azure AD
- Configure Intune to auto-enroll devices
- Enable co-management in Configuration Manager

In this co-management path, you already have Windows 10 devices that are Configuration Manager clients. In addition, you have an on-premises Active Directory that you can connect to Azure Active Directory (Azure AD) in a hybrid Azure AD configuration. 

> [!IMPORTANT]
> If you can't deploy a hybrid Azure Active Directory (AD) that joins your on-premises AD with Azure AD, we recommend you [Enable co-management for new internet-based Windows 10 devices](#enable-co-management-for-new-internet-based-windows-10-devices).

To enable this co-management path, see [Tutorial: Enable co-management for existing Configuration Manager clients](/mem/configmgr/comanage/tutorial-co-manage-clients).

### Hybrid Azure AD 

Azure Active Directory (Azure AD) allows you to link your users, devices, and applications across both cloud and on-premises environments. Registering your devices to Azure AD enables you to improve productivity for your users and security for your resources. Having devices in Azure AD is the foundation for both co-management and [device-based conditional access](/azure/active-directory/conditional-access/require-managed-devices).

In the following video, senior program manager Sandeep Deo and product marketing manager Adam Harbour discuss and demo Azure AD for co-management:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Embedding-Co-management-With-Azure-Active-Directory/player]

You can join your existing domain-joined devices to Azure AD, by using hybrid Azure AD. Hybrid Azure AD supports the following capabilities:
  - Supports Windows 10, Windows 8.1, and Windows 7
  - Set up using AD FS claims or Azure AD Connect  
  - For Windows 10 the join happens in the machine context, so users don't have to take extra steps  
  - For more information, see [How to plan your hybrid Azure Active Directory join implementation](/azure/active-directory/devices/hybrid-azuread-join-plan)  

#### Benefits of Hybrid Azure AD

Joining your devices to Azure AD through either method accelerates your digital transformation. It enables more functionality provided by Microsoft 365. You'll have better experiences, and you'll have greater security for your data. Joining devices to Azure AD provides the following benefits to your organization:

| Benefit | Details |
|---|---|
| Single   sign-on to cloud resources | On   devices joined to Azure AD, you get an integrated experience accessing any   cloud or on-premises resources. Once you sign in to a Windows machine that's   joined to Azure AD, you get single sign-on to all applications without any   additional sign-in prompts. |
| Windows Hello for Business | Windows Hello for Business   brings strong password-less authentication to Windows 10. By joining your   devices to Azure AD, you can enable Windows Hello for Business across your   user base for both cloud and on-premises resources. Windows Hello for   Business eliminates the problem of remembering complex passwords or   inadvertently exposing them. Its sign-in process is both simple and secure. |
| Device-based   conditional access | Enable   conditional access based on the device state to better protect your   organization's data. Device-based conditional access requires a managed   device. This device must be a compliant device or a hybrid Azure AD-joined   device. For Azure AD-joined devices, you need Intune to mark the device as   compliant. But for hybrid Azure AD-joined devices, the device state itself is   used to evaluate conditional access. Co-management provides you the   additional advantage of evaluating compliance through Intune for hybrid Azure   AD-joined devices. This feature makes sure the device configuration is   intact. |
| Automatic device licensing | All Windows 10 devices joined to   Azure AD go through license checks. These checks enable you to automatically   upgrade them from Pro to Enterprise through the Microsoft cloud. When you   remove the relevant subscription from the user, the device automatically   downgrades its license. This feature provides a single pane of control for   managing Windows licenses, without any complicated processes or on-premises   systems. |
| Self-service   functionality | Self-service functionality includes self-service password   reset and BitLocker recovery key. Azure AD also provides you with direct   options to reset your password or access BitLocker recovery keys. You can use   Azure AD to reset your password directly from the Windows lock screen,   instead of from a web browser. These features reduce friction for users and   help cut helpdesk costs for your organization. |
| Enterprise state roaming | All devices joined to Azure AD can sync their settings to the   cloud. Any device to which a user signs in syncs all their settings for a   more productive experience. |

## Enable co-management for new internet-based Windows 10 devices

Just as mentioned above, co-management allows you to keep your well-established processes for using Configuration Manager to manage PCs in your organization. You gain cloud based security and modern provisioning by using Microsoft Intune. When you enable this path to co-management, you do the following steps:

- Request a public [Secure Sockets Layer (SSL)](#secure-sockets-layer) certificate for the [cloud management gateway (CMG)](#cloud-management-gateway)
- Enable Azure cloud services in Configuration Manager
- Deploy and configure a cloud management gateway
- Configure the management point (site system server) and clients to use the cloud management gateway
- Enable co-management in Configuration Manager
- Configure Intune to install the Configuration Manager client

This path to co-management involves having Windows 10 devices that must join Azure AD and be automatically enrolled into Intune. Also, you must install Configuration Manager client to reach a co-management state. When you do this you set up co-management of Windows 10 devices in an environment where you use both Azure Active Directory (AD) and an on-premises AD but don't have a hybrid Azure Active Directory (AD). The Configuration Manager environment includes a single primary site with all site system roles located on the same server, the site server. 

This path to co-management begins with the premise that your Windows 10 devices are already enrolled with Intune. If you are not using Microsoft Intune, you can quickly sign up for the [Intune free trial](/mem/intune/fundamentals/free-trial-sign-up). Or for a complete overview of Intune, see [Set up Microsoft Intune](/learn/modules/set-up-microsoft-intune?azure-portal=true).

> [!IMPORTANT]
> If you have a hybrid Azure AD that joins your on-premises AD with Azure AD, we recommend you enable co-management for existing Windows 10 Configuration Manager devices.

To enable this co-management path, see [Tutorial: Enable co-management for new internet-based devices](/mem/configmgr/comanage/tutorial-co-manage-new-devices).

### Secure Sockets Layer
Secure Sockets Layer (SSL), also known as Transport Layer Security (TLS), has become a standard for securing Internet connections and is used to prevent eavesdropping on the network. The SSL/TLS protocol allows a client and server to authenticate each other and negotiate encryption algorithms. For more information, see [SSL Certificates](/windows/win32/http/ssl-certificates).

### Cloud management gateway
The cloud management gateway (CMG) provides a simple way to manage Configuration Manager clients over the internet. You deploy CMG as a cloud service in Microsoft Azure. Then without more on-premises infrastructure, you can manage clients that roam on the internet or are in branch offices across the WAN. You also don't need to expose your on-premises infrastructure to the internet. For more information, see [Cloud management gateway overview](/mem/configmgr/core/clients/manage/cmg/overview).

### Azure cloud services
To enable Azure cloud services in Configuration Manager you use the Configure Azure Services wizard. This wizard provides a common configuration experience that replaces the individual workflows to set up the cloud services you use with Configuration Manager. This is done by using an **Azure web app** to provide the subscription and configuration details that you otherwise enter each time you set up a new Configuration Manager component or service with Azure.
