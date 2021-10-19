Viva Connections is backed by a SharePoint site chosen as the Home site in your Microsoft 365 tenant. The Home site is also the default site that users see when they navigate to the root URL of your tenant, for example https://contoso.sharepoint.com.

A SharePoint site is a place where users can create web pages and store files such as documents, images, or videos. When building web pages, editors can customize them using web parts. Web parts are building blocks that allow users to add images, files, videos, dynamic content retrieved from secure APIs, or even complete applications to pages.

You can build custom web parts for your organization using modern web technologies. After your organization's administrators deploy them, these web parts will become available for everyone in the organization to use in their sites.

Web parts are one of the few types of extensions that you can build for Viva Connections. The following sections explain the most important characteristics of web parts that you should consider when extending Viva Connections.

> [!IMPORTANT]
> Web parts work only with the Viva Connections desktop experience. They will not show in the mobile Viva Connections app.

## Content editors place web parts on pages

Web parts are building blocks that page editors can add to pages. When working with pages, editors can choose any of the available web parts and add them to a page. Just as developers use reusable components when building applications, page editors in Microsoft 365 can use web parts to create rich pages and dynamic dashboards.

:::image type="content" source="../media/3-web-part-on-page.png" alt-text="Conceptual image showing a web part on a SharePoint page":::

Page editors can add web parts in the content area of the page. They can also choose to add multiple instances of the same web part to a page, for example to embed multiple videos or show the weather forecast for multiple locations. Don't make any assumptions about how the web part will be used or where it will be placed. Instead, you should verify that your web part will work with the different configurations supported by SharePoint pages.

## Content editors configure web parts

Another characteristic unique to web parts is that they're configurable. Let's say you've built a web part that allows editors to embed a video on the page. Rather than having the web part play a specific video, you can make the web part configurable so that editors can choose which video to play when adding the web part to the page.

When building web parts, developers decide which properties editors can configure. These properties will be exposed in the property pane that's visible to editors when configuring the web part.

:::image type="content" source="../media/3-web-part-property-pane.png" alt-text="Conceptual image showing a web part property pane":::

You don't have to make web parts configurable, but you should consider it. If you make your web parts configurable, they will be more flexible, and editors will be able to use them across the different SharePoint sites in your Microsoft 365 tenant.

## You own the HTML and CSS of your web part

When developing web parts, you're responsible for their UI. In the web part's code, you get access to a DOM element where you're supposed to add the web part's HTML. While there are no restrictions as to which HTML tags you can use or how you implement the UI, here are a few recommendations, which will help you build great web parts that users will love.

- **All web parts should use the same design language.** Content editors use web parts to build rich SharePoint pages. Typically, each page contains multiple web parts. If you use the same design language, it will not only make the pages easier to read but it will also make web parts easier to use because they all work in the same way as standard web parts provided with Microsoft 365. Fluent UI is the design language used in Microsoft 365.
- **Web parts should support theming.** Owners of SharePoint sites can use themes to control the look and feel of their sites. Web parts provided with Microsoft 365 adopt these changes and use the theme colors in their UI. The custom web parts that you build, should support theming as well. It's especially important when users configure their computers to use high-contrast or inverted themes where light text is displayed on dark background.

## Build with responsive UI in mind

Editors can place web parts anywhere on the page. When building pages, they can use any combination of sections and web parts to convey the story they want to tell. Readers who view the pages, will access pages on devices ranging from a large monitor to a mobile phone. By design, SharePoint pages use responsive design to adapt to the available screen size and ensure that the content is readable. If you want to benefit from it, all web parts on the page need to support responsive design as well. If you build web parts with responsive design in mind, they will seamlessly integrate with Microsoft 365 on all devices.

:::image type="content" source="../media/3-sharepoint-responsive-ui.png" alt-text="Conceptual image showing how SharePoint pages adapt to desktop, tablet and mobile devices":::

## Web parts can be connected to one another

Another design aspect specific to web parts is that they can be connected to one another. Let's say you wanted to build a list of events and for the selected event, show its location on a map. Rather than building a web part specifically for this purpose, you could build two generic web parts: one to show the list of events with their locations and the other to show a map.

:::image type="content" source="../media/3-connected-web-parts.png" alt-text="Connected web parts showing a list of events and the location of the selected event on a map":::

If both web parts supported connecting, then the list web part would pass the information about the selected event to the map web part. Upon receiving the location information, the map web part would show the correct location on the map. Because both web parts are generic, they can be used for different scenarios but can also be placed independently of each other on the page, allowing editors for greater flexibility when building pages.

## Recommendation

Consider building a web part if you need to extend the Viva Connections desktop experience and want to let content editors decide where they want to put it on the page. If you want to provide content editors with a generic widget, such as a map or a video player, which they can configure to their needs, web parts are also the preferred solution.

In the next exercise, you'll build a web part that retrieves information from a SharePoint list and shows it on a page. You'll test the solution and deploy it to Viva Connections.
