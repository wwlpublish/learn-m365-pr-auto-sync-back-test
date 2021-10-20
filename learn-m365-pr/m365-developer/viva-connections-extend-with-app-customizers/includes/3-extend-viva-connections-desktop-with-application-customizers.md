The Viva Connections desktop experience is backed by a SharePoint site that's chosen as the home site in your Microsoft 365 tenant. By using application customizers, you can add custom code to all pages on the site.

You build application customizers by using modern web technologies. After SharePoint administrators in your organization deploy them, application customizers become automatically enabled on the selected sites.

The following sections explain the most important characteristics of application customizers that you should consider when planning how to extend Viva Connections.

> [!IMPORTANT]
> Application customizers work only with the Viva Connections desktop experience. They won't work in the mobile Viva Connections app.

## Application customizers don't need to have a UI

Application customizers can, but don't need to, have a UI. You can use Application customizers to add custom code to every page in the site. Or instead of manually modifying each page, you can build and enable an application customizer on the site that will add custom code to all pages at once. When you need to update your code or even disable it, you can do it from a central location, which saves you time.

Because application customizers don't need to have a UI, they're the preferred solution if you need to add analytics scripts to the page or prefetch some data from APIs. Unless you choose to render a UI, an application customizer won't take up any space on the screen.

> [!CAUTION]
> SharePoint, which powers Viva Connections, exposes a predefined set of extensibility points that you can use to change how sites and pages look. Your customers might ask you to go outside these extensibility points and, for example, change the font family or rearrange menu items on the page through DOM manipulation. You shouldn't do this! 
>
> A page's DOM is not an API. There's a risk that it could change at any time, breaking your customizations without any notice. By manipulating the DOM, you might also break some new features that your changes didn't consider.

## An application customizer's UI is attached to a placeholder

When you're building application customizers, you can choose to render UI in one of the predefined placeholders. Currently, two placeholders are available: top and bottom. The top placeholder appears between the suite navigation bar and the site navigation. The bottom placeholder appears at the end of the page.

:::image type="content" source="../media/3-placeholders.png" alt-text="Conceptual screenshot that shows top and bottom placeholders on a SharePoint modern page.":::

When you choose to render a UI in a placeholder, you get a container DOM element that's specific for your application customizer. Because each application customizer gets its own DOM element, multiple application customizers can render their UI in the same placeholder without overwriting each other's contents. 

When multiple application customizers render their contents in a placeholder, they get stacked in the order that the developer has defined. If needed, site administrators can change this order programmatically after enabling application customizers on the site.

Instead of using a placeholder to render the UI for application customizers, you can build a floating UI. A floating UI is helpful if you need to add a web chat that floats on top of the content on all pages. Instead of rendering the HTML inside a placeholder, you add it to the page's BODY and make it float on top of the page's content by using CSS.

When you build the UI for application customizers, you own the CSS and HTML. Consider using the Fluent UI design language to make your solution seamlessly integrate with Viva Connections.

## Developers define the position of an app customizer

As a developer, you decide whether the application customizer that you're building should have a UI or not. If the application customizer should have a UI, you as a developer decide to which placeholder it's attached.

By default, content editors have no control over application customizers. Site administrators can choose to enable or disable an application customizer, but they can't control where on the page it's placed.

As a developer, you could write custom code that allows site owners to configure your application customizer. Let's say you build an application customizer that shows a custom footer. You can give site owners a custom configuration UI to manage the content of the footer.

> [!IMPORTANT]
> If you want to provide a configuration UI for your application customizer, you need to build it yourself. Allow only site owners to manage the configuration, because changes appear on all pages on the site.

## Site administrators can configure application customizers

Application customizers support limited configuration capabilities. When you're building application customizers, you can define custom configuration properties, but there's no UI for users to configure them. Instead, use the API or PowerShell to specify values for these properties.

Configuration properties for application customizers allow you to parameterize your solution so that you can reuse it in different scenarios. Typically, you configure these properties in an installation script that you provide with your solution.

## Recommendation

Consider building an application customizer if you want to add code to all pages in the Viva Connections desktop experience. If the solution doesn't need a UI, or if the UI is suited to be displayed in one of the available placeholders, build an application customizer.

In the next exercise, you'll build an application customizer that retrieves information from a SharePoint list and shows it on the page in the top placeholder. You'll also test the solution and deploy it to Viva Connections.
