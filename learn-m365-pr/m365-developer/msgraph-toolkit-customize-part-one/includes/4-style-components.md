Microsoft Graph Toolkit components are flexible for customization. If you want to change the way components look and feel, you can easily do that by using a set of custom CSS properties.

Microsoft Graph Toolkit components use the shadow DOM. It means that they're isolated from the rest of your web app. For example, if you changed the global font color of your web app to blue, Microsoft Graph Toolkit components would still use their default color.

:::image type="content" source="../media/4-styling.png" alt-text="Microsoft Graph Toolkit components styling.":::

This isolation is intentional so that Microsoft Graph Toolkit components always render as intended and aren't affected by the specific styling of your web app.

To style the contents of Microsoft Graph Toolkit, use custom CSS properties exposed by the component. For example, to change the font color used to display events in the agenda component:

```html
<style>
  mgt-agenda {
    --agenda-header-color: blue;
    --event-time-color: blue;
    --event-subject-color: blue;
    --event-location-color: blue;
  }
</style>
```

:::image type="content" source="../media/4-css-properties.png" alt-text="Microsoft Graph Toolkit components styling with CSS custom properties.":::

You can find more information about the available custom CSS properties exposed by each component in their documentation.

Microsoft Graph Toolkit also provides light and dark themes. You can choose the best theme for your web app and apply it as an individual component theme, regional theme, or global theme to the HTML body. You can also customize CSS with a theme.

Let's say you're using the **People picker** component and you want the dark theme. You can apply the dark theme to `<mgt-people-picker>` by assigning a value of **mgt-dark** to the `class` attribute.

```html
<mgt-people-picker class="mgt-dark"></mgt-people-picker>
```

The **People picker** component with the dark theme applied will look like this example.

:::image type="content" source="../media/4-dark-theme.png" alt-text="Microsoft Graph Toolkit components with dark theme.":::

In the next exercise, you'll learn how to use styling with Microsoft Graph Toolkit components to customize your web app.
