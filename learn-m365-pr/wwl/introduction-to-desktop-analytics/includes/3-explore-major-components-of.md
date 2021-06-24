Desktop Analytics is a free, cloud-based service that provides data driven insights, or analytics, about your devices. You can view Desktop Analytics reports in a web browser. Those reports help you to:

 -  detect problems.
 -  monitor device health.
 -  remediate issues across the devices that you administer.
 -  evaluate devices before upgrading them to Windows 10, which keep them up-to-date and secure.

Desktop Analytics includes three different views, called solutions, that can be used individually or in any combination:

 -  **Upgrade Readiness.** As organizations plan and manage the upgrade process, this solution uses diagnostic data to identify and resolve application and driver compatibility issues. Once an organization's devices are up to date on Windows 10, Upgrade Readiness becomes a key tool for itsWindows servicing process. This process continually provides these insights, which enable organizations to test and deploy Windows 10 Semi-Annual Channel feature updates faster.

 -  **Update Compliance.** This solution provides a unified view of Windows Update and Antivirus (AV) status of an organization's Windows 10 devices. This view help keeps the devices secure and up-to-date, regardless of the management solution the organization uses. Windows Update diagnostic data provides immediate visibility into which devices are missing critical Windows security updates. It also assesses protection and threat device status, and tracks deployment progress so you can troubleshoot issues as they arise.

 -  **Device Health.** This solution is designed to help organizations monitor and proactively maintain devices. Device Health uses data to identify and report common device performance and reliability problems that users may experience. This tool enables organizations to resolve the issues quickly and efficiently. By pinpointing disruptive issues like kernel crashes or third-party driver issues, Device Health data provides insight into the scope and scale of an issue. In doing so, organizations can focus on mitigation and remediation over investigation. Proactive monitoring of device health and performance saves organizations time and effort by reducing support calls and improving users’ productivity.

If an organization wants to start using Desktop Analytics, it must first create a free Azure Log Analytics workspace. This workspace provides the organization with a Commercial ID value, which it should deploy to all Windows devices that it wants to begin monitoring in Desktop Analytics. A Commercial ID value can be deployed through various methods, including a script, Group Policy, MDM, or a management tool such as Configuration Manager. Desktop Analytics doesn't require any type of client.

:::image type="content" source="../media/desktop-analytics-solutions-8665a115.jpg" alt-text="graphic displaying the three solutions in Windows Analytics that displays the key components of each" lightbox="../media/desktop-analytics-solutions-8665a115.jpg":::


Desktop Analytics has following requirements:

:::row:::
  :::column:::
    

**Desktop Analytics solution**


  :::column-end:::
  :::column:::
    

**Windows license requirements**


  :::column-end:::
  :::column:::
    

**Windows version requirements**


  :::column-end:::
  :::column:::
    

**Minimum diagnostic data requirements**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Upgrade Readiness


  :::column-end:::
  :::column:::
    

No other requirements


  :::column-end:::
  :::column:::
    

Windows 7 with Service Pack 1, Windows 8.1, Windows 10


  :::column-end:::
  :::column:::
    

Basic level in most cases. Enhanced level to support Windows 10 app usage data and site discovery.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Update Compliance


  :::column-end:::
  :::column:::
    

No other requirements


  :::column-end:::
  :::column:::
    

Windows 10


  :::column-end:::
  :::column:::
    

Basic level.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Device Health


  :::column-end:::
  :::column:::
    

Windows 10 Enterprise


  :::column-end:::
  :::column:::
    

Windows 10


  :::column-end:::
  :::column:::
    

For Windows 10 version 1709 or later: Enhanced (Limited). For earlier versions: Enhanced.


  :::column-end:::
:::row-end:::
