In this exercise, you'll learn how to examine data available in Microsoft Graph Toolkit components. You'll also ensure that components are rendered consistently within your web app. Let's start the exercise by preparing the web app.

## Prepare the web app

1. In Visual Studio Code, open the **index.html** file.
1. Reset its contents to the following HTML content. You'll replace `YOUR-CLIENT-ID` with the **Application (client) ID** from the Azure Active Directory app you registered in the previous module, **[Configure and style Microsoft Graph Toolkit components by using attributes and CSS](/learn/modules/msgraph-toolkit-customize-part-one)**:

    ```html
    <html>
      <head>
        <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
      </head>

      <body>
        <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
        <mgt-login></mgt-login>
        <mgt-agenda days="3" group-by-day></mgt-agenda>
      </body>
    </html>
    ```

1. Verify that the web app works as expected. In Visual Studio Code, run Live Server to test your app. Open your browser, and go to `http://localhost:3000`. You should see a list of events.

## Debug the component template

Now that you've confirmed that the web app works, let's adjust how the **Agenda** component displays events.

1. Change the **Agenda** component to only show an event's title by specifying the following in the template.

    ```html
    <mgt-agenda days="3" group-by-day>
      <template>{{ event.title }}</template>
    </mgt-agenda>
    ```

   The **Agenda** component doesn't show anything now. Let's fix it!

1. Because you want to change the rendering of the events, let's use the `event` template by using the `data-type` attribute.

    ```html
    <mgt-agenda days="3" group-by-day>
      <template data-type="event">{{ event.title }}</template>
    </mgt-agenda>
    ```

1. You see a list of days now, but the component still doesn't show the events' titles. Let's see what data is available in the template by changing it.

    ```html
    <mgt-agenda days="3" group-by-day>
      <template data-type="event">{{ console.log(this) }}</template>
    </mgt-agenda>
    ```

1. After you examine the data logged to the console in the browser's developers' tools, you can see that the event's title is stored in the `subject` property.

   :::image type="content" source="../media/5-exercise.png" alt-text="Screenshot that shows the result of the console.":::

1. Update the template so that it refers to the `subject` property instead of `title`.

    ```html
    <mgt-agenda days="3" group-by-day>
      <template data-type="event">{{ event.subject }}</template>
    </mgt-agenda>
    ```

1. You should now see the title for each event.

   :::image type="content" source="../media/5-result.png" alt-text="Screenshot that shows the result of the exercise.":::

Now, let's change the font color in the web app.

1. In Visual Studio Code, open the **index.html** file. Change the global font color of the web app by adding the following `style` element in the `head` section.

    ```html
    <style>
      body {
        color: blue;
      }
    </style>
    ```

1. In the body, add a greeting to welcome the user.

    ```html
    <h1>Hello</h1>
    ```

1. In the `mgt-agenda` component, remove the custom template you added in the previous exercise. The complete HTML of your web app should look like this example.

    ```html
    <html>
        <head>
          <script src="https://unpkg.com/@microsoft/mgt/dist/bundle/mgt-loader.js"></script>
          <style>
            body {
              color: blue;
            }
          </style>
        </head>

        <body>
          <h1>Hello</h1>
          <mgt-msal2-provider client-id="YOUR-CLIENT-ID"></mgt-msal2-provider>
          <mgt-login></mgt-login>
          <mgt-agenda days="3" group-by-day></mgt-agenda>
        </body>
    </html>
    ```

1. In Visual Studio Code, run Live Server to test your app. Open your browser, and go to `http://localhost:3000`. You should see a list of events.

    :::image type="content" source="../media/5-styling.png" alt-text="Screenshot that shows the result of the styling.":::

    The list of events isn't using the font color you defined. Let's fix it!

1. In Visual Studio Code, extend the `style` definition to include the CSS custom properties for styling events.

    ```html
    <style>
      body {
        color: blue;
      }
      mgt-agenda {
        --agenda-header-color: blue;
        --event-time-color: blue;
        --event-subject-color: blue;
        --event-subject-color: blue;
      }
    </style>
    ```

1. In Visual Studio Code, run Live Server to test your app. Open your browser, and go to `http://localhost:3000`. You should see a list of events displayed that use your web app's font color.

   :::image type="content" source="../media/5-final-result.png" alt-text="Screenshot that shows the final result.":::
