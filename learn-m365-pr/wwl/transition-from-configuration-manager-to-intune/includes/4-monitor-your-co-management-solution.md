When you enable Co-management, you specify which devices should be co-managed and which workloads should be moved to Intune. After that you can use the Co-management dashboard in Configuration Manager to provide information about co-management. The dashboard helps you review devices that are co-managed in your environment. It also includes graphs that can help you identify devices that need attention.

You can view the dashboard by completing the following steps:

1.  Open the Configuration Manager console.
2.  Select the **Monitoring** workspace.
3.  In **Monitoring** pane, select **Co-management**.

The co-management dashboard displays the following graphs for your environment:

 -  **Co-managed devices.** This graph displays number of client devices that are managed by Configuration Manager and the percentage of co-managed devices throughout your environment.

:::image type="content" source="../media/co-managed-devices-graph-6d57d711.jpg" alt-text="graph showing number of co-managed devices":::


 -  **Client OS distribution**. This graph shows the number of client devices that are managed by Configuration manage and which operating system (OS) they run. Operating systems are grouped in the following categories:
    
     -  Windows 7 &amp; 8.x
     -  Windows 10 version lower than 1709
     -  Windows 10 version 1709 and newer

    > [!NOTE]
    > Windows 10 version 1709 or newer is required for co-management.

:::image type="content" source="../media/client-os-distribution-chart-43a95980.jpg" alt-text="graph showing distribution of client operating systems in company":::


 -  **Co-management status**. This graph displays the breakdown of device success or failure in the following categories:
    
     -  Success, hybrid Azure AD Joined
     -  Success, Azure AD Joined
     -  Failure: Auto-enrollment failed

    By hovering over a graph category, you'll see the percentage of devices in that category. If you select a graph section, you'll see the list of devices in that category.<br>

 -  **Workload transition**. This graph displays a bar chart with the number of devices that you transitioned to Microsoft Intune for the four available workloads:
    
     -  Compliance Policies
     -  Resource Access
     -  Windows Update for Business
     -  Endpoint Protection

    Hovering over a chart section displays the number of devices transitioned for each workload.

:::image type="content" source="../media/devices-transitioned-per-workload-chart-bce56d50.jpg" alt-text="bar chart showing the number of devices transitioned for each of the four workloads":::
