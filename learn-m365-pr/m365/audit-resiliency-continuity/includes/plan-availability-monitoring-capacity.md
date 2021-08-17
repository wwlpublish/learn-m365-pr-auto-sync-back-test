Even the most resilient online services require adequate resources to run effectively. This is particularly true during emergency situations when unexpectedly high demand has the potential to impact the availability of Microsoft 365 Services. Microsoft 365 uses extensive availability monitoring and frequent capacity planning to ensure our services remain available to our customers even during emergency situations.

## Availability monitoring

Microsoft 365 implements extensive availability monitoring to ensure our services have the necessary resources to run optimally. Service teams use automated log and telemetry analysis to alert on-call engineers to availability issues. For example, service teams monitor processor and memory utilization for spikes that might threaten the health of the service. In addition to general availability monitoring,  service teams also select appropriate availability metrics based on the nature of their service. For example, SharePoint Online (SPO) monitors core customer functionality, such as homepage availability and the ability to upload and download documents.

In many cases, our services automatically respond to issues that threaten availability by provisioning extra resources or rerouting traffic to unaffected service components. Service team engineers respond to alerts by investigating and resolving any underlying issues. Availability issues that indicate a potential security incident are escalated to the Microsoft 365 Security Response team for resolution using the security incident response process.

## Capacity planning

Capacity planning helps service teams allocate the resources necessary to support Microsoft 365 service availability. Regular capacity planning is required as part of Microsoft's EBCM program. Service teams review capacity data during quarterly reviews, and during emergency situations that warrant additional capacity review.

The raw data for capacity planning is maintained by each service teams and includes metrics like system processing, memory, and hardware capacity. Scheduled reviews use a model of the system's current capacity and test it against projected needs in emergency situations. If the model indicates gaps in capacity, proposed changes to system capacity are submitted to service team leadership for review. Approved changes are incorporated into a new model before implementation by service team engineers.

As part of capacity planning, each service team designates a Capacity Project Manager (PM), who is responsible for collecting performance data and maintaining accurate models of system capacity. In addition to coordinating quarterly capacity reviews, the Capacity PM serves as the primary point of contact for automated availability monitoring alerts. The Capacity PM ensures appropriate service team personnel are notified so they can respond immediately to address availability issues.

## Learn more

- [SLA commitments for online services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37&azure-portal=true)
- [Microsoft 365 Service Health](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity?azure-portal=true)
- [Capacity Planning and Load Testing in SharePoint Online](/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online?azure-portal=true)
- [Exchange Online (EXO) High Availability](/office365/servicedescriptions/exchange-online-service-description/high-availability-and-business-continuity?azure-portal=true)
