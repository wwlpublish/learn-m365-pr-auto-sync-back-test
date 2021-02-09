# Exercise - Show data from Microsoft 365
In this exercise, we'll practice using Microsoft Graph Toolkit components in our application and show data from Microsoft 365.

## Before you start

As a pre-requisite for this exercise, you'll need to complete the first exercise in this module: **Exercise - Sign in your app with the Microsoft Graph Toolkit Components**.

## Add Agenda component in your app

We already completed the steps for building the authentication in the previous exercise.

Now, we would like to show upcoming calendar events for signed-in user in our application. Add your **Agenda** component in the `body` of your HTML file:

```html
<mgt-agenda></mgt-agenda>
```

Final version of your HTML file will be as shown below:

:::image type="content" source="../media/.." alt-text="HTML with Agenda component":::

## Test your app in browser

1. Open **Command Palette** in Visual Studio Code with **`CTRL + Shift + P`**.

2. Select **Live Server: Open with Live Server** to run your app locally:
:::image type="content" source="../media/06-LiveServer.png" alt-text="Live Server":::

3. Now, your app is running on `http://localhost:3000`, sign-in with your account and consent permissions:
:::image type="content" source="../media/..." alt-text="Permissions":::

4. 