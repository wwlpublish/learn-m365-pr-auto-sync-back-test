In this unit, you get a high-level overview of the ways in which you can extend Viva Connections. For more information about these extensions, see the links to the dedicated Lean modules about Viva Connections extensibility in the summary unit.

## Web parts

The Viva Connections desktop experience is implemented through modern SharePoint pages in SharePoint Online. You can extend these pages with HTML widgets named *web parts*. Editors can place web parts in the content area of pages and configure them to their needs.

:::image type="content" source="../media/4-web-parts.png" alt-text="Screenshot of a modern SharePoint page in edit mode, showing different sections and web parts.":::

## Application customizers

Another way to extend the Viva Connections desktop experience is by using application customizers. Application customizers allow you to inject HTML and JavaScript into known locations on a SharePoint page, such as a header or footer. 

Application customizers are useful for running background code such as analytics tracking. They can also be used to show information in one of the predefined content placeholders on a page. Administrators enable application customizers, whereas users can add web parts. 

:::image type="content" source="../media/4-application-customizer-footer.png" alt-text="Screenshot of a site footer built through an application customizer.":::

## Adaptive Card Extensions

Adaptive Card Extensions (ACEs) are similar to web parts but use [Adaptive Cards](https://adaptivecards.io) to implement the UI. Adaptive Cards are JSON structures that can be rendered on desktop and mobile clients.

The advantage of ACEs is that they work on both the mobile and the desktop experience of Viva Connections through a special dashboard that users in your organization configure. In the desktop experience, the dashboard is embedded through a special web part that editors can put on a page. In the mobile experience, the Viva Connections mobile app automatically detects and loads the dashboard that's configured on the home site in your Microsoft 365 tenant.

:::image type="content" source="../media/4-adaptive-card-extensions.png" alt-text="Screenshot that shows sample Adaptive Card Extensions.":::

What's special about Adaptive Card Extensions is that editors can configure them to be visible only to a specific group of users. This capability allows your organization to show users the cards that are most relevant to them.

## Extend Viva Connections with modern web technologies

You build web parts, application customizers, and Adaptive Card Extensions by using the SharePoint Framework. The SharePoint Framework is a development model based on modern web technologies. It uses TypeScript as the programming language, Gulp to run tasks, Yeoman to scaffold projects, and Node.js as the runtime. 

To develop on the SharePoint Framework, all you need to know is TypeScript. Microsoft and the developer community have built many samples by using React, but you can use any JavaScript framework with the SharePoint Framework. Understanding the underlying toolchain will help you in advanced scenarios but is not required to get started.
