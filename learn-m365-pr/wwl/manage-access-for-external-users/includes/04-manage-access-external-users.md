Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.
 
There are various settings that can affect sharing with people outside your organization for the Microsoft 365 workloads: Teams, Microsoft 365 Groups, SharePoint, and OneDrive. These settings are located in the Azure Active Directory, Microsoft 365, Teams, and SharePoint admin centers.


## Azure Active Directory 

Administrators can also use Azure AD to determine whether external collaborators can be invited into your tenant as guests, and in what ways.



Sharing in Microsoft 365 is governed at its highest level by the B2B external collaboration settings in Azure Active Directory. If guest sharing is disabled or restricted in Azure AD, this setting overrides any sharing settings that you configure in Microsoft 365.

You can use the Azure AD admin center to control:

* Guest access to properties and memberships of directory objects
* Guest invite settings
* Enable up guest self-service sign via user flows
* Collaboration restrictions

## Microsoft 365 

Teams uses Microsoft 365 Groups for team membership. The Microsoft 365 Groups guest settings must be turned on in order for guest access in Teams to work.

You can use the Microsoft 365 admin center to control:

* Let users add new guests to the organization
* Let group owners add people outside your organization to groups
* Let group members outside your organization access group content

## Teams 

In Teams, you can control whether the guest experience is enabled or disabled for your Teams organization. The setting applies at the tenant level for Teams. You can also configure permissions for guests in your teams like Audio/Video settings and screen sharing capabilities. 

You can use the Teams admin center to control:

* External access
* Guest access (calling, meeting, and messaging)
* Anonymous users’ meeting experience


## SharePoint and OneDrive 

Teams content such as files, folders, and lists are all stored in SharePoint and OneDrive. In order for guests to have access to these items in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.

You can use the SharePoint admin center to control:

* External sharing 
* File and folder links


## Guest access authorization dependency

The following diagram shows how guest access authorization dependency is granted and integrated between Azure Active Directory, Microsoft 365, Teams, and SharePoint. This dependency means that if you disable guest access at any point in the chain every App down the line will inherit the restriction and you will not be able to create or let your users create new Teams.

:::image type="content" source="../media/teams-guests-dependencies.png" alt-text="Guest access authorization dependency ":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”