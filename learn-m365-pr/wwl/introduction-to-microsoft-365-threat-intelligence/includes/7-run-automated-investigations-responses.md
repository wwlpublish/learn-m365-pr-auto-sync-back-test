Automated investigation and response (AIR) capabilities enable you to run automated investigation processes in response to well known threats that exist today. AIR can help your security operations team operate more efficiently and effectively.

AIR is included in the following subscriptions:

 -  Microsoft 365 E5
 -  Microsoft 365 E5 Security
 -  Office 365 E5
 -  Office 365 Advanced Threat Protection Plan 2

At a high level, the AIR flow works like this:

1.  An alert is triggered, and a security playbook is initiated in response.
2.  Depending on the particular alert and security playbook, automated investigation begins immediately. Alternately, a security analyst can start an automated investigation manually based on a value in a report such as Explorer.
3.  While an automated investigation runs, its scope can increase as additional related alerts are triggered.
4.  During and after an automated investigation, details and results are available to view. Results include recommended actions that can be performed to respond to and remediate any threats that were found. In addition, a playbook log is available that tracks all investigation activity.
5.  Your security operations team reviews the results and recommendations and approves remediation actions. In Office 365, remediation actions are taken only upon approval by your organization's security team.

### Alerts

Alerts represent triggers for security operations team workflows for incident response. Prioritizing the right set of alerts for investigation, while making sure no threats are unaddressed is challenging. When investigations into alerts are performed manually, Security Operations teams must hunt and correlate entities (e.g. content, devices and users) at risk from threats. Such tasks and workflows are very time consuming and involve multiple tools and systems. With AIR, investigation and response are automated into key security and threat management alerts that trigger your security response playbooks automatically.

In the initial release of AIR (beginning April 2019), alerts generated from the following single events alert policies are auto-investigated.

 -  A potentially malicious URL click was detected
 -  Email reported by user as phish\*
 -  Email messages containing malware removed after delivery\*
 -  Email messages containing phish URLs removed after delivery\*
 -  Suspicious email sending patterns detected\#
 -  User restricted from sending email\#

> Note: The alerts listed above that are marked with an asterisk (\*) are assigned an Informational severity in the respective alert policies within the Security &amp; Compliance Center, with email notifications turned off. Email notifications can be turned on through Alert policy configuration. Alerts marked with a hash (\#) are generally available alerts associated with public preview playbooks.

### Security playbooks

Security playbooks are back-end policies that are at the heart of automation in Microsoft Threat Protection. The security playbooks provided in AIR are based on common, real-world security scenarios. A security playbook is launched automatically when an alert is triggered within your organization. Once the alert triggers, the associated playbook is run automatically. The playbook runs an investigation, looking at all the associated metadata (including email messages, users, subjects, senders, and so on). Based on the playbook's findings, AIR recommends a set of actions that your organization's security team can take to control and mitigate the threat.

The security playbooks that are provided with AIR are designed to tackle the most frequent threats that organizations face today. They are based on input from Security Operations and Incident Response teams, including those who help defend Microsoft and its customers' assets.
