Windows 365 is a cloud-based service that automatically creates a new type of Windows virtual machine (Cloud PCs) for your end users. Each Cloud PC is assigned to an individual user and is their dedicated Windows device.

Windows 365 is available in two editions:

 -  **Windows 365 Business**. This edition is made specifically for use in smaller companies (up to 300 seats) who want ready-to-use Cloud PCs with simple management options. There are no licensing prerequisites to set up Windows 365 Business. There are no dependencies on Azure or Active Directory. It's purchased through the Microsoft 365 admin center or the Windows 365 product site.
 -  **Windows 365 Enterprise**. This edition is for larger companies who want unlimited seats for creating Cloud PCs. It includes options to create custom Cloud PCs based on device images that you create, more management options, and full integration with Microsoft Endpoint Manager. It leverages Azure AD and AD DS domains.

### Windows 365 versus Azure Virtual Desktop

Windows 365 and Azure Virtual Desktop are both built on top of the same platform. On the backend, the functionality is essentially the same. They key difference is how they are provisioned and managed. The following table is a general comparison between the two solutions:

:::row:::
  :::column:::
    **Windows 365 Enterprise**
  :::column-end:::
  :::column:::
    **Azure Virtual Desktop**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    VMs manged by Microsoft
  :::column-end:::
  :::column:::
    VM managed by organization
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Easier to set up
  :::column-end:::
  :::column:::
    Requires Azure administration skills
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Managed through Endpoint Manager admin center
  :::column-end:::
  :::column:::
    Managed through Azure portal
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Assigned to individual users
  :::column-end:::
  :::column:::
    Individual or pooled desktops
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Fixed per-user/per-month cost
  :::column-end:::
  :::column:::
    Cost based on Azure usage
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Profiles are stored in the VM instance
  :::column-end:::
  :::column:::
    Uses FSILogix storage solution
  :::column-end:::
:::row-end:::


While setting up AVD has more complexity, because the customer is managing the VMs, it provides the most flexibility. However, not all customers need the level of flexibility that AVD provides. In Windows 365, Microsoft manages the VMs, providing a solution that is relatively simple to set up, with enough flexibility for many organizations. An organization that prefers pooled desktops may deploy or continue to use AVD. Organizations that typically want to assign persistent cloud PCs to users may choose to deploy or migrate to Windows 365.

### Access cloud PCs

Users can navigate to [https://windows365.microsoft.com](https://windows365.microsoft.com/) to access their Cloud PCs, connecting through Remote Desktop.

:::image type="content" source="../media/cloud-personal-computer-gear-04bac88c.png" alt-text="cloudpc-gear.png":::


The Remote Desktop client is available for Windows, macOS, iOS/iPadOS and Android.
