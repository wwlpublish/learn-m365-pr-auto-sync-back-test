Your journey through identity protection typically starts with the Azure AD Identity Protection dashboard. The dashboard provides access to:

 -  Reports such as **Users flagged for risk**, **Risk events,** and **Vulnerabilities.**
 -  Settings such as the configuration of your **Security Policies**, **Notifications,** and **Multi-Factor Authentication registration.**

The dashboard is typically your starting point for an investigation, which is the process of reviewing the activities, logs, and other relevant information related to a risk event to decide whether remediation or mitigation steps are necessary, and to understand how the identity was compromised and used.

### Mitigation sign-in risk events

A sign-in risk level is an indication (High, Medium, or Low) of the likelihood that a sign-in attempt was ***not*** performed by the legitimate owner of a user account.

A mitigation is an action to limit the ability of an attacker to exploit a compromised identity or device without restoring the identity or device to a safe state. A mitigation doesn't resolve previous sign-in risk events associated with the identity or device.

To mitigate risky sign-in attempts automatically, you can configure sign-in risk security policies. Using these policies, you consider the risk level of the user or the sign-in to block risky sign-in attempts or require the user to do multi-factor authentication. These actions may prevent an attacker from exploiting a stolen identity to cause damage. They may also give you some time to secure the identity.

#### Mitigation best practices

Choosing a **High** threshold reduces the number of times a policy is triggered and minimizes the impact to users. However, it also excludes **Low** and **Medium** sign-ins flagged for risk from the policy, which may not block an attacker from exploiting a compromised identity.

Best practices to follow when setting a policy include:

 -  Exclude users who do not/cannot have multi-factor authentication.
 -  Exclude users in locales where enabling the policy isn't practical, such as locales with no access to a helpdesk.
 -  Exclude users who are likely to generate numerous false-positives, such as developers and security analysts.
 -  Use a **High** threshold during initial policy rollout, or if you must minimize challenges seen by end users.
 -  Use a **Low** threshold if your organization requires greater security. Selecting a **Low** threshold introduces other user sign-in challenges, but increased security.

To strike a balance between usability and security, the recommended default for most organizations is to configure a rule for a **Medium** threshold.

The sign-in risk policy is:

 -  Applied to all browser traffic and sign-ins using modern authentication.
 -  Not applied to applications using older security protocols by disabling the WS-Trust endpoint at the federated IDP, such as ADFS.

### User risk

All active risk events that were detected by Azure Active Directory for a user contribute to a logical concept called user risk. A user flagged for risk is an indicator of a user account that might have been compromised.

**Additional reading.** For more information, see [Azure Active Directory Identity Protection](/azure/active-directory/active-directory-identityprotection).

A user risk level is an indication (High, Medium, or Low) of the likelihood that the user’s identity has been compromised. It's calculated based on the user risk events that are associated with a user's identity.

The status of a risk event is either **Active** or **Closed**. Only risk events that are **Active** contribute to the user risk level calculation.

The user risk level is calculated using the following inputs:

 -  Active risk events impacting the user.
 -  Risk level of these events.
 -  Remediation actions have been taken.

You can use the user risk levels to create conditional access policies that block risky users from signing in or force them to securely change their password.

### Closing risk events manually

Organizations usually take remediation actions such as a secure password reset to automatically close risk events. However, remediation actions may not always be possible, such as when:

 -  A user with Active risk events has been deleted.
 -  An investigation reveals that a reported risk event has been performed by the legitimate user.

Because risk events that are **Active** contribute to the user risk calculation, you may have to manually lower a risk level by closing risk events manually.

During an investigation, you can choose to take one of the following actions to change the status of a risk event:

 -  **Resolve**. If you took an appropriate remediation action outside Azure Identity Protection after investigating a risk event and you believe the risk event should be considered closed, mark the event as Resolved. Resolved events will set the risk event’s status to Closed and the risk event will no longer contribute to user risk.
 -  **Mark as false-positive**. In some cases, you may investigate a risk event and discover that it was incorrectly flagged as a risk. You can help reduce the number of such occurrences by marking the risk event as False-positive. Identifying risk events as False-positive helps the machine learning algorithms to improve the classification of similar events in the future. The status of false-positive events is changed to **Closed,** and they'll no longer contribute to user risk.
 -  **Ignore**. If you haven't taken any remediation action but you want the risk event to be removed from the active list, you can mark a risk event **Ignore** and the event status will be automatically changed to **Closed**. Because ignored events don't contribute to user risk, they should only be used under unusual circumstances.
 -  **Reactivate**. Risk events that were manually closed (by choosing **Resolve**, **False positive**, or **Ignore**) can be reactivated by setting the event status back to **Active**. Reactivated risk events contribute to the user risk level calculation. Risk events closed through remediation (such as a secure password reset) cannot be reactivated.

### Remediating user risk events

A remediation is an action to secure an identity or a device that was previously suspected or known to be compromised. A remediation action restores the identity or device to a safe state, and it resolves previous risk events associated with the identity or device.

To remediate user risk events, you can:

 -  Complete a secure password reset to remediate user risk events manually.
 -  Configure a user risk security policy to mitigate or remediate user risk events automatically.
 -  Reimage the infected device.

### Azure Identity Protection notifications

Azure Identity Protection sends two types of automated notification emails to help you manage user risk and risk events:

 -  Users at risk detected email
 -  Weekly digest email

In response to a detected account at risk, AIP generates an email alert with **Users at risk detected** as the email Subject. The email includes a link to the **Users flagged for risk** report. As a best practice, you should immediately investigate the users at risk.

### Azure Active Directory Identity Protection playbook

The playbook helps you understand how Azure Identity Protection works and simulates risk events and vulnerabilities. You can also set up risk-based conditional access policies and test the impact of these policies.

**Additional reading.** For more information, see [Azure Active Directory Identity Protection playbook](/azure/active-directory/active-directory-identityprotection-playbook).
