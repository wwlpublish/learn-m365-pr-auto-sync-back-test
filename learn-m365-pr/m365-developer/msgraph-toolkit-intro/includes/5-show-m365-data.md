# Show data from Microsoft 365

In this unit, we'll discover Microsoft Graph Toolkit components and learn how to show data from Microsoft 365 using the components.

## What are Microsoft Graph Toolkit components?

Microsoft Graph Toolkit components (web components) are actually HTML tags. Components work with providers to get user access token, call Microsoft Graph APIs for getting required data and show this data with Fluent UI.

Basically, these reusable HTML tags have complete functionality to help us integrate pieces of Microsoft 365.

There are many components available to get the most popular Microsoft 365 datasets in your application such as people, tasks, agenda. Let's discover components with some scenarios:

### Scenario 1: Get events from calendar

Suppose you would like to show upcoming calendar events for signed-in user in your application. You can easily implement calendar events by using `mgt-agenda` component in your app. The **Agenda** component will return calendar events from Microsoft Graph `/me/calendarview` API endpoint by default.

```html
<mgt-agenda></mgt-agenda>
```

:::image type="content" source="../media/05-mgt-agenda.png" alt-text="Microsoft Graph Toolkit Agenda":::

### Scenario 2: Show tasks from planner

Let's say you would like to build a web page to show user's tasks. You can use **Tasks** component to get data from Microsoft Planner. The `mgt-tasks` will show user's data with pre-built UI that looks and feels like Microsoft 365 experience:

```html
<mgt-tasks></mgt-tasks>
```

:::image type="content" source="../media/05-mgt-tasks.png" alt-text="Microsoft Graph Toolkit Tasks":::

### Scenario 3: Integrate people search

If you want to show list of people in your app where you can search for a person, you can use **People Picker** component.

```html
<mgt-people-picker></mgt-people-picker>
```

:::image type="content" source="../media/05-peoplepicker.gif" alt-text="Microsoft Graph Toolkit People Picker":::

You can process the results by using attributes available for `mgt-people-picker` such as limiting the maximum number of people showing in the list:

```html
<mgt-people-picker show-max="3"></mgt-people-picker>
```

:::image type="content" source="../media/05-mgt-peoplepicker-showmax.png" alt-text="Microsoft Graph Toolkit People Picker show-max attribute":::

In summary, all components in Microsoft Graph Toolkit share the same structure. They work with Providers to handle the authentication, get data using Microsoft Graph APIs and show the results with pre-built UI.