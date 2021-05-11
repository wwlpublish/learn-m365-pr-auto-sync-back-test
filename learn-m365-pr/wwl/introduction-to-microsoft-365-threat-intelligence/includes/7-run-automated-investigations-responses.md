Automated investigation and response (AIR) capabilities enable organizations to run automated investigation processes in response to well-known threats that exist today. AIR can help an organization's security operations team operate more efficiently and effectively.

AIR is included in the following subscriptions:

 -  Microsoft 365 E5
 -  Microsoft 365 E5 Security
 -  Office 365 E5
 -  Defender for Office 365 Plan 2

At a high level, the AIR flow works like this:

1.  An alert is triggered, and in response, a security playbook is run.
2.  Depending on the particular alert and security playbook, an automated investigation begins immediately. Alternately, a security analyst can start an automated investigation manually based on a value in a report such as Explorer.
3.  While an automated investigation runs, its scope can increase as other related alerts are triggered.
4.  During and after an automated investigation, details and results are available to view. Results include recommended actions that can be performed to respond to and remediate any threats that were found. A playbook log is also available that tracks all investigation activity.
5.  An organization's security operations team reviews the results and recommendations and approves remediation actions. In Microsoft 365, remediation actions are taken only upon approval by the organization's security team.

### Alerts

Alerts act as triggers for the workflows used by a security operations team. In other words, an alert can trigger an incident response. Ranking the right set of alerts for investigation is challenging, especially when making sure no threats are left unaddressed. When investigations into alerts are conducted manually, security operations teams must hunt and correlate entities at risk from threats (such as content, devices, and users). Such tasks and workflows are very time consuming and involve multiple tools and systems. With AIR, investigation and response are automated into key security and threat management alerts that automatically trigger security response playbooks.

Alerts generated from the alert policies of the following events are auto-investigated:

 -  A potentially malicious URL selection was detected.
 -  Email reported by user as phish.\*
 -  Email messages containing malware removed after delivery.\*
 -  Email messages containing phish URLs removed after delivery.\*
 -  Suspicious email sending patterns detected.\#
 -  User restricted from sending email.\#

> [!NOTE]
> The alerts listed above that are marked with an asterisk (\*) are assigned an Informational severity in the respective alert policies within the Security &amp; Compliance Center. Email notifications are turned off for these alerts. Email notifications can be turned on through Alert policy configuration. Alerts marked with a hash (\#) are generally available alerts associated with public preview playbooks.

### Security playbooks

Security playbooks are back-end policies that are at the heart of automation in Microsoft Threat Protection. The security playbooks provided in AIR are based on common, real-world security scenarios. A security playbook is launched automatically when an alert is triggered within an organization. Once the alert triggers, the associated playbook automatically starts. The playbook runs an investigation, looking at all the associated metadata (including email messages, users, subjects, senders, and so on). Based on the playbook's findings, AIR recommends a set of actions that an organization's security team can take to control and mitigate the threat.

The security playbooks that are provided with AIR are designed to address the most frequent threats that organizations face today. They're based on input from Security Operations and Incident Response teams, including those teams who help defend Microsoft and its customers' assets.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”