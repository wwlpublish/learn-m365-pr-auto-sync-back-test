Device Registration is particularly useful when users use their own devices to access company data. If a company enables Device Registration, its users can register and enroll their devices in the company network. After a user enrolls a device:

 -  The device is associated with the user's account in the company directory.
 -  The device object is created in AD DS.
 -  The user certificate is installed on the device.

The device object in AD DS establishes a link between the user and the device. Further communication with company resources that support claims-based authentication (from a device enabled for Device Registration) includes information about the device and the user. Once you properly configure an app to support claim-based authentication, users are not required to enter credentials again.

:::image type="content" source="../media/overview-device-registration-c4c0299f.jpg" alt-text="Diagram showing the process for device registration.":::


After you enable the device for Device Registration, the device is used as a second form of authentication. If multiple users use the same device, each user can enable the device for Device Registration independently. Administrators can configure which apps users then can access from the device without entering credentials, and they can then ensure that company policies and security applies to those devices by configuring a device policy. Be aware that a company Group Policy applies only to domain-joined devices and not to devices enabled for Device Registration. If a device enabled for Device Registration is compromised, or if a device owner leaves the company, an administrator can remove the device object from the domain, and by doing so, the administrator revokes the device’s ability to access domain resources through SSO.

### Scenarios for using Device Registration

Many devices that employees use to access company data are company-owned, and those devices usually are domain-joined. Users also might access company data by using their own devices from inside the company network and over the Internet. The company’s IT department can closely monitor and manage domain-joined computers, but devices that are not domain members can be an issue. Users typically use devices for accessing virtual desktops, for running company apps, and for accessing other company resources.

Environments that adopt the BYOD scenario are particularly suitable for the Device Registration feature. Using this feature, users can access company resources from devices enabled for Device Registration with SSO, and administrators can control access to resources and control the compliance of local copies of company data on such devices while a device is not domain-joined.

A device that is enabled for the Device Registration feature is used as a second authentication factor when accessing claims-based company apps. For such apps, administrators can control who can access them, from which devices they can be accessed, and whether they can be accessed only from the company network or from the Internet as well. Devices enabled for Device Registration trust the company certification authority (CA), which makes it easier to configure them for additional features such as Work Folders.
