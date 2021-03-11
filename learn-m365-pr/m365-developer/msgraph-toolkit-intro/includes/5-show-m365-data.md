In this unit, you'll discover other Microsoft Graph Toolkit components and learn how to show data from Microsoft 365 using these components. 

## What are Microsoft Graph Toolkit components?

Microsoft Graph Toolkit components (web components) are actually HTML tags. Components work with providers to get user access tokens, call Microsoft Graph APIs to retrieve the required data, and show the data using Fluent UI. These reusable HTML tags help you integrate different types of data from Microsoft 365. 

There are many components available that can be used to access the most popular Microsoft 365 datasets in your application such as people, tasks, and agenda. 

Let's discuss a few components and see how they can be used in various scenarios.

### Scenario 1: Get events from calendar

Suppose you would like to show upcoming calendar events for a signed-in user in your application. You can easily implement calendar events by using the `mgt-agenda` component in your app. The **Agenda** component will return calendar events from Microsoft Graph's `/me/calendarview` API endpoint by default.

```html
<mgt-agenda></mgt-agenda>
```

:::image type="content" source="../media/05-agenda.png" alt-text="Microsoft Graph Toolkit Agenda":::

### Scenario 2: Show tasks from planner

Let's say you would like to build a web page to show a user's tasks. You can use the **Tasks** component to get data from Microsoft Planner. The `mgt-tasks` will show a user's data using a pre-built UI that looks and feels like the Microsoft 365 experience:

```html
<mgt-tasks></mgt-tasks>
```

:::image type="content" source="../media/05-tasks.png" alt-text="Microsoft Graph Toolkit Tasks":::

### Scenario 3: Integrate people search

If you want to show a list of people in your app and search for a specific person, you can use the **People Picker** component.

```html
<mgt-people-picker></mgt-people-picker>
```

:::image type="content" source="../media/05-people-picker.gif" alt-text="Microsoft Graph Toolkit People Picker":::

You can process the results by using attributes supported by the `mgt-people-picker` component such as limiting the maximum number of people shown in the list:

```html
<mgt-people-picker show-max="3"></mgt-people-picker>
```

:::image type="content" source="../media/05-people-picker-max.png" alt-text="Microsoft Graph Toolkit People Picker show-max attribute":::

In summary, all components in Microsoft Graph Toolkit share the same structure. They work with Providers to handle the authentication, get data using Microsoft Graph APIs, and show the results using a pre-built UI.