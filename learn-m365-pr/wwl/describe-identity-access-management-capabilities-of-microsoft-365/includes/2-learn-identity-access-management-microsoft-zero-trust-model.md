Cloud applications and the mobile workforce have redefined the security perimeter. Corporate applications and data are moving from on-premises to hybrid and cloud environments. Now, your employees can bring their own devices to work, and increasingly, they have the capability to work remotely from their own homes. Organizational assets, resources, and data are being accessed outside the corporate network and shared with external collaborators such as partners and vendors.

The physical location of the organization no longer defines the security perimeter; it now extends to every access point that hosts, stores, or accesses corporate resources and services, for example, your staff will expect to work at the airport while they wait for a flight, but instead of a laptop, they might use their tablet or smartphone.

Interactions with organizational resources and services now often bypass on-premises perimeter-based security models that rely on network firewalls and VPNs. Organizations that rely solely on on-premises firewalls and VPNs lack visibility, solution integration, and the agility to deliver timely, end-to-end security coverage.

Today, organizations need a new security model that more effectively adapts to the complexity of the modern environment, embraces the mobile workforce, and protects people, devices, applications, and data wherever they’re located.

## Identity and access management

Identity and access management is the bedrock upon which a secure digital estate is built. The credentials that you issue to your users identify them to Microsoft 365, and when combined with strong authentication methods like Multi-Factor Authentication, can be taken as proof positive that the person using them is whom they claim to be. Once their identity is established through authentication, Access Management takes over, using controls like Conditional Access to further assess the user. It takes into consideration factors such as geographical location, the device they are connecting from, the app they used to make the connection, time of day. All of these are used to decide if the user is authorized to access the requested resource.

Identity is the new central defense and point of control. It secures your organization’s data across multiple applications, locations, and devices while delivering a comprehensive identity and access management strategy.

### Hybrid identity

Hybrid identity uses accounts that originate in an on-premises Active Directory Domain System (AD DS) and have been transferred or copied in the Azure AD tenant of a Microsoft 365 subscription.

When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information. Using Azure AD Connect synchronizes user accounts in Azure AD - Integrating your on-premises directories with Azure AD makes your users more productive by providing a common identity for accessing both cloud and on-premises services.

:::image type="content" source="../media/2-hybrid-identity-concept-v4.png" alt-text="Diagram showing the hybrid identity concept":::

The Azure AD tenant has a copy of the on-premises AD DS accounts. In this configuration, users accessing both on-premises and cloud based services can authenticate against Azure AD.

### Cloud identity

A cloud-only identity uses user accounts that exist only in Azure AD.  While initially adopted by small organizations who had no on-premises capabilities, more and more enterprise organizations are seeing the benefits of moving their entire digital estate, data, apps and resources, into the cloud.

:::image type="content" source="../media/2-cloud-only-concept-v4.png" alt-text="Diagram showing the cloud only identity concept":::

In this configuration, all users use their Azure AD user accounts and passwords to access Microsoft 365 cloud services. Azure AD authenticates user credentials based on its stored user accounts and passwords.
 
## Zero Trust security model

Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes every request is a breach in security, and verifies each request as though it originates from an unsecured network. Wherever the request originates or what resource it accesses, Zero Trust teaches us to “never trust, always verify.”

In a Zero Trust model, every access request is strongly authenticated, authorized within policy constraints, and inspected for anomalies before granting access. Everything from the user’s identity to the application’s hosting environment is used to prevent a breach. We apply micro-segmentation and least privileged access principles to minimize lateral movement. Micro-segmentation is where you create secure zones to separate workloads, each of which can be secured. Finally, rich intelligence and analytics help us identify what happened, what was compromised, and how to prevent it from happening again.

Guiding principles of Zero Trust:

- Verify explicitly. Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies.
- Use the least privileged access. Limit user access with Just-In-Time and Just Enough Access (JIT/JEA), risk-based adaptive policies, and data protection to protect both data and productivity.
- Assume breach. Minimize blast radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and application. Verify all sessions are encrypted end to end. Use analytics to get visibility, drive threat detection, and improve defenses.

Zero Trust shifts the focus of governing access away from the network, to intelligent access controls. These controls take advantage of dynamic user and device risk signals and other telemetry to make more informed access decisions about an organization’s data and resources on a case-by-case basis.

By gating access to individual resources using dynamic trust decisions, organizations can take advantage of fine-grained control to further refine user experience and security assurances.

A Zero Trust model has three aspects.

- It requires *signals* to inform decisions. Zero Trust considers many signal sources, from identity systems to device management and device security tools, to create context-rich insights that help make informed decisions.
- Policies to make access *decisions*. The access requested, and the signal’s analyzed to deliver a decision based on finely tuned access policies, providing granular, organization-centric access control.
- *Enforcement* capabilities to implement those decisions effectively. Decisions are enforced across the entire digital estate, such as read-only access to the SaaS app or remediating compromised passwords with a self-service password reset.
