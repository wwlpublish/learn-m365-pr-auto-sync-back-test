This module introduces the methodology of device management known as Co-management. To understand co-management, it helps to understand where device management started and where it stands today.

Windows devices were traditionally managed in on-premises domain environments by using Group Policy and Configuration Manager. IT traditionally built and maintained its infrastructure in its own on-premises data center. This design enabled it to deliver services like Microsoft's Active Directory Domain Services (AD DS). AD DS is used for providing identity management, but also for providing access to company resources, file services, and applications.

While AD DS enables flexible and granular device management, it also requires:

 -  that devices be domain joined.
 -  the Configuration Manager management agent is installed on the device.
 -  at least periodic connectivity to on-premises infrastructure.

With the introduction of cloud computing and Software-as-a-Service (SaaS) offerings, many companies have been moving their services and applications to the cloud. In doing so, on-premises AD DS often becomes connected to Azure Active Directory (Azure AD), and many companies started using Microsoft 365 as their messaging and collaboration solution.

:::image type="content" source="../media/traditional-comparison-to-modern-6a8dd42f.jpg" alt-text="graphic comparing traditional IT to modern IT":::


There are many facets in this transition from traditional device management with on-premises infrastructure to cloud services:

 -  Identity and access management moves from on-premises AD DS to Azure AD.
 -  Legacy app management moves to SaaS solutions that handle messaging, security, and other needs.
 -  Microsoft moves IT management workloads into their cloud-based services, such as the Enterprise Mobility + Security (EMS) suite.<br>

Co-management is the first and fundamental step in this journey. With co-management, you can use existing Windows devices and configurations, but at the same time add a modern Mobile Device Management (MDM) management tool.

This module introduces you to co-management and the benefits it provides to organizations. You'll begin by learning how to plan a strategy for implementing co-management. The module introduces you to device management using Configuration Manager, and you'll learn how to enable co-management by using Azure AD.

After completing this module, you'll be able to:

 -  Describe the benefits of using Co-management to manage your Windows 10 devices.
 -  Plan your strategy to co-management your organization's devices.
 -  Describe the main features in Configuration Manager for deploying software, protecting data, monitoring health, and enforcing compliance on devices.
 -  Enable Co-management by using Azure Active Directory.
