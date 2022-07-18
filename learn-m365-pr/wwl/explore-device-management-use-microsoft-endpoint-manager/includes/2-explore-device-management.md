A key task of any administrator is to protect and secure an organization’s resources and the data on its devices. This task is known as device management. Users receive and send email from personal accounts, browse websites from anywhere outside the office (such as home, restaurants, and so on) and install apps and games. These users are also employees and students. On their devices, they want to access work and school resources, such as email and OneNote, and access them quickly. An administrator's goal is to protect these resources, and provide easy access for users across their many devices, all at the same time.

Device management enables organizations to protect and secure their resources and data, and from different devices.

 -  An organization can use a device management provider to ensure that only authorized users and devices get access to proprietary company information.
 -  Device users can feel at ease accessing work data from their phones because they know their devices meet their organization's security requirements.

Most organizations ask themselves - What should we use to protect our resources? Microsoft's answer is Microsoft Endpoint Manager.

### Device management solutions in Microsoft Endpoint Manager

Microsoft Endpoint Manager helps deliver the modern workplace and modern management to keep an organization's data secure, both in the cloud and on-premises. Endpoint Manager includes the services and tools an organization can use to manage and monitor:

 -  mobile devices
 -  desktop computers
 -  virtual machines
 -  embedded devices
 -  servers

Endpoint Manager combines services an organization may know and already be using. For example, Microsoft Intune, Configuration Manager, Desktop Analytics, co-management, and Windows Autopilot. These services are part of the Microsoft 365 stack to help secure access, protect data, respond to risk, and manage risk.

Endpoint Manager includes the following device management services:

 -  **Microsoft Intune**. Intune is a 100% cloud-based mobile device management (MDM) and mobile application management (MAM) provider for an organization's apps and devices. It enables organizations to control features and settings on Android, Android Enterprise, iOS/iPadOS, macOS, and Windows 10 devices. It integrates with other services, including Azure Active Directory (AD), mobile threat defenders, ADMX templates, Win32 and custom LOB apps, and more.
    
    If an organization has an on-premises infrastructure, such as Exchange or an Active Directory, the following Intune connectors are also available:
    
    
     -  **Intune Connector for Active Directory**. This connector adds entries to an organization's on-premises Active Directory domain for computers that enroll using Windows Autopilot. For more information, see [Deploy hybrid Azure AD-joined devices](/mem/autopilot/windows-autopilot-hybrid?azure-portal=true).
     -  **Intune certificate connector**. This connector processes certificate requests from devices that use certificates for authentication and S/MIME email encryption. For more information, see [Use certificates for authentication](/mem/intune/protect/certificates-configure?azure-portal=true).
    
    As part of Endpoint Manager, Intune is used to create and check for device compliance. It's also used to deploy apps, features, and settings to an organization's devices using the cloud.
 -  **Configuration Manager**. Configuration Manager is an on-premises management solution that manages desktops, servers, and laptops that are internet-based or on an organization's network. An organization can cloud-enable Configuration Manager to integrate it with Intune, Azure Active Directory (AD), Microsoft Defender for Endpoint, and other cloud services. Configuration Manager can deploy apps, software updates, and operating systems. It can also monitor compliance, query and act on clients in real time, and much more.
    
    As part of Endpoint Manager, Configuration Manager can continue to be used by an organization as it always has been. However, if the organization is ready to move some tasks to the cloud, then it should consider co-management.
 -  **Co-management**. Co-management combines an organization's existing on-premises Configuration Manager investment with the cloud. It does so by using Intune and other Microsoft 365 cloud services. In a co-management scenario, an organization must choose whether Configuration Manager or Intune is the management authority.
    
    As part of Endpoint Manager, co-management uses cloud features, including conditional access. Some tasks are kept on on-premises, while other tasks are run in the cloud with Intune.
 -  **Desktop Analytics**. Desktop Analytics is a cloud-based service that integrates with Configuration Manager. It provides insight and intelligence for an organization to make more informed decisions about the update readiness of its Windows clients. The service combines data from an organization with data aggregated from millions of devices connected to the Microsoft cloud. It provides information on security updates, apps, and devices in an organization. It also identifies compatibility issues with apps and drivers.
    
    As part of Endpoint Manager, the cloud-powered insights of Desktop Analytics can be used to keep Windows devices current.

Endpoint Manager is integrated with the following features:

 -  **Windows Autopilot**. Windows Autopilot sets up and pre-configures new devices. By doing so, it prepares them for use. It's designed to simplify the lifecycle of Windows devices, for both IT and end users, from initial deployment through end of life. As part of Endpoint Manager, Autopilot can be used to preconfigure devices, and automatically enroll devices in Intune. It can also be integrated with Configuration Manager and co-management for more complex device configurations (in preview).
 -  **Azure Active Directory (AD)**. Azure AD is used by Endpoint Manager for identity of devices, users, groups, and multi-factor authentication (MFA). Azure AD Premium, which may be an extra cost, has other features to help protect devices, apps, and data, including dynamic groups, auto-enrollment, and conditional access.
 -  **Endpoint Manager admin center**. The Enterprise Manager admin center is a one-stop web site to create policies and manage devices. It plugs-in other key device management services, including groups, security, conditional access, and reporting. This admin center also shows devices managed by Configuration Manager and Intune (in preview).

### Which device management solution in Endpoint Manager is right for you?

There are a few ways to determine what's right for an organization. An organization's next steps depend on what it's trying to achieve.

For example, if an organization:

 -  Constantly implements new devices, then it should start with Windows Autopilot.
 -  Adds rules and control settings for its users, apps, and devices, then it should start with Intune.
 -  Currently uses Configuration Manager to deploy apps, and it wants to use conditional access based on security requirements, then it should start with co-management.
 -  Currently uses Configuration Manager and it's responsible for keeping Windows devices up-to-date, then it should start with Desktop Analytics.
 -  Plans to implement MDM and MAM, or use ADMX templates to control Office, Microsoft Edge, and Windows settings, then it should start with Intune.

When you think about Endpoint Manager, you should think of it in three parts:

 -  **Cloud**. All data is stored in Azure; there are no more data centers. This approach gives organizations the mobility benefits of the cloud, and the security benefits of Azure.
 -  **On-premises**. If an organization has an on-premises infrastructure that includes Configuration Manager, or it isn't ready to use the cloud, then it can keep its existing systems.
 -  **Cloud + on-premises**. Many environments are mixed. As such, they use a combination of cloud and on-premises. For new devices, an organization can use the benefits of Intune to access and protect data. If an organization uses Configuration Manager, it can connect to the cloud for extra functionality and analytics. If it wants to move some workloads to the cloud, then co-management is a good option.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”