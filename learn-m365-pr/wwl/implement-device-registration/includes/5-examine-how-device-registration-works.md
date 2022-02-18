The main purposes of the Device Registration feature are to provide:

 -  Registration in AD DS for non-domain joined devices.
 -  SSO for selected application and resources in a company’s internal network.

Device Registration works by using Device Registration Service and Active Directory Federation Services (AD FS) with Device Authentication enabled. When a user registers a device through the enrollment process, Device Registration Service will provision a certificate for the device. This certificate is used to authenticate the device when it accesses internal resources. In addition, the device becomes associated to the specific user in AD DS, so administrators can configure access policies to apply to users and their registered devices.

:::image type="content" source="../media/device-registration-process-a86e6bf2.jpg" alt-text="Diagram showing the process of device registration.":::


By implementing the Web Application Proxy component, you also can enable registered devices to access company resources from external networks such as the Internet. A user can be in a coffee shop or at home, and if their device is registered, it can access internal applications through Web Application Proxy and AD FS. If the user is using their registered device in an internal network, it will communicate directly to AD FS and AD DS to authenticate. For devices that are registered, you also can enable SSO for some applications. By doing this, the user is not prompted for credentials each time they try to access the resource.
