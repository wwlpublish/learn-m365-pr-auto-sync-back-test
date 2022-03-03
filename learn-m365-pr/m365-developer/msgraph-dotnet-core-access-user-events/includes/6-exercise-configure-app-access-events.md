Let’s use all the concepts discussed up to this point and make changes to the sample app to access the calendar events.

1. Open **Startup.cs** in your editor and take a moment to explore the Microsoft Identity, Microsoft Graph, and ASP.NET Core middleware that is defined in `ConfigureServices`.
1. Locate the following code in the `ConfigureServices()` method. This code enables dependency injection for custom objects named **GraphProfileClient** and **GraphEmailClient**. The objects are scoped to the HTTP request, which means they'll be created once per request to the server.

    ```csharp
    services.AddScoped<GraphProfileClient>();
    services.AddScoped<GraphCalendarClient>();
    ```

1. Open **Graph/GraphCalendarClient.cs** and take a moment to explore the existing code. Note the following fields and methods:

    - Two `readonly` fields named `_logger` and `_graphServiceClient` are included in the class. Objects injected into the constructor will be assigned to these fields.
    - The class contains `GetEvents()`, `GetUserMailboxSettings()`, and `GetUtcStartOfWeekInTimeZone()` methods.

1. Remove the existing code in the constructor.
1. Modify the constructor to inject `ILogger<GraphCalendarClient>` and `GraphServiceClient` and assign the parameter values to the associated fields:

    ```csharp
    public GraphCalendarClient(
      ILogger<GraphCalendarClient> logger,
      GraphServiceClient graphServiceClient)
    {
        _logger = logger;
        _graphServiceClient = graphServiceClient;
    }
    ```

1. Locate the `GetEvents()` method and replace the existing code with the following. This code defines start and end dates for calendar events that will be retrieved.

    ```csharp
    _logger.LogInformation($"User timezone: {userTimeZone}");
    // Configure a calendar view for the current week
    var startOfWeek = DateTime.Now;
    var endOfWeek = startOfWeek.AddDays(7);
    var viewOptions = new List<QueryOption>
    {
      new QueryOption("startDateTime", startOfWeek.ToString("o")),
      new QueryOption("endDateTime", endOfWeek.ToString("o"))
    };
    ```

1. Immediately below the previous code added in `GetEvents()`, add the following `try/catch` code blocks:

    ```csharp
    try
    {

    }
    catch (Exception ex)
    {
        _logger.LogError($"Error calling Graph /me/calendaview: { ex.Message}");
        throw;
    }
    ```

1. Within the `try` block, add the following code to use the `viewOptions`, define the calendar event properties to return, define how to sort the results, and initiate the call to `me/calendarView`:

    ```csharp
    // Use GraphServiceClient to call Me.CalendarView
    var calendarEvents = await _graphServiceClient
        .Me
        .CalendarView
        .Request(viewOptions)
        .Header("Prefer", $"outlook.timezone=\"{userTimeZone}\"")
        .Select(evt => new
        {
          evt.Subject,
          evt.Organizer,
          evt.Start,
          evt.End
        })
        .OrderBy("start/DateTime")
        .GetAsync();

    return calendarEvents;
    ```

1. Save **GraphCalendarClient.cs** before continuing.
1. Open **Pages/Calendar.cshtml.cs** and take a moment to explore the existing code. Note the following features:

    - The `CalendarModel` class contains several fields and properties such as `_logger`, `_graphCalendarClient`, `_graphProfileClient`, `MailboxSettings`, and `Events`.
    - `ILogger<CalendarModel>`, **GraphCalendarClient**, and **GraphProfileClient** are injected into the constructor and assigned to the associated fields.
    - A `FormatDateTimeZone()` method is included in the class. It’s used to format a `DateTime` object.

1. Locate the `OnGetAsync()` method and replace the existing code with the following code:

    ```csharp
    MailboxSettings = await _graphCalendarClient.GetUserMailboxSettings();
    var userTimeZone = (String.IsNullOrEmpty(MailboxSettings.TimeZone))
        ? "Pacific Standard Time"
        : MailboxSettings.TimeZone;
    Events = await _graphCalendarClient.GetEvents(userTimeZone);
    ```

    This code retrieves the user’s mailbox settings, determines if a time zone is defined, and passes the user’s time zone to the `GetEvents()` method that you created earlier in the **GraphCalendarClient** class. The retrieved events are stored in the class’s **Events** property.

