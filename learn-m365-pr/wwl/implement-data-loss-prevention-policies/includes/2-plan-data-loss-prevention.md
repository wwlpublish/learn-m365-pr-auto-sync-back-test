Organizations have sensitive information under their control. This information includes financial data, proprietary data, credit card numbers, health records, social security numbers, and so on. To help protect this sensitive data and reduce risk, they need a way to prevent their users from inappropriately sharing it with people who shouldn't have it. This practice is called data loss prevention (DLP).

In Microsoft Purview, you implement data loss prevention by defining and applying DLP policies. With a DLP policy, you can identify, monitor, and automatically protect sensitive items across:

 -  Microsoft 365 services such as Teams, Exchange, SharePoint, and OneDrive
 -  Office applications such as Word, Excel, and PowerPoint
 -  Windows 10, Windows 11 and macOS (Catalina 10.15 and higher) endpoints
 -  Non-Microsoft cloud apps
 -  On-premises file shares and on-premises SharePoint

Microsoft Purview DLP detects sensitive items by using deep content analysis rather than just a simple text scan. It analyzes content by:

 -  looking for primary data matches to keywords.
 -  evaluating regular expressions.
 -  validating internal functions.
 -  looking for secondary data matches that are in proximity to the primary data match.

DLP also uses machine learning algorithms and other methods to detect content that matches an organization's DLP policies.

### Multiple starting points

Every organization will plan for and implement data loss prevention (DLP) differently. Why? Because every organization's business needs, goals, resources, and situation are unique to them. However, there are elements that are common to all successful DLP implementations. This unit presents the best practices that are used by organizations in their DLP planning.

Many organizations choose to implement DLP to comply with various governmental or industry regulations. Organizations also implement data loss prevention to protect their intellectual property. But the starting place and ultimate destination in the DLP journey vary from one organization to another.

Organizations can start their DLP journey in various ways. For example:

 -  From a platform focus, they want to protect information in Teams Chat and Channel messages or on Windows devices.
 -  They know what sensitive information they want to prioritize protecting, like health care records. Given this information, they may go straight to defining policies to protect it.
 -  They may not know what their sensitive information is, where it is, and who is doing what with it. As such, they start with discovery and categorization and take a more methodical approach.
 -  They may not know what their sensitive information is, where it is, or who is doing what with it. Even without this information, they may still move straight to defining policies. From there, they'll use those outcomes as a starting place and then refine their policies from there.
 -  They want to implement the full Microsoft Purview Information Protection stack. As such, they intend to take a longer, more methodical approach to DLP implementation.

These examples are just some ways in which customers can approach DLP. It doesn't matter where an organization starts from. Microsoft Purview DLP is flexible enough to accommodate various types of information protection journeys - from their start, to a fully realized data loss prevention strategy.

### Overview of the Microsoft Purview DLP planning process

There are three different aspects of the Microsoft Purview DLP planning process. Each of these considerations is examined in the following sections.

#### Identify stakeholders

When implemented, DLP policies can be applied across large portions of an organization. IT can't develop a broad ranging plan on their own without negative consequences. Instead, an organization must identify the stakeholders who can:

 -  describe the regulations, laws, and industry standards the organization is subject to.
 -  the categories of sensitive items to be protected.
 -  the business processes they're used in.
 -  the risky behavior that should be limited.
 -  prioritize which data should be protected first based on the sensitivity of the items and risk involved.
 -  outline the DLP policy match event review and remediation process.

In general, these needs tend to be 85% regulatory and compliance protection, and 15% intellectual property protection. Here are some suggestions on roles to include in an organization's planning process:

 -  Regulatory and compliance officers
 -  Chief risk officer
 -  Legal officers
 -  Security and compliance officers
 -  Business owners for the data items
 -  Business users
 -  IT

#### Describe the categories of sensitive information to protect

The stakeholders then describe the categories of sensitive information to be protected and the business process that they're used in. For example, DLP may define the following categories:

 -  Financial
 -  Medical and health information
 -  Privacy
 -  Custom

The stakeholders may identify the sensitive information as "We're a data processor, so we must implement privacy protections on data subject information and financial information".

#### Set goals and implementation plan

Once an organization has identified its stakeholders and it knows which sensitive information needs protection and where it's used:

 -  The stakeholders can set their protection goals.
 -  IT can develop an implementation plan.

An organization's implementation plan should include:

 -  Mapping out its starting state and desired end state and the steps to get from one to the other.
 -  How it will address discovery of sensitive items.
 -  Policy planning and the order they'll be implemented.
 -  How it will address any prerequisites.
 -  Planning on how policies will first be tested before moving to enforcement.
 -  How it will train its end users.
 -  How it will test and tune its policies.
 -  How it will review and update its data loss prevention strategy based on changing regulatory, legal, industry standard or intellectual property protection and business needs.

#### Map out path from start to desired end state

Why is it essential for an organization to document how it's going to get from its starting state to the desired end state? Because documentation is key to communicating with its stakeholders and setting the project scope.

