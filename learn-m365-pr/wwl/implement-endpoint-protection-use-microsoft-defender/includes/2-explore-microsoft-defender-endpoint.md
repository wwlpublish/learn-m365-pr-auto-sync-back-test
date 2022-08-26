Microsoft Defender for Endpoint is an enterprise endpoint security platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats.

Microsoft Defender for Endpoint uses the following combination of technology built into Windows 10 and later and Microsoft's robust cloud service:

 -  **Endpoint behavioral sensors**. These sensors are embedded in Windows 10 and later. They begin by collecting and processing behavioral signals from the operating system. They then send this sensor data to an organization's private, isolated, cloud instance of Microsoft Defender for Endpoint.
 -  **Cloud security analytics**. Enterprise cloud products (such as Microsoft 365) and online assets apply big-data, device learning, and unique Microsoft optics across the Windows ecosystem. Behavioral signals are translated into insights, detections, and recommended responses to advanced threats.
 -  **Threat intelligence**. Microsoft hunters and security teams generate threat intelligence. This information is then augmented by threat intelligence provided by partners. Threat intelligence enables Microsoft Defender for Endpoint to:
     -  Identify attacker tools, techniques, and procedures.
     -  Generate alerts when they're observed in collected sensor data.

### Microsoft Defender for Endpoint architecture

:::image type="content" source="../media/microsoft-defender-for-endpoint-overview-22e3358a.png" alt-text="Diagram showing the key services provided by Microsoft Defender for Endpoint, which is a service of Microsoft 365 Defender.":::


**Additional viewing**. Select the following link to watch a short video on the [Microsoft Defender for Endpoint architecture](https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0&amp;postJsllMsg=true?azure-portal=true).

Microsoft Defender for Endpoint is a service of Microsoft 365 Defender. Under the Microsoft 365 Defender umbrella are centralized configuration and administration APIs, followed by the Microsoft Defender for Endpoint services. These capabilities are outlined below:

 -  [Threat &amp; Vulnerability Management](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt?azure-portal=true). This built-in capability uses a game-changing risk-based approach to the discovery, prioritization, and remediation of endpoint vulnerabilities and misconfigurations.
 -  [Attack surface reduction](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction?azure-portal=true). The attack surface reduction set of capabilities provides the first line of defense in the stack. To support this feature, organizations should ensure configuration settings are properly set and exploit mitigation techniques are applied. By doing so, the attack surface reduction capabilities can resist attacks and exploitation. The capabilities also include network protection and web protection. These features regulate access to malicious IP addresses, domains, and URLs.
 -  [Next-generation protection](/microsoft-365/security/defender-endpoint/next-generation-protection?azure-portal=true). To further reinforce the security perimeter of your network, Microsoft Defender for Endpoint uses next-generation protection designed to catch all types of emerging threats.
 -  [Endpoint detection and response](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response?azure-portal=true). Endpoint detection and response capabilities are put in place to detect, investigate, and respond to advanced threats that may have made it past the first two security pillars. Advanced hunting provides a query-based threat-hunting tool that lets you proactively find breaches and create custom detections.
 -  [Automated investigation and remediation](/microsoft-365/security/defender-endpoint/automated-investigations?azure-portal=true). Microsoft Defender for Endpoint can quickly respond to advanced attacks. It also offers automatic investigation and remediation capabilities that help reduce the volume of alerts in minutes at scale.
 -  [Microsoft Secure Score for Devices](/microsoft-365/security/defender-endpoint/tvm-microsoft-secure-score-devices?azure-portal=true). Microsoft Defender for Endpoint includes Microsoft Secure Score for Devices. This feature helps organizations:
     -  dynamically assess the security state of their enterprise network.
     -  identify unprotected systems.
     -  take recommended actions to improve the overall security of the organization.
 -  [Microsoft Threat Experts](/microsoft-365/security/defender-endpoint/microsoft-threat-experts?azure-portal=true). Microsoft Defender for Endpoint's new managed threat hunting service provides proactive hunting, prioritization, and other context and insights. These features further empower Security operation centers (SOCs) to identify and respond to threats quickly and accurately.
    
    > [!IMPORTANT]
    > Microsoft Defender for Endpoint customers must apply for the Microsoft Threat Experts managed threat hunting service to get proactive Targeted Attack Notifications and to collaborate with experts on demand. Experts on Demand is an add-on service. Targeted Attack Notifications are always included after you've been accepted into Microsoft Threat Experts managed threat hunting service. If you aren't enrolled yet and would like to experience its benefits, go to **Settings &gt; General &gt; Advanced features &gt; Microsoft Threat Experts** to apply. Once accepted, you'll get the benefits of Targeted Attack Notifications, and start a 90-day trial of Experts on Demand. Contact your Microsoft representative to get a full subscription of Experts on Demand.

 -  [Centralized configuration and administration, APIs](/microsoft-365/security/defender-endpoint/management-apis?azure-portal=true). Integrate Microsoft Defender for Endpoint into your existing workflows.
 -  [Integration with Microsoft solutions](/microsoft-365/security/defender-endpoint/threat-protection-integration?azure-portal=true). Microsoft Defender for Endpoint directly integrates with various Microsoft solutions, including:
     -  Microsoft Defender for Cloud
     -  Microsoft Sentinel
     -  Intune
     -  Microsoft Defender for Cloud Apps
     -  Microsoft Defender for Identity
     -  Microsoft Defender for Office 365
     -  Skype for Business
 -  [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender?azure-portal=true). Microsoft Defender for Endpoint and other Microsoft security solutions (Defender for Identity, Defender for Office 365, and Defender for Cloud Apps), together with Microsoft 365 Defender, form a unified pre- and post-breach enterprise defense suite. It natively integrates across endpoint, identity, email, and applications. This design enables it to detect, prevent, investigate, and automatically respond to sophisticated attacks.

