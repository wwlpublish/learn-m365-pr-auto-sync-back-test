An incident in Microsoft 365 Defender is a collection of correlated signals, alerts, and other relevant items that are combined into a single comprehensive view representing the whole attack.

Incidents ensure elements otherwise spread across various portals and queues are presented in a single coherent view, which improves your security team's ability to respond to threats and attacks.

Grouping related alerts and threat data into an incident helps you see:

- Where the attack started
- What tactics were used
- How far the attack has gone into your tenant
- The scope of the attack, such as how many devices, users, and mailboxes were impacted
- All the data associated with the attack

## Example cyber attack

:::image type="content" source="../media/2-attack-chain-overpass-the-hash-spear-phishing-lateral-movement.png" alt-text="Diagram showing the initial access through spear-phishing and lateral movement through overpass-the-hash attack" lightbox="../media/2-attack-chain-overpass-the-hash-spear-phishing-lateral-movement.png":::

In this example, an attacker starts with a spear-phishing email targeting a specific user. The email contains a malicious link to download a file that contains the Meterpreter payload. With the malicious code running on the target device, an attacker performs reconnaissance to understand which users have signed into the device and which other devices these users have access to.

The attacker finds the credentials of an IT helpdesk team member. Impersonating this IT helpdesk team member using the overpass-the-hash method, the attacker moves laterally to a second device. On a new device, they steal the user's web credentials, which they use to remotely access the user's cloud apps like OneDrive or SharePoint. This allows the attacker to insert a malicious macro into an existing online Word document, which they then deploy in a lateral phishing attack by distributing links to the malicious document to other users in the organization.

As a security analyst for an attack like this, you need all of the alert and threat information from multiple sources collated in the same place, such as Microsoft Defender for Office 365 for the phishing email, Microsoft Defender for Endpoint for the devices, Microsoft Defender for Identity for the compromised user accounts, and Microsoft Cloud App Security for OneDrive and SharePoint.

Microsoft 365 Defender can automatically collect and correlate isolated alerts and other related security events into incidents in an incident queue, reducing workloads so you have fewer, more comprehensive work items. The incident queue brings together related alerts, affected assets, and other evidence, making it easier to understand the complete attack story and take informed actions.

This short video will introduce the concept of incident management and how it can benefit your organization.

>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?rel=0&preserve-view=true]

### Use different aspects to investigate an incident

You'll use the incident queue to sort through incidents, and to prioritize and create an informed cybersecurity response decision. Microsoft 365 Defender allows you to view the threat data of incidents from many different viewpoints:

- **Alerts**: All the alerts related to the incident and their information.
- **Devices**: All the devices that have been identified to be part of or related to the incident.
- **Users**: All the users that have been identified to be part of or related to the incident.
- **Mailboxes**: All the mailboxes that have been identified to be part of or related to the incident.
- **Investigations**: All the automated investigations triggered by alerts in the incident.
- **Evidence and Response**: All the supported events and suspicious entities in the alerts in the incident.

### The incident queue

The Microsoft 365 Defender incident queue uses sophisticated correlation logic, which means that from the incident queue, you can now see all related alerts and open them directly. In addition, you have a broad range of data points to filter and select from, like investigation status, device group, and other filtering options.

The key features of the incident queue are:

- Nested lists of alerts grouped by incident, which enables you to quickly view which alerts make up each incident and easily drill down to each alert.
- Filters on the list of incidents improve your ability to group and manage incidents with common criteria, such as severity, status, threat information source, and many others.
- Full alignment with the Microsoft Defender for Endpoint alert queue.

## Prioritizing incidents

As a security analyst, one of your first responsibilities in managing the incident queue is to prioritize them, ensuring that the most severe and impactful incidents get the most immediate attention.

### Sorting and filters

From the default incident queue, you can select **Filters** to see a Filters pane, from which you can specify the subset of incidents you want to see.

:::image type="content" source="../media/2-incidents-ss-incidents-filters.png" alt-text="Screenshot showing the use of Filters in the incident queue" lightbox="../media/2-incidents-ss-incidents-filters.png":::

