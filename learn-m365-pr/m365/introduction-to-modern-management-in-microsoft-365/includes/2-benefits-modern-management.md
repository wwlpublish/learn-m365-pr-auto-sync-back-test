Until recently, managing an organization's technological infrastructure and PCs was done using dissimilar tools and methods that meant IT professionals had to do lots of hands-on, manual, and time-consuming tasks. New kinds of device form factors, new approaches in Windows 10 management, advancements in cloud technology, and **bring your own device (BYOD)** trends have made the move toward modern management more compelling for many organizations - not only for mobile devices, but also for PCs.

Modern management is a novel approach of managing Windows 10 similar to how mobile devices are managed by **Enterprise Mobility Management (EMM)** solutions. This approach allows you to simplify deployment and management, improve security, provide better end-user experiences, and lower costs for your Windows devices. With modern management, you can now manage Windows 10 devices of all kinds, from desktop PCs to HoloLens and Surface Hubs, company-owned or employee-owned, as well as mobile devices using one management platform.

Video: Modern Windows 10 Management with Enterprise Mobility + Security

|:::image type="content" source="../media/video-icon.png" alt-text="Icon indicating play video." border="false":::|Watch this video to learn why you should consider implementing a modern management approach for Windows devices in your organization:|
| :--- | :--- |
| |[Modern Windows 10 Management with Enterprise Mobility + Security](https://www.youtube.com/watch?v=3gAtjMOJ-uw)|

## Pillars of modern management

|Pillar|Description|
| :--- | :--- |
| **Easy to deploy and manage**| Traditional operating system deployment (OSD) while powerful is typically complex and time consuming. There is now a simpler way to provision new Windows 10 devices. Windows Autopilot, which is deeply integrated with Azure Active Directory (Azure AD) and Intune, simplifies and personalizes out-of-the-box (OOBE) experience for users, joins the device to Azure AD, and enrolls it in Intune. Users' email, apps, files, preferences as well organization's security settings are also automatically applied by Intune without needing to create custom OS images.|
| **Always up-to-date**| Keeping up with emerging security threats and increasing user productivity requires a shift in how often Windows 10 and Microsoft 365 Apps need to be updated. With aligned updates, powerful insights driven by cloud intelligence, and a modern management approach with EMS, there is now a better way to keep devices up-to-date without the complexity of maintaining an on-premises infrastructure.|
| **Intelligent security, built in**| Attackers are becoming more sophisticated, and Microsoft 365 was designed with security in mind. There are many new and evolving security features built directly in the Microsoft 365 platform, including Windows Hello, Microsoft Defender for Endpoint, Windows Information Protection, Azure AD Identity Protection, Conditional Access, and more. These security features are powered by Microsoft Intelligent Security Graph which uses billions of signals, constantly improving machine learning algorithms, and human expertise to help you protect your company data and respond to sophisticated attacks.|
| **Proactive insights**| With rich telemetry and cloud intelligence, you can now proactively discover device and app issues before they affect end users, be more confident when applying OS updates, discover security issues, and more. The fusion of machine intelligence with human expertise can create a unique and powerful partnership.|

## Deployment and provisioning

With Windows 10, you can continue to use traditional OS deployment for small scale implementations, but you can also "manage out of the box" for a simpler experience for both users and IT. To transform new devices into fully configured, fully managed devices, you can:

- Avoid reimaging with cloud-based device management services such as [Microsoft Autopilot](/windows/deployment/windows-10-auto-pilot) for Windows 10 and [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) for dynamic provisioning of subscriptions, applications, devices, and user profiles.

- Create self-contained provisioning packages built with the [Windows Configuration Designer](https://technet.microsoft.com/itpro/windows/deploy/provisioning-packages).

- Use traditional imaging techniques such as deploying custom images using [System Center Configuration Manager](/sccm/core/understand/introduction).

You have multiple options for [upgrading to Windows 10](https://technet.microsoft.com/itpro/windows/deploy/windows-10-deployment-scenarios). For existing devices running Windows 7 or Windows 8.1, it is recommended to use the robust in-place upgrade process for a fast, reliable move to Windows 10 while automatically preserving all the existing apps, data, and settings. This can mean significantly lower deployment costs, and improved productivity as end users can be immediately productive – everything is right where they left it. Of course, you can also use a traditional wipe-and-load approach if you prefer, using the same tools that you use today with Windows 7.

## Updating and servicing

With **Windows as a Service**, your IT department no longer needs to perform complex imaging (wipe-and-load) processes with each new Windows release. Devices on Windows 10 semi-annual channel (SAC) versions receive the latest feature and quality updates through simple – often automatic – patching processes. For more information, see [Windows 10 deployment scenarios](https://technet.microsoft.com/itpro/windows/deploy/windows-10-deployment-scenarios).

**Mobile Device Management (MDM)** with Intune provide tools for applying Windows updates to client computers in your organization. Configuration Manager allows rich management and tracking capabilities of these updates, including maintenance windows and automatic deployment rules.

## Identity and authentication

You can use Windows 10 and services like [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) in new ways for cloud-based identity, authentication, and management. You can offer your users the ability to "bring your own device" (BYOD) or to "choose your own device" (CYOD) from a selection you make available. At the same time, you might be managing PCs and tablets that must be domain-joined because of specific applications or resources that are used on them.

You can envision user and device management as falling into these two categories:

- Corporate (CYOD) or personal (BYOD) devices used by mobile users for SaaS apps. With Windows 10, your employees can self-provision their devices.

- Domain joined PCs and tablets used for traditional applications and access to important resources. These may be traditional applications and resources that require authentication or accessing highly sensitive or classified resources on-premises. With Windows 10, if you have an on-premises [Active Directory](https://technet.microsoft.com/windows-server-docs/identity/whats-new-active-directory-domain-services) domain that's [integrated with Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-devices-group-policy/), when employee devices are joined, they automatically register with Azure AD.

Domain-joined PCs and tablets can continue to be managed with the [System Center Configuration Manager](/sccm/core/understand/introduction) client or Group Policy.