The following diagram displays a set of steps that are commonly used to deploy DLP. You'll want more detail than what's provided here, but you can use this outline to frame your DLP adoption path.

:::image type="content" source="../media/dlp-deployment-planning-234bbd15.png" alt-text="Diagram showing the common order of tasks that are required to deploy data loss protection.":::


#### Sensitive item discovery

There are multiple ways to discover what individual sensitive items are and where they're located. An organization may have sensitivity labels already deployed. Or, it may have decided to deploy a broad DLP policy to all locations that only discovers and audits items. To learn more, see [Know your data](/microsoft-365/compliance/information-protection?azure-portal=true).

#### Policy planning

As organizations begin their DLP adoption, they can use the following questions to focus their policy design and implementation efforts.

| **Question**                                                                      | **Answer**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | **Example**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| What laws, regulations and industry standards must your organization comply with? | Because many organizations come to DLP with the goal of regulatory compliance, answering this question is a natural starting place for planning their DLP implementation. But, as the IT implementer, you're probably not positioned to answer it. It needs to be answered by your legal team and business executives.                                                                                                                                                                                                                                                                                                                                                                                             | Your organization is subject to U.K. financial regulations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| What sensitive items does your organization want to protect from leakage?         | Once an organization knows where it stands in terms of regulatory compliance needs, it will have some idea of:<br><br>\- The sensitive items that must be protected from leakage.<br>\- How it wants to prioritize policy implementation to protect them.<br><br>This information will help it choose the most appropriate DLP policy templates. Microsoft Purview comes with pre-configured DLP templates for Financial, Medical and health, and Privacy. An organization can also build its own template using the Custom template feature. As an organization designs and creates its actual DLP policies, knowing the answer to this question will also help it choose the correct sensitive information type. | To get started quickly, you pick the U.K. Financial Data policy template. This template includes the Credit Card Number, EU Debit Card Number, and SWIFT Code sensitive information types.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Where are the sensitive items and what business processes are they involved in?   | The items that contain an organization's sensitive information are used every day in the course of doing business. An organization must know where instances of that sensitive information may occur, and what business processes they're used in. Knowing this information will help it choose the right locations in which to apply its DLP policies. DLP policies can be applied to the following locations:<br><br>\- Exchange email<br>\- SharePoint sites<br>\- OneDrive accounts<br>\- Teams chat and channel messages<br>\- Windows 10 and 11 Devices<br>\- Microsoft Defender for Cloud Apps<br>\- On-premises repositories<br>                                                                           | Your organizations' internal auditors are tracking a set of credit card numbers. They keep a spreadsheet of them in a secure SharePoint site. Several of the employees make copies and save them to their work OneDrive for Business site, which is synced to their Windows 10 and 11 devices. One of them pastes a list of 14 credit card numbers in an email and tries to send it to the outside auditors for review.<br><br>You want to apply the policy to the secure SharePoint site, all the internal auditors' OneDrive for Business accounts, their Windows 10 and 11 devices, and Exchange email.                                                                                                                                                                                                                                                                                                                                                                            |
| What is your organization's tolerance for leakage?                                | Different groups in your organization may have different views on what's an acceptable level of sensitive item leakage and what's not. Achieving the perfection of zero leakage may come at too high a cost to the business.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Your organizations' security group, along with the legal team, both feel there should be no sharing of credit card numbers with anyone outside the organization. It insists on zero leakage. But, as part of its regular review of credit card number activity, the internal auditors must share some credit card numbers with third-party auditors.<br><br>If your DLP policy prohibits all sharing of credit card numbers outside the organization, there will be a significant business process disruption. There will also be an added cost to mitigate the disruption in order for the internal auditors to complete their tracking. However, this extra cost is unacceptable to the executive leadership.<br><br>To resolve this situation, there must be an internal conversation to decide an acceptable level of leakage. Once that's decided, the policy can provide exceptions for certain individuals to share the information. Or, it can be applied in audit only mode. |

#### Planning for prerequisites<br>

Before an organization can monitor DLP locations, there are prerequisites that must be met. For more information, see the **Before you begin** section in the following articles:

 -  [Get started with the data loss prevention on-premises scanner](/microsoft-365/compliance/dlp-on-premises-scanner-get-started?azure-portal=true).
 -  [Get started with Endpoint data loss prevention](/microsoft-365/compliance/endpoint-dlp-getting-started?azure-portal=true).
 -  [Get started with the Microsoft compliance extension](/microsoft-365/compliance/dlp-chrome-get-started?azure-portal=true).
 -  [Use data loss prevention policies for non-Microsoft cloud apps](/microsoft-365/compliance/dlp-use-policies-non-microsoft-cloud-apps?azure-portal=true).

#### Policy deployment

When an organization creates its DLP policies, it should consider rolling them out gradually to assess their effect. It should also test their effectiveness before fully enforcing them. For example, an organization doesn't want a new DLP policy to unintentionally block access to thousands of documents or to break an existing business process.

