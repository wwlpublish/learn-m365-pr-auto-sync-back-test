As an alternative to using WSUS, organizations implementing Windows can use Windows Update for Business. Windows Update for Business enables commercial customers to manage which Windows Updates are received when, as well as the experience a device has when it receives them.

Windows Update for Business enables information technology administrators to keep the Windows devices in their organization always up to date with the latest security defenses and Windows features by directly connecting these systems to Windows Update service. You can use Group Policy or MDM solutions such as Intune to configure the Windows Update for Business settings that control how and when Windows devices are updated. In addition, by using Intune, organizations can manage devices that are not joined to a domain at all or are joined to Microsoft Azure Active Directory (Azure AD) alongside your on-premises domain-joined machines.

Specifically, Windows Update for Business lets you control update offerings and experiences to allow for reliability and performance testing on a subset of devices before deploying updates across the organization. It also provides a positive update experience for people in your organization.

Specifically, Windows Update for Business allows for:

 -  The creation of deployment rings, where administrators can specify which devices go first in an update wave, and which ones will come later (to ensure any quality bars are met).
 -  Selectively including or excluding drivers as part of Microsoft-provided updates.
 -  Integration with existing management tools such as Windows Server Update Services (WSUS), Configuration Manager, and Microsoft Intune.
 -  Peer-to-peer delivery for Microsoft updates, which optimizes bandwidth efficiency and reduces the need for an on-site server caching solution.

Windows Update for Business provides the following types of updates in Windows:

 -  **Feature Updates**. Previously referred to as upgrades, Feature Updates contain not only security and quality revisions, but also significant feature additions and changes. Starting with version 21H2, they are now released annually.
 -  **Quality Updates**. these are traditional operating system updates, typically released the second Tuesday of each month (though they can be released at any time). These include security, critical, and driver updates. Windows Update for Business also treats non-Windows updates (such as those for Microsoft Office or Visual Studio) as Quality Updates. These non-Windows Updates are known as Microsoft Updates and devices can be optionally configured to receive such updates along with their Windows Updates.
 -  **Driver updates**. Updates for non-Microsoft drivers that are relevant to your devices. Driver updates are on by default, but you can use Windows Update for Business policies to turn them off if you prefer.
 -  **Microsoft product updates**. Updates for other Microsoft products, such as versions of Office that are installed by using Windows Installer (MSI). Versions of Office that are installed by using Click-to-Run can't be updated by using Windows Update for Business. Product updates are off by default. You can turn them on by using Windows Update for Business policies.

### Defer an update

A Windows Update for Business administrator can defer the installation of both feature and quality updates from deploying to devices within a bounded range of time from when those updates are first made available on the Windows Update service. You can use this deferral to allow time to validate deployments as they are pushed to devices. Deferrals work by allowing you to specify the number of days after an update is released before it is offered to a device. That is, if you set a feature update deferral period of 365 days, the device will not install a feature update that has been released for less than 365 days. To defer feature updates, use the **Select when Preview Builds and feature updates are received** policy.

:::row:::
  :::column:::
    **Category**
  :::column-end:::
  :::column:::
    **Maximum deferral period**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Feature updates
  :::column-end:::
  :::column:::
    365 days
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Quality updates
  :::column-end:::
  :::column:::
    30 days
  :::column-end:::
:::row-end:::
