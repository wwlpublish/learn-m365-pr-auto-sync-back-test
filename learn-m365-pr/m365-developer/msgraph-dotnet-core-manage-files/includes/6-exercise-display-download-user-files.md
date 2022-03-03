In this exercise, you'll extend the app to display a list of files in the user’s OneDrive for Business root folder.

## Get the list of files

Start by adding a Microsoft Graph call into the application.

1. Open **Startup.cs** in your editor and take a moment to explore the Microsoft Identity, Microsoft Graph, and ASP.NET Core middleware that is defined in `ConfigureServices()`.
1. Locate the following code in the `ConfigureServices()` method. This code enables dependency injection for custom objects named **GraphProfileClient** and **GraphFilesClient**. The objects are scoped to the HTTP request, which means they’ll be created once per request to the server.

    ```csharp
    services.AddScoped<GraphProfileClient>();
    services.AddScoped<GraphFilesClient>();
    ```

1. Open **Graph/GraphFilesClient.cs** and take a moment to explore the existing code. Note the following features:

    - Two `readonly` fields named `_logger` and `_graphServiceClient` are included in the class. Objects injected into the constructor will be assigned to these fields.
    - The class contains `GetFiles()`, `DownloadFile()`, `UploadFile()`, and `UploadLargeFile()` methods.

1. Remove the existing code in the constructor.
1. Modify the constructor to inject `ILogger<GraphFilesClient>` and `GraphServiceClient` and assign the parameter values to the associated fields:

    ```csharp
    public GraphFilesClient(
      ILogger<GraphFilesClient> logger,
      GraphServiceClient graphServiceClient)
    {
      _logger = logger;
      _graphServiceClient = graphServiceClient;
    }
    ```

1. Locate the `GetFiles()` method. Within the `try` block, replace the existing code with the following code to use `_graphServiceClient` to retrieve files from the user’s account.

    ```csharp
    return await _graphServiceClient.Me.Drive.Root.Children
                .Request()
                .Select(file => new
                {
                    file.Id,
                    file.Name,
                    file.Folder,
                    file.Package
                })
                .GetAsync();
    ```

1. Locate the `DownloadFile()` method and replace the existing code in the `try` block with the following code to retrieve a file based on its ID.

    ```csharp
    return await _graphServiceClient
        .Me.Drive.Items[fileId].Content
        .Request()
        .GetAsync();
    ```

1. Save the **GraphFilesClient.cs** file before continuing.
1. Open **Pages/Files.cshtml.cs** and take a moment to explore the existing code. Note the following features:

    - The `FilesModel` class contains several fields and properties such as `_logger`, `_graphFilesClient`, `UploadedFile`, and `Files`.
    - `GraphFilesClient` is injected into the constructor and assigned to the `_graphFilesClient` field.
    - `OnGetAsync()`, `OnPostAsync()`, and `OnGetDownloadFile()` methods are defined.

1. Locate the `OnGetAsync()` method and replace the existing code with the following code:

    ```csharp
    Files = await _graphFilesClient.GetFiles();
    ```

    This code uses the `GraphFilesClient` instance to retrieve user files and assigns them to the `Files` property.

1. Locate the `OnGetDownloadFile()` method and replace the existing code in the method with the following code:

    ```csharp
    var stream = await _graphFilesClient.DownloadFile(id);
    return File(stream, MediaTypeNames.Application.Octet, name);
    ```

    This code does the following tasks:
    - It calls the `_graphFilesClient.DownloadFile` method, which accepts the file ID as a parameter.
    - Once the file stream is returned, `OnGetDownloadFile()` returns a new `File` object from the Razor page. This step allows the file to be downloaded in the user's browser.

1. Save the **Files.cshtml.cs** file before continuing.

## Display and download files in the app

The next step is to show the user's files in a webpage and allow them to be downloaded.

1. Open the **Files.cshtml** file in your editor.
1. Take a moment to look through the HTML and Razor code and notice that it handles the following tasks:

    - Ensures that the user is authenticated.
    - Checks the `Model.Files` property to see if there are any files to iterate through and display in the page.

1. Locate the `@* Add foreach here *@` comment in the file and replace it with the following code:

    ```cshtml
    @foreach(var file in Model.Files)
    {
    ```

1. Locate the `@* Add foreach closing bracket here *@` comment and replace it with a closing bracket for the `foreach` statement added in the previous step.

1. Add the following code in the `foreach` loop:

    ```cshtml
    if (file.Folder == null && file.Package == null) {
        <li>
            <a asp-page-handler="DownloadFile"
                asp-route-name="@file.Name"
                asp-route-id="@file.Id">@file.Name</a>
        </li>
    }
    ```

    This code does the following tasks:
    - Checks that the file object isn't a folder or package.
    - Uses Razor syntax to create a hyperlink.  When the user selects the link, the file name and file ID will be passed to the `FilesModel`'s `DownloadFile` method that you modified earlier.

1. Save the **Files.cshtml** file before continuing.

## Run the app

Before running the application, ensure that the account used to sign in has some files in OneDrive. It's time to run your application and try it out!

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
1. Select the *Files* link in the header to view the user’s OneDrive files.

    :::image type="content" source="../media/6-files-list.png" alt-text="Page displaying calendar events.":::

    > [!NOTE]
    > If you’re not seeing any files, please ensure that the user has files in OneDrive.

1. Select a file in the list to download it to your machine.

1. Close your browser and press <kbd>CTRL</kbd>+<kbd>C</kbd> in the terminal window to stop the server before continuing.

    > [!NOTE]
    > If you’ve opened the project in Visual Studio, you can close the browser or select <kbd>SHIFT</kbd>+<kbd>F5</kbd> in Visual Studio to stop the server. Close the terminal window Visual Studio created if it's still open.

You’ve successfully demonstrated how to access, display, and download files for a signed in user using Microsoft Graph and ASP.NET Core!
