New threats emerge constantly as attackers frequently change their tactics. To keep your endpoints protected, you need to be able to keep up with changes in the external threat environment.

You can use Microsoft Defender for Endpoint to continuously assess how new threats can impact your endpoints. Additionally, you can review how resilient your endpoints are against exposure to new threats, and identify which actions to take to prevent or contain new threats.
Here, you'll learn about threat analytics.

## What is threat analytics?

Threat analytics in Microsoft Defender for Endpoints is a set of detailed threat analysis reports conducted by Microsoft security researchers. You can use threat analytics to get information on:

- The most popular and newest attack tactics
- The most critical vulnerabilities
- Common attack surfaces
- Active campaigns from threat actors
- Prevalent malware

Additionally, threat analytics incorporates data from your network indicating whether the threat is active and if you have applicable protections in place. You access the threat analytics from the Microsoft 365 Defender portal. Do this by selecting **Threat analytics** from the navigation pane.

:::image type="content" source="../media/4-select-threat-analytics.png" alt-text="A screenshot showing where to find Threat analytics." lightbox="../media/4-select-threat-analytics.png":::

At the top of the threat analytics dashboard, you'll see information on the latest threats, high-impact threats, and an overall summary of threats. In the lower section of the dashboard, you can see a list of threats that have been identified. You're able to select any threat in the list. This will take you to a detailed threat analytics report on your chosen threat.

:::image type="content" source="../media/4-threat-analytics-report.png" alt-text="A screenshot showing a threat analytics report." lightbox="../media/4-threat-analytics-report.png":::

Each threat analytics report consists of several sections including:

- Overview
- Analyst report
- Mitigations

### Overview

The **Overview** section is the starting page of the report. You use the overview section to get an overall understanding of the threat at a glance. You'll see information such as:

- Devices that have been impacted by the threat
- The number of alerts that have been raised as a result of the threat
- Information on incidents related to the threat
- Information on configurations recommendations that have been implemented to mitigate the threat

### Analyst report

Use the **Analyst report** section to access a detailed write-up on the threat provided by Microsoft security researchers.

:::image type="content" source="../media/4-analyst-report.png" alt-text="A screenshot showing the analyst report section." lightbox="../media/4-analyst-report.png":::

You'll find information such as:

- An analysis of the nature of the threat
- A detailed explanation of tactics and techniques of the threat
- A comprehensive list of recommendations to mitigate the threat
- Details on how the threat has been detected
- Guidance on how to use Advanced hunting to hunt for the threat

### Mitigations

Use the **Mitigations** section to help you to review the recommendations that you can implement to improve your organization's protection against a threat.

:::image type="content" source="../media/4-mitigations-section.png" alt-text="A screenshot of the mitigations section." lightbox="../media/4-mitigations-section.png":::

Mitigations are categorized into:

- **Vulnerability patching**
  - These are security updates or patches that you can use to mitigate vulnerabilities that are relevant to the threat across exposed devices.
- **Secure configuration**
  - Actionable security configuration recommendations that you can take to mitigate the threat on devices.

> [!NOTE]
> There are some considerations you should keep in mind when using threat analytics:
>
> - The data you see is going to be scoped to your role-based-access control role.
> - If devices don't transmit data to the service, they're labeled as unavailable.
> - Devices with non-Microsoft antivirus solutions installed can sometimes be labeled as exposed.
