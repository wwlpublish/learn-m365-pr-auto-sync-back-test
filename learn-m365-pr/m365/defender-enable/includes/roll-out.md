Before you can use Microsoft 365 Defender, you need to set up and configure your environment. Once enabled, Microsoft 365 Defender can use incident, automated investigation and remediation, and advanced hunting capabilities within the scope of the deployed products. If Defender for Endpoint, Defender for Identity, or Defender for Office 365 are not deployed, Microsoft 365 Defender will not display any data from that product and will be unable to take any action in those areas. Before you can roll out Microsoft 365 Defender, you'll need to learn about the licensing, hardware and software requirements, and other configuration settings to provision and use Microsoft 365 Defender in your organization.

## Getting started

Preparation is key to any successful deployment. To get started with Microsoft 365 Defender, you'll first need to verify that you have the right licenses and permissions to access the portal.

Next, you'll need to deploy the supported services that come with Microsoft 365 Defender, for example, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, or Microsoft Defender for Identity. These services increase your visibility of threat signals from assets across your network.

### Check licenses

A license to a Microsoft 365 security product typically entitles you to use Microsoft 365 Defender in the Microsoft 365 Defender portal without extra licensing cost.

For detailed licensing information, [read the licensing requirements](/microsoft-365/security/defender/prerequisites).

### Check roles and permissions

To enable Microsoft 365 Defender, you must be a global administrator or a security administrator in your organization's Azure Active Directory (Azure AD).

Accounts assigned the following Azure AD roles can access Microsoft 365 Defender functionality and data:

- Global administrator
- Security administrator
- Security Operator
- Global Reader
- Security Reader

> [!NOTE]
> Role-based access control settings in Microsoft Defender for Endpoint influence access to data. For more information, read about [managing access to Microsoft 365 Defender](/microsoft-365/security/defender/m365d-permissions).

## Deploying supported services

Microsoft 365 Defender aggregates data from the various supported services that you've already deployed. It will process and store data centrally to identify new insights and make centralized response workflows possible. It does this without affecting existing deployments, settings, or data associated with the integrated services.

To get the best protection and optimize Microsoft 365 Defender, you should deploy all applicable supported services on your network.

For more information on deploying supported services, see the [deploy threat protection page](/microsoft-365/solutions/deploy-threat-protection).

The supported security services are:

- **Microsoft Defender for Endpoint** – Endpoint protection suite built around powerful behavioral sensors, cloud analytics, and threat intelligence.
- **Microsoft Defender for Office 365** – Advanced protection for your apps and data in Office 365, including email and other collaborations tools like Microsoft Teams.
- **Microsoft Defender for Identity** – Defend against advanced threats, compromised identities, and malicious insiders.
- **Microsoft Cloud App Security** – Identify and combat cyber threats across your Microsoft and third-party cloud services.

When deploying the supported security services, there are typically two approaches:

- Full deployment
- Limited deployment

### Full deployment

To gain the complete benefits of Microsoft 365 Defender, your security team should roll out all supported services. Here are some of the key benefits of full deployment:

- Incidents are identified and correlated based on alerts and event signals from all available sensors and service-specific analysis capabilities.
- Automated investigation and remediation (AIR) actions apply across various entity types, including devices, mailboxes, and user accounts.
- A more comprehensive advanced hunting schema can be queried for event and entity data from devices, mailboxes, and other entities.

### Limited deployment

Each supported service that you deploy provides a rich set of raw signals and correlated information. While limited deployment doesn't cause Microsoft 365 Defender functionality to turn off, its ability to provide comprehensive visibility across your endpoints, apps, data, and identities are affected. At the same time, any remediation capabilities only apply to entities that can be managed by the services you've deployed.

### Preferred Deployment Sequence

Regardless of which deployment path you choose and which services your organization chooses to roll out, there is a preferred order you should configure them. This list assumes a full deployment, so you'll need to adapt it to meet the services you need.

1. Microsoft Defender for Office 365
1. Microsoft Defender for Identity
1. Microsoft Cloud App Security
1. Microsoft Defender for Endpoint

#### Deploy the services

Deploying each service typically requires provisioning to your tenant and some initial configuration. See the following table to understand how each of these services is deployed.

|Service|Provisioning instructions|Initial configuration|
|-|-|-|
|Microsoft Defender for Endpoint|[Microsoft Defender for Endpoint deployment guide](/microsoft-365/security/defender-endpoint/deployment-phases)|See provisioning instructions|
|Microsoft Defender for Office 365|None, provisioned with Office 365|[Configure Microsoft Defender for Office 365 policies](/microsoft-365/security/office-365-security/defender-for-office-365)|
|Microsoft Defender for Identity|[Quickstart: Create your Microsoft Defender for Identity instance](/defender-for-identity/install-step1)|See provisioning instructions|
|Microsoft Cloud App Security|None|[Quickstart: Get started with Microsoft Cloud App Security](/cloud-app-security/getting-started-with-cloud-app-security)|
