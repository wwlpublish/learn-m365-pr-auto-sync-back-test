Co-management enables companies to take advantage of new features and capabilities, such as:

 -  compliance policies
 -  selective wipe
 -  provisioning new Windows 10 devices from the cloud with Windows AutoPilot

Co-management enables companies to use Mobile Device Management (MDM) features, such as Conditional Access policies, while still using Configuration Manager to complete more complex software deployments.

### **Scenarios to enable co-management**

Co-management implies that:

 -  Windows 10 devices are joined to AD DS.
 -  On-premises AD DS is synced to Azure AD.
 -  Those devices are managed by Configuration Manager and Intune at the same time.

You can enable co-management for both Windows 10 devices enrolled in Microsoft Intune and existing Windows 10 Configuration Manager clients. Devices running an older version of Windows must first be upgraded to Windows 10, version 1709 (Fall Creators Update) or later.

### **Windows 10 devices that are Configuration Manager clients**

If you have Windows 10 devices that are Configuration Manager clients, you can:

 -  enroll these devices into Intune.
 -  enable co-management from the Configuration Manager console.

Configuration Manager triggers automatic enrollment into Intune based on the Azure AD tenant information.

:::image type="content" source="../media/co-management-device-comparison-9b9710d8.jpg" alt-text="graphic showing differences between devices managed by configuration manager, devices managed by Intune, and new devices, and which portion of each fall under co-management":::


### **Windows 10 devices that are enrolled in Intune**

If Windows 10 devices are enrolled in Intune, you can create an app in Intune to install the Configuration Manager client on the devices. The app must use a specific command-line argument. You can then enable co-management from the Configuration Manager console. When Configuration Manager is enabled, you can start moving specific workloads to Intune for specific Windows 10 devices.

For new Windows 10 devices, you can use Windows Autopilot to configure the out-of-box experience. This experience includes automatic enrollment that enrolls devices in Intune.

### **Windows 10 devices that aren't enrolled in Intune or that aren't Configuration Manager clients**

For Windows 10 devices that aren't enrolled in Intune or don't have the Configuration Manager client installed you can use automatic enrollment to enroll the device in Intune. You can then create an app in Intune to deploy the Configuration Manager client. After you enable co-management, Configuration Manager continues to manage all workloads. When you decide that you're ready, Intune can start managing available workloads.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”