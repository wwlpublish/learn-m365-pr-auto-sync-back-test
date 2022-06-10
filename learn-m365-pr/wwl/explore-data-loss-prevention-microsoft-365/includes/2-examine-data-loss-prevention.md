Organizations have sensitive information under their control, such as financial data, proprietary data, credit card numbers, health records, and social security numbers. To help protect this sensitive data and reduce risk, they need a way to prevent their users from inappropriately sharing it with people who shouldn't have it. This practice is called data loss prevention (DLP).

In Microsoft Purview, data loss prevention is implemented by defining and applying DLP policies. With a DLP policy, you can identify, monitor, and automatically protect sensitive items across:

 -  Microsoft 365 services such as Teams, Exchange, SharePoint, and OneDrive
 -  Office applications such as Word, Excel, and PowerPoint
 -  Windows 10, Windows 11 and macOS (Catalina 10.15 and higher) endpoints
 -  non-Microsoft cloud apps
 -  on-premises file shares and on-premises SharePoint.

DLP detects sensitive items by using deep content analysis, not by just a simple text scan. Content is analyzed:

 -  for primary data matches to keywords.
 -  by the evaluation of regular expressions.
 -  by internal function validation.
 -  by secondary data matches that are in proximity to the primary data match.

DLP also uses machine learning algorithms and other methods to detect content that matches your DLP policies.

### DLP is part of the larger Microsoft Purview offering

DLP is just one of the Microsoft Purview tools that you'll use to help protect your sensitive items wherever they live or travel. You should understand the other tools in the Microsoft Purview tools set, how they interrelate, and work better together.

**Additional reading**. For more information about the Microsoft Purview Information Protection process, see [Microsoft Purview tools](/microsoft-365/compliance/protect-information?azure-portal=true).

### Protective actions of DLP policies

DLP policies are how you:

 -  Monitor the activities that users take on sensitive items at rest, sensitive items in transit, or sensitive items in use.
 -  Take protective actions.

For example, when a user attempts to take a prohibited action, like copying a sensitive item to an unapproved location or sharing medical information in an email or other conditions laid out in a policy, DLP can:

 -  show a pop-up policy tip to the user that warns them that they may be trying to share a sensitive item inappropriately.
 -  block the sharing and, via a policy tip, allow the user to override the block and capture the users' justification.
 -  block the sharing without the override option.
 -  for data at rest, sensitive items can be locked and moved to a secure quarantine location.
 -  for Teams chat, the sensitive information won't be displayed.

All DLP monitored activities are recorded to the Microsoft 365 Audit log by default. They're then routed to Activity Explorer, which provides a historical view of activities on your labeled content (Activity Explorer is covered later in this training). When a user performs an action that meets the criteria of a DLP policy, and you have alerts configured, DLP provides alerts in the DLP alert management dashboard.

### DLP lifecycle

A Microsoft Purview DLP implementation typically follows these major phases:

 -  Phase 1 - Plan for DLP
 -  Phase 2 - Prepare for DLP
 -  Phase 3 - Deploy your policies in production

Each of these phases is introduced in the following sections.

#### Phase 1 - Plan for DLP

DLP monitoring and protection are native to the applications that users use every day. This design helps to protect an organization's sensitive items from risky activities, even if its users are unaccustomed to data loss prevention thinking and practices.

If an organization and its users are new to data loss prevention practices, the adoption of DLP may require a change to its business processes. This scenario usually involves a culture shift for the organization's users. But, with proper planning, testing and tuning, an organization's DLP policies will protect its sensitive items while minimizing any potential business process disruptions.

Planning for data loss prevention should include the following facets:

 -  **Technology planning for DLP**. Keep in mind that DLP as a technology can monitor and protect your data at rest, data in use, and data in motion. There are planning implications for:
     -  the different locations.
     -  the type of data you want to monitor and protect.
     -  the actions to be taken when a policy match occurs.
 -  **Business processes planning for DLP**. DLP policies can block prohibited activities, like inappropriate sharing of sensitive information within email. As you plan your DLP policies, you must identify the business processes that touch your sensitive items. The business process owners can help you identify appropriate user behaviors that should be allowed and inappropriate user behaviors that should be protected against. You should plan your policies and deploy them in test mode. You should then evaluate their effect through Activity Explorer first, before applying them in more restrictive modes.
 -  **Organizational culture planning for DLP**. A successful DLP implementation is as much dependent on getting your users trained and acclimated to data loss prevention practices as it is on well planned and tuned policies. Since your users are heavily involved, be sure to plan for training for them too. You can strategically use policy tips to raise awareness with your users before changing the policy enforcement from test mode to more restrictive modes.

#### Phase 2 - Prepare for DLP

You can apply DLP policies to data at rest, data in use, and data in motion. Data can be in various locations, such as:

 -  Exchange Online email
 -  SharePoint Online sites
 -  OneDrive accounts
 -  Teams chat and channel messages
 -  Microsoft Cloud App Security
 -  Windows 10, Windows 11, and macOS (Catalina 10.15 and higher) devices
 -  On-premises repositories
 -  Power BI sites

Each location has different prerequisites. Sensitive items in some locations, like Exchange Online, can be brought under the DLP umbrella by configuring a policy that applies just to them. Other locations, such as on-premises file repositories, require a deployment of Azure Information Protection (AIP) scanner. You'll need to prepare your environment, create draft policies, and test them thoroughly before activating any blocking actions.

#### Phase 3 - Deploy your policies in production

Deploying DLP policies into an organization's production environment should include the following tasks:

 -  **Design your policies**. An organization should start by defining its control objectives, and how they apply across each respective workload. It should draft a policy that embodies its objectives. It should feel free to start with one workload at a time, or across all workloads - there's no effect yet.
 -  **Implement policy in test mode**. Evaluate the effect of the controls by implementing them with a DLP policy in test mode. An organization can apply the policy to all workloads in test mode. This practice enables it to receive the full breadth of results, but it can start with one workload if it wants to.
 -  **Monitor outcomes and fine-tune the policy**. While in test mode, an organization should monitor the outcomes of the policy and fine-tune it so that it meets the company's control objectives. While fine tuning, the organization should ensure it isn't adversely or inadvertently impacting valid user workflows and productivity. Some of the things to fine-tune may include:
     -  adjusting the locations and people/places that are in or out of scope.
     -  tune the conditions and exceptions that are used to determine if an item and what is being done with it matches the policy.
     -  the sensitive information definition/s.
     -  the actions.
     -  the level of restrictions.
     -  add new controls.
     -  add new people.
     -  add new restricted apps.
     -  add new restricted sites.

> [!NOTE]
> **Stop processing more rules** doesn't work in test mode, even when it's turned on.

Once the policy meets all the organization's objectives, the organization should turn on the policy. It should then continue to monitor the outcomes of the policy application and fine tune as needed.

> [!NOTE]
> In general, policies take effect about an hour after being turned on.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”

## Multiple Choice
Contoso is planning to implement Microsoft Purview Data Loss Prevention. It just finished planning its business processes for DLP. It created its policies and deployed them in test mode. What's the next step that it should complete?
( ) Apply the policies in more restrictive modes {{Incorrect. This action isn't the next step that Contoso should take as part of business process planning for DLP.}}
( ) Use policy tips to raise awareness with its users before changing the policy enforcement from test mode to more restrictive modes {{Incorrect. This action is part of the organizational culture planning for DLP.}}
(x) Use Activity Explorer to evaluate the effect of the policies {{Correct. In business process planning for DLP, you should plan your policies and deploy them in test mode. You should then evaluate their effect through Activity Explorer first, before applying them in more restrictive modes.}}

