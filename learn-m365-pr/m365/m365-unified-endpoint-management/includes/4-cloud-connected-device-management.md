If you have an existing on-premises Configuration Manager infrastructure, you can connect it with your cloud-based Intune management system. This enables you to concurrently manage Windows 10 devices by using both Configuration Manager and Microsoft Intune. This is called **co-management**. It brings Intune functionality into your device management ecosystem and provides immediate value, such as:

- **Hybrid Azure AD** - Azure Active Directory (Azure AD) allows you to link your users, devices, and applications across both cloud and on-premises environments. Registering your devices to Azure AD enables you to improve productivity for your users and security for your resources. Having devices in Azure AD is the foundation for both co-management and device-based conditional access.

   - Single sign on to cloud resources
   - Windows Hello for Business
   - Device Based Conditional Access
   - Automatic Device Licensing
   - Self Service functionality
   - Enterprise state roaming
- **Conditional access** - Conditional access makes sure that only trusted users can access organizational resources on trusted devices using trusted apps. With co-management, Intune evaluates every device in your network to determine how trustworthy it is. Intune makes sure a device or app is managed and securely configured. Intune detects active security incidents on a device.
- **Remote actions** – allows you to manage every device that you have registered every time it connects, no matter where it is. Remote device actions give you management controls on the device without interfering with personal data. These remote device actions allow you to:
   - Delete company data on lost or stolen devices
   - Rename a device
   - Restart a device
   - Review device inventory
   - Remotely control a device
   - Wipe out pre-installed OEM apps with a Fresh Start reboot
   - Do a factory reset on any Windows 10 device
- **Client Health** – Configuration Manager can monitor client device health while it is connected to your network. On a co-managed device, Intune can communicate with and monitor the health of the device even when it is not connected to your network. With co-management, Intune can report on the client health state. It provides timestamp information for the validity of the data. This information tells you if your devices are healthy, able to connect, able to install apps, or can update to the required OS builds. With this feature, you have an external data source with Intune. It allows you to determine what the next steps should be taken when troubleshooting a vast array of client issues. You don't need to create additional reports or use other tools to pull back client data.
- **Windows 10 Autopilot** - When you use co-management and Autopilot together, you make sure that new devices entering your network end up in the same state of management. In this setup, devices are enrolled in Intune and have a Configuration Manager client. It allows you to use the new Windows 10 provisioning model, and helps you eliminate the need to create, maintain, and update custom OS images.
   - Reduce time, costs, and complexity
   - Improve the user experience
   - Use Autopilot and Configuration Manager to migrate existing Windows 7 devices to Windows 10
   - Modernizing device provisioning for all types of workers
