Upgrading devices to a new operating system has traditionally been a challenging, complex, and slow process. It can be very time consuming to discover used apps and drivers and then test them for potential compatibility issues. With Windows 10 versions being released twice per year, it's important that organizations verify apps and driver compatibility with new Windows 10 versions on an ongoing basis.

With Upgrade Readiness, Microsoft provides the tools to plan and manage the upgrade process from start to finish and adopt new Windows versions faster. Windows Upgrade Readiness supports upgrade management from Windows 7 and Windows 8.1 to Windows 10. It also supports Windows 10 upgrades in the Windows as a service (WaaS) servicing model.

Upgrade Readiness collects system, application, and driver data for analysis. It then identifies compatibility issues that can block an upgrade and suggest known fixes. Apps are automatically segmented and grouped so that you don’t have to review them one by one. Upgrade Readiness enables an organization to see which apps:

 -  are most widely used.
 -  are supported on Windows 10 by their software vendor.
 -  are considered low risk for compatibility problems.

Based on this information, an organization can focus on critical apps first and start resolving any issues that could block the upgrade. This automated process is the same for evaluating driver compatibility. It also enables you to focus on important device drivers for which Windows 10 compatibility information isn't yet available.

### Benefits of the Upgrade Readiness solution

The Upgrade Readiness solution provides:

 -  a visual workflow that guides organizations from pilot to production.
 -  detailed computer and application inventory.
 -  powerful computer level search and drill-downs.
 -  guidance and insights into application and driver compatibility issues, with suggested mitigations.
 -  data-driven application rationalization tools.
 -  application usage information, allowing targeted validation and workflow to track validation progress and decisions.
 -  data exported to CSV format and integration with Configuration Manager.

An organization can use Upgrade Readiness to:

 -  schedule and work through application and driver issues.
 -  assign and track issue resolution status.
 -  identify computers that are ready to upgrade.
 -  deploy Windows with confidence, knowing that it's addressed potential blocking issues.
    
     -  Based on devices’ diagnostic data, Upgrade Readiness identifies apps and driver compatibility issues that may block Windows upgrades. This information enables an organization to make data-driven decisions about its upgrade readiness.
     -  Information in Upgrade Readiness is refreshed daily so that an organization can monitor its upgrade progress. Any changes that it makes, such as assigning app importance and marking apps as ready to upgrade, are reflected in Upgrade Readiness within 24 hours.

### Upgrade workflow

When organizations are ready to begin the upgrade process, Upgrade Readiness provides a workflow to guide them through critical high-level upgrade tasks.

Each step in the workflow is enumerated and shown on the separate blue tile. Useful information and data are provided on white tiles to help an organization get started, to monitor its progress, and to complete each step.

The following information and workflow is provided:

 -  **Upgrade overview**. This view displays:
    
     -  the total count of devices that are sharing diagnostic data with Microsoft.
     -  the number of upgraded devices.
     -  the number of discovered apps.
     -  when the status was last updated.
     -  the target OS version to which you would like to upgrade your devices.
 -  **Step 1: Identify important apps**. This view displays apps, grouped by importance level. You can set the importance level for the applications, which enables you to rank applications for upgrade.
 -  **Step 2: Resolve issues**. This view reports app and driver inventor. It displays:
    
     -  which apps have known issues.
     -  which apps have no known issues.
     -  which drivers have issues.
     -  which apps and drivers need attention.
     -  suggestions on how to mitigate the issue if information about the issue is available.
    
    <br>:::image type="content" source="../media/upgrade-workflow-identify-resolve-8dc2a14f.jpg" alt-text="screenshot of the workflow showing the critical high-level upgrade tasks for the first two steps, Identify and Resolve Issues" lightbox="../media/upgrade-workflow-identify-resolve-8dc2a14f.jpg":::
    <br>

 -  **Step 3: Deploy**. After you've worked through compatibility testing, you can see the list of devices that are ready to upgrade. You can list the devices or export their list in a CSV file that can be imported to your management tool.<br><br>:::image type="content" source="../media/upgrade-workflow-deploy-29ebbe23.jpg" alt-text="screenshot of Step 3 (Deploy) in the workflow":::
    <br><br>
 -  **Step 4: Monitor**. You can use this view to monitor the deployment progress. It displays:
    
     -  the number of upgraded devices.
     -  the number of failed upgrades.
     -  the number of devices for which the upgrade process hasn't begun.
     -  driver issues during an upgrade.
     -  user feedback.
    
    <br>:::image type="content" source="../media/upgrade-workflow-monitor-fd933c4e.jpg" alt-text="screenshot of Step 4 (Monitor) in the workflow" lightbox="../media/upgrade-workflow-monitor-fd933c4e.jpg":::
    <br>

> [!NOTE]
> You can integrate Upgrade Readiness with Configuration Manager. By doing so, the list of devices that are ready for the upgrade is automatically displayed in Configuration Manager.

**Additional reading.** For more information, see [Upgrade Readiness](/windows/deployment/upgrade/use-upgrade-readiness-to-manage-windows-upgrades).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”