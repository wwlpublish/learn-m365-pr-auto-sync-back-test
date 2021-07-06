If you need to manage only cloud-based endpoints, you can use Microsoft Intune. If you need to manage only on-premises endpoints, such as the computers your organization has attached to your internal network, you can use Microsoft Endpoint Configuration Manager. However, if you need to manage a combination of both cloud and on-premises endpoints, you can use cloud attach to leverage both Intune and Configuration Manager from Microsoft Endpoint Manager.

There are two steps to cloud attach your on-premises devices. The first step of attachment is called tenant-attach, which is registering your Intune tenant with your Configuration Manager deployment. The second step is called co-management, which is concurrently managing Windows 10 devices with both Configuration Manager and Microsoft Intune. These are incremental steps on the journey to having full cloud attachment. You get immediate value through tenant-attach and you get additional value through co-management.

> [!TIP]
> **Cloud attach** consists of **tenant-attach** plus **co-management**.

Tenant-attach is the first of two steps when implementing cloud-attach. It allows you to recognize your Configuration Manager devices and infrastructure by the Intune cloud service and take actions from Microsoft Endpoint Manager. Your tenant is where you manage your end user's devices and apps. 

> [!NOTE]
> Your tenant is a dedicated instance of Azure Active Directory (Azure AD) where your subscription to Intune is hosted and where your on-premises devices can be linked and managed. Your organization receives this tenant at the beginning of your Azure relationship with Microsoft.

Tenant-attach sets up synchronization between your Configuration Manager site and your Intune tenant. This synchronization provides you with a single view for all devices that you manage with Microsoft Endpoint Manager. Configuration Manager uses the Configuration Manager connector to enable data flow to Microsoft Endpoint Manager. This connector requires a connection to an Intune tenant, and doesn't require turning on co-management.

When you use tenant-attach, you don't do any extra device enrollment. Instead, you upload your Configuration Manager devices to be managed by Microsoft Endpoint Manager admin center, without enabling automatic enrollment for co-management or switching workloads to Intune. You can see a list of your organization's devices, and run actions on Configuration Manager managed devices. For example, you could run specific remote actions, see your on-premises servers, and get OS information.

Tenant-attach is included with your [Configuration Manager co-management license](/mem/configmgr/core/understand/product-and-licensing-faq.md) at no extra cost. It's the easiest way to integrate the cloud, using Microsoft Intune, with your on-premise Configuration Manager set up.

## Co-management and tenant-attach

Many organizations use on-premises Configuration Manager to manage devices, including desktops and servers. You can cloud attach your on-premises Configuration Manager to Microsoft Intune. When you cloud attach, you can do more than just access your on-premises servers, you get the benefits of Intune and the cloud, including the following:

- [Conditional access](/mem/configmgr/comanage/quickstart-conditional-access.md)
- [Remote actions](/mem/configmgr/comanage/quickstart-remote-actions.md)
- [Windows Autopilot](/mem/configmgr/comanage/quickstart-autopilot)
- [Antivirus settings for Configuration Manager devices](/mem/intune/protect/antivirus-microsoft-defender-settings-windows-tenant-attach.md)
- [Endpoint detection and response policy settings for Configuration Manager devices](/mem/configmgr/protect/endpoint-security-edr-profile-settings.md#endpoint-detection-and-response-configmgr)
- [Firewall policy settings for Configuration Manager devices](/mem/configmgr/protect/endpoint-security-firewall-profile-settings-tenant-attach.md)
