Windows Autopilot depends on specific capabilities available in Windows 10, Azure Active Directory, and MDM services such as Microsoft Intune. Windows Autopilot is maintained through Microsoft Endpoint Manager. The following sections examine the software and hardware requirements that must be met to use Windows Autopilot.

### Software requirements

A supported version of Windows 10 semi-annual channel is all that's required to use Windows Autopilot. The following editions are supported:

 -  Windows 10 Pro<br>
 -  Windows 10 Pro Education
 -  Windows 10 Pro for Workstations
 -  Windows 10 Enterprise
 -  Windows 10 Education
 -  Windows 10 Enterprise 2019 LTSC

### Networking requirements

Windows Autopilot's network requirements are a bit more involved than its software requirement. The network requirements depend on various internet-based services. Access to these services must be provided for Autopilot to function properly. In the simplest case, complete the following steps to enabling proper functionality:

 -  Ensure DNS name resolution for internet DNS names.
 -  Allow access to all hosts through ports 80 (HTTP), 443 (HTTPS), and 123 (UDP/NTP).

In environments that have more restrictive Internet access, or for those environments that require authentication before internet access can be obtained, more configuration may be required to allow access to the required services. The following table provides more details about each of these services and their specific requirements.

:::row:::
  :::column:::
    

**Service**


  :::column-end:::
  :::column:::
    

**Information** 


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Windows Autopilot Deployment Service and Windows Activation


  :::column-end:::
  :::column:::
    

After a network connection is in place, each Windows 10 device will contact the Windows Autopilot Deployment Service.

