Let's use all the concepts discussed up to this point and make changes to the sample app to access the calendar events.

1. Locate the **index.html** file in your code editor. Add the following HTML code in the `<main>` tag just before its closing `</main>` tag.

    ```html
    <button id="btnShowEvents" style="display: none;" onclick="displayEvents();">Show events</button>
    <div id="eventWrapper" style="display: none;">
      <p>Your events retrieved from Microsoft Graph for the upcoming week:</p>
      <ul id="events"></ul>
    </div>
    ```

1. Locate the **graph.js** file in your editor. Add a new function to get the calendar events of the signed-in user for the upcoming week by using the Microsoft Graph API endpoint `/me/calendarView`. You'll call this function `getEvents()`.

    Add the following code to the end of the file:

    ```javascript
    async function getEvents() {
      ensureScope('Calendars.read');
      const dateNow = new Date();
      const dateNextWeek = new Date();
      dateNextWeek.setDate(dateNextWeek.getDate() + 7);
      const query = `startDateTime=${dateNow.toISOString()}&endDateTime=${dateNextWeek.toISOString()}`;

      return await graphClient
      .api('/me/calendarView').query(query)
      .select('subject,start,end')
      .orderby(`start/DateTime`)
      .get();
    }
    ```

1. Locate the **ui.js** file, and add a new function to display the calendar events received from Microsoft Graph in the list element. You'll call this function `displayEvents()`.

    Add the following code to the end of the file:

    ```javascript
    async function displayEvents() {
      var events = await getEvents();
      if (!events || events.value.length < 1) {
        var content = document.getElementById('content');
        var noItemsMessage = document.createElement('p');
        noItemsMessage.innerHTML = `No events for the coming week!`;
        content.appendChild(noItemsMessage)

      } else {
        var wrapperShowEvents = document.getElementById('eventWrapper');
        wrapperShowEvents.style = "display: block";
        const eventsElement = document.getElementById('events');
        eventsElement.innerHTML = '';
        events.value.forEach(event => {
          var eventList = document.createElement('li');
          eventList.innerText = `${event.subject} - From  ${new Date(event.start.dateTime).toLocaleString()} to ${new Date(event.end.dateTime).toLocaleString()} `;
          eventsElement.appendChild(eventList);
        });
      }
      var btnShowEvents = document.getElementById('btnShowEvents');
      btnShowEvents.style = "display: none";
    }
    ```

1. In the same **ui.js** file, update the `displayUI()` function to display the **Show events** button only on successful authorization.

    Add the following code to the end of the `displayUI()` function:

    ```javascript
    var btnShowEvents = document.getElementById('btnShowEvents');
    btnShowEvents.style = "display: block";
    ```

Now that you've added all the other functions and code snippets to a signed-in user's events for the upcoming week, the next step is to run the app locally.

## Run the app

To run and test the application, you'll need to add some calendar events into your calendar by using Microsoft Outlook or Microsoft Teams. The events should fall within a one-week period.

>[!TIP]
> For this step, make sure you have Node.js installed in your machine.

It's time to see your application run locally.

1. In the terminal window, go to the project folder where the source code is located.
1. Run the following script in the command line to start your app locally by opening `http://localhost:8080` in the browser.

    ```console
    npm start
    ```

1. If the app is configured correctly, you'll see a sign in button.

    :::image type="content" source="../media/6-sign-in-button.png" alt-text="Screenshot showing the Sign-in with Microsoft button.":::

1. Sign in by using an account in the same Microsoft 365 developer tenant used in unit 2, where you registered the Azure Active Directory application.
1. After you successfully sign in, you're prompted to give consent.

     :::image type="content" source="../media/6-consent-page.png" alt-text="Screenshot showing the consent page.":::

1. Select **Accept** to give consent for the application to do operations for the user.
1. After you consent, the application tries to get an access token by using the validated account information. The Microsoft Authentication Library handles this step for you.
1. After the token is back in the application, a GET request is made to the Microsoft Graph `/me` endpoint. The access token is passed in the Authorization Header. The call to `/me` then retrieves the data securely from the service.
1. After the response is received from Microsoft Graph, you'll see the welcome message with the name of the signed-in user. Select the **Show events** button.

     :::image type="content" source="../media/6-welcome-message.png" alt-text="Screenshot showing the welcome message.":::

1. Another consent dialog appears. Notice the **Read your calendar** permission scope you're consenting to.

    :::image type="content" source="../media/6-consent-page-calendar.png" alt-text="Screenshot showing the consent page for calendar permission.":::

1. Select **Accept** to give consent for the application to do operations for the user.
1. After you consent, the application tries to get an access token by using the validated account information. The Microsoft Authentication Library handles this step for you.
1. After the token is back in the application, a GET request is made to the Microsoft Graph `/me/calendarView` endpoint. The access token is passed in the Authorization Header. The call to `/me/calendarView` then retrieves the data securely from the service.
1. After the response is received from Microsoft Graph, you'll see the signed-in user's calendar events listed for the upcoming week.

    :::image type="content" source="../media/6-show-events.png" alt-text="Screenshot showing the user's events for the week":::

You've successfully demonstrated how to access and display Microsoft 365 calendar events for a signed-in user by using Microsoft Graph.
