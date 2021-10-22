Viva Connections is backed by a SharePoint site that's chosen as the home site in your Microsoft 365 tenant. The home site is also the default site that users see when they go to the root URL of your tenant, such as https://contoso.sharepoint.com.

A SharePoint site is a place where users can create webpages and store files such as documents, images, or videos. When editors build webpages, they can customize those pages by using web parts. Web parts are building blocks that allow users to add images, files, videos, dynamic content retrieved from secure APIs, or even complete applications to pages.

You can build custom web parts for your organization by using modern web technologies. After your organization's administrators deploy them, these web parts will become available for everyone in the organization to use on their sites.

Web parts are one of the few types of extensions that you can build for Viva Connections. The following sections explain the most important characteristics of web parts that you should consider when extending Viva Connections.

> [!IMPORTANT]
> Web parts work only with the Viva Connections desktop experience. They won't work in the mobile Viva Connections app.

## Content editors place web parts on pages

Web parts are building blocks that page editors can add to pages. When editors are working with pages, they can choose any of the available web parts and add them to a page. Just as developers use reusable components when building applications, page editors in Microsoft 365 can use web parts to create rich pages and dynamic dashboards.

:::image type="content" source="../media/3-web-part-on-page.png" alt-text="Conceptual screenshot that shows a web part on a SharePoint page.":::

Page editors can add web parts in the content area of a page. They can also choose to add multiple instances of the same web part to a page. For example, they can use the same web part to embed multiple videos or show the weather forecast for multiple locations. 

Don't make assumptions about how a web part will be used or where it will be placed. Instead, verify that it will work with the configurations that SharePoint pages support.

## Content editors configure web parts

Another characteristic unique to web parts is that they're configurable. Let's say you've built a web part that allows editors to embed a video on the page. Rather than have the web part play a specific video, you can make the web part configurable so that editors can choose which video to play when adding the web part to the page.

When developers are building web parts, they decide which properties editors can configure. These properties will be exposed on the property pane that's visible to editors when they're configuring the web part.

:::image type="content" source="../media/3-web-part-property-pane.png" alt-text="Conceptual screenshot that shows a web part's property pane.":::

You don't have to make web parts configurable, but you should consider it. If you make your web parts configurable, they'll be more flexible. Editors will be able to use them across SharePoint sites in your Microsoft 365 tenant.

## You own the HTML and CSS of your web part

When you're developing web parts, you're responsible for their UI. In the web part's code, you get access to a DOM element where you're supposed to add the web part's HTML. Although there are no restrictions on which HTML tags you can use or how you implement the UI, the following recommendations will help you build web parts that users will love:

- **All web parts should use the same design language**. Content editors use web parts to build rich SharePoint pages. Typically, each page contains multiple web parts. If you use the same design language, it will make the pages easier to read. It will also make web parts easier to use because they'll all work in the same way as standard web parts provided with Microsoft 365. Fluent UI is the design language used in Microsoft 365.
- **Web parts should support themes**. Owners of SharePoint sites can use themes to control the look and feel of their sites. Web parts provided with Microsoft 365 adopt these changes and use the theme colors in their UI. The custom web parts that you build should also support themes. It's especially important when users configure their computers to use high-contrast or inverted themes where light text is on a dark background.

## Build with responsive UI in mind

Editors can place web parts anywhere on a page. When they build pages, they can use any combination of sections and web parts to convey the story that they want to tell. 

Readers access pages on devices that range from a large monitor to a mobile phone. By design, SharePoint pages use responsive design to adapt to the available screen size and ensure that the content is readable. If you want to benefit from it, all web parts on the page also need to support responsive design. If you build web parts with responsive design in mind, they'll seamlessly integrate with Microsoft 365 on all devices.

:::image type="content" source="../media/3-sharepoint-responsive-ui.png" alt-text="Conceptual screenshot that shows how SharePoint pages adapt to desktop, tablet, and mobile devices.":::

## Web parts can be connected to one another

Another design aspect specific to web parts is that they can be connected to one another. Let's say you want to build a list of events and show the location of a selected event on a map. Rather than build a web part specifically for this purpose, you could build two generic web parts: one to show the list of events with their locations and the other to show a map.

:::image type="content" source="../media/3-connected-web-parts.png" alt-text="Screenshot of connected web parts, including a list of events and the location of the selected event on a map.":::

If both web parts support connecting, then the list web part passes the information about the selected event to the map web part. Upon receiving the location information, the map web part shows the correct location on the map. Because both web parts are generic, they can be used for different scenarios. They can also be placed independently of each other on the page, allowing editors more flexibility when building pages.

## Recommendation

Consider building a web part if you need to extend the Viva Connections desktop experience and want to let content editors decide where they want to put it on the page. If you want to provide content editors with a generic widget, such as a map or a video player, that they can configure to their needs, web parts are also the preferred solution.

In the next exercise, you'll build a web part that gets information from a SharePoint list and shows the information on a page. You'll test the solution and deploy it to Viva Connections.
