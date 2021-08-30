Microsoft Endpoint Manager helps you by providing a single, modern, integrated management platform for managing, protecting, and monitoring all of your organization's endpoints. Endpoints include tablets, smartphones, desktops, laptops computers, and apps that an organization uses whether they connect over the internet (cloud-based) or are on-premises. Microsoft Endpoint Manager is the overall management platform you can use to manage your organization's endpoints. Both Microsoft Intune and Microsoft Endpoint Configuration Manager are part of Microsoft Endpoint Manager.

If you need to manage only cloud-based endpoints, you can use Microsoft Intune. If you need to manage only on-premises endpoints, such as the computers your organization has attached to your internal network, you can use Microsoft Endpoint Configuration Manager. However, if you need to manage a combination of both cloud and on-premises endpoints, you can use cloud attach to leverage both Intune and Configuration Manager from Microsoft Endpoint Manager.

There are two steps to cloud attach your on-premises devices. The first step of attachment is called tenant attach, which is registering your Intune tenant with your Configuration Manager deployment. The second step is called co-management, which is concurrently managing Windows 10 devices with both Configuration Manager and Microsoft Intune. These are incremental steps on the journey to having full cloud attachment. You get immediate value through tenant attach and you get additional value through co-management.

> [!TIP]
> **Cloud attach** consists of **tenant attach**, **co-management** and **Endpoint analytics**. Each can be added independently.

Suppose that you're the administrator or business decision maker of a company with several thousand employees. You need to keep your corporate data safe by protecting data, apps, and devices that your employees use, as well as keep your employees productive and maximize the return on your endpoint management investment. You and your company have determined that you need to manage both on-premises endpoints, as well as cloud-based endpoints. You have already [set up tenant attach](/learn/modules/endpoint-manager/setup-tenant-attach-using-configuration-manager?azure-portal=true), the first part of cloud attaching your on-premises computers. Now, you need to fully co-manage your on-premises machines using Microsoft Endpoint Manager admin center.

> [!NOTE]
> It's important to understand that you have more than one option when considering a migration path to device management in the cloud. Any of the following options will put you on the path to modern endpoint management:
> - Add tenant attach with Microsoft Endpoint Configuration Manager
> - Set up co-management with Microsoft Endpoint Configuration Manager
> - Move from Configuration Manager to Intune
> - Start from scratch with Microsoft 365 and Intune
> 
> For detailed guidance when you currently use Microsoft Endpoint Configuration Manager as your on-premises management solution and need to understand the above endpoint management options, see [Currently use Configuration Manager](/mem/intune/fundamentals/deployment-guide-intune-setup?azure-portal=true.md#currently-use-configuration-manager).

In this module, you'll step through the process of setting up co-management. When you're complete, you'll have enabled co-management for both existing Configuration Manager clients and new internet-based devices.

## Learning objectives

In this module, you will:

- Understand co-management
- Learn about co-management prerequisites
- Confirm the Configuration Manager connector status
- Learn about paths to co-management
- Enable co-management for existing Configuration Manager clients
- Enable co-management for new internet-based devices
