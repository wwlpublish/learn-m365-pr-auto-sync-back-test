Windows 10 devices can be Co-managed if they're managed by Configuration Manager and enrolled to Intune. To be managed by Configuration Manager, you must install the Configuration Manager client on a device. You can install the client by using any of the following options:

 -  Client push installation
 -  Software update point-based installation
 -  Group policy installation
 -  Sign in script installation
 -  Manual installation
 -  Microsoft Intune MDM installation

> [!NOTE]
> In most companies, the Configuration Manager client is installed using client push installation.<br>

**Additional reading.** For more information, see [Installing the Configuration Manager client](/sccm/core/clients/deploy/plan/client-installation-methods).

You can enroll a Windows 10 device to Intune in several different ways, including:

 -  Settings app to manually connect device to work or school.
 -  Provisioning package for bulk enrollment to the MDM service.
 -  Group Policy, by configuring **Auto MDM enrollment with AAD token** setting.
 -  Configuration Manager to trigger automatic enrollment to Intune.

You can connect a Windows 10 device to work and school, which enrolls it to Intune, by completing following steps:

1.  On Windows 10 device, on the taskbar select **Start**, type **work or school** and then select **Connect to work or school**. The **Settings** app opens.
2.  In **Settings** app, in the details pane, select **+Connect**.
3.  In the **Set up a work or school account** window, in the **Email address** text box, type your Azure Active Directory credentials and then select **Next**.
4.  In the **Enter password** window, in the **Password** text box, type your password and then select **Sign in**.
5.  In the **You’re all set!** window, select **Done**.

You can also enable automatic enrollment of Azure AD-joined devices to MDM. This design requires the Azure Active Directory Premium edition, which enables Windows 10 devices to be joined to Azure AD and Intune at the same time.

**Additional reading.** For more information, see:

 -  [How to enable automatic enrollment of Azure Active Directory joined devices to MDM](/intune/windows-enroll).

 -  [Using the Settings app to manually connect a device to work or school](/windows/client-management/mdm/mdm-enrollment-of-windows-devices).
