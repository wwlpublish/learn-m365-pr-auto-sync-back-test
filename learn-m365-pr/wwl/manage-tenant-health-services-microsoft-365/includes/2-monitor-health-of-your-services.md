To access the Health page, log into the Microsoft 365 admin center and then select the Health option in the navigation pane. The Health portal will be displayed, along with all the current services and their availability.

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

The following graphic shows that Microsoft 365 tracks the health of each of its services. In the Health portal, a check mark indicates a healthy status, an X indicates an unavailable service, and an exclamation point indicates a degraded service. For this reason, it's important that organizations constantly monitor the health status of each service.

:::image type="content" source="../media/m365-service-health-d5eaacb0.jpg" alt-text="Graphic showing that Microsoft 365 tracks the health of each of its services. The graphic shows a check mark next to each service, which indicates a healthy status.":::


The table that you access from the **Support** page displays status information for the current day and the previous six days. This table shows the status of each of the online service components, and you can select their status icons for more information.

You can also select **View history** to see further historical service health data. On the **History** page, you can see specific incidents that have occurred within the last 30 days and the categories they fall under, including Microsoft 365 Portal, Identity Service, Skype for Business Online, and Exchange Online.

To see specific incident details, find the incident in the calendar and then select it. Chronological data about the outage or issue and any resolution to the problem will then be displayed. If a post-incident report has published, you can also download or view the report for more details.

The **Service health** page only includes information about the health of your online services; it doesn't cover other items, such as network infrastructure issues.

### Planned maintenance

You can view information about any upcoming Microsoft 365 maintenance tasks in the **Support** page. This page displays the date and time of any planned maintenance, and you can select the link for each maintenance task for more information.

### RSS feeds

Microsoft 365 also provides a link to an RSS feed for Microsoft 365 service health. You can add the feed to your Common RSS Feed List. You can view this feed in programs that use the Common RSS Feed List, such as Microsoft Edge and Outlook. The feed updates each time a new incident event adds or an existing incident event updates.

### System Center Operations Manager

You can use Operations Manager for basic monitoring of Microsoft 365 services, including checking Internet connectivity and service availability. The Operations Manager management pack for Microsoft 365 provides monitoring functionality for all versions of Operations Manager starting with System Center 2012 Operations Manager.

To monitor Microsoft 365 services, you must import the Microsoft 365 management pack for Operations Manager into the System Center. After you add a Microsoft 365 subscription, the management pack enables you to monitor services such as:

 -  Subscription health
 -  Service status
 -  Active and resolved incidents
 -  Message Center
 -  Alerts

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”