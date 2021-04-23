SharePoint hub sites provide an important building block for your intranet. They're the "connective tissue" you use when organizing families of team sites and communication sites together.

One of the key principles of modern intranets based on Microsoft SharePoint is that each unit of work should get a separate site collection. This design helps you to manage governance and growth over time. Each communication site and Microsoft 365 group-connected team site is created as a site collection that can have its own permissions. A hub site (most commonly created from a communication site) should also be considered its own unit of work that brings together many other sites.

In the past, many organizations used subsites to create connective tissue for their intranets. They used the site collection's shared navigation to connect sites and the hierarchical structure of subsite relationships to nest sites within sites. However, subsites don't give any room for flexibility and change. Since subsites are a physical construct reflected in the URL for content, if you reorganize your business relationships, you break all the intranet relationships in your content. Subsites can also create challenges when it comes to governance because many features (including policy features like retention and classification) in SharePoint apply to all sites within the site collection, whether you want them to or not. This design means that you must frequently enable a feature for the entire site collection, even if it's only applicable to one subsite.

What is the one thing that you can guarantee is going to happen in every business? Change! As your organization evolves, you need intranets that make it easy to align experiences with the way you work and that can adapt to the inevitable changes in the way you work. This feature is a key benefit provided by SharePoint hub sites. They model relationships as links, rather than hierarchy or ownership. This design enables your to adapt to the changes in the way you work in a dynamic, changing world.

SharePoint administrators determine how many hub sites can be created in your organization, who can associate sites with each hub site, and whether associating a site to a hub requires approval.

### Intranet building blocks

Microsoft 365 provides three main building blocks to help you create your intranet in a way that allows you to configure experiences that align with your organization, your employees, and your readiness. Different organizations will use the building blocks in different ways, but the building blocks themselves reflect common patterns that organizations use to get work done:


 *  Team sites (collaboration)
 *  Communication sites (communication)
 *  Hub sites (connection)

The three types of building blocks share a common structure at their core. For example, they share the same set of internal web parts. However, there are some fundamental differences in intent, usage expectations, governance (including how they are created), and how and which web parts you might use on each type of site.

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
    

**Collaborate**
When you want to create a place where the members of a work group or project team can work together on project deliverables, plan an event, track status, or exchange ideas, you want a team site.

Team sites are connected by default to a Microsoft 365 group to deliver a full range of communication and collaboration tools, including Microsoft Teams and Planner.



  :::column-end:::
  :::column:::
    

**Communicate**
When you want to broadcast a message, tell a story, share content for viewing (but not editing), or showcase services or people, you want a communication site.

Communication site owners often want to include an engagement component - for example an "Ask Business Development" area on a site communicating information about business development.

A communication site is a great place to connect a Yammer group.



  :::column-end:::
  :::column:::
    **Connect**
When you want to create a shared experience for a family of related sites—to discover related content by rolling up site activity and news, organize related sites so that they share a common navigation, and apply a common look and feel.

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
    

Hub site owner defines the shared experiences for hub navigation and theme.

Hub site members create content on the hub site as with any other SharePoint site.

Owners and members of the sites associated with the parent hub create content on individual sites.



  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Governance**
(as allowed for your organization based on the settings in the Security &amp; Compliance center)

  :::column-end:::
  :::column:::
    Norms typically determined by the team. Practices are aligned in the best way to get work done.

  :::column-end:::
  :::column:::
    Policies often determined by the organization to ensure consistency of experience and effective management of organizational information.

  :::column-end:::
  :::column:::
    

Governance determined by each owner of the associated site based on the type of site and organizational policies.

The best experience for visitors is achieved when everyone has at least Read permissions for associated sites (although it isn't required).



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
    Global admin or SharePoint admin in Microsoft 365

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Examples**

  :::column-end:::
  :::column:::
    

Project team working together to complete deliverables and manage tasks.


Holiday party planning committee planning the annual get-together
HR performance management team.


Executive committee—different leadership groups within the organization
Extranet site to work with Partner A.



  :::column-end:::
  :::column:::
    

Travel team publishing guidelines about corporate travel.


Policies and procedures.


Micro-site for a new corporate initiative.


Resources for the sales team for a product or service.



  :::column-end:::
  :::column:::
    

HR hub that provides a connection and roll-up for all HR functions, such as benefits, compensation, performance management, talent acquisition, and a manager portal.


Sales hub providing enterprise resources for the Sales organization and connecting regional sales team and communication sites.


Location-specific hub that groups the communication and team sites for a specific location (the New York office)



  :::column-end:::
:::row-end:::


###  Hub site considerations

Hub sites complement the search experience by helping you discover information in context.

One of the biggest challenges with intranet design is figuring out how the intranet navigation should be organized. In the new world where all team and communication sites are peer site collections, information architects must think about creating experiences that will allow intranet users to find what they need in multiple "find" scenarios:

 *  I know it exists, and I know where it is.
    
 *  I know it exists, but I don't know where it is.
    
 *  I don't know if it exists.
    

These scenarios are enabled with a combination of navigation, search, and discovery (or serendipity) and should be a factor in how you design and organize your hub sites. One of the important capabilities that hub sites enable is the serendipitous discovery of information because they can surface contextually relevant content from sites you may not follow but are associated with the hub. The SharePoint start page was built to support discovery and search across the entire organization's content, but if you already have a particular context in mind, hub sites can be helpful in narrowing those experiences down to a handful of related sites.

As a starting point in your hub planning, think about hub sites for key functions that your users need to get work done—for example: HR, Finance, Communications or Public Relations, Legal, and IT. These functions may be represented in different organizational departments or business units in large organizations or combined into the role of a few people in smaller organizations.

Consider the following items when creating hub sites:


 *  You must be a SharePoint administrator to create a SharePoint hub site. Site owners, however, can associate a SharePoint site with a hub site that already exists. Sites created by clicking the Create site link in the top-right corner of a hub site will automatically be associated with that hub site.
 *  It's recommended that you select a communication site or a team site that uses the modern template. If you use a classic team site, the hub site navigation will only appear on modern pages, including document libraries, lists, and site contents. Hub site settings will only appear on modern pages.
 *  You can create up to 2000 hub sites for an organization.
 *  If you set up SharePoint Multi-Geo for your organization, any geographic location where the SharePoint workload is available can be associated with a hub site.
 *  When users associate their sites with a hub site, it doesn't impact the permissions of either the hub site or the associated sites. It's important to ensure that all users you allow to associate sites to the hub site have permission to the hub site.
 *  The hub site navigation that is shown on all associated sites is based on the top navigation bar of the hub site. To make programmatic changes to the hub site navigation, you can use the REST API, CSOM API, or PnP PowerShell.
 *  Sites associated with a SharePoint hub site don't inherit the permissions of the hub site or any other sites associated with it. Each site, including the hub site, will keep their current permission settings.
 *  You can use PowerShell cmdlets or the SharePoint REST API to automate tasks such as creating, removing, or controlling permissions for hub sites.
