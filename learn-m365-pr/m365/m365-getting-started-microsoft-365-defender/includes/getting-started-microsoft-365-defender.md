Before you can use Microsoft 365 Defender, you need to set up and configure your environment. Once enabled, Microsoft 365 Defender can use incident, automation, and hunting data within the scope of the deployed products. If Defender for Endpoint, Defender for Identity, or Defender for Office 365 are not deployed, Microsoft 365 Defender will not display any data from that product and will be unable to take any action in those areas.

Here, you'll learn about the licensing, hardware and software requirements, and other configuration settings to provision and use Microsoft 365 Defender in your organization.

## Getting Started

Preparation is key to any successful deployment. Getting started with Microsoft 365 Defender requires only a few steps. First, you’ll need to turn on the service by making sure you have the right license in place, and roles are assigned so that you can access the portal.

Next, you'll need to deploy the supported services that come with Microsoft 365 Defender, for example Microsoft Defender for Endpoint, or Microsoft Defender for Identity. These services increase your visibility of threat signals from assets across your network.

### Check Licenses

A license to a Microsoft 365 security product generally entitles you to use Microsoft 365 Defender in Microsoft 365 Defender portal without extra licensing cost.

For detailed licensing information, [read the licensing requirements](/microsoft-365/security/defender/prerequisites?view=o365-worldwide#licensing-requirements&preserve-view=true).

### Check roles and permissions

To enable Microsoft 365 Defender, you  must be a global administrator or a security administrator in your organization’s Azure Active Directory.

Accounts assigned the following Azure Active Directory (AD) roles can access Microsoft 365 Defender functionality and data:

- Global administrator
- Security administrator
- Security Operator
- Global Reader
- Security Reader

> [!NOTE]
> Role-based access control settings in Microsoft Defender for Endpoint influence access to data. For more information, read about managing access to Microsoft 365 Defender.

## Deploying supported services

Microsoft 365 Defender aggregates data from the various supported services that you've already deployed. It will process and store data centrally to identify new insights and make centralized response workflows possible. It does this without affecting existing deployments, settings, or data associated with the integrated services.

To get the best protection and optimize Microsoft 365 Defender, you should deploy all applicable supported services on your network.

For more information on deploying supported services, see the [deploy threat protection page](/microsoft-365/solutions/deploy-threat-protection?view=o365-worldwide&preserve-view=true).

The supported security services are:

- **Microsoft Defender for Endpoint** – Endpoint protection suite built around powerful behavioral sensors, cloud analytics, and threat intelligence.
- **Microsoft Defender for Office 365** – Advanced protection for your apps and data in Office 365, including email and other collaborations tools like Microsoft Teams.
- **Microsoft Defender for Identity** – Defend against advanced threats, compromised identities, and malicious insiders.
- **Microsoft Cloud App Security** – Identify and combat cyberthreats across your Microsoft and third-party cloud services.

When deploying the supported security services, there are typically two approaches:

- Full Deployment
- Limited Deployment

### Full deployment

To gain the complete benefits of Microsoft 365 Defender, your security team should roll out all supported services. Here are some of the key benefits of full deployment:

- Incidents are identified and correlated based on alerts and event signals from all available sensors and service-specific analysis capabilities.
- Automated investigation and remediation (AIR) playbooks apply across various entity types, including devices, mailboxes, and user accounts.
- A more comprehensive advanced hunting schema can be queried for event and entity data from devices, mailboxes, and other entities.

### Limited deployment

Each supported service that you deploy provides a rich set of raw signals and correlated information. While limited deployment doesn’t cause Microsoft 365 Defender functionality to turn off, its ability to provide comprehensive visibility across your endpoints, apps, data, and identities are affected. At the same time, any remediation capabilities only apply to entities that can be managed by the services you’ve deployed.

### Preferred Deployment Sequence

Regardless of which deployment path you choose, and which services your organization chooses to roll out, there is a preferred order you should configure them in. This list assumes a full deployment, so you’ll need to adapt it to meet the services needed.

1. Microsoft Defender for Office 365
1. Microsoft Defender for Identity
1. Microsoft Cloud App Security
1. Microsoft Defender for Endpoint
