Organizations today are using a diverse tool set. There's the team of developers using team chat, the executives sending email, and the entire organization connecting over enterprise social.  

Collaboration governance is how you uniformly manage user access, ensure security, and service compliance needs. Follow these basic steps to create your governance plan:
    
‎:::image type="content" source="../media/collaboration-governance-steps.png" alt-text="Collaboration governance planning step-by-step":::

1. Consider key business goals and processes - create your governance plan to meet the needs of your business.

2. Understand settings in services - settings in groups and SharePoint interact with each other, as do settings in groups, SharePoint, and Teams and other services. Be sure to understand these interactions as you plan your governance strategy.

3. Plan to manage user access - plan the level of access you want to grant users in groups, SharePoint, and Teams.

4. Plan to manage compliance settings - review the available compliance options for Microsoft 365 groups, Teams, and SharePoint collaboration.
5. Plan to manage communications - review the available communications governance options for collaboration scenarios.
6. Plan for organization and lifecycle governance - choose the policies you want to use for group and team creation, naming, expiration, and archiving. Also, understand the end of lifecycle options for groups, teams, and Yammer
    
Microsoft 365 has a rich set of tools to implement any governance capabilities. 

‎:::image type="content" source="../media/governance-capabilities.png" alt-text="Microsoft 365 governance capabilities":::


## Group and team creation, naming, classification, and guest access

Your organization might require that you implement strict controls on how teams are named and classified, whether guests can be added as team members, and who can create teams. You can configure these areas by using Azure Active Directory (Azure AD) and sensitivity labels. Key decision points to consider:

* Does your organization require a specific naming convention for teams?
* Do team creators need the ability to assign organization-specific classifications to teams?
* Do you need to restrict the ability to add guests to teams on a per-team basis?
* Does your organization require limiting who can create teams?


| **Capability**| **Details**| **Azure AD Premium license required**| **When to use** |
| - |-|-|-|
| **Group creation**| Limit team creation to security group members.| P1| For organizations that want to control who can create groups. |
| **Group naming policy**| Use Prefix-Suffix–based, Custom Blocked Words.| P1| When organizations need to enforce a consistent naming strategy for groups created by users in your organization. |
| **Group guest access**| Allow or prevent guests from being added to groups.| No| When users need to collaborate with people outside of their organization. For example, access can be granted to a partner, vendor, supplier, or consultant. Guests are granted access to group conversations, files, calendar invitations, and the group notebook. |

## Group and team expiration, retention, and archiving

Your organization might have other requirements for setting policies for expiration, retention, and archiving teams and teams data (channel messages and channel files). You can configure group expiration policies to automatically manage the lifecycle of the group and retention policies to preserve or delete information as needed, and you can archive teams (set them to read-only mode) to preserve a point-in-time view of a team that’s no longer active. Teams that are archived continue to have the expiration policy applied and may be deleted unless excluded or renewed. Key decision points to consider:

* Does your organization require specifying an expiration date for teams?
* Does your organization require specific data retention policies be applied to teams?
* Does your organization expect to require the ability to archive inactive teams to preserve the content in a read-only state?


| **Capability**| **Details**| **Azure AD Premium license required**| **When to use** |
| - |-|-|-|
| **Expiration policy**| Manage the lifecycle of Microsoft 365 Groups by setting an expiration policy.| P1| Used in organizations that have a large number of inactive groups. |
| **Retention policy**| Retain or delete data for a specific time period by setting retention policies for Microsoft 365 Groups in the Security & compliance center. **Note**: Using this feature requires licensing of Office 365 Enterprise E3 or above.| No| In organizations that need to comply with industry regulations and internal policies for retaining content for a specific minimum period of time. |
| **Archive and restore**| Archive a team when it’s no longer active but you want to keep it around for reference or to reactivate in the future.| No| Used in organizations that need to archive the group content when it is no longer active, with ability to reactivate in the future if needed. |


## Group and team membership management

Managing members can be hard because team owners can leave and users don’t usually leave groups on their own accord when a project ends or when they change roles. The best way to manage group membership that allows users to get access when needed but ensure the group doesn't have a risk of inappropriate access is through two district processes: entitlement management and access reviews. Key decision points to consider:

* Does your organization require a consistent process for managing membership of one or more teams?
* Does your organization require owners, or the members themselves, to justify their continued membership of one or more teams regularly?
* Does your organization require approval for users and guests to request access to resources including teams, groups, SharePoint sites, and apps?

| **Capability**| **Details**| **Azure AD Premium license required**| **When to use** |
| - |-|-|-|
| **Azure AD access reviews**| Perform reviews to efficiently manage group memberships for both internal and guests| P2| In organizations that need to s to review group memberships, access to enterprise applications, and role assignments. |
|**Entitlement management**| Setup access package to allow users and guests to request access to teams|	P2| In organizations that need to ensure that only the appropriate users are able to request access, that there are approvers for their request, and that their access to those resources is time-limited and will expire if not renewed.|


## Teams feature management

Another important aspect of governance and lifecycle management for Teams is the ability to control what features your users will have access to. You can manage messaging, meeting, and calling features, either at the Microsoft 365 or Office 365 organization level or per-user. Key decision points to consider:

* Does your organization require limiting Teams features for your entire tenant?
* Does your organization require limiting Teams features for specific users?

## Security and compliance

Teams is built on the advanced security and compliance capabilities of Microsoft 365 and Office 365 and supports auditing and reporting, compliance content search, e-discovery, Legal Hold, and retention policies.

For more information, see [Plan for governance in Microsoft 365 Groups](/office365/admin/create-groups/plan-for-groups-governance).

 



 
