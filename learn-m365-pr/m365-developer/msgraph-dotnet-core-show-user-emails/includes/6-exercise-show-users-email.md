Let’s use all the concepts discussed up to this point and make changes to the sample app to access their email.

## Load emails from Microsoft Graph

Start by adding a call to Microsoft Graph to load the current user’s last 10 emails.

1. Open *Startup.cs* in your editor and take a moment to explore the Microsoft Identity, Microsoft Graph, and ASP.NET Core middleware that is defined in `ConfigureServices`.

1. Locate the following code in the `ConfigureServices` method. 

    ```csharp
    services.AddScoped<GraphProfileClient>();
    services.AddScoped<GraphEmailClient>();
    ```

    This code enables dependency injection for custom objects named `GraphProfileClient` and `GraphEmailClient`. The objects are scoped to the HTTP request, which means they'll be created once per request to the server.

1. Open *Graph/GraphEmailClient.cs* and take a moment to explore the existing code. Note the following features:

    - Two `readonly` fields named `_logger` and `_graphServiceClient` are included in the class. Objects injected into the constructor will be assigned to these fields.
    - The class contains `GetUserMessages`, `GetUserMessagesPage`, and `GetNextLink` methods.

1. Remove the existing code in the constructor. 

1. Modify the constructor to inject `ILogger<GraphEmailClient>` and `GraphServiceClient` and assign the parameter values to the associated fields:

    ```csharp
    public GraphEmailClient(
      ILogger<GraphEmailClient> logger, 
      GraphServiceClient graphServiceClient)
    {
        _logger = logger;
        _graphServiceClient = graphServiceClient;
    }
    ```

1. Locate the `GetUserMessages` method and replace the existing code with the following `try/catch` code blocks:

    ```csharp
    try
    {
              
    }
    catch (Exception ex)
    {
      _logger.LogError($"Error calling Graph /me/messages: { ex.Message}");
      throw;
    }
    ```

1. Within the `try` block, add the following code to use `_graphServiceClient` to retrieve 10 email messages from the user’s account. The code will order the results by the `receivedDatetime` property and only select the `Subject`, `BodyPreview`, and `ReceivedDateTime` properties.

    ```csharp
    var emails = await _graphServiceClient.Me.Messages
                .Request()
                .Select(msg => new
                {
                    msg.Subject,
                    msg.BodyPreview,
                    msg.ReceivedDateTime
                })
                .OrderBy("receivedDateTime desc")
                .Top(10)
                .GetAsync();
    return emails.CurrentPage;
    ```

1.	Save the *GraphEmailClient.cs* file before continuing.

1.	Open *Pages/Email.cshtml.cs* and take a moment to explore the existing code. Note the following features:

    - The `EmailModel` class contains several fields and properties such as `_graphEmailClient`, `NextLink`, and `Messages`.
    - `GraphCalendarClient` is injected into the constructor and assigned to the `_graphEmailClient` field.

1.	Locate the `OnGetAsync` method and replace the existing code with the following code:

    ```csharp
    Messages = await _graphEmailClient.GetUserMessages(); 
    ```

    This code uses the `GraphEmailClient` object to retrieve 10 email messages and assigns them to the `Messages` property.

1.	Save the *Email.cshtml.cs* file before continuing.

## Display emails in the app

The next step is to show the emails in the webpage.

1.	Open the *Email.cshtml* file in your editor.

1.	Take a moment to look through the HTML and Razor code and notice that it handles the following tasks:

    - Ensures that the user is authenticated.
    - Checks the `Model.Messages` property to see if there are any email messages to iterate through and display in the page.

1.	Locate the `@* Add foreach here *@` comment in the file and replace it with the following code:

    ```cshtml
    @foreach(var message in Model.Messages) 
    {
    ```

1.	Locate the `@* Add foreach closing bracket here *@` comment and replace it with a closing bracket for the `foreach` statement added in the previous step.

1.	Locate the `@* Add message subject here *@` comment and replace it with the following code to write out each message's subject:

    ```cshtml
    @message.Subject
    ```

1.	Locate the `@* Add message received date/time here *@` comment and replace it with the following code to write out the event’s start date and time:

    ```cshtml
    @message.ReceivedDateTime.GetValueOrDefault().UtcDateTime
    ```

1.	Finally, locate the `@* Add message body preview here *@` comment and replace it with the following code to write out a preview of the body of the message:

    ```cshtml
    @message.BodyPreview
    ```

1.	Save the *Email.cshtml* file before continuing.

## Run your app

Before running the application, ensure that the account used to sign in has some emails in it. It's time to run your application and try it out!

1. Perform the following step based on your code editor:

    - **Visual Studio**
    
        Press F5 to build and run the project.

    - **Visual Studio Code or another code editor**

        Open a terminal window in the *Begin* folder and run the following command:

        ```console
        dotnet run
        ```
 
1.	Open a browser and visit `https://localhost:5001`.

1.	Sign in using the Microsoft 365 developer tenant that you used earlier when registering the Azure Active Directory Application.

1.	Select the **Email** link in the header to view the user’s email messages.
 
1.	Once the page loads, a GET request is made to the Microsoft Graph `/me/messages` endpoint and the access token is passed in the Authorization Header. The call to `/me/messages` will then retrieve the data securely from the service and display it in the page.

    :::image type="content" source="../media/6-email-messages.png" alt-text="Page displaying email messages retrieved from Microsoft Graph.":::

    > [!NOTE]
    > If you’re not seeing any email messages, please ensure that there are emails in the inbox of the account that you use to sign in to the app.

1. Close your browser and press Ctrl+C in the terminal window to stop the server before continuing.

    > [!NOTE]
    > If you’ve opened the project in Visual Studio, you can close the browser or select Shift+F5 in Visual Studio to stop the server. Close the terminal window Visual Studio created if it's still open.
 
You've successfully demonstrated how to access and display Microsoft 365 email messages for a signed in user using Microsoft Graph and ASP.NET Core! 


