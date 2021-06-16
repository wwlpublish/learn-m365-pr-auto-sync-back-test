An organization can enable its users to enroll their Windows 10 devices to Mobile Device Management (MDM) by using the Autodiscover service. Windows devices (Windows Phone 8.1 and 10 ,and Windows PCs 8.1 and 10) have a UI built into the operating system to enroll a device for management. The user enters a corporate email address which matches the User Principal Name (UPN) set for user identity. The device tries to autodiscover the enrollment server and start the enrollment process. If the Autodiscover service isn't configured, the device enrollment server won’t be found. In this case, the device presents a screen for the user to enter the server address.

The Autodiscover service is configured when you create an alias (CNAME resource record type) in the domain DNS zone that automatically redirects enrollment requests to Intune servers.

 -  **Autodiscover won't be configured if you don’t add this CNAME record.** In this case, users can still enroll devices to MDM, but they'll have to manually provide the address of the enrollment server.
 -  **Autodiscover will be configured if you add this CNAME record.** With the Autodiscover service enabled, users just have to provide credentials when they want to enroll their devices to MDM.

If a company is using Azure AD Premium, it can integrate Azure AD with Intune to configure automatic MDM enrollment. By doing this, Windows 10 devices that are joined to Azure AD will be automatically enrolled to Intune. In such a scenario, you don’t need to add a CNAME record to the domain DNS zone to enable the Autodiscover service. But if your company isn't using Azure AD Premium, or if users manually enroll devices to MDM by using the Settings app, you can still benefit from autodiscovery.

The Autodiscover service is simple to set up for your domain because it only requires that you create a CNAME resource record in your external (public) DNS. CNAME records let you hide the implementation details of your network from the clients that connect to it. Used internally in your network, CNAME records enable users to use the simpler URI mail.domain.com instead of host.examplemachinename.domain.com. Creating a CNAME resource record type in the domain DNS zone that automatically redirects enrollment requests to Intune servers is used in multiple scenarios. For example:

 -  If your company is using the contoso.com DNS domain, you would create a CNAME record that redirects **contoso.com** to **enterpriseenrollment.manage.microsoft.com**.
 -  If your company is using multiple DNS domains or multiple UPN suffixes, you must create one CNAME record for each domain name and point it to **manage.microsoft.com**.

Many organizations also want to enable the Autodiscover service for registering devices in Azure AD. In such environments, you would also add an **EnterpriseRegistration** CNAME DNS record that points to **EnterpriseRegistration.windows.net**.

If you want to enable the Autodiscover service for MDM enrollment and for registering devices to Azure AD, you must add the following DNS records:

:::row:::
  :::column:::
    

**Host name**


  :::column-end:::
  :::column:::
    

**Record type**


  :::column-end:::
  :::column:::
    

**Address**


  :::column-end:::
  :::column:::
    

**TTL**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

EnterpriseEnrollment


  :::column-end:::
  :::column:::
    

CNAME


  :::column-end:::
  :::column:::
    

EnterpriseEnrollment.manage.microsoft.com


  :::column-end:::
  :::column:::
    

3600


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

EnterpriseRegistration


  :::column-end:::
  :::column:::
    

CNAME


  :::column-end:::
  :::column:::
    

EnterpriseRegistration.windows.net


  :::column-end:::
  :::column:::
    

3600


  :::column-end:::
:::row-end:::


Android and iOS devices are enrolled to MDM by using the Company Portal app. The Company Portal app includes information on how to locate enrollment servers, and it doesn't use autodiscover DNS records.

**Additional reading.** For more information on configuring domains for MDM and enrolling Windows 10 devices to MDM, see the following resources:

 -  [Set up enrollment for Windows devices](https://docs.microsoft.com/intune/windows-enroll?azure-portal=true)
 -  [Set up Mobile Device Management (MDM) in Office 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd?azure-portal=true)
 -  [Which CNAMEs to use for Autodiscovery during MDM Enrollment](https://blogs.technet.microsoft.com/intunesupport/2017/03/04/which-cnames-to-use-for-auto-discovery-during-mdm-enrollment/?azure-portal=true)