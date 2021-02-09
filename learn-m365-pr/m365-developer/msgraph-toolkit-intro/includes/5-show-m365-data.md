# Show data from Microsoft 365

In this unit, we'll discover Microsoft Graph Toolkit components and learn how to show data from Microsoft 365 using the components.

## What are Microsoft Graph Toolkit components?

The Microsoft Graph Toolkit provides a collection of web components powered by Microsoft Graph APIs. Components give us the opportunity of building experiences with Microsoft 365.

Suppose you would like to show upcoming calendar events for signed-in user in your application. You can easily implement calendar events by using `mgt-agenda` component in your application. The **Agenda** component will return calendar events from Microsoft Graph by default.

## Benefits of using the components

Microsoft Graph Toolkit components make implementing Microsoft 365 experiences in your application simple and easy.

### Less coding, more features

The components are designed to work with Microsoft Graph in a simple way. Each component provides M365 experiences with pre-built UI and it requires no customization.  

As a developer, you'll only need to add a single line of code to implement a component in your app and, show data from Microsoft 365.

For example, if you want to provide people search ability and show list of results in your app, you can use **People Picker** component. The `mgt-people-picker` will show user's data with pre-built UI that looks and feels like Microsoft 365 experience:

```html
<mgt-people-picker></mgt-people-picker>
```

:::image type="content" source="../media/05-peoplepicker.gif" alt-text="Microsoft Graph Toolkit People Picker":::

### Works with every modern browser and web framework

Microsoft Graph Toolkit components are built based on web standards.

The components are compatible with any modern browser such as Microsoft Edge, Firefox, Chrome, Safari, and more.

Any modern web framework can be used for building apps with Microsoft Graph Toolkit components, some examples for the web frameworks are React, Angular and, Vue.

### Flexible for customization

The components are designed to give unique Microsoft 365 experiences with their pre-built UI. However, they're flexible to be customized and adapted in your application's design guidelines.