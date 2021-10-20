Microsoft 365 offers several tools to manage your devices. The two primary tools include:

 -  **Configuration Manager.** An on-premises solution that provides comprehensive control over feature updates for Windows 10 devices.
 -  **Microsoft Intune.** A cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). You control how your organization’s devices are used, including mobile phones, tablets, and laptops. You can also configure specific policies to control applications.

Co-management integrates these tools together, which enables you to concurrently manage Windows 10 devices by using both Configuration Manager and Microsoft Intune. It lets you cloud-attach your existing investment in Configuration Manager by adding new functionality. By using co-management, you have the flexibility to use the technology solution that works best for your organization.<br>

When a Windows 10 device has the Configuration Manager client installed and is enrolled to Intune, you get the benefits of both services. You control which workloads, if any, you want to switch authority from Configuration Manager to Intune. Configuration Manager continues to manage all other workloads, including workloads that you don't switch to Intune. If you switch a workload to Intune, but later change your mind, you can switch it back to Configuration Manager.

Co-management supports the following workloads:

 -  Compliance policies
 -  Windows Update policies
 -  Resource access policies
 -  Endpoint Protection
 -  Device configuration
 -  Office Click-to-Run apps
 -  Client apps

You're also able to pilot a workload with a separate collection of devices. Piloting allows you to test the Intune functionality with a subset of devices before switching a larger group.

> [!IMPORTANT]
> Based on recent updates, Microsoft Intune and Configuration Manager have been moved into Microsoft Endpoint Manager. Microsoft Endpoint Manager is a unified platform that includes Configuration Manager, Microsoft Intune, Desktop Analytics, and Co-management.

:::image type="content" source="../media/co-management-architecture-7720e7a9.jpg" alt-text="graphic showing co-management architecture":::


> [!NOTE]
> When you concurrently manage Windows 10 devices with both Configuration Manager and Microsoft Intune, this configuration is called *co-management*. When you manage devices with Configuration Manager and enroll to a third-party MDM service, this configuration is called *coexistence*.<br><br>Having two management authorities for a single device can be challenging if not properly orchestrated between the two. With co-management, Configuration Manager and Intune balance the workloads to make sure there are no conflicts. This interaction doesn't exist with third-party services, so there are limitations with the management capabilities of coexistence.

Organizations should consider and implement co-management even if its current on-premises management solution meets all its current needs. Microsoft is continuously developing new features, such as compliance policies, Conditional Access, and Mobile Application Management. None of these features are available with traditional device management.

Transitioning to co-management can be a challenging and lengthy process. However, if you already manage your environment with Configuration Manager, you can enable co-management with just four clicks - it’s that easy to configure.

Some of the benefits of implementing co-management include:

 -  **Compliance policies and Conditional Access**. Conditional Access enables you to ensure that any device requesting access to corporate data is compliant with your policies and can be trusted on your network. Conditional Access with device compliance enables you to control user access to corporate resources based on compliance rules from Intune. With Co-management you can apply these policies to Windows devices, iOS devices, and Android devices. Intune is the only enterprise mobility management (EMM) solution that can set the Conditional Access policies for Microsoft 365 across Windows, iOS, Android, and Mac.
 -  **Remote actions from Intune.** Run remote actions from Intune for co-managed devices. You can run instant actions (such as remote factory reset or wipe for a stolen device) on devices no matter where they live – whether they’re behind the firewall or on the Internet.
 -  **Configuration Manager client health.** Maintain visibility of Configuration Manager client health from the Intune on Azure portal.
 -  **Azure Active Directory (Azure AD).** With Azure AD, you can take advantage of improved productivity for your users and security for your resources, across both cloud and on-premises environments.
 -  **Windows Autopilot.** Windows Autopilot is a collection of technologies used to set up and pre-configure new Windows 10 devices, getting them ready for productive use. AutoPilot reduces the time, resources, costs, and complexity associated with deploying, managing, and retiring or recycling devices. It also creates a better experience for end users.
 -  **Anti-virus protection.** With Configuration Manager version 1802 or newer, you can use Endpoint Manager with Intune. Endpoint Manager is Microsoft’s powerful anti-virus protection.
 -  **Update management from the cloud.** With Co-management, you can modernize your Windows updates by managing updates from the cloud. This design is ideal for managing users who are always in motion. It also reduces your on-premises infrastructure costs.
 -  **Remote control of your Windows devices.** With Intune’s TeamViewer integration, you can remote control your Windows devices no matter where they are.

**Additional reading.** For more information, see [Co-management benefits and how to enable it by just four clicks](https://cloudblogs.microsoft.com/enterprisemobility/2018/04/10/co-management-is-instant-and-easy-with-just4clicks/?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”