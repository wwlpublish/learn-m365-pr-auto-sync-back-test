Threat analytics is our in-product threat intelligence solution from expert Microsoft security researchers. It's designed to assist security teams to be as efficient as possible while facing emerging threats, such as:

 -  Active threat actors and their campaigns
 -  Popular and new attack techniques
 -  Critical vulnerabilities
 -  Common attack surfaces
 -  Prevalent malware

**Additional viewing**. Select the following link to learn more about how threat analytics can help you track the latest threats and stop them: [Microsoft 365 Defender Threat Analytics](https://www.microsoft.com/videoplayer/embed/RWwJfU?postJsllMsg=true?azure-portal=true).

You can access the **Threat analytics** dashboard from the navigation pane in the Microsoft 365 Defender portal. You can also access it from a dedicated dashboard card that shows the top threats to your organization, both in terms of effect, and in terms of exposure. The following image of the Microsoft 365 Defender home page highlights both methods of selection.

:::image type="content" source="../media/threat-analytics-page-6374e5c6.png" alt-text="Screenshot of the Microsoft 365 Defender portal with the Threat Analytics access options highlighted." lightbox="../media/threat-analytics-page-6374e5c6.png":::


High impact threats have the greatest potential to cause harm. High exposure threats are the ones that your assets are most vulnerable to. Getting visibility on active or ongoing campaigns and knowing what to do through threat analytics can help equip your security operations team with informed decisions.

With more sophisticated adversaries and new threats emerging frequently and prevalently, it's critical to be able to quickly:

 -  Identify and react to emerging threats.
 -  Learn if you're currently under attack.
 -  Assess the effect of the threat to your assets.
 -  Review your resilience against or exposure to the threats.
 -  Identify the mitigation, recovery, or prevention actions you can take to stop or contain the threats.

The Threat Analytics reports provide analysis of a tracked threat. They also provide guidance on how to defend against that threat. Each report incorporates data from your network, indicating whether the threat is active and if you have applicable protections in place.

### View the threat analytics dashboard

The threat analytics dashboard highlights the reports that are most relevant to your organization. It summarizes the threats in the following sections:

 -  **Latest threats**. Lists the most recently published or updated threat reports, along with the number of active and resolved alerts.
 -  **High-impact threats**. Lists the threats that have the greatest effect on your organization. This section lists threats with the highest number of active and resolved alerts first.
 -  **Highest exposure**. Lists threats with the highest exposure levels first. The exposure level of a threat is calculated using two pieces of information:
    
     -  How severe the vulnerabilities associated with the threat are.
     -  How many devices in the organization could be exploited by those vulnerabilities.

Select a threat from the dashboard to view the report for that threat. You can also select the **Search** field to enter a keyword that's related to the threat analytics report you would like to see.

:::image type="content" source="../media/threat-analytics-dashboard-0afd0936.png" alt-text="Screenshot of the Threat Analytics dashboard in the Microsoft 365 Defender portal." lightbox="../media/threat-analytics-dashboard-0afd0936.png":::


### View a threat analytics report

Each threat analytics report provides information in several tabs:

 -  Overview
 -  Analyst report
 -  Related incidents
 -  Impacted assets
 -  Prevented email attempts
 -  Exposure & mitigations

Each of these tabs is examined in greater detail in the following sections.

#### Overview tab: Quickly understand the threat, assess its impact, and review defenses

The **Overview** tab provides a preview of the detailed analyst report. It also provides charts that highlight:

 -  The impact of the threat to your organization.
 -  Your exposure through misconfigured and unpatched devices.

:::image type="content" source="../media/overview-section-threat-analytics-page-3a6ec605.png" alt-text="Screenshot of the overview section of the threat analytics report." lightbox="../media/overview-section-threat-analytics-page-3a6ec605.png":::


Each report includes charts designed to provide information about the organizational impact of a threat:

 -  **Related incidents**. Provides an overview of the impact of the tracked threat to the organization with the following data:
    
     -  Number of active alerts and the number of active incidents they're associated with.
     -  Severity of active incidents.
 -  **Alerts over time**. Shows the number of related Active and Resolved alerts over time. The number of resolved alerts indicates how quickly the organization responds to alerts associated with a threat. Ideally, the chart should be showing alerts resolved within a few days.
 -  **Impacted assets**. Shows the number of distinct devices and email accounts (mailboxes) that currently have at least one active alert associated with the tracked threat. Alerts are triggered for mailboxes that received threat emails. Organizations should review both org- and user-level policies for overrides that cause the delivery of threat emails.
 -  **Prevented email attempts**. Shows the number of emails from the past seven days that were either blocked before delivery or delivered to the junk mail folder.

Each report includes charts that provide an overview of how resilient the organization is against a given threat:

 -  **Secure configuration status**. Shows the number of devices with misconfigured security settings. Organizations should apply the recommended security settings to help mitigate the threat. Devices are considered Secure if they've applied *all* the tracked settings.
 -  **Vulnerability patching status**. Shows the number of vulnerable devices. Organizations should apply security updates or patches to address vulnerabilities exploited by the threat.

You can filter the threat report list and view the most relevant reports according to a specific threat tag (category) or a report type.

 -  Threat tags. Assist you in viewing the most relevant reports according to a specific threat category. For example, all reports related to ransomware.
 -  **Report types**. Assist you in viewing the most relevant reports according to a specific report type. For example, all reports that cover tools and techniques.
 -  **Filters**. Assist you in efficiently reviewing the threat report list and filtering the view based on a specific threat tag or report type. For example, review all threat reports related to ransomware category, or threat reports that cover vulnerabilities.

The Microsoft Threat Intelligence team has added threat tags to each threat report:

 -  Four threat tags are now available:
    
     -  Ransomware
     -  Phishing
     -  Vulnerability
     -  Activity group
 -  Threat tags are presented at the top of the threat analytics page.
 -  There are counters for the number of available reports under each tag.
 -  The list can also be sorted by threat tags.
 -  Filters are available per threat tag and report type.

#### Analyst report tab: Get expert insight from Microsoft security researchers

The **Analyst report** tab includes detailed expert analysis on the threat. Most reports provide detailed descriptions of attack chains, including tactics and techniques mapped to the MITRE ATT&CK framework, exhaustive lists of recommendations, and powerful [threat hunting](/microsoft-365/security/defender/advanced-hunting-overview?azure-portal=true) guidance.

**Additional reading**. For more information, see [Learn more about the analyst report](/microsoft-365/security/defender/threat-analytics-analyst-reports?azure-portal=true).

#### Related incidents tab: View and manage related incidents

The **Related incidents** tab provides the list of all incidents related to the tracked threat. You can assign incidents or manage alerts linked to each incident.

:::image type="content" source="../media/related-incidents-section-threat-analytics-report-bee37b17.png" alt-text="Screenshot of the related incidents section of a threat analytics report." lightbox="../media/related-incidents-section-threat-analytics-report-bee37b17.png":::


#### Impacted assets tab: Get list of impacted devices and mailboxes

An asset is considered impacted if it's affected by an active, unresolved alert. The **Impacted assets** tab lists the following types of impacted assets:

 -  **Devices**. Endpoints that have unresolved Microsoft Defender for Endpoint alerts. These alerts typically fire on sightings of known threat indicators and activities.
 -  **Mailboxes**. Mailboxes that have received email messages that have triggered Microsoft Defender for Office 365 alerts. While most messages that trigger alerts are typically blocked, user- or org-level policies can override filters.

:::image type="content" source="../media/impacted-assets-section-threat-analytics-report-0d7b74f3.png" alt-text="Screenshot of the impacted assets section of a threat analytics report." lightbox="../media/impacted-assets-section-threat-analytics-report-0d7b74f3.png":::


#### Prevented email attempts tab: View blocked or junked threat emails

Microsoft Defender for Office 365 typically blocks emails with known threat indicators, including malicious links or attachments. In some cases, proactive filtering mechanisms that check for suspicious content will instead send threat emails to the junk mail folder. In either case, the chances of the threat launching malware code on the device is reduced.

The Prevented email attempts tab lists all the emails that have either been blocked before delivery or sent to the junk mail folder by Microsoft Defender for Office 365.

:::image type="content" source="../media/prevented-email-attempts-section-threat-analytics-report-149d55b7.png" alt-text="Screenshot of the prevented email attempts section of a threat analytics report.":::


#### Exposure and mitigations tab: Review list of mitigations and the status of your devices

In the **Exposure and mitigations** section, an organization should review the list of specific actionable recommendations that can help increase its resilience against the threat. The list of tracked mitigations includes:

 -  **Security updates**. Deployment of supported software security updates for vulnerabilities found on onboarded devices
 -  **Supported security configurations**. These mitigations include:
    
     -  Cloud-delivered protection
     -  Potentially unwanted application (PUA) protection
     -  Real-time protection

Mitigation information in this tab incorporates data from [threat and vulnerability management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt?azure-portal=true). This feature also provides detailed drill-down information from various links in the report.

:::image type="content" source="../media/mitigation-section-secure-details-7c51e9f1.png" alt-text="Screenshot of the mitigation section showing secure configuration details." lightbox="../media/mitigation-section-secure-details-7c51e9f1.png":::


:::image type="content" source="../media/mitigation-section-vulnerability-details-3b8044f4.png" alt-text="Screenshot of the mitigation section showing vulnerability details.":::
