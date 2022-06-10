The prior unit examined the high-level tasks necessary to implement security and compliance within Microsoft 365. This unit focuses on a specific aspect within those tasks, which involves the compliance tasks that should be completed within Microsoft Purview.

If you're new to Microsoft Purview and wondering where to start, this unit provides guidance on the basics and prioritizes important compliance tasks. This unit will help you quickly get started with:

 -  managing and monitoring your data.
 -  protecting information.
 -  minimizing insider risks.

This unit is also helpful if you're figuring out how best to:

 -  manage risks.
 -  protect your data.
 -  remain compliant with regulations and standards with a newly remote workforce.

Employees are now collaborating and connecting with each other in new ways. As such, an organization's existing compliance processes and controls may need to adapt. Identifying and managing these new compliance risks within an organization is critical to safeguarding its data and minimizing threats and risks.

After an organization has completed these basic compliance tasks, it should consider expanding its compliance coverage by implementing more Microsoft Purview solutions.

### Task 1: Configure compliance permissions

The Microsoft Purview compliance portal provides easy access to the data and tools an organization needs to manage its compliance needs. It’s important to manage who in an organization has access to the Microsoft Purview compliance portal to view content and perform management tasks. Microsoft 365 provides administrative roles specific to compliance and for using the tools included in the Microsoft Purview compliance portal.

An organization should start by assigning compliance permissions to the appropriate people. By doing so, they can perform these tasks and prevent unauthorized people from having access to areas outside of their responsibilities. An organization should ensure that it's assigned the proper people to the **Compliance data administrator** and the **Compliance administrator** roles before it starts to configure and implement compliance solutions included with Microsoft 365. It must also assign users to the **Azure Active Directory global reader** role to view data in the Compliance Manager tool.

### Task 2: Know your state of compliance

It’s difficult to know where to go if you don’t know where you are. To meet its compliance needs, an organization must understand its current level of risk and what updates it may need in these ever changing times. Whether an organization is new to compliance requirements or has deep experience with standards and regulations that govern its industry, the single best thing it can do to improve compliance is to understand its current state of compliance.

Microsoft Purview Compliance Manager can help an organization understand its compliance posture. It can also highlight areas that may need improvement. Compliance Manager uses a centralized dashboard to calculate a risk-based score, measuring an organization's progress in completing actions that help reduce risks around data protection and regulatory standards. Compliance Manager can also be used to track an organization's risk assessments. It provides workflow capabilities to help an organization efficiently complete its risk assessments through a common tool.

> [!IMPORTANT]
> Security and compliance are tightly integrated for most organizations. It’s important that an organization address basic security, threat protection, and identity and access management areas. Doing so will help it provide a defensive, in-depth approach to both security and compliance. Organizations should check their compliance score in Compliance Manager. They should then complete the tasks outlined in the following articles: [Security roadmap - Top priorities for the first 30 days, 90 days, and beyond](/microsoft-365/security/office-365-security/security-roadmap?azure-portal=true) and [Top 12 tasks for security teams to support working from home](/microsoft-365/security/top-security-tasks-for-remote-work?azure-portal=true).

**Additional reading**. For step-by-step guidance to get started with Compliance Manager, see [Get started with Compliance Manager](/microsoft-365/compliance/compliance-manager-setup?azure-portal=true).

### Task 3: Enable auditing for your organization

At this point, an organization should have determined its current state and assigned permissions to the users who can manage compliance functions. The next step is to ensure it has the data to conduct compliance investigations and generate reports for network and user activities. Enabling auditing is also an important prerequisite for compliance solutions covered later in this unit.

Insights provided by the audit log are a valuable tool in helping to match an organization's compliance requirements to solutions that can help it manage and monitor compliance areas needing improvement. Audit logging must be enabled before activities are recorded and before an organization can search the audit log. When enabled, user and admin activity is recorded in the audit log and retained for 90 days. It can also be retained up to one year depending on the license assigned to users.

**Additional reading**. For step-by-step instructions to turn on auditing, see [Turn audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off?azure-portal=true).

### Task 4: Create policies to alert you about potential compliance issues

Microsoft provides several built-in alert policies that help identify:

 -  permissions abuse by administrators
 -  malware activity
 -  potential external and internal threats
 -  information governance risks

These policies are turned on by default. However, an organization may need to configure custom alerts to help manage specific compliance requirements.

Alert policy and alert dashboard tools can be used to create custom alert policies. They can also be used to view the alerts generated when users perform activities that match the policy conditions. For example, an organization can use alert policies to track user and admin activities affecting compliance requirements, permissions, and data loss incidents.

**Additional reading**. For step-by-step guidance to create custom alert policies, see [Alert policies in Microsoft 365](/microsoft-365/compliance/alert-policies?azure-portal=true).

### Task 5: Classify and protect sensitive data

Users in an organization often collaborate with others both inside and outside their company. By doing so, content no longer stays behind a firewall. It can roam everywhere, across devices, apps, and services. And when it roams, organizations want it to do so in a secure, protected way that meets their business and compliance policies.