For all supported Windows 10 releases, Windows Autopilot uses Windows Activation services. For more information, see [Windows activation or validation fails with error code 0x8004FE33](https://support.microsoft.com/help/921471/windows-activation-or-validation-fails-with-error-code-0x8004fe33?azure-portal=true) for details about problems that may occur when you connect to the Internet through a proxy server.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Azure Active Directory


  :::column-end:::
  :::column:::
    

User credentials are validated by Azure Active Directory, and the device can also be joined to Azure Active Directory.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Intune


  :::column-end:::
  :::column:::
    

Once authenticated, Azure Active Directory will trigger enrollment of the device into the Intune MDM service.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Windows Update


  :::column-end:::
  :::column:::
    

During the out-of-box-experience (OOBE) process, and after the Windows 10 OS is fully configured, the Windows Update service is used to retrieve needed updates. If there are problems connecting to Windows Update, see [How to solve connection problems concerning Windows Update or Microsoft Update](https://support.microsoft.com/help/818018/how-to-solve-connection-problems-concerning-windows-update-or-microsof?azure-portal=true).


If Windows Update is inaccessible, the Autopilot process will still continue, but critical updates won't be available.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Delivery Optimization


  :::column-end:::
  :::column:::
    

When downloading Windows Updates, Microsoft Store apps and app updates, Office Updates, and Intune Win32 Apps, the [Delivery Optimization](/windows/deployment/update/waas-delivery-optimization) service is contacted to enable peer-to-peer sharing of content. By doing so, only a few devices need to download it from the internet.

If the Delivery Optimization Service is inaccessible, the Autopilot process will still continue with Delivery Optimization downloads from the cloud (without peer-to-peer).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Network Time Protocol (NTP) Sync


  :::column-end:::
  :::column:::
    

When a Windows device starts up, it will talk to a network time server to ensure that the time on the device is correct. Ensure that UDP port 123 to time.windows.com is accessible.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Domain Name Services (DNS)


  :::column-end:::
  :::column:::
    

To resolve DNS names for all services, the device communicates with a DNS server, typically provided through DHCP. This DNS server must resolve internet names.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Diagnostics data


  :::column-end:::
  :::column:::
    If diagnostic data can't be sent, the Autopilot process will still continue, but services that depend on diagnostic data, such as Desktop Analytics, won't work.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Network Connection Status Indicator (NCSI)


  :::column-end:::
  :::column:::
    

Windows must determine whether the device can access the internet. For more information, see [Network Connection Status Indicator (NCSI)](https://docs.microsoft.com/windows/privacy/manage-windows-1709-endpoints#network-connection-status-indicator-ncsi?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Windows Notification Services (WNS)


  :::column-end:::
  :::column:::
    

This service is used to enable Windows to receive notifications from apps and services.

If the WNS services aren't available, the Autopilot process will still continue without notifications.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Microsoft Store, Microsoft Store for Business


  :::column-end:::
  :::column:::
    

Apps in the Microsoft Store for Business can be pushed to the device and triggered through Intune (MDM). App updates and other apps may also be needed when the user first signs in.

If the Microsoft Store for Business isn't accessible, the Autopilot process will still continue without Microsoft Store for Business apps.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Microsoft 365


  :::column-end:::
  :::column:::
    

As part of the Intune device configuration, installation of Microsoft 365 Apps for enterprise (formerly Office 365 Pro Plus) may be required.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Certificate revocation lists (CRLs)


  :::column-end:::
  :::column:::
    

Some of these services must also check certificate revocation lists (CRLs) for certificates used in the services. A full list of these certificates is documented at [Office 365 URLs and IP address ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_crl?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Hybrid Azure AD join


  :::column-end:::
  :::column:::
    

Hybrid Azure Active Directory can be joined, but the machine should be on a corporate network for hybrid Azure AD join to work.


  :::column-end:::
:::row-end:::


### Licensing requirements

Windows Autopilot depends on specific capabilities available in Windows 10 and Azure Active Directory. It also requires an MDM service such as Microsoft Intune. These capabilities can be obtained through various editions and subscription programs.

To provide needed Azure Active Directory and MDM functionality, including automatic MDM enrollment and company branding features, one of the following subscriptions is required:

 -  [Microsoft 365 Business subscriptions](https://www.microsoft.com/microsoft-365/business?azure-portal=true).
 -  [Microsoft 365 F1 subscriptions](https://www.microsoft.com/microsoft-365/enterprise/firstline?azure-portal=true).
 -  [Microsoft 365 Academic A1, A3, or A5 subscriptions](https://www.microsoft.com/education/buy-license/microsoft365/default.aspx?azure-portal=true).
 -  [Microsoft 365 Enterprise E3 or E5 subscriptions](https://www.microsoft.com/microsoft-365/enterprise?azure-portal=true), which include all Windows 10, Microsoft 365, and EM+S features (Azure AD and Intune).
 -  [Enterprise Mobility + Security E3 or E5 subscriptions](https://www.microsoft.com/cloud-platform/enterprise-mobility-security?azure-portal=true), which include all needed Azure AD and Intune features.
 -  [Intune for Education subscriptions](/intune-education/what-is-intune-for-education), which include all needed Azure AD and Intune features.
 -  [Azure Active Directory Premium P1 or P2](https://azure.microsoft.com/services/active-directory/?azure-portal=true) and [Microsoft Intune subscriptions](https://www.microsoft.com/cloud-platform/microsoft-intune?azure-portal=true) (or an alternative MDM service).

The following subscriptions are also recommended, but not required:

 -  [Microsoft 365 Apps for enterprise](https://www.microsoft.com/p/office-365-proplus/CFQ7TTC0K8R0?azure-portal=true) (formerly Office 365 Pro Plus), which can easily be deployed through Intune (or other MDM services).
 -  [Windows Subscription Activation](/windows/deployment/windows-10-enterprise-subscription-activation), to automatically upgrade devices from Windows 10 Pro to Windows 10 Enterprise.

### Configuration requirements

Before Windows Autopilot can be used, the following configuration tasks must be completed to support the common Autopilot scenarios:

 -  **Configure Azure Active Directory automatic enrollment.** For Microsoft Intune, see [Enable Windows 10 automatic enrollment](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment?azure-portal=true) for details. If using a different MDM service, contact the vendor for the specific URLs or configuration needed for those services.
 -  **Configure Azure Active Directory custom branding.** Organizations can display a company-specific sign-in page during the Autopilot process. To do so, Azure AD must be configured with the images and text that should be displayed. For more information, see [Quickstart: Add company branding to your sign-in page in Azure AD](/azure/active-directory/fundamentals/customize-branding). Key elements for Autopilot are the "square logo," "sign in page text," and the Azure AD tenant name (configured separately in the Azure AD tenant properties).
 -  **Enable Windows Subscription Activation.** To automatically upgrade from Windows 10 Pro to Windows 10 Enterprise, you must enable Windows Subscription Activation.

Specific scenarios may also have other requirements. Generally, there are two tasks that must be completed:

 -  **Device registration.** Devices must be added to Windows Autopilot to support most Windows Autopilot scenarios.
 -  **Profile configuration.** Once devices have been added to Windows Autopilot, a profile of settings must be applied to each device.

**Additional reading.** For a list of OEMs that currently support Windows Autopilot, see the **Participant device manufacturers** section at [Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”