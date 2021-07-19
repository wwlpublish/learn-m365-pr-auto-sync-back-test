Microsoft defines resilience as "the ability of a business process or service to meet customer expectations in the face of faults and challenges to normal operations." At the scale of Microsoft 365, resilience is crucial for maintaining the availability of our online services. We build our services to be resilient because we know that:

- **Hardware will fail.** Assume a Mean Time Before Failure (MTFB) of 100,000 hours for a hard drive. For a single hard drive, this seems like a manageable one failure every 11.5 years. But if you have 10,000,000 hard drives, that comes to one failure roughly every 30 seconds. Resilience against the failure of common hardware components is a key feature of how we design and build our online services.
- **Humans will make mistakes.** Assume a human in a typical IT implementation performs 100 operations per day in a system of 100 servers. At 99% accuracy, that is still one mistake per day. Scaled to 250,000 servers, this is 2500 mistakes per day.
- **Software will have bugs.** Software updates must be deployed continuously to keep services up to date. Resilient services must protect themselves from both new and previously undiscovered bugs in software.

We respond to these challenges by using Microsoft's hyper-scale cloud and employing service automation to make our services resilient against multiple failure modes.

![A graphic representation of engineering for resilience principles - active/active service design, fault isolation, reduced blast radius, and continuous improvement](../media/engineering-resilience-principles.png)

## Active/Active service design

Wherever possible, we ensure our services are designed and deployed with Active/Active resiliency. This means that if a critical component of the service fails, an identical component is available to take over without a loss of availability. Active/Active deployments replace older Active/Passive models, in which Passive components took time to take over the workload if Active components failed, temporarily disrupting service availability and data integrity. Active/Active service design represents a significant improvement over other deployment models and provides resilience against many kinds of service failures.

## Fault isolation

Fault isolation increases service resilience by preventing faults in one component from causing other components to fail. Fault isolation complements Active/Active service design by reducing the scope required for automated recovery from component failures. Microsoft 365 works continuously to reduce the size of fault-zones in our services to prevent failures from spreading and impacting other system components.

Some of the strategies we use for fault isolation are:

- **Fine-grained fault control within and between service components:** For example, Exchange Online Database Availability Groups limit the impact of failures within the service to specific availability groups.
- **Multi-protocol management for service availability:** For example, an incident affecting access to files in Teams can be mitigated by file accessibility via SharePoint Online.
- **Regionalization and granular system design:** Our service design separates logical and physical service infrastructure into ever-smaller units. This enables us to respond appropriately to incidents based on their scope using the flexibility of both small- and large-scale service management.
- **Load-balancing and throttling:** Our services routinely shuffle traffic and data between system components as part of normal service operation. Non-essential service-side traffic is throttled in favor of critical traffic like mail delivery. This allows our systems to automatically prioritize critical services in the event of a component failure or service incident.

## Reduced blast radius

Closely related to fault isolation is the concept of an incident's "blast radius." When an incident occurs, the blast radius refers to how broadly the incident impacts our online services. Microsoft works constantly to reduce the blast radius of potential incidents. When an incident response post-mortem uncovers a type of incident with an unacceptable blast radius, we respond by investing in service updates designed to reduce the impact of similar incidents in the future.

## Continuous improvement

When incidents occur, our incident response process ensures each incident is managed to resolution. We use standardized metrics to track the impact of incidents on service availability and performance. Incidents with significant impact to customers are subjected to a Post-Incident Review. Key findings and mitigations resulting from the Post-Incident Review are posted to the Service Health Dashboard for impacted customers to view.

Post-Incident Reviews help to identify resiliency improvements that might prevent or limit the scope of similar issues in the future. Lessons learned from incidents are shared across service teams, so each team can implement improvements without directly experiencing a similar incident.

## Learn more

- [Microsoft 365 Service Resilience and Customer Guidance](https://aka.ms/M365ServiceResilienceGuidance?azure-portal=true)
- [Data Resiliency in Microsoft 365](/office365/Enterprise/office-365-data-resiliency-overview?azure-portal=true)