1. Save **Calendar.cshtml.cs** before continuing.
1. Open **Pages/Calendar.cshtml**. This is a Razor Pages file used to render calendar event data stored in the **CalendarModel** class. It handles iterating through events stored in the **CalendarModel** class’s **Events** property and writes out the details about each calendar event in the page.
1. Take a moment to look through the HTML and Razor code and notice that it handles the following tasks:

    - Ensures that the user is authenticated.
    - Checks the `Model.Events` property to see if there are any events to iterate through and display in the page.

1. Locate the `@* Add foreach here *@` comment in the file and replace it with the following code:

    ```cshtml
    @foreach(var evt in Model.Events)
    {
    ```

1. Locate the `@* Add foreach closing bracket here *@` comment and replace it with a closing bracket for the `foreach` statement added in the previous step.

1. Locate the `@* Add event subject here *@` comment and replace it with the following code to write out each event’s subject:

    ```cshtml
    @evt.Subject
    ```

1. Locate the `@* Add event start date/time here *@` comment and replace it with the following code to write out the event’s starting date and time:

    ```cshtml
    @Model.FormatDateTimeTimeZone(evt.Start)
    ```

1. Finally, locate the `@* Add event end date/time here *@` comment and replace it with the following code to write out the event’s ending date and time:

    ```cshtml
    @Model.FormatDateTimeTimeZone(evt.End)
    ```

    The `FormatDateTimeTimeZone()` function in the `CalendarModel` class handles converting the start and end date time values to the logged in user’s defined time zone using the `MailboxSettings` that were retrieved when the page loaded.

1. Save *Calendar.cshtml* before continuing.

Now that you’ve added the code snippets to display a signed in user’s events for the upcoming week, the next step is to run the app locally.

## Run the app

To run and test the application, you’ll need to add some calendar events into your calendar using Microsoft Outlook or Microsoft Teams. The events should fall within a one-week period starting from the current date.

It's time to run your application and try it out!

1. Perform the following step based on your code editor:

    - **Visual Studio**

        Press <kbd>F5</kbd> to build and run the project.

    - **Visual Studio Code or another code editor**

        Open a terminal window in the **Begin** folder and run the following command:

        ```console
        dotnet run
        ```

1. Open a browser and visit `https://localhost:5001`.
1. Sign in using the Microsoft 365 developer tenant that you used earlier when registering the Azure Active Directory Application.
1. Once you've consented to the required permissions, the application will try to get an access token using the validated account information. This is handled for you by the middleware discussed earlier in **Startup.cs**.
1. After successfully getting the token back in the application, a **GET** request is made to the Microsoft Graph `/me` endpoint and the access token is passed in the authorization header. The call to `/me` will then retrieve the data securely from the service.
1. After the response is received from Microsoft Graph, you'll see the welcome message with the name of the signed in user.

    :::image type="content" source="../media/6-page-load-after-login.png" alt-text="Page displaying user name after signing into the application.":::

1. Select the *Calendar* link in the header to view the user’s calendar events.
1. Once the page loads, a **GET** request is made to the* Microsoft Graph `/m*e/calendarView` endpoint and the access token is passed in the Authorization Header. The call to `/me/calendarView ` will then retrieve the data securely from the service and display it in the page.

    :::image type="content" source="../media/6-calendar-list.png" alt-text="Page displaying calendar events.":::

    > [!NOTE]
    > If you’re not seeing any calendar events, please add some to the user's account that you used to sign in to the app.

1. Close your browser and press <kbd>CTRL</kbd>+<kbd>C</kbd> in the terminal window to stop the server before continuing.

    > [!NOTE]
    > If you’ve opened the project in Visual Studio, you can close the browser or select <kbd>SHIFT</kbd>+<kbd>F5</kbd> in Visual Studio to stop the server. Close the terminal window Visual Studio created if it's still open.

You've successfully demonstrated how to access and display Microsoft 365 calendar events for a signed in user using Microsoft Graph and ASP.NET Core!
