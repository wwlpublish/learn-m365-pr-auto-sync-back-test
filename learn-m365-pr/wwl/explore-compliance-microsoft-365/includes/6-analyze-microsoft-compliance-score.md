The Compliance Manager dashboard displays an organization's overall compliance score. This score measures a company's progress in completing recommended improvement actions within controls. Its score can help it understand its current compliance posture. It can also help the company prioritize actions based on their potential to reduce risk.

A score value is assigned at three levels:

 -  **Improvement action score**. Each action has a different effect on a company's overall score. Its effect depends on the potential risk involved with the action.
 -  **Control score**. This score is the sum of points earned by completing improvement actions within the control. This sum is applied in its entirety to the company's overall compliance score when the control meets both of the following conditions:
     -  Implementation Status equals **Implemented** or **Alternative Implementation.**
     -  Test Result equals **Passed**.
 -  **Assessment score**. This score is the sum of the control scores. It's calculated using action scores. Each Microsoft action and each improvement action managed by and organization is counted once, regardless of how often it's referenced in a control.

The overall compliance score is calculated using action scores:

 -  Each Microsoft action is counted once.
 -  Each technical action the company manages is counted once.
 -  Each non-technical action the company manages is counted once per group.

This logic is designed to provide the most accurate accounting of how actions are implemented and tested in an organization.

> [!NOTE]
> You may notice that this design can cause your overall compliance score to differ from the average of your assessment scores. For more information, see the section below on how score values are determined.

### Initial score based on Microsoft 365 data protection baseline

Compliance Manager gives an organization an initial score based on the Microsoft 365 data protection baseline. This baseline is a set of controls that includes key regulations and standards for data protection and general data governance. This baseline draws elements primarily from:

 -  NIST CSF (National Institute of Standards and Technology Cybersecurity Framework)
 -  ISO (International Organization for Standardization)
 -  FedRAMP (Federal Risk and Authorization Management Program)

A company's initial score is calculated according to the default Data Protection Baseline assessment provided to all organizations. Upon a company's first visit, Compliance Manager is already collecting signals from its Microsoft 365 solutions. An organization can see at a glance how it's performing relative to key data protection standards and regulations. It can also see suggested improvement actions to take.

Because every organization has specific needs, Compliance Manager relies on each organization to set up and manage assessments. These assessments should be designed to minimize and mitigate risk as comprehensively as possible.

### How Compliance Manager continuously assesses controls

Compliance Manager automatically identifies settings in an organization's Microsoft 365 environment that help determine when certain configurations meet improvement action implementation requirements. Compliance Manager detects signals from other compliance solutions the company may have deployed, such as:

 -  data lifecycle management
 -  information protection
 -  communication compliance
 -  insider risk management

Compliance Manager also applies compliance score monitoring of complementary improvement actions.

An organization's action status is updated on its Compliance Manager dashboard within 24 hours of a change being made. Once an organization follows a recommendation to implement a control, it will typically see the control status updated the next day.

For example, if a company turns on multi-factor authentication (MFA) in the Azure AD portal, Compliance Manager detects the setting and reflects it in the control access solution details. Conversely, if a company doesn't turn on MFA, Compliance Manager flags that as a recommended action for you to take.

### Action types and points

Compliance Manager tracks two types of actions:

 -  **Your improvement actions**. Actions that your organization manages.
 -  **Microsoft actions**. Actions that Microsoft manages.

Both types of actions have points that count toward a company's overall score when completed.

### Technical and non-technical actions

Actions are grouped by whether they're technical or non-technical in nature. The scoring effect of each action differs by type.

 -  **Technical actions**. These actions are implemented by interacting with the technology of a solution (for example, changing a configuration). The points for technical actions are granted once per action, regardless of how many groups it belongs to.
 -  **Non-technical actions**. These actions are managed by an organization and implemented in ways other than working with the technology of a solution. There are two types of non-technical actions: documentation and operational. The points for these actions are applied to the company's compliance score at a group level. This rule means that if an action exists in multiple groups, the company will receive the action's point value each time it implements it within a group.

#### Example of how technical and non-technical actions are scored

Let's look at an example to see how the scoring mechanism for technical and non-technical actions applies in a real-world scenario. In this example, let's say that Contoso has:

 -  A technical action worth three points that exists in five groups.
 -  A non-technical action worth three points that exists in the same five groups.

If Contoso successfully implements the technical action, the total number of points it receives is three. Why only three points? Because Contoso only needs to implement the action once for its tenant. The implementation and test status for the technical action will show the same in all instances of that action, in every group it belongs to.

If Contoso successfully implements the non-technical action in each of the five groups, the total number of points it receives is 15. Why 15 and not three? Because Contoso must implement the action in each group; as such, it receives the points for the action (three) each time it completes the action (in each of the five groups). The implementation and test status for the non-technical action will differ across groups because the action is implemented separately within each of its groups.

This scoring logic is designed to provide the most accurate accounting of how actions are implemented and tested in an organization.

### How score values are determined

Actions are assigned a score value based on whether they’re mandatory or discretionary, and whether they’re preventative, detective, or corrective.

#### Mandatory and discretionary actions

 -  **Mandatory actions**. These actions can't be bypassed, either intentionally or accidentally. An example of a mandatory action is a centrally managed password policy that sets requirements for password length, complexity, and expiration. Users must follow each of these requirements to access the system.
 -  **Discretionary actions**. These actions rely upon users to understand and adhere to a policy. For example, a policy requiring users to lock their computer when they leave is a discretionary action because it relies on the user.

#### Preventative, detective, and corrective actions

 -  **Preventative actions**. These actions address specific risks. For example, protecting information at rest using encryption is a preventative action against attacks and breaches. Separation of duties is a preventative action to manage conflict of interest and guard against fraud.
 -  **Detective actions**. These actions actively monitor systems to identify irregular conditions or behaviors that represent risk, or that can be used to detect intrusions or breaches. Examples include system access auditing and privileged administrative actions. Regulatory compliance audits are a type of detective action used to find process issues.
 -  **Corrective actions**. These actions try to keep the adverse effects of a security incident to a minimum, take corrective action to reduce the immediate effect, and reverse the damage if possible. Privacy incident response is a corrective action to limit damage and restore systems to an operational state after a breach.

The following table identifies how each action has an assigned value in Compliance Manager based on the risk it represents. Since each type of action (preventative, detective, and corrective) can be both mandatory and discretionary, there are six total combinations of actions that can be scored.

| **Type**                   | **Assigned score** |
| -------------------------- | ------------------ |
| Preventative mandatory     | 27                 |
| Preventative discretionary | 9                  |
| Detective mandatory        | 3                  |
| Detective discretionary    | 1                  |
| Corrective mandatory       | 3                  |
| Corrective discretionary   | 1                  |

:::image type="content" source="../media/compliance-score-action-scoring-b26923ac.png" alt-text="Diagram showing a graphical chart of the Compliance Manager action point values.":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”