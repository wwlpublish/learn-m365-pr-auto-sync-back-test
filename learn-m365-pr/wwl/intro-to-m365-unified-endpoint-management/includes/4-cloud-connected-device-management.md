If you have an existing on-premises Configuration Manager infrastructure, you can connect it with your cloud-based Intune management system using the “co-management” function from Configuration Manager. This cloud-connected scenario lets you manage Windows 10 devices using Configuration Manager and Microsoft Intune concurrently. It brings Intune functionality into your device management ecosystem and provides immediate value, such as:

 - **Conditional access**. Conditional access makes sure that only trusted users can access your organizational resources on trusted devices using trusted apps. With co-management, Intune evaluates every device in your network to determine how trustworthy it is. Intune makes sure devices and apps are managed and securely configured, and detects active security incidents on a device.
- **Remote actions**. You can manage every registered device every time it connects, no matter where it is. Remote device actions give you management controls on the device without interfering with personal data of your users. These remote device actions allow you to:
   - Delete company data on lost or stolen devices
   - Rename a device
   - Restart a device
   - Review device inventory
   - Remotely control a device
   - Wipe out pre-installed OEM apps with a Fresh Start reboot
   - Do a factory reset on any Windows 10 device
- **Client Health**. Configuration Manager monitors client device health while it’s connected to your network. On a co-managed device, Intune communicates with and monitors the health of the device - even when it’s not connected to your network. With co-management, Intune can report on the health of the client. It provides timestamp information for the validity of the data, which tells you if your devices are healthy, able to connect, able to install apps, or able to update to the required OS builds. With this feature, you have an external data source with Intune. It allows you to determine what the next steps should be when troubleshooting client issues. You don't need to create additional reports or use other tools to get client data, which saves you time and effort.
- **Windows 10 Autopilot**. When you use co-management and Autopilot together, new devices entering your network get configured the same way as existing devices. In this setup, devices are enrolled in Intune and have a Configuration Manager client. It allows you to use the Windows 10 provisioning model and helps you eliminate the need to create, maintain, and update custom operating system images. It can also reduce time, costs, and complexity, and lets you use Autopilot and Configuration Manager to migrate existing Windows 7 devices to Windows 10.

- **Hybrid Azure AD**. Azure Active Directory (Azure AD) allows you to link your users, devices, and applications across both cloud and on-premises environments. Registering your devices to Azure AD helps you improve productivity for your users and improve security for your resources. Having devices in Azure AD is the foundation for both co-management and device-based Conditional Access. It also includes:
   - Single sign-on to cloud resources
   - Windows Hello for Business
   - Device-based Conditional Access
   - Automatic device licensing
   - Self Service functionality
   - Enterprise state roaming
