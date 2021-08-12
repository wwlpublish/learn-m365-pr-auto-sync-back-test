
On any given day, you and your security team have to deal with a seemingly never-ending flow of security threats to your organization's assets and infrastructure. Continued exposure to high volumes of incidents can sometimes lead to alert or incident fatigue, which can increases the time between identification and remediation.

With automated investigation and response (AIR), Microsoft 365 Defender can help reduce the number of remediation actions you need to determine and perform, reducing the demands on your security team to deal with ongoing volume of alerts and incidents.

## What is automated investigation and response

In Microsoft 365 Defender, automated self-healing mimics the steps you and members of your security team would take to forensically investigate and remediate organizational assets affected by attacks. This is the equivalent of increasing the size of your security team and having them working 24/7 at no extra cost.

Automated self-healing helps by responding more efficiently to investigate and remediate alerts and free you and your team to focus on other tasks.

An automated investigation begins before any member of your security team receives the alert. It starts by investigating impacted assets and grouping them together. Then, it collects all the evidence of compromise across apps, identity, endpoints and data to provide visibility into related events, and timelines. At each stage in the automated investigation, Microsoft 365 Defender gives each piece of evidence a verdict:

- Suspicious
- Malicious
- Clean

Depending on the verdict assigned by the automated investigation, Microsoft 365 Defender will act appropriately. Which means it will take immediate action, for example, on a "malicious" process by forcefully closing it, a "malicious" URL by blocking it, or on a "suspicious" email by quarantining it. The final step in an automated investigation is to include details on other potentially affected assets, before starting a new investigation.

Automated investigation and self-healing look at an enormous number of entities, across all domains, which dramatically reduce the time an attacker can operate before remediation shuts them down.

## Action center

Action center provides a comprehensive view of Microsoft 365 Defender automated investigation and response (AIR) actions. When you visit the Action center page, you'll be presented with two lists of actions:

- **Pending**: The list of actions that require your review and approval.
- **History**: An audit log for actions that were taken.

> [!NOTE]
> You can approve or reject actions one at a time or select multiple actions if they have the same type of action, such as Quarantine file.

:::image type="content" source="../media/2-action-center-page.png" alt-text="Screenshot showing a fragment of the action center page." lightbox="../media/2-action-center-page.png":::

The Action center brings together remediation actions across Defender for Endpoint and Defender for Office 365. It defines a common language for all remediation actions and provides a unified investigation experience where you can:

- Approve pending remediation actions from the **Pending** tab.
- View an audit log of already approved remediation actions.

The **History** tab is where you can see the state of previous actions. It also lets you see if the decision was made automatically or by you or a member of your security team.

## Actions available in Action center

In addition to remediation actions that are taken automatically because of automated investigations, the Action center also tracks actions you and your security team has taken to address detected threats, or actions that were taken as a result of threat protection features in Microsoft 365 Defender.

All actions, whether they're pending approval or were already taken, are tracked in the Action center.

The available actions for devices are:

- Collect investigation package
- Isolate device
- Offboard machine
- Release code execution
- Release from quarantine
- Request sample
- Restrict code execution
- Run antivirus scan
- Stop and quarantine

The available actions for emails are:

- Block URL (time-of-click)
- Soft delete email messages or clusters
- Quarantine email
- Quarantine an email attachment
- Turn off external mail forwarding
