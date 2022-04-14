SharePoint Online provides three main building blocks to help an organization create its intranet. These building blocks enable an organization to configure experiences that align with the organization, its employees, and its readiness. Different organizations will use the building blocks in different ways. However, the building blocks themselves reflect common patterns that organizations use to get work done. These SharePoint Online building blocks include:<br>

 -  **Team sites (collaboration)**. A SharePoint team site provides a location where you and your team can work on projects and share information from anywhere on any device. A team site includes a group of related web pages, a default document library for files, lists for data management, and web parts that you can customize to meet your needs. A Microsoft 365 group is automatically created when a user creates a team site in SharePoint Online.
 -  **Communication sites (communication)**. SharePoint communication sites are designed to inform and engage. The primary goal of a team site is to collaborate to create content with a small group. If your intention is to broadcast information out to a broad audience, a communication site is the better choice than a team site. With a communication site, typically only a small set of members contributes content that is consumed by a much larger audience.
 -  **Hub sites (connection)**. SharePoint hub sites provide an important building block for organizations that are designing their own intranets. Hub sites are the "connective tissue" a company can use when organizing families of team sites and communication sites together.

The following table identifies the features of each building block. It also offers recommendations on when each type of site should be used.<br>

:::row:::
  :::column:::
    
  :::column-end:::
  :::column:::
    Team site
  :::column-end:::
  :::column:::
    Communication site
  :::column-end:::
  :::column:::
    Hub site
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Primary business goal**
  :::column-end:::
  :::column:::
    **Collaborate**Used when an organization wants to create a place where the members of a work group or project team can work together on project deliverables, plan an event, track status, or exchange ideas.Team sites are connected by default to a Microsoft 365 group. This design enables teams sites to deliver a full range of communication and collaboration tools, including Microsoft Teams and Planner.
  :::column-end:::
  :::column:::
    **Communicate**Used when an organization wants to broadcast a message, tell a story, share content for viewing (but not editing), or showcase services or people.Communication site owners often want to include an engagement component - for example an "Ask Business Development" area on a site communicating information about business development.A communication site is a great place to connect a Yammer group.
  :::column-end:::
  :::column:::
    **Connect**Used when an organization wants to create a shared experience for a family of related sites—to discover related content by rolling up site activity and news, organize related sites so that they share a common navigation, and apply a common look and feel.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Content authors**
  :::column-end:::
  :::column:::
    All members are content authors who jointly create and edit content.
  :::column-end:::
  :::column:::
    Small number of content authors and a much larger number of content readers or consumers.
  :::column-end:::
  :::column:::
    The hub site owner defines the shared experiences for hub navigation and theme.Hub site members create content on the hub site as with any other SharePoint site.Owners and members of the sites associated with the parent hub create content on individual sites.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Governance**(as allowed for an organization based on its settings in the Security &amp; Compliance center)
  :::column-end:::
  :::column:::
    Norms are typically determined by the team. Practices are aligned in the best way to get work done.
  :::column-end:::
  :::column:::
    Policies are often determined by the organization to ensure consistency of experience and effective management of organizational information.
  :::column-end:::
  :::column:::
    Governance is determined by each owner of the associated site based on the type of site and organizational policies.The best experience for visitors is achieved when everyone has at least Read permissions for associated sites (although it isn't required).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Permissions**
  :::column-end:::
  :::column:::
    Microsoft 365 group, plus SharePoint groups and permission levels.
  :::column-end:::
  :::column:::
    SharePoint group.
  :::column-end:::
  :::column:::
    Same as original site type. Hub sites don't alter an associated site's permissions.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Created by**
  :::column-end:::
  :::column:::
    Site owner (unless it's been disabled in your organization) or admin.
  :::column-end:::
  :::column:::
    Site owner (unless it's been disabled in your organization).
  :::column-end:::
  :::column:::
    Global admin or SharePoint admin in Microsoft 365.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Examples**
  :::column-end:::
  :::column:::
    Project team working together to complete deliverables and manage tasks.Holiday party planning committee planning the annual get-together with the HR performance management team.Executive committee—different leadership groups within the organization Extranet site to work with Partner A.
  :::column-end:::
  :::column:::
    Travel team publishing guidelines about corporate travel.Policies and procedures.Micro-site for a new corporate initiative.Resources for the sales team for a product or service.
  :::column-end:::
  :::column:::
    HR hub that provides a connection and roll-up for all HR functions, such as benefits, compensation, performance management, talent acquisition, and a manager portal.Sales hub providing enterprise resources for the Sales organization and connecting regional sales team and communication sites.Location-specific hub that groups the communication and team sites for a specific location (the New York office)
  :::column-end:::
:::row-end:::


### Site collections and subsites - a look back at the past

A site collection is a group of websites that have the same owner and share administrative settings, such as permissions and quotas. Site collections are created within a web application. When you create a site collection, a top-level site is automatically created in the site collection. You can then create one or more subsites below the top-level site. The entire structure of the top-level site and all its subsites is called a site collection.

One of the key principles of modern intranets based on Microsoft SharePoint is that each unit of work should get a separate site collection. This design helps organizations manage governance and growth over time. Each communication site and Microsoft 365 group-connected team site is created as a site collection that can have its own permissions. A hub site (most commonly created from a communication site) should also be considered its own unit of work that brings together many other sites.

In the past, many organizations used subsites to create connective tissue for their intranets. They used the site collection's shared navigation to connect sites, and the hierarchical structure of subsite relationships to nest sites within sites. However, the downside of subsites is that they don't provide any room for flexibility and change. Since subsites are a physical construct reflected in the URL for content, if an organization reorganizes its business relationships, it breaks all the intranet relationships in its content.

Subsites can also create challenges when it comes to governance. Many features (including policy features like retention and classification) in SharePoint apply to all sites within the site collection, whether an organization wants them to or not. This design means that a feature for the entire site collection must be frequently enabled, even if it's only applicable to one subsite.

### Hub sites - the future is here

What is the one thing that you can guarantee is going to happen in every business? Change! As an organization evolves, it needs intranets that make it easy to align experiences with the way the organization works. It also needs intranets that can adapt to the inevitable changes that occur in the way they work.

This feature is a key benefit provided by SharePoint hub sites. They model relationships as links, rather than hierarchy or ownership. This design enables organizations to adapt to the changes in the way they work in a dynamic, changing world. SharePoint hub sites help you meet the needs of your organization by connecting and organizing sites based on project, department, division, region, and so on. This design makes it easier to:

 -  Discover related content such as news and other site activities.
 -  Apply common navigation, branding, and site structure across associated sites.
 -  Search across all associated sites.

SharePoint administrators determine:

 -  how many hub sites can be created in an organization.
 -  who can associate sites with each hub site.
 -  whether associating a site to a hub requires approval.

One of the biggest challenges with intranet design is figuring out how the intranet navigation should be organized. In the new world where all team and communication sites are peer site collections, information architects must think about creating experiences that enable intranet users find what they need in the following search scenarios:

 -  I know it exists, and I know where it is.
 -  I know it exists, but I don't know where it is.
 -  I don't know if it exists.

These scenarios are enabled with a combination of navigation, search, and discovery. They should be a factor in how an organization designs and organizes its hub sites. One of the important capabilities that hub sites enable is the serendipitous discovery of information. Hub sites can surface contextually relevant content from sites that users may not follow, but that are associated with the hub. The SharePoint start page was built to support discovery and search across an entire organization's content. However, if the user already has a particular context in mind, hub sites can be helpful in narrowing those experiences down to a handful of related sites.

When an organization plans its hub sites, it should think about hub sites and the key functions that its users need to get work done.

 -  For larger organizations, these functions may be represented in different organizational departments or business units, such as HR, Finance, Public Relations, Legal, IT, and so on.
 -  For smaller organizations, these functions may also be combined into the role of a few people.

Consider the following items when creating hub sites:

 -  Only SharePoint administrators can create a SharePoint hub site. Site owners, however, can associate a SharePoint site with a hub site that already exists. Sites created by selecting the **Create site** link in the top-right corner of a hub site are automatically associated with that hub site.
 -  It's recommended that organizations use the modern template when selecting a communication site or a team site. If a classic team site is used, the hub site navigation will only appear on modern pages, including document libraries, lists, and site contents. Hub site settings will only appear on modern pages.
 -  Up to 2000 hub sites can be created for an organization.
 -  If SharePoint Multi-Geo is set up for an organization, any geographic location where the SharePoint workload is available can be associated with a hub site.
 -  When users associate their sites with a hub site, it doesn't impact the permissions of either the hub site or the associated sites. It's important to ensure that all users that are allowed to associate sites to the hub site have permission to the hub site.
 -  The hub site navigation that is shown on all associated sites is based on the top navigation bar of the hub site. An organization should use the REST API, CSOM API, or PnP PowerShell to make programmatic changes to hub site navigation.
 -  Sites associated with a SharePoint hub site don't inherit the permissions of the hub site by default. Hub owners can enable [hub site permissions sync](https://support.microsoft.com/office/set-up-your-sharepoint-hub-site-e2daed64-658c-4462-aeaf-7d1a92eba098?azure-portal=true) to push visitors to associated sites. With that said each site, including the hub site, will retain their current permission settings.
 -  When you sync hub permissions to associated sites, it increases access for viewers across all sites in the hub. To sync permissions, the hub owner must first enable hub permissions to sync to associated sites. Then, associated site owners can choose to sync with hub permissions. Syncing with hub permissions won't override or change site permissions.
 -  After you associate your site to a hub site, if you decide you no longer want your site to inherit permissions from the hub, you can change the settings.
 -  PowerShell cmdlets or the SharePoint REST API can be used to automate tasks such as creating, removing, or controlling permissions for hub sites.

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Site management](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-100/M4-L3-E2-T1/index.html?azure-portal=true).

This simulation guides you through the steps to manage sites using SharePoint Online for the fictitious Adatum Corporation.
