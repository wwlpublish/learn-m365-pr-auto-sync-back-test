Here are some of the terms you should be familiar with as you use Compliance Manager to assign, test, and monitor your compliance activities:

- Controls
- Assessments
- Assessment templates
- Improvement actions

## Controls

A control is a requirement of a regulation, standard, or policy. It defines how you assess and manage system configuration, organizational process, and people responsible for meeting a specific requirement of a regulation, standard, or policy. Controls are organized into control families that align with the assessment structure for corresponding certifications or regulations. Based on the shared responsibility model for security and compliance in the cloud, controls can be:

- **Microsoft-managed controls:** Microsoft is responsible for these controls and provides detailed information on how they are implemented.
- **Your controls:** Sometimes referred to as customer-managed controls, these are controls your organization is responsible for implementing.
- **Shared controls:** These are controls that both your organization and Microsoft share responsibility for implementing.

For example, Compliance Manager includes a control with the title *Privacy Compliance - DLP Policies for Sensitive Data*, which is part of the *Privacy and Compliance* control family. It is a shared control since both your organization and Microsoft share the implementation responsibility.

## Assessments

An assessment is a grouping of controls designed to represent the regulations, standards, or policies your organization is subject to. Completing the actions within an assessment help you meet the requirements of a standard, regulation, or law. For instance, you may have an assessment that, when you complete all actions within it, helps to bring your Microsoft 365 environment in line with ISO 27001 requirements. Assessments have several components, including the following:

- **In-scope services:** Service or services applicable to the assessment.
- **Controls:** Requirements of a regulation, standard, or policy.
- **Improvement actions:** Activity that helps satisfy a control.
- **Assessment score:** Points achieved by completing actions within that assessment.

When creating an assessment, you will be asked to identify the group you want the assessment to be a part of. You can choose to use groups to organize assessments by year, area, compliance standard, or other way that helps you stay organized.

To take our example one step further, the *Privacy Compliance - DLP Policies for Sensitive Data* control is part of the *Data Protection Baseline* assessment in a group named *Default Group*. The Data Protection Baseline is a set of controls that includes key regulations and standards for data protection and general data governance.

## Assessment templates

Compliance Manager provides pre-configured templates that help you create assessments. Simply put, instantiated templates become assessments. These templates encompass industry and regional standards and regulations. You can use these templates as-is or modify them to meet your requirements. Data Protection Baseline, European Union GDPR, ISO 27001:2013, and NIST 800-53 Rev.4 assessment templates are included in selected Microsoft 365 SKUs, subject to your organization's licensing agreement. Additionally, your organization may choose to obtain one or more of the over 175 pre-built premium assessment templates. You can also create your own assessment templates using the guidance we provide.

In our example, the Data Protection Baseline *assessment template* was used to create the Data Protection Baseline *assessment.*
  
## Improvement actions

An improvement action is an activity that helps implement one or more controls. Each action provides information to help you align with regulations and standards. Improvement actions can be assigned to users in your organization to implement and test. Documentation can be stored, and action status can be recorded for auditing or other purposes.

In our example, besides the actions Microsoft has taken on your behalf, the three improvement actions your organization can take that align with the Privacy Compliance - DLP Policies for Sensitive Data control of the Data Protection Baseline are:

- Create DLP Policies for personal information.  
- Create customized DLP Policies for Company Sensitive Information.
- Create customized or use default DLP Policies for Personal Data.

## Control mapping

A single improvement action can help satisfy the requirements of more than one control. This is referred to as control mapping. The additional control or controls can be part of the same assessment or another assessment. This helps eliminate duplication of effort, increases efficiency, and saves time. To illustrate, completing one improvement action, Enable Multifactor Authentication, helps satisfy controls in 50 different regulations.

In our example, if we use the EU GDPR assessment template to add a second assessment to Compliance Manager, completing the improvement action Create customized DLP Policies for Company Sensitive information would help satisfy both the Privacy Compliance - DLP Policies for Sensitive Data control of the Data Protection Baseline and numerous EU GDPR controls including one with the title *Integrity and Confidentiality of Personal Data.*

## Action characteristics

There are a few different ways to classify improvement actions, including whether they are:

- Your improvement actions or Microsoft's improvement actions
- Technical or non-technical actions
- Mandatory or discretionary actions
- Preventative, detective, or corrective actions

Actions can be managed by your organization or by Microsoft. Microsoft completes the actions it manages on your behalf and provides details on how the action was implemented. Of course, your organization is responsible for taking the steps necessary to complete your actions.

*Technical actions* are implemented by interacting with technology. For example, *Create customized DLP policies for Company Sensitive Information* would be considered a technical action you would be responsible for completing in the Data Loss Prevention solution in the Microsoft 365 compliance center.

*Non-technical actions* are implemented in some way other than interacting with technology. An action with the name *Conduct exit interview upon termination* is a non-technical action. The act of conducting an exit interview, while it may involve the use of technology like Microsoft Teams, can be accomplished without using it. 

*Mandatory actions* cannot be bypassed either intentionally or accidentally. An example is a centrally managed password policy that sets requirements for password length, complexity, and expiration. Users must comply with these requirements to access the system.

*Discretionary actions* rely on users to understand policy and act accordingly. For example, a policy requiring users to lock their computer when they leave it unattended is discretionary because it relies on the user to do something. Another example of a discretionary action would be a policy requiring users to manually classify a document as confidential if it contains information that should not be shared.

*Preventative actions* address specific risks. For example, protecting information at rest using encryption is a preventative action against attacks and breaches. Separation of duties is a preventative action to manage conflict of interest and guard against fraud.

*Detective actions* actively monitor systems to identify irregular conditions or behaviors that represent risk, or that can be used to detect intrusions, or determine if a breach occurs. System access auditing and privileged administrative actions auditing are types of detective actions. Regulatory compliance audits are a type of detective action used to identify process issues.

*Corrective actions* try to keep the adverse effects of an incident to a minimum, take corrective action to reduce the immediate effect, and reverse the damage if possible. Privacy incident response is a corrective action to limit damage and restore systems to an operational state after a breach.

In our example, the *Create customized DLP Policies for Company Sensitive Information* improvement action is a *technical, mandatory,* and *preventative* improvement action managed by your organization.
