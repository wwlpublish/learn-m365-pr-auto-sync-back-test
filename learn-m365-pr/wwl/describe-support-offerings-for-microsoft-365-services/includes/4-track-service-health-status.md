Knowing the health status of Microsoft 365 services used by an organization is crucial. This will help your organization to, for instance, understand when a specific service will undergo maintenance, so your organization can prepare and minimize the impact on your users and systems.

## View the health status of services

Your organization’s administrators can use the Microsoft 365 admin center to view the current health status of your Microsoft 365 services and tenant, and information about outages or disruptions to services. This makes it possible to quickly check the health status of services to find out whether you’re dealing with a known issue that has a resolution that is being implemented without having to spend time troubleshooting or calling support.

Your administrator’s can use the service health page of the Microsoft 365 admin center to view the health status of each service:

:::image type="content" source="../media/3-service-health.png" alt-text="Screenshot of the service health page, showing all services":::

Your administrators can also report an issue if organization has experiencing service issues. Administrators can also view specific details about service issues to understand what kind of impact an issue is having on the service and the current status of the issue:

:::image type="content" source="../media/3-service-health-advisories.png" alt-text="Screnshot showing the service health, advisories page":::

## Keep track of incidents

A service incident is any event that has an effect on a service. Incidents might occur because of hardware or software failures or issues. Your organization can set up notifications for any new incidents, or notifications for updates to any active incidents that might affect your organization. Microsoft will provide two different types of notifications:

- **Unplanned downtime**: Where an incident has caused a service to become unresponsive or unavailable.
- **Planned maintenance**: Where Microsoft regularly carries out service updates to the software and infrastructure that run services.

Microsoft also analyzes unplanned service incidents for you through Post-Incident Reviews where you’ll receive a preliminary review within the first two days of incident resolution, and a final review within five business days.  Final Post-Incident Reviews will detail the following information:

- How you might have been impacted, and how the user experience was impacted.
- A date and time breakdown detailing when an incident started and when it was resolved.
- An analysis of the root cause, and what actions are to be carried out to prevent the incident in the future.

Your organization can keep track of the health status of services in different ways:

| **Tool**                    | **Description**                                              |
| --------------------------- | ------------------------------------------------------------ |
| **Admin App**               | Your  administrators can use the Admin App to view and stay up to date with the  health status of the services on the go. |
| **Microsoft System Center** | Your administrators  can view all service communications from within System Center if your  organization has the Office 365 Management Pack. |
| **API**                     | Your  organization can use the Office 365 Service Communications API to create or  use tools that can connect and monitor the service status for you in  real-time. |

## Continuity and availability

Microsoft services run on highly resilient infrastructures and systems to keep up peak service demand and performance.  This makes it possible for Microsoft to rapidly recover services from unexpected issues whether they are hardware related issues, software related issues, or even catastrophic issues like natural disasters.

For example, to protect and keep your organization’s data available Microsoft does the following:

- **Data storage redundancy**: Microsoft stores your data through multiple levels of redundancy using data replication and secure data protection capabilities, that make it possible to ensure rapid availability and recovery of your data.
- **Monitoring data**: Your databases are monitored for you. Your data is monitored packet loss, latencies in queries, and more.
- **Preventative measures**: Microsoft regularly carries out checks for database consistency, reviews of error logs, and more.
