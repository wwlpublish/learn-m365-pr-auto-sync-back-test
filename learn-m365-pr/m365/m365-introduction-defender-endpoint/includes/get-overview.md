Unprotected or misconfigured devices can pose a risk to your organization. Attackers can take advantage and do damage to your devices or data. Many organizations have suffered reputational and financial loss at the hands of attackers. To protect your organization, you need to protect your devices. 

In your medium-sized organization, you're concerned that your security posture may not be as secure as it needs to be, given the attacks that are regularly attempted from malicious actors. You want to know if Microsoft Defender for Endpoint can help to reduce weaknesses in your computers.

Here, you're going to look into how Microsoft Defender for Endpoint can help you to achieve your goal.

## What is Microsoft Defender for Endpoint?

Microsoft Defender for Endpoint is an endpoint security solution that offers vulnerability management, endpoint protection, endpoint detection and response, mobile threat defense, and managed services in a single, unified platform. It enables you to prevent, detect, investigate, and respond to security threats and risks across Windows, Windows Server, macOS, Linux, Android, and iOS devices.

>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Microsoft Defender for Endpoint takes advantage of technologies including:

- **Endpoint behavioral sensors**: Microsoft Defender for Endpoint gathers and processes behavioral signals and activities on the endpoints and shares this information with a private Microsoft Defender for Endpoint cloud instance.
- **Cloud security analytics**: Microsoft Defender for Endpoint translates behavioral signals into insights, detailed detections, and recommends actions to respond to advanced threats. It does this using tools such as on device machine learning, big-data, cloud-based machine learning, and Microsoft's unique visibility into activity across other products such as Microsoft 365 and its Windows ecosystem.
- **Threat intelligence**: Microsoft security teams and partners provide threat intelligence that allows Microsoft Defender for Endpoint to identify tools, procedures, and techniques used by attackers. Microsoft Defender for Endpoint then generates alerts when any of these are identified in the sensor data that it has collected.

### Understand the capabilities

:::image type="content" source="../media/1-components.png" alt-text="Diagram showing the Microsoft Defender for Endpoint components." lightbox="../media/1-components.png" border="false":::

Microsoft Defender for Endpoint provides protection through several different capabilities:

- **Threat and vulnerability management**: Provides risk-based discovery, prioritization, and remediation of misconfigurations and vulnerabilities across your endpoints.
- **Attack surface reduction**: Helps you to resist attacks and exploitation by applying mitigation techniques and ensuring configuration settings are set properly. It provides protections such as application control, network protection, and web protection to regulate access to your applications, domains, IP address, and more.
- **Next-generation protection**: Protects against emerging threats through behavior-based antivirus protection, and cloud-delivered protection.
- **Endpoint detection and response**: Enables you to detect, investigate, and respond appropriately to even advanced threats that might have successfully succeeded in evading the attack surface reduction and threat and vulnerability components. It also allows you to conduct advanced hunting, through a query-based hunting tool to identify breaches proactively and use custom detections.
- **Automated investigation and remediation**: Enables you to use sophisticated automatic investigation and remediation capabilities to efficiently and consistently respond to threats at scale.
- **Microsoft Threat Experts**: Enables you to take advantage of expert-level monitoring, analysis, and access to experts on demand for critical threats specific to your environment.
- **Centralized management and API**: Microsoft Defender for Endpoint supports different tools, such as Group Policy, and non-Microsoft tools that can be used for device management. Microsoft Defender for Endpoint comes with built-in API that you can use to automate workflows and extend its capabilities using your custom apps. Additionally, Microsoft Defender for Endpoint integrates directly with several Microsoft solutions including Microsoft Endpoint Manager, Microsoft Sentinel, Microsoft Defender for Cloud, and more.

## Understand the architecture

To help understand how Microsoft Defender for Endpoint can protect your organization, it's helpful to understand the architecture of Microsoft Defender for Endpoint. Watch the video below to get an overview of Microsoft Defender for Endpoint's architecture.

>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4]

Microsoft Defender for Endpoint's architecture consists of the following components:

- Dedicated tenant
- Sensors
- The Microsoft 365 Defender portal

### Dedicated tenant

During onboarding, a Microsoft Defender for Endpoint tenant is provisioned for your organization. Tenants are isolated from other tenants. This means your organization's data is never shared with other tenants, and it's only accessible to your organization. Additionally, all access audited to ensure your data remains protected. Your tenant relies on its own components including:

- **A built-in dictionary**
  - Each tenant comes with a built-in dictionary that defines behavioral rules, anomaly detection algorithms, to detect suspicious events when gathering sensor data from your devices.
- **Custom sandboxes**
  - Your tenant also enables you to create sandbox environments so that you can upload suspicious files, investigate those files, and generate detailed reports about those files based on the findings of your investigations.

### Sensors

You install sensors on your devices to gather security-related information on each device, and send that information over to your organization's Microsoft Defender for Endpoint tenant. Sensors enable you to detect breaches, investigate events, collect information for security analytics, and more. Sensors also enable you to trigger actions on devices, such as gathering suspicious files, or isolating a device from the network.

### The Microsoft 365 Defender portal

You use the Microsoft 365 Defender portal to access your tenant. From here, you manage the security of the devices that are part of your tenant. This is where you can use all the capabilities you need to manage to protect your endpoints, such as threat and vulnerability management, endpoint detection and response, automated investigation and remediation, and more.

## Learn more

- [Supported Windows versions](/microsoft-365/security/defender-endpoint/minimum-requirements#supported-windows-versions)
- [Licensing requirements](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)