There are many filters available. Some of the more useful filters are:

- **Status** – Display incidents based on their overall status such as new or in-progress. A typical filter is for all incidents with a **New** status so that they can be evaluated and assigned.
- **Severity** – Display incidents with one or more severity ratings. A typical filter is for all incidents with high severity so they can be prioritized for investigation
- **Service source** – Display incidents that are from specified sources, such as Defender for Identity, so that specialists on your team can focus on specific types of incidents.

## Managing incidents

Incident management is critical in ensuring that threats are addressed by the right people and contain helpful information for in-progress and post-resolution processes used in your Security Operations Center (SOC). There are several ways you can manage your incidents:

- Change the incident name
- Add incident tags.
- Assign the incident to a user account
- Resolve them
- Set its classification and determination
- Add comments.

You can manage incidents from the **Manage incident** pane for an incident.

> [!NOTE]
> The incident queue has customizable columns that give you visibility into different characteristics of the incident or the affected entities. This helps you make an informed decision about the prioritization of incidents for analysis.

:::image type="content" source="../media/2-incidents-manage.png" alt-text="Screen shot showing how to manage incidents" lightbox="../media/2-incidents-manage.png":::

### Incident name

Microsoft 365 Defender automatically assigns a name based on alert attributes such as the number of endpoints affected, users affected, detection sources, or categories. This allows you to quickly understand the scope of the incident. You can modify the default name, for example, to match your SOC best practices.

### Incident tags

You can add custom tags to an incident, for example to flag a group of incidents with a common characteristic. You can later filter the incident queue for all incidents that contain a specific tag. For example, you can use tags already defined by your SOC best practices.

### Assign to me

If an incident hasn't yet been assigned, you can select **Assign to me** to assign it to your user account. Doing so assigns ownership of the incident and all the alerts associated with it to you.

### Resolve incident

Indicate if the incident has been remediated. When you resolve an incident, it also resolves all the linked and active alerts related to the incident.

### Classification

The incident classification is whether it was a true alert or a false alert, which you configure from the Classification field.

If it was a true alert, you should also specify what type of threat it was with the Determination field. Specifying the threat type helps your security team see threat patterns and act to defend your organization from them.

### Comment

You can add multiple comments to an incident with the Comment field. Each comment gets added to the historical events of the incident. You can see the comments and history of an incident from the Comments and history link on the Summary page. This allows you to see what has been done on an incident, for example when handing off the incident to another security analyst, and for post-remediation analysis.

## Example incident response workflow

Here's an example workflow for responding to incidents with the Microsoft 365 Defender portal.

:::image type="content" source="../media/2-incidents-example-workflow.png" alt-text="Diagram showing the incident response workflow" lightbox="../media/2-incidents-example-workflow.png":::

On an ongoing basis, identify the highest priority incidents for analysis and resolution in the incident queue and get them ready for response. This is a combination of:

- Triaging to determine the highest priority incidents through filtering and sorting of the incident queue.
- Managing incidents by modifying their title, assigning them to an analyst, and adding tags and comments.

1. For each incident, begin an attack and alert analysis:
   - View the summary of the incident to understand its scope and severity and what entities are affected (the Summary tab).
   - Begin analyzing the alerts to understand their origin, scope, and severity (the Alerts tab).
   - As needed, gather information on affected devices, users, and mailboxes (the Devices, Users, and Mailboxes tabs).
   - See how Microsoft 365 Defender has automatically resolved some alerts (the Investigations tab).
   - As needed, use the data set for the incident for more information (the Evidence and Response tab).

1. After or during your analysis, perform containment to reduce any additional impact of the attack and eradication of the security threat.
1. As much as possible, recover from the attack by restoring your tenant resources to the state they were in before the incident.
1. Resolve the incident and take time for post-incident learning to:
   - Understand the type of the attack and its impact.
   - Research the attack in Threat Analytics and the security community for a security attack trend.
   - Recall the workflow you used to resolve the incident and update your standard workflows, processes, policies, and playbooks as needed.
   - Determine whether changes in your security configuration are needed and implement them.