### Compare Microsoft Defender for Endpoint plans

Microsoft Defender for Endpoint provides advanced threat protection. This feature includes antivirus, antimalware, ransomware mitigation, and more, together with centralized management and reporting.

Two plans are available. The following table lists the features provided in each plan at a high level.

:::row:::
  :::column:::
    **[Defender for Endpoint Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1?azure-portal=true)**
  :::column-end:::
  :::column:::
    **[Defender for Endpoint Plan 2](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint?azure-portal=true)**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Next-generation protection

Attack surface reduction

Manual response actions

Centralized management

Security reports

APIs
  :::column-end:::
  :::column:::
    Defender for Endpoint Plan 1

plus:

Device discovery

Threat and vulnerability management

Threat Analytics

Automated investigation and response

Advanced hunting

Endpoint detection and response

Microsoft Threat Experts
  :::column-end:::
:::row-end:::


### Microsoft Defender for Endpoint licensing

The following list identifies the licensing options for Microsoft Defender for Endpoint:

 -  **Microsoft Defender for Endpoint Plan 1**. Microsoft Defender for Endpoint Plan 1 is available as a standalone user subscription license for commercial and education customers. It's also included as part of Microsoft 365 E3/A3.
 -  **Microsoft Defender for Endpoint Plan 2**. Microsoft Defender for Endpoint Plan 2 is available as a standalone license and as part of the following plans:
     -  Windows 11 Enterprise E5/A5
     -  Windows 10 Enterprise E5/A5
     -  Microsoft 365 E5/A5/G5 (which includes Windows 10 or Windows 11 Enterprise E5)
     -  Microsoft 365 E5/A5/G5/F5 Security
     -  Microsoft 365 F5 Security &amp; Compliance
 -  **Microsoft Defender for Endpoint Server**. For server security, Microsoft offers Microsoft Defender for Cloud. It has the best and most appropriate capabilities for server and cloud protection. As of April 2022, Microsoft introduced Microsoft Defender for Servers Plan 1 and Plan 2. For more information, please read [Microsoft Defender for Servers - the benefits and features \| Microsoft Docs](/azure/defender-for-cloud/defender-for-servers-introduction?azure-portal=true).

### Plan your Microsoft Defender for Endpoint deployment

Plan your Microsoft Defender for Endpoint deployment so that you can maximize the security capabilities within the suite and better protect your enterprise from cyber threats.

This solution provides guidance on how to identify your environment architecture, select the type of deployment tool that best fits your needs, and guidance on how to configure capabilities.

:::image type="content" source="../media/defender-for-endpoint-deployment-guide-plan-609441ab.png" alt-text="Diagram showing how to identify your environment architecture, select the deployment tool, and configure capabilities.":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”