If an organization is creating DLP policies with a large potential effect, it's recommended that it follow this sequence:

1.  **Start in Test mode without Policy Tips.** By doing so, the organization can use the DLP reports and any incident reports to assess the effect. It can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, it can fine-tune the policies as needed. In test mode, DLP policies won't affect the productivity of people working in the organization. This stage should also be used to test the organization's workflow for DLP event review and issue remediation.
2.  **Move to Test mode with notifications and Policy Tips**. Doing so will enable an organization to begin teaching users about its compliance policies. It will also prepare them for the policies that are going to be applied. It's useful to have a link to an organization policy page that provides more details about the policy in the policy tip. At this stage, the organization can also ask users to report false positives so that it can further refine the policies. An organization should move to this stage once it has confidence the results of its policy application match what the stakeholders had in mind.
3.  **Start full enforcement on the policies**. By doing so, the actions in the rules will be applied and the content will be protected. Continue to monitor the DLP reports and any incident reports or notifications. When doing so, ensure the results are what was intended.
    
    :::image type="content" source="../media/dlp-policy-deployment-options-cec65ae9.png" alt-text="Screenshot of the dialog box from the policy wizard asking whether you want to turn on the policy now or test it out first.":::
    
    
    An organization can turn off a DLP policy at any time, which affects all rules in the policy. However, each rule can also be turned off individually by toggling its **Status** in the rule editor.
    
    :::image type="content" source="../media/dlp-policy-status-toggle-switch-834a710e.png" alt-text="Screenshot of the dialog box from the policy wizard in which you can identify the types of sensitive information you want to protect.":::
    
    
    An organization can also change the priority of multiple rules in a policy. To do that, open a policy for editing. In the row for a rule, select the appropriate Up or Down arrow to rearrange the order of the rules.
    
    :::image type="content" source="../media/dlp-set-rule-priority-a8145801.png" alt-text="Screenshot of the dialog box from the policy wizard in which you can identify the types of sensitive information you want to protect.":::
    

#### End-user training

When a DLP policy is triggered, an organization can configure its policies to [Send email notifications and show policy tips for DLP policies](/microsoft-365/compliance/use-notifications-and-policy-tips?azure-portal=true) to admins and end users. Policy tips are useful ways to raise awareness of risky behaviors on sensitive items and train users to avoid those behaviors in the future. This design is especially true while an organization's policies are still in test mode and before they're set to enforce a blocking action.

#### Review DLP requirements and update strategy

The regulations, laws, and industry standards that an organization is subject to will change over time. An organization's business goals for DLP will also change. An organization should include regular reviews of all these areas so that it stays in compliance, and its DLP implementation continues to meet its business needs.

### Approaches to deployment

The following table identifies sample scenarios for three fictitious companies. The scenarios describe the business needs for each company. These business needs are real-world requirements taken from real-world implementations. For each company, the table also identifies the approach it should consider when implementing DLP to meet its business needs.

| **Description of the customer's business needs**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | **DLP implementation approach**                                                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Contoso Bank** is in a highly regulated industry and has many different types of sensitive items in many different locations. The company:<br>\- knows which types of sensitive information are top priority.<br>\- must minimize business disruption as policies are rolled out.<br>\- has IT resources and can hire experts to help plan, design, and deploy.<br>\- has a premier support contract with Microsoft.                                                                                                                                                                                                                         | - Take the time to understand what regulations it must comply with and how it's going to comply.<br>\-Take the time to understand the better value of the Microsoft Purview Information Protection stack.<br>\- Develop sensitivity labeling scheme for prioritized items and apply them.<br>\- Involve business process owners.<br>\- Design/code policies, deploy in test mode, and train users.<br>\- Repeat. |
| **Lucerne Publishing** doesn’t know what it has or where it is. It also has little to no resource depth. It extensively uses Teams, OneDrive for Business, and Exchange.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | - Start with simple policies on the prioritized locations.<br>\- Monitor what gets identified.<br>\- Apply sensitivity labels accordingly.<br>\- Refine policies and train users.                                                                                                                                                                                                                                |
| **Fabrikam** is a small startup. It wants to protect its intellectual property, but it must move quickly. It's willing to dedicate some resources to implementing DLP, but it can't afford to hire outside experts. Fabrikam is currently facing the following issues:<br>\- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint.<br>\- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use, and DropBox and Google drive to share/store items.<br>\- Employees value speed of work over data protection discipline.<br>\- It splurged and bought all 18 employees new Windows 11 devices. | - Take advantage of the default DLP policy in Microsoft Teams.<br>\- Use the **Restricted by default** setting for SharePoint items.<br>\- Deploy policies that prevent external sharing.<br>\- Deploy policies to prioritized locations.<br>\- Deploy policies to Windows 11 devices.<br>\- Block uploads to non-OneDrive for Business cloud storage.                                                           |

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”