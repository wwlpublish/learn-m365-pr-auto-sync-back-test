You can view the health of your Microsoft services, including Office on the web, Yammer, Microsoft Dynamics CRM, and mobile device management cloud services, on the **Service health** page in the Microsoft 365 admin center. If you're experiencing a problem with a cloud service, you can check the service's health to determine whether the problem is a known issue with a resolution in progress before you call support or spend time troubleshooting.

To access the **Service health** page, log into the Microsoft 365 admin center and then navigate to **Health &gt; Service health** in the navigation pane. The Health portal will be displayed, along with all the current services and their availability.

Each online service’s health will display one of the following statuses:

 -  **Normal service.** This status indicates the service is available and suffered no incidents during the reporting period. The icon for this status doesn't link to any other information.
 -  **Extended recovery.** This status indicates that steps have completed to resolve the service incident. However, it will take an extended period for service operations to return to normal. During this time, some service behaviors might take longer than normal to complete.
 -  **Investigating.** This status indicates that a potential service incident is under investigation.
 -  **Service restored.** This status indicates that an incident was active earlier today, but the service was restored.
 -  **Service interruption.** This status indicates the service isn't functioning, and users can't access the service.
 -  **Additional information.** This status indicates that an incident was active during a previous day. The incident may be resolved, or it may still be active.
 -  **Service degradation.** This status indicates the service is slow or is occasionally unresponsive for brief periods.
 -  **PIR published.** This status indicates that a report of the service incident has been published.
 -  **Restoring service.** This status indicates the service incident is being resolved.

> > [!NOTE]
> > In the unlikely event the Microsoft 365 admin center is unavailable, navigate to the Service Health dashboard. If the issue relates to Azure Active Directory - for example, sign-in issues - refer to the [Azure Status](https://aka.ms/kfxpxv?azure-portal=true) site.

The following graphic shows that Microsoft 365 uses visualizations to display the health of each of its services. In the Health portal:

 -  A check mark indicates a healthy status.
 -  An X indicates an unavailable service.
 -  An exclamation point indicates a degraded service.

Because two out of three statuses are problematic, it's important that organizations constantly monitor the health status of each service.

:::image type="content" source="../media/m365-service-health-d5eaacb0.jpg" alt-text="Graphic showing that Microsoft 365 tracks the health of each of its services. The graphic shows a check mark next to each service, which indicates a healthy status.":::


On the **Service health** page, the health state of each cloud service is shown in a table format.

The **All services** tab (the default view) shows all services, their current health state, and any active incidents or advisories. An icon and status in the **Health** column indicate the state of each service.

If there's an active incident or advisory for a service, they'll be listed directly under the service name in a nested table. You can collapse the nested table to hide the incidents or advisories in this view by clicking on the chevron icon to the left of the service name.

To filter your view to only show all the active incidents, select the **Incidents** tab at the top of the page. Selecting the **Advisories** tab will only show all the active advisories posted.

The **History** tab shows all incidents and advisories that have been resolved within the last 7 or 30 days.

If you're experiencing an issue with a Microsoft 365 service and you don't see it listed on the **Service health** page, you should report it to Microsoft by selecting **Report an issue**, and completing the short form. Microsoft will look at related data and reports from other organizations to see how widespread the issue is. It will also check whether the issue originated with Microsoft's service. If it did, Microsoft will add it as a new incident or advisory on the **Service health** page, where you can track its resolution. The **Reported Issues** page will show all issues your tenant has reported from this form and the status.

To customize your view of which services show up on the dashboard, select **Preferences** &gt; **Custom view**. Then clear the check boxes for the services you want to filter out of your **Service health** dashboard view. Ensure the check box is selected for each service that you want to monitor.

To sign up for email notifications of new incidents that affect your tenant and status changes for an active incident, complete the following steps:

1.  Select **Preferences** &gt; **Email**.
2.  Select **Send me service heath notifications in email**.
3.  Specify:
    
     -  Up to two email addresses.
     -  Whether you want notifications for incidents or advisories.
     -  The services for which you want notification.

You can also subscribe to email notifications for individual events instead of every event for a service. To do so:

1.  Select the active issue you want to receive email notification updates for.
2.  Select **Manage notifications for this issue.**
3.  Specify up to two email addresses.

> [!NOTE]
> Each admin can have their Preferences set and the above limit of two email address is per admin account.

> [!TIP]
> You can also use the Microsoft 365 Admin app on your mobile device to view Service health. The **Service health** page in this app is a great way to stay current with push notifications.

### Planned maintenance

You can view information about any upcoming Microsoft 365 maintenance tasks in the **Support** page. This page displays the date and time of any planned maintenance, and you can select the link for each maintenance task for more information.

### System Center Operations Manager

You can use Operations Manager for basic monitoring of Microsoft 365 services, including checking Internet connectivity and service availability. The Operations Manager management pack for Microsoft 365 provides monitoring functionality for all versions of Operations Manager, starting with System Center 2012 Operations Manager.

To monitor Microsoft 365 services, you must import the Microsoft 365 management pack for Operations Manager into the System Center. After you add a Microsoft 365 subscription, the management pack enables you to monitor services such as:

 -  Subscription health
 -  Service status
 -  Active and resolved incidents
 -  Message Center
 -  Alerts

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”