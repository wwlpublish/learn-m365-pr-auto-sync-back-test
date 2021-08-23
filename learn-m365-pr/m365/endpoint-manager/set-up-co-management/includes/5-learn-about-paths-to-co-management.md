There are two primary ways for you to set up co-management. It's important to understand the prerequisites for each path. They each require some combination of Azure Active Directory (Azure AD), Configuration Manager, Microsoft Intune, and Windows 10.

Once you decide to move to Configuration Manager or extend your existing Configuration Manager solution, there are two main paths to reach co-management:

- **Existing Configuration Manager clients**: You have Windows 10 devices that are already Configuration Manager clients. You set up hybrid Azure AD, and enroll them into Intune.
- **New internet-based devices**: You have new Windows 10 devices that join Azure AD and automatically enroll to Intune. You install the Configuration Manager client to reach a co-management state.

>[!Tip]
> As we talk with our customers that are using Microsoft Endpoint Manager to deploy, manage, and secure their client devices, we often get questions regarding co-managing devices and hybrid Azure Active Directory (AD) joined devices. Many customers confuse these two topics – the first is a management option, while the second is an identity option. See the blog post [Understanding hybrid Azure AD and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201). This blog aims to clarify Hybrid Azure AD Join and co-management, how they work together but are not the same thing.

> [!NOTE]
> It's important to understand that you have more than one option when considering a migration path to device management in the cloud. Any of the following options will put you on the path to modern endpoint management:
> - Add tenant attach with Microsoft Endpoint Configuration Manager
> - Set up co-management with Microsoft Endpoint Configuration Manager
> - Move from Configuration Manager to Intune
> - Start from scratch with Microsoft 365 and Intune

For detailed guidance when you currently use Microsoft Endpoint Configuration Manager as your on-premises management solution and need to understand your endpoint management options, see the [Currently use Configuration Manager](/mem/intune/fundamentals/deployment-guide-intune-setup?azure-portal=true.md#currently-use-configuration-manager).