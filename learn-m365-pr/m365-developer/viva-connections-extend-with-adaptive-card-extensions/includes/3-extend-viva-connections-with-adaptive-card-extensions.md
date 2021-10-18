One of the extensions that you can build for Viva Connections are Adaptive Card Extensions, or ACEs for short. Editors can place ACEs on the dashboard, configure their properties, and add multiple instances of each ACE. What's special about Adaptive Card Extensions, is that they're the only type of Viva Connections extensions that works both in the desktop and mobile experience. What's more, editors can choose to display ACEs only to a specific group of users. The following sections explain the most important characteristics of Adaptive Card Extensions that you should consider when extending Viva Connections.

## Editors place Adaptive Card Extensions on the dashboard

Editors, who work with the Home site that supports Viva Connections, add Adaptive Card Extensions on a special dashboard page. You can create this dashboard page only in the site chosen as the Home site in your Microsoft 365 tenant.

:::image type="content" source="../media/3-viva-connections-dashboard-desktop-edit-mode.png" alt-text="Viva Connections dashboard with multiple Adaptive Card Extensions in desktop edit mode.":::

In the Viva Connections desktop experience, editors can embed the dashboard in the home page of Viva Connections using the Dashboard for Viva Connections web part.

:::image type="content" source="../media/3-viva-connections-dashboard-desktop.png" alt-text="Dashboard with Adaptive Card Extensions rendered in the Viva Connections desktop experience.":::

The Viva Connections mobile experience renders Adaptive Card Extensions placed in the dashboard in a mobile-friendly way.

:::image type="content" source="../media/3-viva-connections-dashboard-mobile.png" alt-text="Viva Connections dashboard mobile experience.":::

When adding Adaptive Card Extensions to the dashboard, editors decide where they place each card. For each card, they can change its settings and they can also choose to add multiple instances of the same card.

## Adaptive Card Extensions are configurable

If you make Adaptive Card Extensions configurable, they'll be suitable for many scenarios. For example, if you build an ACE that shows stock information, you'd make the stock name configurable so that the same ACE can be used to show information about different stocks without changing code.

:::image type="content" source="../media/3-adaptive-card-extension-configuration.png" alt-text="Adaptive Card Extension property pane with configuration options.":::

You don't have to make your Adaptive Card Extensions configurable, but you should consider it. As business requirements change, letting editors configure your ACE will help them quickly apply changes without updating the code.

## Editors can target Adaptive Card Extensions to a specific audience

Some Adaptive Card Extensions are relevant only to a specific group of users. For example, an ACE that allows managers to quickly review vacation requests, is relevant only to managers. Editors who place ACEs on the dashboard, can configure them to show only to a specific group of users. This allows organizations to show users only cards that are relevant to them. Organizations can decide themselves how they define audiences. The organization structure or job type are two common examples of audiences that many organizations configure.

## Adaptive Card Extensions use Adaptive Cards to render the UI

Adaptive Card Extensions use the Adaptive Cards technology to render their UI. When building other extensions for Viva Connections, your render the UI using HTML and JavaScript. In ACEs, you use the Adaptive Card JSON schema to define your card's UI and then bind data to it.

> [!TIP]
> For more information about Adaptive Cards, see [https://adaptivecards.io](https://adaptivecards.io).

Each card consists of the default card view, and an optional quick view that allows you to show extra details, before taking users to another app, like a Teams personal app, a bot, or a web app.

:::image type="content" source="../media/3-adaptive-card-extension-user-flow-desktop.png" alt-text="User flow when using Adaptive Card Extensions in Viva Connections desktop.":::

Viva Connections automatically adjusts the rendering to the desktop and mobile experience.

:::image type="content" source="../media/3-adaptive-card-extension-user-flow-mobile.png" alt-text="User flow when using Adaptive Card Extensions in Viva Connections mobile.":::

**Card view**

To build the card view, you can choose from three templates:

- Basic

  :::image type="content" source="../media/3-card-view-basic.png" alt-text="Sample Adaptive Card Extension using the basic card view.":::
- Image

  :::image type="content" source="../media/3-card-view-image.png" alt-text="Sample Adaptive Card Extension using the image card view.":::
- Primary text

  :::image type="content" source="../media/3-card-view-primary-text.png" alt-text="Sample Adaptive Card Extension using the primary text card view.":::

> [!IMPORTANT]
> You choose which card template you want to use when you add an Adaptive Card Extension to your project. While it's possible to change the template later, it's more convenient to choose the right card template from the start.

Each card consists of an icon, a title, and a body area that's different for each card template. For the icon, you can either use a Fluent UI icon or a custom image.

> [!TIP]
> Adaptive Card Extensions support only a subset of Fluent UI icons. To see which icons are supported, add the Web link ACE to the dashboard and in its properties, open the icon picker.

Each card can also have buttons linked to specific actions, like showing the ACE's quick view or opening an app.

**Quick view**

When building Adaptive Card Extensions, you can choose to include a quick view. A quick view is an extra view in an Adaptive Card Extension.

In the Viva Connections desktop experience, it's rendered as a tooltip.

:::image type="content" source="../media/3-adaptive-card-extension-quick-view-desktop.png" alt-text="Adaptive Card Extension with quick view showing additional information in Viva Connections desktop.":::

In the Viva Connections mobile experience, the quick view is rendered as an overlay.

:::image type="content" source="../media/3-adaptive-card-extension-quick-view-mobile.png" alt-text="Adaptive Card Extension with quick view showing additional information in Viva Connections mobile.":::

The quick view can be informative and show users additional information. It can also show forms that users can fill in, without having to open a separate application. The quick view gives you a lot of flexibility in designing your solution. You can choose to build a solution that consists of an ACE with just the card view that links to an app. You can also build a solution that consists of just an ACE with the card- and quick views. Finally, you can build a solution that has an ACE with card- and quick views, which link to an external app.

:::image type="content" source="../media/3-adaptive-card-extension-quick-view-form.png" alt-text="Adaptive Card Extension with quick view showing a form in Viva Connections desktop.":::

When building quick views, you specify the complete Adaptive Card and bind the data to it. This allows you to fully benefit from adaptive cards and offer your users rich experiences.

> [!TIP]
> The easiest way to design a quick view is to use the Adaptive Card Designer at [https://adaptivecards.io/designer/](https://adaptivecards.io/designer/).

## Adaptive Card Extensions can link to other resources

Adaptive Card Extensions keep employees informed. They communicate important information in a succinct way. Often, you'll need to provide users with more context or a richer experience. In such cases, you can configure the Adaptive Card Extension to link to other resources, like a Teams personal app, a bot, or a web app. The main benefit of linking ACEs to other apps is that users stay in the same context and can easily get back to their previous task.

On both the card- and the quick view, you can add buttons that link to other apps. You can also configure the card itself as a link.

## Adaptive Card Extensions work with Viva Connections desktop and mobile experiences

When extending Viva Connections, Adaptive Card Extensions are the only type of extension that work both in the desktop and the mobile experience of Viva Connections. An ACE will automatically render in a desktop- or a mobile-friendly way, depending on the Viva Connections experience someone is using, without any extra development work on your part. When you build a solution that should be visible in both Viva Connections experiences, you should consider building Adaptive Card Extensions.
