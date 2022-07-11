
Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.

There are various settings that can affect sharing with people outside your organization for the Microsoft 365 workloads: Teams, Microsoft 365 Groups, SharePoint, and OneDrive. These settings are located in the Azure Active Directory, Microsoft 365, Microsoft Purview compliance portal, Teams, and SharePoint admin centers.

## Azure Active Directory

Azure AD External Identities refers to all the ways you can securely interact with users outside of your organization. Administrators can use External Identities to determine whether external collaborators can be invited into your tenant as guests, and in what ways. 

Sharing in Microsoft 365 is governed at its highest level by the B2B external collaboration settings in Azure Active Directory. If guest sharing is disabled or restricted in Azure AD, this setting overrides any sharing settings that you configure in Microsoft 365.

You can use the Azure AD External Identities to control:

* Guest access to properties and memberships of directory objects

* Guest invite settings

* Enable up guest self-service sign via user flows

* Collaboration restrictions

* Cross-tenant access

Shared channels in Microsoft Teams create collaboration spaces where you can invite people who are not in the team. You can invite people outside your organization to participate in a shared channel by configuring **B2B direct connect** in Azure AD cross-tenant access settings.

When you enable shared channels in Teams with another organization:
* Team owners in your organization will be able to invite people from other organizations to participate in shared channels.
* Your organization's custom (line of business) apps will be available in shared channels and external participants will be able to access them.
* Your organization's apps list will be available in shared channels and external participants will be able to access them.

    ‎:::image type="content" source="../media/shared-channel.png" alt-text="Screenshot of sharing a shared channel with external users.":::

## Microsoft Purview compliance portal

Administrators can use sensitivity labels to control guest access to your teams. Teams created with a label that doesn't allow guest access are only available to users in your organization. People outside your organization can't be added to the team.

You can use the sensitivity labels to protect content in the Microsoft Teams sites, Microsoft 365 groups, and SharePoint sites with the following label settings:

* Privacy (public or private) of teams sites and Microsoft 365 groups
* External user access
* External sharing from SharePoint sites
* Access from unmanaged devices
* Authentication contexts (in preview)
* Default sharing link for a SharePoint site (PowerShell-only configuration)
* In preview: Site sharing settings (PowerShell-only configuration)


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

‎:::image type="content" source="../media/teams-guests-dependencies.png" alt-text="Diagram that shows Guest access authorization dependency.":::

## Remove guest users 
Guests can leave the team at any time from within Teams or the owners can manually remove the guest accounts from their teams.

:::image type="content" source="../media/remove-guests.png" alt-text="Screenshot of removing guests from Teams client.":::

However, leaving the team doesn't remove the guest account from your organization's directory. This must be done by a Microsoft 365 global admin or an Azure AD admin.

As a Microsoft 365 global admin or an Azure AD admin, you can remove a guest user from the following locations:
 
* Microsoft 365 admin center.
* Azure AD admin center. 

