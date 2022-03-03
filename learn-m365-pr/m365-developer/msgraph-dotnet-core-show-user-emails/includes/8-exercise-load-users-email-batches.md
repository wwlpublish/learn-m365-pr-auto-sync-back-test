In this exercise, you'll extend the app to let you load a user's emails in batches of 10 items.

## Load emails in batches of 10 items

Start, by modifying the `GraphEmailClient` class to supporting loading batches of emails.

1. In your code editor, open the **Graph/GraphEmailClient.cs** file.
1. Take a moment to locate the `GetNextLink()` method. Notice that it accepts an **IUserMessagesCollectionPage** object named `pagedMessages` as a parameter. It uses this parameter to check if a next page request URL value exists.
1. Locate the `GetUserMessagesPage()` method and notice that it accepts a parameter named `nextPageLink` that represents the URL of the next batch of emails to retrieve. The method also accepts a parameter named `top`. `GetUserMessagesPage()` returns a tuple object that contains the retrieved messages and the URL for the next batch of emails.

    ```csharp
    public async Task<(IEnumerable<Message> Messages,
      string NextLink)> GetUserMessagesPage(
        string nextPageLink = null, int top = 10)
    {

    }
    ```

1. Replace the existing code in the `GetUserMessagesPage()` method with the following code:

    ```csharp
    IUserMessagesCollectionPage pagedMessages;

    try
    {
    }
    catch (Exception ex)
    {
      _logger.LogError($"Error calling Graph /me/messages to page messages: {ex.Message}");
      throw;
    }

    return (Messages: pagedMessages,
            NextLink: GetNextLink(pagedMessages));
    ```

1. Add the following code in the `try` block.

    ```csharp
    if (nextPageLink == null)
    {
      // Get initial page of messages
      pagedMessages = await _graphServiceClient.Me.Messages
              .Request()
              .Select(msg => new
              {
                  msg.Subject,
                  msg.BodyPreview,
                  msg.ReceivedDateTime
              })
              .Top(top)
              .OrderBy("receivedDateTime desc")
              .GetAsync();
    }
    else
    {
      // Use the next page request URI value to get the page of messages
      var messagesCollectionRequest = new UserMessagesCollectionRequest(nextPageLink, _graphServiceClient, null);
      pagedMessages = await messagesCollectionRequest.GetAsync();
    }
    ```

    This code does the following checks:

    - If no `nextPageLink` value exists, the `_graphServiceClient` instance injected into the class is used to retrieve the initial batch of messages.
    - If a `nextPageLink` value does exist, the code retrieves the next batch of emails by passing `nextPageLink` and `_graphServiceClient` to a new instance of `UserMessagesCollectionRequest`.

1. Save **GraphEmailClient.cs** before continuing.
1. Open **Pages/Email.cshtml.cs** in your code editor.
1. Replace the code in the `OnGetAsync()` method with the following to use the `GetUserMessagesPage()` method you modified previously:

    ```csharp
    var messagesPagingData = await _graphEmailClient.GetUserMessagesPage(NextLink);
    Messages = messagesPagingData.Messages;
    NextLink = messagesPagingData.NextLink;
    await Task.CompletedTask;
    ```

1. Save **Email.cshtml.cs** before continuing.
1. Open **Pages/Email.cshtml** in your code editor and locate the following code. This code block handles storing the `NextLink` property value in the page. As the user selects the **Next Page** button, the link value will be passed to the server and used to retrieve the next batch of emails.

    ```csharp
    @if (!String.IsNullOrEmpty(Model.NextLink)) {
        <a asp-page="/Email" asp-route-nextlink="@Model.NextLink"
          class="btn btn-primary">Next Page</a>
    }
    ```

## Run your app

Before running the application, ensure that the account used to sign in has some emails in it.

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
1. Select the **Email** link in the header to view the user’s email messages.
1. When the page loads, the user’s email messages will be displayed. If there are more than 10 messages, you should see a **Next Page** button at the bottom of the page. Select the button to view the next batch of email messages.

    :::image type="content" source="../media/8-email-messages-batch.png" alt-text="Page displaying email messages retrieved from Microsoft Graph.":::

    > [!NOTE]
    > If you’re not seeing any email messages, please ensure that there are emails in the inbox of the account that you use to sign in to the app.

1. Close your browser and press Ctrl+C in the terminal window to stop the server before continuing.

    > [!NOTE]
    > If you’ve opened the project in Visual Studio, you can close the browser or select Shift+F5 in Visual Studio to stop the server. Close the terminal window Visual Studio created if it's still open.

You've successfully demonstrated how to access and display Microsoft 365 email messages for a signed in user using Microsoft Graph and ASP.NET Core!
