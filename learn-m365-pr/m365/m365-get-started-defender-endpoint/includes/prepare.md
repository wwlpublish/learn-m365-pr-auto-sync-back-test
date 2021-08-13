To prepare your organization for Microsoft Defender for Endpoint, you'll need to take some considerations into account. These range from people-related processes, to deciding the order in which you want to implement Microsoft Defender for Endpoint's different capabilities.

Here, you'll learn how to prepare for Microsoft Defender for Endpoint by identifying key considerations.

## Identify your stakeholders

Although your project is technology focused, you should also consider the people involved. These stakeholders will range from key individuals who are actively involved with the rollout, to people who simply need to be informed, such as end users.

With your stakeholders and their roles identified, you can then move to reviewing your environment. From the unique endpoints that Microsoft Defender for Endpoint will be managing, to the servers and Security information and event management (SIEM) systems.

There are stakeholder roles that you can use to help you to conceptualize the different responsibilities of stakeholders. These roles include:

- **Chief Information Security Officer (CISO)**
  - The sponsor and senior executive representative. This could be a role that your organizations CTO has. They approve the project and responsible for its success.
- **Security Operations Center**
  - Lead or member of the CDOC team. Responsible for defining how the project aligns to the current security processes. Approves, monitors, and reports on the projects progress to the CISO.
- **Security Architect**
  - A member of the security team in charge of how this project is aligned with your organization's security architecture. Provides input and reviews the outputs from the project.

You can use the **Learn more** section to find out about more roles that you can identify.

With this information, you create a list of individuals who are assigned these roles. You'll then use this contact list throughout the project's lifecycle.

## Assess your environment

Your starting point once, you've identified your pilot users, and therefore endpoint devices, is to gather the list of operating systems and hardware. Create an inventory of the number of desktops, laptops, servers, Windows versions, Linux versions, macOS versions, and mobile (Android and iOS versions) devices that exist in your environment.

With your endpoints recorded, move up through your environment to identify servers, management engines, and finally the SIEM systems you'll be using with Microsoft Defender for Endpoint.

## Decide on your role-based access control structure

You have a choice of two ways to manage the permissions for access and usage to Microsoft Defender for Endpoint.

1. **Basic permissions**: Grant users full access or read-only. You could use Global Administrator, Security Administrator, and Security Reader roles.
1. **Role-based access control (RBAC)**: Create specific roles and groups and assign granular permissions to each of them.

To help you assign the correct level of permissions it's helpful to consider the required access in terms of tiers.

|Tier|Description|Permissions|
|-|-|-|
|1 least access|Local security operations team / IT team|No access|
|2 limited access|Regional security operations team|Read-only view of the data|
|3 most access|Global security operations team|View data, alerts investigations, manage portal and security settings|

## Select the adoption order of Microsoft Defender for Endpoint capabilities

Microsoft Defender for Endpoint has a variety of components and Microsoft has provided a recommended adoption order that you can use to help your organization to gain immediate value when rolling it out.

### 1. Endpoint detection and response

The first and most valuable capability to adopt is Endpoint detection and response (EDR). This enables you to detect, investigate, and respond to advanced threats by correlating behavioral alerts and offering a rich set of response actions. You can also take advantage of advanced hunting by using a querying tool to proactively find breaches and create custom detections.

### 2. Threat and vulnerability management

Once you've enabled EDR, you can begin to use threat and vulnerability management. Threat and vulnerability management uses a risk-based based approach that can help you to discover, prioritize, and remediate endpoint vulnerabilities and misconfigurations. It provides:

- **Real-time device inventory** - Devices onboarded to Defender for Endpoint automatically report and push vulnerability and security configuration data to the dashboard.
- **Visibility into software and vulnerabilities** - Optics into the organization's software inventory, and software changes like installations, uninstalls, and patches. Newly discovered vulnerabilities are reported with actionable mitigation recommendations for Microsoft and non-Microsoft applications.
- **Application runtime context** - Visibility on application usage patterns for better prioritization and decision-making.
- **Configuration posture** - Visibility into organizational security configuration or misconfigurations. Issues are reported in the dashboard with actionable security recommendations.

### 3. Next generation protection

You can use Microsoft Defender for Endpoint's next generation protection to block sophisticated threats and malware. With it, you can leverage a combination of both client-based and cloud-based protection engines and machine learning. You're able to use behavior based real-time protection, blocks file-based and fileless malware, and stop malicious activity from applications. You can take advantage of its antivirus engine that runs in a sandbox and has additional tamper protection capabilities.

Next-gen protection capabilities are built into Windows 10 and available across macOS, Linux server, Android, and iOS.

### 4. Attack surface reduction

The fourth capability to you can adopt is attack surface reduction. Attack surface reduction eliminates risks by reducing your surface area of attack. It works by ensuring devices settings are correctly configured with capabilities such as hardware-based isolation, application control, network and web protection, and more. You can use granular controls through rules that target certain software behaviors to keep your organization safe.

### 5. Auto investigation and remediation

AIR is a core part of Microsoft Defender for Endpoint, and therefore With automated investigation and remediation, you can let Microsoft Defender for Endpoint automatically investigate threats, and remediate them for you at scale, based on controls that you set. Use automated investigation and remediation to help to reduce the volume of alerts for your organization's security team.

### 6. Microsoft Threat Experts

Microsoft Threat Experts is a managed service to get access to security experts. You can use it to get access to insights that you can use to better understand threats and take appropriate action. This is a separate service, so it's not a direct capability of Microsoft Defender for Endpoint.

## Learn more

- [Prepare Microsoft Defender for Endpoint deployment](/microsoft-365/security/defender-endpoint/prepare-deployment)
