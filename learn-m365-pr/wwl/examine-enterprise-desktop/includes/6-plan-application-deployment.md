Application deployment planning consists of three phases: managing application inventory and compatibility, packaging applications, and providing life-cycle support.

#### Application inventory and compatibility

Application compatibility can have a far-reaching impact on your organization, but you can significantly reduce that impact by properly planning your application compatibility project. Updates to Windows generally don't impact application compatibility, however, it can and does happen. When upgrading from a previous OS, such as upgrading from Windows 8.1 to Windows 10, most applications will function normally, however, there are typically always some applications (such as Anti-virus) that will require attention.

Gathering an application inventory is the first step in understanding the effect of application compatibility changes in your environment. Microsoft offers several tools to perform asset inventories, such as Endpoint Manager and a Desktop Analytics solution called Compatibility assessment. Organizations may also utilize the hardware inventory and asset intelligence features of Configuration Manager to assist in gathering inventory data.

For environments that have thousands of managed applications, you can undertake an application compatibility project to reduce the number of applications in the environment, which in turn will reduce the costs associated with application proliferation. An easy, immediate way to reduce the number of applications within an environment is to standardize the application versions in use across an organization.

Newer applications might supersede many older applications that provide similar functionality, thus enabling you to remove older applications. Every time you remove an application, you eliminate corresponding licensing and support costs. During an application compatibility project, you can analyze application compatibility across your entire enterprise. Configuration Manager can manage superseded applications and their removal.

#### Application packaging

Application packaging and automated installation generally involve using silent installation commands from vendors. You can find these commands in installation guides, on Internet forums, or by launching the setup application with the **/help** or **/?** command-line options.

Silent installation commands may not be available for applications that you develop in-house. If this occurs, you will either need to package those applications or repackage them if the installer package does not work. If necessary, you can create Windows Installer packages. App-V provides a packaging mechanism with the application sequencing that it uses to create virtual applications. App-V is integrated with Configuration Manager for virtual app deployments.

#### Application life-cycle support

Application life-cycle support usually involves deploying new applications, installing new versions of existing applications, and updating applications.

 -  **Deploying new applications.** New applications are typically tested for compatibility issues with existing applications.
 -  **Installing new versions of existing applications.** Version upgrades usually are significantly more complex to perform than updates, and comprehensive planning and testing are fundamental to ensuring that the upgrade release occurs properly.
 -  **Updating applications.** Updates are usually far more frequent and require less testing than version upgrades.

#### Application Delivery

Organizations have several options for choosing how to deliver applications. Applications can be installed automatically (such as during deployment, based on user group memberships) or through a portal, where users choose to install applications on-demand. Consideration should also be given on whether the organization will support access to applications and data on personal devices. Most common scenarios include the ability to access work e-mail using Outlook on a mobile phone but can also include the ability for users to install LOB apps on personal devices as well.

**Microsoft Store for Business**

The Microsoft Store for Business is a Microsoft Azure–based portal for finding, distributing, and managing applications in an enterprise. You can filter applications by device, such as phone, Surface Hub, IoT, and HoloLens. You can develop line-of-business (LOB) applications and publish them through the Microsoft Store for Business so that they are available only to your organization. The Microsoft Store for Business may not be available in all locations.

> [!NOTE]
> The Microsoft Store for Business will be retired in Q1 2023. Organizations will be able to host and manage their own private stores using solutions such as Microsoft Intune to deploy private applications. More on this will be announced in early 2022.

**Microsoft Endpoint Manager**

Microsoft Endpoint Manager is a suite of tools for centralized device deployment and management. Customers can choose to manage their app deployments using Microsoft Intune and Microsoft Endpoint Configuration Manager. Endpoint Manager supports a wide variety of application installation types. This includes common apps such as Office, application package deployment, line-of-business (LOB) apps, Microsoft Store for Business apps, and curation of built-in apps. Endpoint Manager also supports application policies to protect data in BYOD scenarios and ensuring that only devices that meet compliance rules can access application data.

**Virtual Application Delivery**

Virtual application delivery can be beneficial when the client is unable to run the application. Applications are installed on a server and delivered remotely using Remote Desktop Services. Azure Virtual Desktop can deliver an entire desktop experience to a client. These solutions can also be used in scenarios where installing the application isn't practical or desired, such as providing temporary access to a contractor.
