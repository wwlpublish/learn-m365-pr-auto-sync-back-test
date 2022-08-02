An organization can enable its users to enroll their Windows 10 and 11 devices to Mobile Device Management (MDM) by using the Autodiscover service. Windows devices (Windows Phone 8.1, 10, and 11) and Windows PCs (Windows 8.1, 10, and 11) have a UI built into the operating system to enroll a device for management. The user enters a corporate email address that matches the User Principal Name (UPN) set for user identity. The device tries to autodiscover the enrollment server and start the enrollment process. If the Autodiscover service isn't configured, the device enrollment server won’t be found. In this case, the device presents a screen for the user to enter the server address.

The Autodiscover service is configured when you create an alias (CNAME resource record type) in the domain DNS zone that automatically redirects enrollment requests to Intune servers.

 -  **Autodiscover won't be configured if you don’t add this CNAME record.** In this case, users can still enroll devices to MDM. However, they'll have to manually provide the address of the enrollment server.
 -  **Autodiscover will be configured if you add this CNAME record.** With the Autodiscover service enabled, users just have to provide credentials when they want to enroll their devices to MDM.

If an organization is using Azure AD Premium, it can integrate Azure AD with Intune to configure automatic MDM enrollment. By doing this, Windows 10 and 11 devices that are joined to Azure AD will be automatically enrolled to Intune. In such a scenario, the organization doesn't need to add a CNAME record to the domain DNS zone to enable the Autodiscover service. But if the company isn't using Azure AD Premium, or if its users manually enroll devices to MDM by using the Settings app, it can still benefit from autodiscovery.

The Autodiscover service is easy to set up for a domain because it only requires the organization to create a CNAME resource record in its external (public) DNS. ACNAME record lets an organization hide the implementation details of its network from the clients that connect to it. A CNAME record is used internally in an organization's network. It enables users to use the simpler URI mail.domain.com instead of host.examplemachinename.domain.com.

Creating a CNAME resource record type in the domain DNS zone that automatically redirects enrollment requests to Intune servers is used in multiple scenarios. For example:

 -  Contoso is using the contoso.com DNS domain. As such, it should create a CNAME record that redirects **contoso.com** to **enterpriseenrollment.manage.microsoft.com**.
 -  Fabrikam is using multiple DNS domains or multiple UPN suffixes. As such, it must create one CNAME record for each domain name and point it to **manage.microsoft.com**.

Many organizations also want to enable the Autodiscover service for registering devices in Azure AD. In such environments, they must also add an **EnterpriseRegistration** CNAME DNS record that points to **EnterpriseRegistration.windows.net**.

If an organization wants to enable the Autodiscover service for MDM enrollment and for registering devices to Azure AD, it must add the DNS records that are outlined in the following table.

| **Host name**          | **Record type** | **Address**                               | **TTL** |
| ---------------------- | --------------- | ----------------------------------------- | ------- |
| EnterpriseEnrollment   | CNAME           | EnterpriseEnrollment.manage.microsoft.com | 3600    |
| EnterpriseRegistration | CNAME           | EnterpriseRegistration.windows.net        | 3600    |

Android and iOS devices are enrolled to MDM by using the Company Portal app. The Company Portal app includes information on how to locate enrollment servers. It doesn't use autodiscover DNS records.

**Additional reading.** For more information on configuring domains for MDM and enrolling Windows 10 and 11 devices to MDM, see the following resources:

 -  [Set up enrollment for Windows devices](/intune/windows-enroll?azure-portal=true).
 -  [Set up Mobile Device Management (MDM) in Office 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd?azure-portal=true).
 -  [Which CNAMEs to use for Autodiscovery during MDM Enrollment](https://blogs.technet.microsoft.com/intunesupport/2017/03/04/which-cnames-to-use-for-auto-discovery-during-mdm-enrollment/?azure-portal=true).