Sensitivity labels let organizations classify and protect their data. In doing so, these labels ensure that user productivity and their ability to collaborate isn't hindered. Sensitivity labels can be used to:

 -  enforce message encryption.
 -  enforce usage restrictions.
 -  apply visual markings.
 -  protect information across platforms and devices, on-premises and in the cloud.

**Additional reading**. For step-by-step guidance to configure and use sensitivity labels, see [Get started with sensitivity labels](/microsoft-365/compliance/get-started-with-sensitivity-labels?azure-portal=true).

### Task 6: Configure retention policies

A retention policy lets you proactively decide whether to retain content, delete content, or both retain content and then delete the content at the end of a specified retention period. These actions may be needed to comply with industry regulations and internal policies. They can also reduce an organization's risk if it's involved in litigation or a security breach.

When content is subject to a retention policy, people can continue to edit and work with the content as if nothing's changed. The content is retained in place, in its original location. But if someone edits or deletes content that's subject to the retention policy, a copy of the original content is saved to a secure location. It's retained in that location while the retention policy for that content is in effect.

An organization can quickly put retention policies in place for multiple services in its Microsoft 365 environment. These services include:

 -  Teams and Yammer messages
 -  Exchange email
 -  SharePoint sites
 -  OneDrive accounts

There are no limits to the number of users, mailboxes, or sites that a retention policy can automatically include. But if an organization needs to get more selective, it can do so by configuring either:

 -  an adaptive scope that's query-based to dynamically target specific instances.
 -  a static scope that specifies specific instances to always include or always exclude.

**Additional reading**. For step-by-step guidance to configure retention policies, see [Create and configure retention policies](/microsoft-365/compliance/create-retention-policies?azure-portal=true). Because retention policies form the cornerstone of a data lifecycle management strategy for Microsoft 365 apps and services, also see [Get started with data lifecycle management](/microsoft-365/compliance/get-started-with-data-lifecycle-management?azure-portal=true).

### Task 7: Configure sensitive information and offensive language policies

Protecting sensitive information and detecting and acting on workplace harassment incidents is an important part of compliance with internal policies and standards. Communication compliance in Microsoft 365 helps minimize these risks by helping organizations quickly detect, capture, and take remediation actions for email and Microsoft Teams communications. These risks include:

 -  Inappropriate communications containing profanity, threats, and harassment.
 -  Communications that share sensitive information inside and outside of the organization.

A pre-defined **Offensive language and anti-harassment** policy template enables organizations to scan internal and external communications for policy matches so they can be examined by designated reviewers. Reviewers can investigate scanned email, Microsoft Teams, Yammer, or third-party communications in their organization. They can also take appropriate remediation actions to make sure they're compliant with their organization's standards.

The pre-defined **Sensitive information** policy template helps organizations quickly create a policy to scan email and Microsoft Teams communications containing defined sensitive information types or keywords. By doing so, the policy can help ensure that important data isn't shared with people that shouldn't have access. These activities could include unauthorized communication about confidential projects or industry-specific rules on insider trading or other collusion activities.

**Additional reading**. For step-by-step guidance to plan and configure communication compliance, see [Plan for communication compliance](/microsoft-365/compliance/communication-compliance-plan?azure-portal=true) and [Get started with communication compliance](/microsoft-365/compliance/communication-compliance-configure?azure-portal=true). For communication compliance licensing information, see [Microsoft 365 licensing guidance for security &amp; compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance?azure-portal=true).

### Task 8: See what's happening with your sensitive items

Sensitivity labels, sensitive information types, retention labels and policies, and trainable classifiers can be used to classify and label sensitive items across Exchange, SharePoint, and OneDrive. The last step in your quick task journey is to see which items have been labeled and what actions your users are taking on those sensitive items. Content explorer and Activity explorer provide this visibility.

#### Content explorer

Content explorer enables an organization to view, in their native format, all the items that:

 -  Are classified as a sensitive information type.
 -  Belong to a certain classification by a trainable classifier.
 -  Have a sensitivity or retention label applied.

**Additional reading**. For step-by-step guidance to using content explorer, see [Know your data - data classification overview](/microsoft-365/compliance/data-classification-overview?azure-portal=true), and [Get started with content explorer](/microsoft-365/compliance/data-classification-content-explorer?azure-portal=true).

#### Activity explorer

Activity explorer helps an organization monitor what's being done with its classified and labeled sensitive items across:

 -  SharePoint
 -  Exchange
 -  OneDrive

There are over 30 different filters available for use, including:

 -  date range
 -  activity type
 -  location
 -  user
 -  sensitivity label
 -  retention label
 -  file path
 -  DLP policy

**Additional reading.** For step-by-step guidance to using activity explorer, see [Get started with activity explorer](/microsoft-365/compliance/data-classification-activity-explorer?azure-portal=true).
