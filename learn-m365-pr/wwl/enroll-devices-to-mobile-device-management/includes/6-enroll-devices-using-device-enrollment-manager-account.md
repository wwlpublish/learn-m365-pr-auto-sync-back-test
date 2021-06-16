In many companies, users enroll company-owned devices to MDM themselves. But there are scenarios in which these same organizations prefer to have a device already enrolled by the time a user receives it. For example, when devices are used by non-technical users, or if the same device is shared by multiple users.

Every user can enroll only a limited number of devices to MDM. This limit doesn't apply to the Device enrollment manager (DEM). The DEM account is a special user account used to enroll devices. The features of this account include:
-  It can be used to enroll up to 1000 devices to MDM.-  It enables organizations to use Intune to manage large numbers of mobile devices with a single user account.-  An organization can add multiple users to the DEM account to give them the special DEM capabilities. Only users that have been assigned an Intune license can be assigned to the DEM account.

When a user enrolls a device, they're associated with that device. But when a DEM account enrolls the device, no user is associated with the device, and the device has no assigned user. If an organization plans to bulk enroll many devices at one time, it can specify the users who will do the bulk enrollment as device enrollment managers on the Intune view in the Azure portal.

### Example scenario

For example, consider following scenario:<br>

A restaurant wants to provide 50 point-of-sale tablet devices for the employees that deal with customers. The employees never need to access company data or sign in as users.

The Intune administrator creates a new device enrollment manager account for the restaurant supervisor. This account is separate from the supervisor's primary user account, and it's used only for enrolling shared devices to Intune.

Each Intune user can only enroll up to five devices, by default. However, the supervisor can enroll all 50 tablet devices by using the DEM credentials.

### Comparing DEM-enrolled devices to user-enrolled devices

Devices that are enrolled by a device enrollment manager have the following differences when compared to devices that are enrolled individually by users:
-  Devices that are enrolled by a DEM account don't have a per-user access. Because devices don't have an assigned user, the device has no email or company data access. VPN configurations, for example, could still be used to provide device apps with access to data.-  The DEM account can't use the Company Portal to unenroll DEM-enrolled devices. Only the Intune administrator can unenroll such devices.-  Users can't use Apple Volume Purchase Program (VPP) apps with user licenses because of per-user Apple ID requirements for app management.-  If the DEM account enrolls iOS devices, you can't use the Apple Configurator, Apple Device Enrollment Program, or Apple School Manager to enroll devices.-  A maximum of 10 Android work profile devices may be enrolled per DEM account. This limitation is specific for Android devices, and it doesn't apply to legacy Android enrollment.-  A device doesn't need an Intune license to be enrolled by a DEM account.

A user must be a Microsoft 365 Global Administrator or a member of the Intune Service Administrator Azure AD role to complete the tasks related to DEM enrollment.

The DEM account is only used for device enrollment. Removing a DEM account doesn't affect devices that are already enrolled. When a DEM account is removed:
-  Enrolled devices are unaffected and continue to be fully managed.-  The removed DEM account credentials remain valid.-  The removed DEM account can't wipe or retire devices.-  The removed DEM account can only enroll devices up to the per-user limit configured by the Intune administrator.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”