In cloud environments, customers and cloud service providers share the responsibility for achieving a compliant and secure computing environment. Microsoft uses [a shared responsibility model](/azure/security/fundamentals/shared-responsibility?azure-portal=true) to define security and operational accountability in Microsoft 365 services. While Microsoft 365 secures the underlying cloud infrastructure and services, customers need to be aware of their responsibilities for ensuring a secure tenant environment for their users and data.

> [!NOTE]
> Microsoft Secure Score provides customers with clear analysis of their tenant configuration and makes actionable suggestions for improving security. We encourage every customer to use self-assessment tools like Microsoft Secure Score to ensure that our shared responsibilities for security and privacy are met.

At Microsoft, we use a Defense-in-Depth approach to secure our services by applying security protections at multiple layers. Defense-in-Depth provides overlapping safeguards to protect against security threats. While we build our services with security in mind, we also prepare our services for the possibility of compromise using an Assume Breach strategy. Assume Breach limits the trust placed in applications, services, identities, and networks by approaching them all—internal and external—as insecure and already compromised. The principles of Assume Breach help to limit the impact of security incidents by reducing the damage an adversary can cause and enabling rapid detection and response to security threats.

In this module, we will focus on how Microsoft 365 investigates, manages, and responds to security threats to protect customers in the Microsoft 365 cloud environment.
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wI1J]

## What is a security incident?

Microsoft defines a security incident in its online services as a confirmed breach of security leading to the accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to customer data or personal data while being processed by Microsoft. For example, unauthorized access to Microsoft 365 infrastructure systems and exfiltration of customer data constitutes a security incident, while compliance events that do not affect confidentiality, integrity, or availability of services or customer data are not considered security incidents.

Whenever there is a security incident, Microsoft 365 strives to respond quickly and effectively to protect Microsoft 365 services and customer data. Microsoft's customer notification commitments are detailed in the [Microsoft Online Services Data Protection Addendum](https://www.microsoft.com/licensing/product-licensing/products):

*If Microsoft becomes aware of a breach of security leading to the accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to Customer Data or Personal Data while processed by Microsoft (each a "Security Incident"), Microsoft will promptly and without undue delay (1) notify Customer of the Security Incident; (2) investigate the Security Incident and provide Customer with detailed information about the Security Incident; (3) take reasonable steps to mitigate the effects and to minimize any damage resulting from the Security Incident.*

## Federated incident response at Microsoft

To effectively respond to security incidents, Microsoft employs a federated security incident response model. All major online service teams, such as Exchange Online, SharePoint Online, Microsoft Teams, and Azure Active Directory, have dedicated security teams with specialized engineering skills. At the same time, each team adheres to a shared incident management process, shared definitions, and shared training to provide consistency across all online services.

The Microsoft 365 Security Response team provides service teams with centralized security expertise and incident response guidance as part of our federated security response model. Depending on the nature of the incident, the Microsoft 365 Security Response team and service teams may engage security partners and subject matter experts from other organizations within Microsoft for investigative assistance, such as:

- Microsoft Threat Intelligence Center – for investigative support and threat intelligence support
- Microsoft Core Engineering Digital Security & Risk Engineering – for investigative assistance with incidents involving Microsoft corporate assets and networks
- Microsoft Security Response Center – for support on externally reported vulnerabilities and Software and Services Incident Response
- Microsoft Corporate, External, Legal Affairs – for legal insight and guidance regarding security incident investigations
- O365 Trust Privacy team – for guidance on regulatory requirements, compliance, and privacy
- C&AI Security – for technical assistance in investigations within the hosting environment
- Microsoft 365 Customer Experience team – for supporting tenant escalations from Customer Service and Support Group and other sources

## Incident response in Microsoft 365

Within Microsoft 365, responsibilities for security incident response are shared between the Microsoft 365 Security Response team and each Microsoft 365 service team. The Microsoft 365 Security Response team coordinates with service teams to implement our enterprise-wide incident response strategy while leveraging service team expertise.

Our incident response strategy, which is based on the NIST 800-61 response management phases, proceeds through four phases of interconnected activity: preparation; detection and analysis; containment, eradication, and recovery; and post-incident activity.

:::image type="content" source="../media/assurance-sim-phases.png" alt-text="A visual diagram of NIST phases" border="false":::

Each phase of the response management process is important for effective incident response.

## Learn more

- [Shared Responsibilities for Cloud Computing](/azure/security/fundamentals/shared-responsibility?azure-portal=true)
- [National Institute of Standards and Technology (NIST) Special Publication (SP) 800-61](https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final?azure-portal=true)
- [Microsoft Secure Score](/microsoft-365/security/mtp/microsoft-secure-score-new?azure-portal=true)
- [Microsoft 365 security incident management](/compliance/assurance/assurance-security-incident-management?azure-portal=true)
