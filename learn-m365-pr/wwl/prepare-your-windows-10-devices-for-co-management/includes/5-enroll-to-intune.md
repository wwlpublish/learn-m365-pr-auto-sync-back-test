To manage devices in Microsoft Intune, devices must first be enrolled in the Intune service. Both personally owned and corporate-owned devices can be enrolled for Intune management.

There are two ways to get devices enrolled in Intune:

 -  Users can self-enroll their Windows PCs.
 -  Administrators can configure policies to force automatic enrollment without any user involvement.

> [!TIP]
> For guidance on which enrollment method is right for your organization, see [Deployment guide: Enroll Windows devices in Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows?azure-portal=true).

### User self-enrollment in Intune

Users can self-enroll their Windows device by using any of these methods:

 -  **Bring your own device (BYOD)**. Users enroll their personally owned devices by downloading and installing the Company Portal App. This app completes the following steps during the enrollment process:
     -  Registers the device with Azure Active Directory to gain access to corporate resource, such as email.
     -  Enrolls the device in Intune as a personally owned device (BYOD).
    
    If an administrator has configured **Auto enrollment** (available with Azure AD Premium subscriptions), the user only has to enter their credentials once. Otherwise, they'll have to enroll separately through **MDM only enrollment** and reenter their credentials. For more information, see [Bring your own device (BYOD)](/mem/intune/user-help/enroll-windows-10-device?azure-portal=true).
    
    > [!NOTE]
    > **MDM only enrollment** is introduced at the end of this section. It's NOT a recommended enrollment method for the reasons described below. As such, it's recommended that **Auto enrollment** be configured whenever possible (keep in mind, **Auto enrollment** does require an Azure AD Premium subscription).
 -  **Azure Active Directory (Azure AD) Join**. This enrollment method Joins the device with Azure Active Directory. It then enables users to sign in to Windows with their Azure AD credentials. If **Auto Enrollment** is enabled, the device is automatically enrolled in Intune. The benefit of auto enrollment is a single-step process for the user. Otherwise, they'll have to enroll separately through **MDM only enrollment** and reenter their credentials. Users enroll this way either during initial Windows OOBE or from Settings. The device is marked as a corporate-owned device in Intune. For more information, see [Azure Active Directory (Azure AD) Join](/azure/active-directory/user-help/user-help-join-device-on-network?azure-portal=true).
 -  **Autopilot**. This enrollment method automates Azure AD Join and enrolls new corporate-owned devices into Intune. This method simplifies the out-of-box experience and removes the need to apply custom operating system images onto the devices. When admins use Intune to manage Autopilot devices, they can manage policies, profiles, apps, and more after they're enrolled. There are four types of Autopilot deployment:
     -  [Self Deploying Mode](/windows/deployment/windows-autopilot/self-deploying?azure-portal=true) (for kiosks, digital signage, or a shared device).
     -  [User Driven Mode](/windows/deployment/windows-autopilot/user-driven?azure-portal=true) (for traditional users).
     -  [Windows Autopilot for pre-provisioned deployment](/windows/deployment/windows-autopilot/white-glove?azure-portal=true) enables partners or IT staff to pre-provision a PC running Windows 10 or Windows 11. Doing so fully configures the device and makes it business-ready.
     -  [Autopilot for existing devices](/windows/deployment/windows-autopilot/existing-devices?azure-portal=true) enables you to easily deploy the latest version of Windows to your existing devices.

MDM only enrollment is another availableself-enrollment method. However, this method is NOT recommended. It lets users enroll an existing Workgroup, Active Directory, or Azure Active directory-joined PC into Intune. Users enroll from Settings on the existing Windows PC. This enrollment method is NOT recommended because:

 -  It doesn't register the device into Azure Active Directory (AD). Users may not get access to organization resources, such as email.
 -  It prevents using some Azure AD features, such as Conditional Access.

### Administrator-based enrollment in Intune

Administrators can set up the following methods of enrollment that require no user interaction:

 -  **Hybrid Azure AD Join**. This enrollment method lets administrators configure Active Directory group policy to automatically enroll devices that are hybrid Azure AD joined. For more information, see [Hybrid Azure AD Join](/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy?azure-portal=true).
 -  **Configuration Manager Co-management**. This method lets administrators enroll their existing Configuration Manager managed devices into Intune to get the dual benefits of Intune and Configuration Manager. For more information, see [Configuration Manager Co-management](/configmgr/comanage/overview?azure-portal=true).
 -  **Device enrollment manager (DEM)**. DEM is a special service account. Device enrollment manager accounts have permissions that let authorized users enroll and manage multiple corporate-owned devices. These types of devices are good for point-of-sale or utility apps, for example, but not for users who need to access email or company resources. There are some limitations with DEM accounts as documented [here](/mem/intune/enrollment/device-enrollment-manager-enroll#limitations?azure-portal=true). For more information on DEM, see [Device enrollment manager](/mem/intune/enrollment/device-enrollment-manager-enroll?azure-portal=true).
 -  **Bulk enrollment**. This method lets an authorized user join large numbers of new corporate-owned devices to Azure Active Directory and Intune. You create a provisioning package with the Windows Configuration Designer (WCD) app. Then, using USB media during initial Windows OOBE experience or from existing Windows PC, you install the provisioning package to automatically enroll the devices into Intune. For more information, see [Bulk enroll](/mem/intune/enrollment/windows-bulk-enroll?azure-portal=true).
 -  **Windows IoT Core device enrollment**. This process consists of the following steps:
    1.  Prepare the device by using the Windows IoT Core Dashboard.
    2.  Create a provisioning package by using Windows Configuration Designer.
    3.  Install the provisioning package to automatically enroll the devices into Intune by using an SD Card media during initial boot up. For more information, see [Enrolling Windows IoT Core devices](/windows/iot-core/manage-your-device/intunedeviceenrollment?azure-portal=true).
