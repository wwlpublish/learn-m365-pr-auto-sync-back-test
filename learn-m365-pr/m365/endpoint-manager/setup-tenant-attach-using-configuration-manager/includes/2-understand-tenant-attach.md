If you need to manage only cloud-based endpoints, such as mobile devices, you can use Microsoft Intune. If you need to manage only on-premises endpoints, such as the computers your organization has attached to your internal network, you can use Microsoft Endpoint Configuration Manager. However, if you need to manage a combination of both cloud and on-premises endpoints, you can use cloud attach to leverage both Intune and Configuration Manager from Microsoft Endpoint Manager.

> [!NOTE]
> When you use tenant attach, your on-premises devices that are not co-managed are still managed by only Configuration Manager until you enable co-management. Once co-management is enabled, you can concurrently manage your on-premises device with both Configuration Manager and Intune.

There are two steps to cloud attach your on-premises devices. The first step of attachment is called tenant attach, which is registering your Intune tenant with your Configuration Manager deployment. The second step is called co-management, which is concurrently managing Windows 10 devices with both Configuration Manager and Microsoft Intune. These are incremental steps on the journey to having full cloud attachment. You get immediate value through tenant attach and you get additional value through co-management. This module focuses on tenant attach.

> [!TIP]
> **Cloud attach** consists of **tenant attach**, **co-management**, and **Endpoint analytics**. Each can be added independently.

Tenant attach sets up synchronization between your Configuration Manager site and your Intune tenant. This synchronization provides you with a single view for all devices that you manage from Microsoft Endpoint Manager admin center. Configuration Manager uses the *Configuration Manager connector* to enable data flow to Microsoft Endpoint Manager, which provides you with a single view for all devices. This connector requires a connection to your Intune tenant, and doesn't require turning on co-management.

Tenant attach allows you to recognize your Configuration Manager uploaded devices and take actions from Microsoft Endpoint Manager. For instance, you can view device data, see a timeline of device events, install apps, and run PowerShell scripts from Microsoft Endpoint Manager admin center.

> [!NOTE]
> Your tenant is where you manage your end user's devices and apps via the cloud. It's a dedicated instance of [Azure Active Directory (Azure AD)](/azure/active-directory/users-groups-roles/directory-assign-admin-roles). Also, it's where your subscription to Intune is hosted and where your on-premises devices can be linked and managed. Your organization receives this tenant at the beginning of your Azure relationship with Microsoft.

When you use tenant attach, you don't do any extra device enrollment. Instead, you upload your Configuration Manager devices to be managed by Microsoft Endpoint Manager admin center, without enabling automatic enrollment for co-management or switching workloads to Intune. You can see a list of your organization's devices, and run actions on Configuration Manager managed devices. For example, you could run specific device actions, see your on-premises servers, and get OS information.

Tenant attach is included with your [Configuration Manager co-management license](/mem/configmgr/core/understand/product-and-licensing-faq) at no extra cost. It's the easiest way to integrate the cloud, using Microsoft Intune, with your on-premise Configuration Manager set up.

