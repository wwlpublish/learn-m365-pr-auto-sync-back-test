In this unit, you'll discover other Microsoft Graph Toolkit components and learn how to show data from Microsoft 365 by using these components.

## What are Microsoft Graph Toolkit components?

Microsoft Graph Toolkit components (web components) are actually HTML tags. Components work with providers to get user access tokens, call Microsoft Graph APIs to retrieve the required data, and show the data by using Fluent UI. These reusable HTML tags help you integrate different types of data from Microsoft 365.

There are many components available that you can use to access the most popular Microsoft 365 datasets in your application. Let's discuss a few components and see how to use them in various scenarios.

### Scenario 1: Get events from calendar

Suppose you want to show upcoming calendar events for a signed-in user in your application. You can easily implement calendar events by using the `mgt-agenda` component in your app. By default, this component returns calendar events from Microsoft Graph `/me/calendarview` API endpoint.

```html
<mgt-agenda></mgt-agenda>
```

:::image type="content" source="../media/05-agenda.png" alt-text="Screenshot of the Agenda component of the Microsoft Graph Toolkit.":::

### Scenario 2: Show tasks from planner

Let's say you want to build a web page to show a user's tasks. You can use the Tasks component to get data from Microsoft Planner. `mgt-tasks` will show a user's data by using a pre-built UI that's similar to the Microsoft 365 experience:

```html
<mgt-tasks></mgt-tasks>
```

:::image type="content" source="../media/05-tasks.png" alt-text="Screenshot of the Tasks component of the Microsoft Graph Toolkit.":::

### Scenario 3: Integrate people search

If you want to show a list of people in your app and search for a specific person, you can use the People Picker component.

```html
<mgt-people-picker></mgt-people-picker>
```

:::image type="content" source="../media/05-people-picker.gif" alt-text="Brief animation of the People Picker component of the Microsoft Graph Toolkit.":::

You can process the results by using attributes supported by the `mgt-people-picker` component. For example, you can limit the maximum number of people shown in the list:

```html
<mgt-people-picker show-max="3"></mgt-people-picker>
```

:::image type="content" source="../media/05-people-picker-max.png" alt-text="Screenshot of the show-max attribute in the People Picker component.":::

In summary, all components in Microsoft Graph Toolkit share the same structure. They work with providers to handle the authentication, get data by using Microsoft Graph APIs, and show the results by using a pre-built UI.
