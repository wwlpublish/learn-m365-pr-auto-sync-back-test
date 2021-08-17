Sharing is a good way to give selected people access to dashboards and reports so they can view and interact with the shared content. Dashboards and reports can be shared from most places in the Power BI service, such as Favorites, Recent, My Workspace, and Shared with me (if the owner allows it). Users can also share from other workspaces if they have the Admin, Member, or Contributor role in the workspace. A Power BI Pro license is required to share content. Recipients also need Power BI Pro licenses, unless the content is in a [Premium capacity](/power-bi/service-premium-what-is) (refer to the unit titled "Administer permissions, licensing, and row level security in Power BI").

Selecting **My Workspace**, for example, displays a list of content. By holding a mouse over the name, the icons for the available options are displayed. Selecting the **Share** icon opens the dialog box to configure the following sharing options:

 -  Select email of recipients. A warning screen is displayed if a recipient’s email is outside of the organization.
 -  Add an optional message.
 -  Select whether to **Allow recipients to share your dashboard (or report)**. Allowing others to share is called resharing. Enabling this option allows users to reshare from the Power BI service, the mobile apps, or forward the email invitation to other users within their organization. The invitation expires after one month. People outside the organization can't reshare. The owner of the content can turn off resharing or revoke resharing on an individual basis.
 -  Select whether to **Allow users to build new content using the underlying datasets**. Users can create their own reports in other workspaces based on the dataset for this dashboard.
 -  Select whether to **Send email notification to recipients**. Power BI sends an email invitation to the individuals, but not to groups, with a link to the shared content.

When a user shares a dashboard or report, the people to which it's shared can view it and interact with it, but they can't edit it. They see the same data as the owner or person who shared the content, unless [row-level security (RLS)](/power-bi/service-admin-rls) is applied. Users within the organization to which the content is shared can also reshare it if that option is configured. Resharing isn't allowed when content is shared externally.

Sometimes it's necessary to see the list of users to which the content has been shared. To do so, select the **Access** option on the **Share** dashboard. If the people to which the content is shared see either a locked tile in a dashboard or a **Permission required** message when they try to view a report, it's likely because of the permission setting for the underlying dataset. This scenario can be fixed by going to the dataset, selecting the ellipsis icon, and selecting **Manage permissions**. The owner can then add the user and grant the necessary access.

Reports and dashboards can also be added as tabs to Teams channels, and they can be [embedded as a report web part with SharePoint Online.](/power-bi/service-embed-report-spo)

An alternative way to share content is through an app. A common scenario is where a user or team creates a workspace and develops reports and dashboards. That content can be published as an app that can be shared across the organization, or with users outside the organization.

Once a report or dashboard is shared, the recipient can view and interact with the content using the Power BI service.

### View with Power BI mobile

Users on the go can also keep track of their business data with Power BI’s touch friendly mobile applications for iOS, Android, and Windows devices. Users sign in to their account by using their Power BI service account information. The first screen displays all the content to which they have access, including reports, dashboards, and groups.

Tapping any dashboard opens it. Within a dashboard, users can tap on a tile to focus on it in a larger view. A user can note any insights by tapping the **Annotate** button in the top-right corner. The Annotate feature enables a user to draw on a focused tile to highlight areas of interest. The annotation tools are along the bottom of the screen.

While offline, users can access and interact with dashboards they've previously accessed from the mobile app.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”