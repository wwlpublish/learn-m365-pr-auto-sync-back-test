Microsoft Endpoint Manager helps you by providing a single, modern, integrated management platform for managing, protecting, and monitoring all of your organization's endpoints. Endpoints include tablets, smartphones, desktops, laptops computers, and apps that an organization uses whether they connect over the internet (cloud-based) or are on-premises. Microsoft Endpoint Manager is the overall management platform you can use to manage your organization's endpoints. Both Microsoft Intune and Microsoft Endpoint Configuration Manager are part of Microsoft Endpoint Manager and are also involved in co-management.

If you need to manage only cloud-based endpoints, you can use Microsoft Intune. If you need to manage only on-premises endpoints, such as the computers your organization has attached to your internal network, you can use Microsoft Endpoint Configuration Manager. However, if you need to manage a combination of both cloud and on-premises endpoints, you can use co-management to leverage both Intune and Configuration Manager from the Microsoft Endpoint Manager admin center.

Co-management is one way to cloud attach your on-premises devices. Co-management allows you to concurrently manage Windows 10 or Windows 11 devices with both Configuration Manager and Microsoft Intune. The other way of attachment is called tenant attach, which is registering your Intune tenant with your Configuration Manager deployment. It is important to note that each of these methods (tenant attach and co-management) can be added independently. Once you implement both, you have full cloud attachment. You get immediate value through tenant attach and you get additional value through co-management. Attaching your tenant using tenant attach is relatively quick. Co-managing your devices involves more planning and choices.

When you enable co-management, Configuration Manager is still the management authority for all functional areas known as workloads. So, you continue to manage your devices the same way. If you don't switch any workloads to Intune, all of the Configuration Manager settings and apps continue to work the same as before you enabled co-management. Additionally, enabling co-management is completely transparent to the end user. There's no reboot, no agent installation, no interruption, and no user notification.

Suppose that you're the administrator or business decision maker of a company with several thousand employees. You need to keep your corporate data safe by protecting data, apps, and devices that your employees use, as well as keep your employees productive and maximize the return on your endpoint management investment. You and your company have determined that you need to manage both on-premises endpoints, as well as cloud-based endpoints. Specifically, you would like to have centralized visibility of the health of all your organization's devices, whether those devices are connected via the cloud using Intune or are on-premises. You've already set up Configuration Manager's [tenant attach](/learn/modules/endpoint-manager/setup-tenant-attach-using-configuration-manager?azure-portal=true) for your devices, and you want to add additional value to fully cloud attach your on-premises machines using Microsoft Endpoint Manager admin center.

In this module, you'll review and prepare for co-management. When you're complete, you'll understand the possible paths to enabled co-management for both existing Configuration Manager clients and new internet-based devices.

## Learning objectives

In this module, you will:

- Learn about the benefits of co-management
- Understand the co-management prerequisites
- Confirm the Configuration Manager connector status
- Learn about paths to implement co-management

> [!NOTE]
> It's important to understand that you have more than one option when considering a migration path to device management in the cloud. Any of the following options will put you on the path to modern endpoint management:
> - Add tenant attach with Microsoft Endpoint Configuration Manager
> - Set up co-management with Microsoft Endpoint Configuration Manager
> - Move from Configuration Manager to Intune
> - Start from scratch with Microsoft 365 and Intune
> 
> For detailed guidance when you currently use Microsoft Endpoint Configuration Manager as your on-premises management solution and need to understand the above endpoint management options, see [Currently use Configuration Manager](/mem/intune/fundamentals/deployment-guide-intune-setup?azure-portal=true.md#currently-use-configuration-manager).
