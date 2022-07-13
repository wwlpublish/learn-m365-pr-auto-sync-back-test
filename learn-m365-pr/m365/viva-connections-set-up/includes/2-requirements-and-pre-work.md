Before building the Viva Connections experience, you must first prepare
your organization’s SharePoint intranet. Viva Connections has two
mandatory requirements and one optional (but highly recommended)
requirement:

**Step 1: Design and set a SharePoint communication site as the home
site (required)**

:::image type="content" source="../media/sharepoint-homesite.png" alt-text="Screenshot of sharepoint home site." :::
A home site is the main landing page for your intranet and will also
serve as the landing page for the Viva Connection’s desktop experience.
Home sites have special capabilities beyond a typical communication site
like:

- Provide a gateway to other high-traffic portals

- Connect people with an intranet-wide search experience

- Display targeted news and content

Once you've designed your [communication
site](https://support.microsoft.com/en-us/office/create-a-communication-site-in-sharepoint-7fb44b20-a72f-4d2c-9173-fc8f59ba50eb#:~:text=Steps%20to%20create%20a%20communication%20site%3A%201%20Sign,5%20Give%20your%20new%20communication%20site%20a%20name),
set it as a home site in the SharePoint admin center. Learn more about
[how to design a home site just for Viva
Connections](/viva/connections/create-sharepoint-home-site-for-viva-connections)
and how to [plan, build, and launch a home
site](/viva/connections/home-site-plan).

**Note:** You must have SharePoint administrator permissions or higher
to set a communication site as a home site.

**Step 2: Customize global navigation in SharePoint (required)**

:::image type="content" source="../media/enable-global-nav.png" alt-text="Screenshot of enabling global navigation of the sharepoint home site." :::
Now that your home site is set up, you can [enable and customize global
navigation](/viva/connections/sharepoint-app-bar).
Global navigation gives users access to the news, sites, and documents
relevant to their work. Navigational links that get added to global
navigation can be [audience targeted
to](/viva/connections/use-audience-targeting-in-viva-connections#apply-audience-targeting-to-links-in-resources)
personalize the viewing experience. Content in the global navigation
gets inherited by the Viva Connections experience as the Resources
component. To display the global navigation content, select the Viva
Connections app icon twice in the desktop experience and the Resource
tab in the mobile experience.

Keep in mind that the sites linked in the global navigation panel should
be [modernized to display properly in
Teams](/sharepoint/dev/transform/modernize-classic-sites#:~:text=%20Modernize%20your%20classic%20SharePoint%20sites%20%201,site%20transformation%20is%20transforming%20your%20site...%20See%20More.)
without opening in a separate browser window.

> [!NOTE]
> You must have site owner permissions or higher to the homesite to customize global navigation.

**Step 3: Modernize classic SharePoint sites and pages (recommended)**

Only modern SharePoint sites and pages will display inside the Microsoft Teams experience. Classic sites and pages will open in a separate browser window. We highly recommend to [modernize popular portals](/sharepoint/dev/transform/modernize-classic-sites#:~:text=%20Modernize%20your%20classic%20SharePoint%20sites%20%201,site%20transformation%20is%20transforming%20your%20site...%20See%20More.), which are linked in global navigation and to cards on the Dashboard to create the best viewing experience.

### Lamna Healthcare

:::image type="icon" source="../media/lamna-logo-white-bg-200.png"  :::

In this module, let's imagine that you're the Internal Communications Manager at a large chain of regional hospitals, Lamna Healthcare. Your organization needs an employee experience tool for their various types of employees. These employees include physicians and surgeons, nurse practitioners, HR professionals, IT professionals, office administrators, custodial staff, and many more.  

After carefully researching and examining existing platforms, executive leadership has decided that Viva Connections is an ideal solution since they already subscribe to Microsoft 365. Leadership has asked you to lead the deployment of Viva Connections along with a team of stakeholders that represent different roles.

:::image type="icon" source="../media/story-telling-logo-white-bg.png"  :::

### Learn how Lamna Healthcare meets requirements

Lamna Healthcare uses a SharePoint intranet to store files and share
information about benefits, tools, and upcoming events. Currently, Lamna
Health care is using a SharePoint communication site as a landing place
for their intranet experience. The intranet contains a combination of
classic and modern SharePoint sites and pages. Therefore, it doesn't
currently meet the requirements to use Viva Connections as an app in
Microsoft Teams. As the Internal Communications manager, you work with a
team of stakeholders to systematically audit the SharePoint intranet to
prepare. You know you need to get a home site, customize global
navigation, and modernize high-traffic portals that are connected to the
Viva Connections experience.

Working with the planning team, you decide to use the existing landing
page as Lamna Healthcare’s home site. You start by auditing the content
on the communication site to ensure it’s relevant and accessible to the
entire organization. Once the content and design are ready, you set the
communication site as an official home site in the SharePoint admin
center. Once set, you let the site owners of the home site know that
they can set up global navigation and start working on the Dashboard.

You continue working with the planning team to decide which navigational
links should be displayed in the global navigation. These navigational
links will display as resources in both the desktop and mobile Viva
Connections experiences. Prior to deciding which navigational links to be included, you've conducted the needs
assessment with the Viva Connections planning team. You've created a
planning spreadsheet to all findings from the needs assessment, which
are scenarios and tasks that can be supported by Viva Connections. Now,
you use this planning spreadsheet to identify which roles and audiences
need access to certain tools and resources. After editing labels and
links in global navigation, the site owners apply audience targeting to
select navigational links to personalize the viewing experience.

Next, you work with the planning team to consider which sites and pages
should be modernized. You know that only modern sites and pages will
display in Microsoft Teams, otherwise they'll open in a separate
browser window outside of the experience. Using the planning
spreadsheet, the planning team identifies which sites and pages are
linked to the Dashboard and Resources. Then, the planning team ensures
content is updated and relevant. Then they use the PowerShell tool to
quickly modernize the sites and pages that relate to the Viva
Connections experience. Lastly, you run a health check on the sites and
pages that will receive a high volume of visitors (thousands per day) to
ensure the ideal viewing experience.

Now that Lamna Healthcare has a home site, customized global navigation,
and modern sites and pages for Viva Connections experiences, you're
ready to start building the Viva Connections Dashboard.
