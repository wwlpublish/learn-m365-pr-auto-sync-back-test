As with earlier releases of Windows, Windows 10 and later includes support for the deployment of new releases using Windows Update, Windows Server Update Services, Endpoint Manager, and third-party configuration management tools. Because of the importance of the Windows as a Service (WaaS) approach to delivering innovations to businesses, and the proven ability of Windows Update to deploy releases quickly and seamlessly to consumers and small businesses, several of the largest investments in Windows focus on enabling broader use of Windows Update within enterprises.

Although Windows Update greatly simplifies and accelerates update deployment, enterprises are not using Windows Update as broadly as consumers and small businesses. This is largely because Windows Update maintains control over which updates are installed and the timing of installation. This makes it difficult for IT administrators to test updates before deployment in their specific environment.

To help address the concerns of IT administrators, Microsoft released Windows Server Update Services in 2005. Windows Server Update Services enables IT administrators to obtain the updates that Windows Update determines are applicable to the devices in their enterprise, perform additional testing and evaluation on the updates, and select the updates they want to install. Windows Server Update Services also provides IT administrators with an all or nothing way to specify when they want an approved update to be installed. Because IT administrators ultimately select and install most updates identified by Windows Update, the role of Windows Server Update Services in many enterprises is to provide IT administrators with the additional time they need to gain confidence in the quality of updates prior to deployment.

### Servicing Tools

There are many tools with which IT pros can service Windows as a service. Each option has its pros and cons, ranging from capabilities and control to simplicity and low administrative requirements. The following are examples of the servicing tools available to manage Windows as a service updates:

 -  **Windows Update** is a service that provides software updates that keep your computer up to date and protected. In the Settings app, in Update &amp; security, on the Windows Update tab, you can view the updates that are available for your Windows client device. Under Advanced options, you can configure how Windows Update downloads and installs updates for your computer. Generally, you must configure computers that are running Windows to download and install updates automatically to ensure that the computer has the most up-to-date and protected configuration possible. Windows Update also can update non-Microsoft software components including drivers.
    
    > [!NOTE]
    > By default, Windows 10 and later will download and install updates automatically.
 -  **Windows Server Update Services (WSUS)** provides extensive control over Windows updates and is natively available in the Windows Server operating system. In addition to the ability to defer updates, organizations can add an approval layer for updates and choose to deploy them to specific computers or groups of computers whenever ready.
 -  **Windows Update for Business** is the second option for servicing Windows as a service. This servicing tool includes control over update deferment and provides centralized management using either Group Policy or Microsoft Intune. Windows Update for Business can be used to defer updates by up to 365 days, depending on the version. These deployment options are available to clients in the General Availability Channel.
 -  **Configuration Manager** provides the greatest control over servicing Windows as a service. IT pros can defer updates, approve them, and have multiple options for targeting deployments and managing bandwidth usage and deployment times.

With all these options, which an organization chooses depends on the resources, staff, and expertise its IT organization already has. For example, if IT already uses Configuration Manager to manage Windows updates, it can continue to use it. Similarly, if IT is using WSUS, it can continue to use that.

For a consolidated look at the benefits of each tool see the following table:

:::row:::
  :::column:::
    **Servicing Tool**
  :::column-end:::
  :::column:::
    **Can updates be deferred?**
  :::column-end:::
  :::column:::
    **Ability to approve updates**
  :::column-end:::
  :::column:::
    **Peer-to-peer option**
  :::column-end:::
  :::column:::
    **Additional features**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Windows Update**
  :::column-end:::
  :::column:::
    Yes (manual)
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Delivery Optimization
  :::column-end:::
  :::column:::
    None
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Windows Update for Business**
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Delivery Optimization
  :::column-end:::
  :::column:::
    Other Group Policy objects
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **WSUS**
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    BranchCache or Delivery Optimization
  :::column-end:::
  :::column:::
    Upstream/downstream server scalability
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Configuration Manager**
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    BranchCache, Client Peer Cache
  :::column-end:::
  :::column:::
    Distribution points, multiple deployment options
  :::column-end:::
:::row-end:::


For more information on deploying Windows Updates, you can see this link: https://aka.ms/AA60cod

### Rolling Back Upgrades

With Windows, you can roll back an upgrade to the previous Windows operating system version. This can be helpful if unforeseen circumstances occur after updating. There is a default 10-day grace period to roll back to the previous version, however this can be changed with the DISM image tool. When rolling back, any changes will be lost, including installed apps, and it’s recommended that user data be backed up prior to a rollback.

To roll back to the previous version, open the **Settings app**, select the **Update &amp; security** category, and then select **Recovery**. Here, you have the option to go to the previous version.
