SharePoint hub sites connect and organize sites based on organizational attributes such as project, department, division, or region. By connecting and organizing sites in this manner, SharePoint hub sites make it easier to:

 *  Discover related content such as news and other site activities.
 *  Apply common navigation, branding, and site structure across associated sites.
 *  Search across all associated sites.

SharePoint administrators determine how many hub sites can be created in your organization, who can associate sites with each hub site, and whether associating a site to a hub requires approval.

Consider the following items when creating hub sites:

 *  You must be a SharePoint administrator to create a SharePoint hub site. Site owners, however, can associate a SharePoint site with a hub site that already exists. Sites created by clicking the Create site link in the top-right corner of a hub site will automatically be associated with that hub site.
 *  It's recommended that you select a communication site or a team site that uses the modern template. If you use a classic team site, the hub site navigation will only appear on modern pages, including document libraries, lists, and site contents. Hub site settings will only appear on modern pages.
 *  You can create up to 2000 hub sites for an organization.
 *  If you set up SharePoint Multi-Geo for your organization, any geographic location where the SharePoint workload is available can be associated with a hub site.
 *  When users associate their sites with a hub site, it doesn't impact the permissions of either the hub site or the associated sites. It's important to ensure that all users you allow to associate sites to the hub site have permission to the hub site.
 *  The hub site navigation that is shown on all associated sites is based on the top navigation bar of the hub site. To make programmatic changes to the hub site navigation, you can use the REST API, CSOM API, or PnP PowerShell.
 *  Sites associated with a SharePoint hub site don't inherit the permissions of the hub site or any other sites associated with it. Each site, including the hub site, will keep their current permission settings.
 *  You can use PowerShell cmdlets or the SharePoint REST API to automate tasks such as creating, removing, or controlling permissions for hub sites.

### Associating sites to a hub site

You can add sites to a hub site using either of the following methods:

 *  You can create a new site that is automatically associated with your hub site by selecting **Create site** in the top-right corner of the hub site.
 *  Existing sites can be linked to a hub site through an approved association flow. Hub site owners can set up your SharePoint hub site to automatically evaluate requests for sites before the association takes place.

### Shared hub navigation

The hub site navigation bar appears at the top of a hub site and any associated sites. If you're the hub site owner, you can customize this navigation bar and choose to use the mega menu layout.

:::image type="content" source="../media/sharepoint-hub-site-nav-bar-df4a318e.png" alt-text="screenshot that shows a SharePoint hub site with the hub site navigation bar highlighted":::


### Search across the hub site

When you search from a SharePoint hub site, content on the hub site itself and from any associated sites are returned in the search results. Viewers will only see content for which they have access to.

:::image type="content" source="../media/sharepoint-hub-site-search-results-9c2601f1.png" alt-text="screenshot that shows the results from searching from a SharePoint hub site":::


### Recommended web parts

When a SharePoint administrator creates a hub site, they're converting an existing SharePoint site to a hub site. A hub site navigation bar will appear at the top of the site, but the home page and all site contents will remain the same.

To get the most out of your hub site, the site's owner can add the following web parts to the home page:

#### News roll-up

News published on a hub site and on any associated sites is automatically aggregated and shown on the home page of the hub site by using the News web part. You can choose which associated sites display news on the hub site home page and viewers will only see news for sites they have access to. Selecting a news article link takes you to the site on which the article was published.

:::image type="content" source="../media/sharepoint-hub-site-news-rollup-bb698633.png" alt-text="screenshot that shows news roll-up on a hub site":::


#### Associated sites

By using the Sites web part, you can display the most active sites associated with the hub site on the home page.

:::image type="content" source="../media/sharepoint-hub-site-associated-sites-47cad0c6.png" alt-text="screenshot displaying associated sites on a hub site":::


#### Highlighted content

The Highlighted content web part dynamically displays content from sites associated with the hub site on the home page.

:::image type="content" source="../media/sharepoint-hub-site-highlighted-content-7315fc1b.png" alt-text="screenshot displaying the Highlighted content web part that dynamically displays content from sites associated with the hub site":::


#### Events

By using the Events web part, you can dynamically display events from sites associated with the hub site on the home page.

:::image type="content" source="../media/sharepoint-hub-site-upcoming-events-0a9681c3.png" alt-text="screenshot displaying upcoming events on a hub site":::
