You can apply both application and Windows operating system updates in a number of ways. For single computers and smaller networks, you might decide to implement updates on a reactive basis and by using a process that requires either a local user or administrator to initiate the updates manually.

For many computers in larger networks, the reactive manual approach is too time-consuming. Administrators of larger networks will most likely opt to use an automated method for distributing updates for Windows operating systems, devices, and installed applications.

You can automate the update process in several ways, as identified in the following table.

:::row:::
  :::column:::
    **Method**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Windows Update
  :::column-end:::
  :::column:::
    This option provides software updates that keep your computer up-to-date and protected. On the Windows Update page, you can review the important and optional updates that are available for your computer. You can configure Windows Update to download and install updates for your computer automatically, or you can install updates manually. As discussed earlier, your computer will use one of the servicing options. Windows Update downloads your computer’s updates in the background while you’re online. If your internet connection is interrupted before an update downloads fully, the download process resumes when the connection becomes available.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Windows Server Update Services (WSUS)
  :::column-end:::
  :::column:::
    This option is a server role included in the Windows Server operating system that downloads and distributes updates to Windows clients and servers. WSUS can obtain updates that are applicable to the Windows operating system, and common Microsoft programs such as the Microsoft Office suite, and Microsoft SQL Server.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Windows Update for Business
  :::column-end:::
  :::column:::
    This option can be compared to a Microsoft-hosted cloud-based WSUS. Windows Update for Business is free for devices that run Windows Pro or Windows Enterprise operating systems.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Endpoint Configuration Manager
  :::column-end:::
  :::column:::
    This option performs many configuration management–based tasks in an enterprise, including update management. You can use Configuration Manager to incorporate WSUS into your configuration management environment, and to provide greater control over update scheduling, deployment, and reporting. You can also deploy non-Microsoft updates with Configuration Manager.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Microsoft Intune
  :::column-end:::
  :::column:::
    One Intune feature is central update management, with which you can send out updates. Updates can include Windows operating systems and non-Microsoft updates for non-Microsoft apps. Intune also provides you with reports that inform you about which updates the clients require, which updates are pending, and which updates are already installed. Windows updates are made available automatically through Intune, as soon as they’re released to Windows Update. However, with non-Microsoft updates, you must obtain and upload the updates to Intune cloud storage before you can approve and deploy them to client computers.
  :::column-end:::
:::row-end:::
