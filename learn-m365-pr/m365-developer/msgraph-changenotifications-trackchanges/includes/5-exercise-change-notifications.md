> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OO3j]

In this exercise, you'll extend the existing ASP.NET Core web API application to receive notifications from Microsoft Graph subscriptions. The notifications are sent after a subscription is successfully created, requesting Microsoft Graph to notify an endpoint when specified entities are created, updated, or deleted.

> [!IMPORTANT]
> This exercise assumes you have created the Azure AD application and .NET console application from the previous unit in this module. You'll edit the existing Azure AD application and .NET console application created in that exercise in this exercise.

## Update the ASP.NET Core web API project

Open the **Startup.cs** file and comment out the following line to disable SSL redirection.

```csharp
//app.UseHttpsRedirection();
```

### Add model classes

The application uses several new model classes for (de)serialization of messages to/from the Microsoft Graph.

Right-click in the project file tree, select **New Folder**, and name the new folder **Models**.

Right-click the **Models** folder and add three new files:

- **Notification.cs**
- **ResourceData.cs**
- **MyConfig.cs**

Replace the contents of **Notification.cs** with the following code:

```csharp
using System;
using System.Text.Json.Serialization;

namespace msgraphapp.Models
{
  public class Notifications
  {
    [JsonPropertyName("value")]
    public Notification[] Items { get; set; }
  }

  // A change notification.
  public class Notification
  {
    // The type of change.
    [JsonPropertyName("changeType")]
    public string ChangeType { get; set; }

    // The client state used to verify that the notification is from Microsoft Graph. Compare the value received with the notification to the value you sent with the subscription request.
    [JsonPropertyName("clientState")]
    public string ClientState { get; set; }

    // The endpoint of the resource that changed. For example, a message uses the format ../Users/{user-id}/Messages/{message-id}
    [JsonPropertyName("resource")]
    public string Resource { get; set; }

    // The UTC date and time when the webhooks subscription expires.
    [JsonPropertyName("subscriptionExpirationDateTime")]
    public DateTimeOffset SubscriptionExpirationDateTime { get; set; }

    // The unique identifier for the webhooks subscription.
    [JsonPropertyName("subscriptionId")]
    public string SubscriptionId { get; set; }

    // Properties of the changed resource.
    [JsonPropertyName("resourceData")]
    public ResourceData ResourceData { get; set; }
  }
}
```

Replace the contents of **ResourceData.cs** with the following:

```csharp
using System.Text.Json.Serialization;

namespace msgraphapp.Models
{
  public class ResourceData
  {
    // The ID of the resource.
    [JsonPropertyName("id")]
    public string Id { get; set; }

    // The OData etag property.
    [JsonPropertyName("@odata.etag")]
    public string ODataEtag { get; set; }

    // The OData ID of the resource. This is the same value as the resource property.
    [JsonPropertyName("@odata.id")]
    public string ODataId { get; set; }

    // The OData type of the resource: "#Microsoft.Graph.Message", "#Microsoft.Graph.Event", or "#Microsoft.Graph.Contact".
    [JsonPropertyName("@odata.type")]
    public string ODataType { get; set; }
  }
}
```

Replace the contents of **MyConfig.cs** with the following code:

```csharp
namespace msgraphapp
{
  public class MyConfig
  {
    public string AppId { get; set; }
    public string AppSecret { get; set; }
    public string TenantId { get; set; }
    public string Ngrok { get; set; }
  }
}
```

Open the **Startup.cs** file. Locate the method `ConfigureServices()` method and replace it with the following code:

```csharp
public void ConfigureServices(IServiceCollection services)
{
  services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_3_0);
  services.AddSwaggerGen(c =>
  {
    c.SwaggerDoc("v1", new OpenApiInfo { Title = "msgraphapp", Version = "v1" });
  });  
  var config = new MyConfig();
  Configuration.Bind("MyConfig", config);
  services.AddSingleton(config);
}
```

Open the **appsettings.json** file and replace the content with the following JSON.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "MyConfig":
  {
    "AppId": "<APP ID>",
    "AppSecret": "<APP SECRET>",
    "TenantId": "<TENANT ID>",
    "Ngrok": "<NGROK URL>"
  }
}
```

Replace the following variables with the values you copied earlier:

- `<NGROK URL>`: set to the https ngrok url you copied earlier
- `<TENANT ID>`: set to your Office 365 tenant ID you copied earlier
- `<APP ID>` & `<APP SECRET>`: set to the application ID and secret you copied earlier when you registered the app in the Azure AD admin center

### Add notification controller

The application requires a new controller to process the subscription and notification.

Right-click the **Controllers** folder, select **New File**, and name the controller **NotificationsController.cs**.

Replace the contents of **NotificationsController.cs** with the following code:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using msgraphapp.Models;
using System.Text.Json;
using System.Net;
using System.Threading;
using Microsoft.Graph;
using Microsoft.Identity.Client;
using System.Net.Http.Headers;

namespace msgraphapp.Controllers
{
  [Route("api/[controller]")]
  [ApiController]
  public class NotificationsController : ControllerBase
  {
    private readonly MyConfig config;

    public NotificationsController(MyConfig config)
    {
      this.config = config;
    }

    [HttpGet]
    public async Task<ActionResult<string>> Get()
    {
      var graphServiceClient = GetGraphClient();

      var sub = new Microsoft.Graph.Subscription();
      sub.ChangeType = "updated";
      sub.NotificationUrl = config.Ngrok + "/api/notifications";
      sub.Resource = "/users";
      sub.ExpirationDateTime = DateTime.UtcNow.AddMinutes(5);
      sub.ClientState = "SecretClientState";

      var newSubscription = await graphServiceClient
        .Subscriptions
        .Request()
        .AddAsync(sub);

      return $"Subscribed. Id: {newSubscription.Id}, Expiration: {newSubscription.ExpirationDateTime}";
    }

    public async Task<ActionResult<string>> Post([FromQuery]string validationToken = null)
    {
      // handle validation
      if(!string.IsNullOrEmpty(validationToken))
      {
        Console.WriteLine($"Received Token: '{validationToken}'");
        return Ok(validationToken);
      }

      // handle notifications
      using (StreamReader reader = new StreamReader(Request.Body))
      {
        string content = await reader.ReadToEndAsync();

        Console.WriteLine(content);

        var notifications = JsonSerializer.Deserialize<Notifications>(content);

        foreach(var notification in notifications.Items)
        {
          Console.WriteLine($"Received notification: '{notification.Resource}', {notification.ResourceData?.Id}");
        }
      }

      return Ok();
    }

    private GraphServiceClient GetGraphClient()
    {
      var graphClient = new GraphServiceClient(new DelegateAuthenticationProvider((requestMessage) => {
        // get an access token for Graph
        var accessToken = GetAccessToken().Result;

        requestMessage
            .Headers
            .Authorization = new AuthenticationHeaderValue("bearer", accessToken);

        return Task.FromResult(0);
      }));

      return graphClient;
    }

    private async Task<string> GetAccessToken()
    {
      IConfidentialClientApplication app = ConfidentialClientApplicationBuilder.Create(config.AppId)
        .WithClientSecret(config.AppSecret)
        .WithAuthority($"https://login.microsoftonline.com/{config.TenantId}")
        .WithRedirectUri("https://daemon")
        .Build();

      string[] scopes = new string[] { "https://graph.microsoft.com/.default" };

      var result = await app.AcquireTokenForClient(scopes).ExecuteAsync();

      return result.AccessToken;
    }

  }
}
```

**Save** all files.

Update the Visual Studio Code debugger launch configuration:

> [!NOTE]
> By default, the .NET Core launch configuration will open a browser and navigate to the default URL for the application when launching the debugger. For this application, we instead want to navigate to the NGrok URL. If you leave the launch configuration as is, each time you debug the application it will display a broken page. You can just change the URL, or change the launch configuration to not launch the browser:

In Visual Studio Code, open the file **.vscode/launch.json**.

Delete the following section in the default configuration:

```json
// Enable launching a web browser when ASP.NET Core starts. For more information: https://aka.ms/VSCode-CS-LaunchJson-WebBrowser
"serverReadyAction": {
  "action": "openExternally",
  "pattern": "^\\s*Now listening on:\\s+(https?://\\S+)"
},
```

Save your changes.

### Test the application

In Visual Studio Code, select **Run > Start debugging** to run the application. Visual Studio Code will build and start the application.

Once you see the following in the **Debug Console** window...

![Screenshot of the VS Code Debug Console](../media/05-vscode-debug-app-01.png)

Open a browser and navigate to **http://localhost:5000/api/notifications** to subscribe to change notifications. If successful you'll see output that includes a subscription ID like the one below:

![Screenshot of a successful subscription](../media/05-vscode-debug-app-02.png)

Your application is now subscribed to receive notifications from the Microsoft Graph when an update is made on any user in the Office 365 tenant.

Now, test the subscription by updating a user to trigger a notification from Microsoft Graph:

Open a browser and navigate to the [Microsoft 365 admin center (https://admin.microsoft.com/AdminPortal)](https://admin.microsoft.com/AdminPortal).

If you're prompted to sign-in, sign-in using an admin account.

Select **Users > Active users**.

![Screenshot of the Microsoft 365 Admin Center](../media/05-vscode-debug-app-03.png)

Select an active user and select **Edit** for their **Contact information**.

![Screenshot of a user's details](../media/05-vscode-debug-app-04.png)

Update the **Phone number** value with a new number and Select **Save**.

In the Visual Studio Code **Debug Console**, you'll see a notification has been received. Sometimes this may take a few minutes to arrive. An example of the output is below:

```console
Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
```

This indicates the application successfully received the notification from the Microsoft Graph for the user specified in the output. You can then use this information to query the Microsoft Graph for the users full details if you want to synchronize their details into your application.

### Renew subscriptions

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OATd]

Subscriptions for notifications expire and need to be renewed periodically. The following steps will demonstrate how to renew notifications

Open **Controllers > NotificationsController.cs** file

Add the following two member declarations to the `NotificationsController` class:

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;
```

Add the following new methods. These will implement a background timer that will run every 15 seconds to check if subscriptions have expired. If they have, they'll be renewed.

```csharp
private void CheckSubscriptions(Object stateInfo)
{
  AutoResetEvent autoEvent = (AutoResetEvent)stateInfo;

  Console.WriteLine($"Checking subscriptions {DateTime.Now.ToString("h:mm:ss.fff")}");
  Console.WriteLine($"Current subscription count {Subscriptions.Count()}");

  foreach(var subscription in Subscriptions)
  {
    // if the subscription expires in the next 2 min, renew it
    if(subscription.Value.ExpirationDateTime < DateTime.UtcNow.AddMinutes(2))
    {
      RenewSubscription(subscription.Value);
    }
  }
}

private async void RenewSubscription(Subscription subscription)
{
  Console.WriteLine($"Current subscription: {subscription.Id}, Expiration: {subscription.ExpirationDateTime}");

  var graphServiceClient = GetGraphClient();

  var newSubscription = new Subscription
  {
    ExpirationDateTime = DateTime.UtcNow.AddMinutes(5)
  };

  await graphServiceClient
    .Subscriptions[subscription.Id]
    .Request()
    .UpdateAsync(newSubscription);

  subscription.ExpirationDateTime = newSubscription.ExpirationDateTime;
  Console.WriteLine($"Renewed subscription: {subscription.Id}, New Expiration: {subscription.ExpirationDateTime}");
}
```

The `CheckSubscriptions()` method is called every 15 seconds by the timer.

> [!TIP]
> For production use this should be set to a more reasonable value to reduce the number of unnecessary calls to Microsoft Graph.

The `RenewSubscription()` method renews a subscription and is only called if a subscription is going to expire in the next two minutes.

Locate the method `Get()` and replace it with the following code:

```csharp
[HttpGet]
public async Task<ActionResult<string>> Get()
{
  var graphServiceClient = GetGraphClient();

  var sub = new Microsoft.Graph.Subscription();
  sub.ChangeType = "updated";
  sub.NotificationUrl = config.Ngrok + "/api/notifications";
  sub.Resource = "/users";
  sub.ExpirationDateTime = DateTime.UtcNow.AddMinutes(15);
  sub.ClientState = "SecretClientState";

  var newSubscription = await graphServiceClient
    .Subscriptions
    .Request()
    .AddAsync(sub);

  Subscriptions[newSubscription.Id] = newSubscription;

  if (subscriptionTimer == null)
  {
    subscriptionTimer = new Timer(CheckSubscriptions, null, 5000, 15000);
  }

  return $"Subscribed. Id: {newSubscription.Id}, Expiration: {newSubscription.ExpirationDateTime}";
}
```

### Test the changes

Within Visual Studio Code, select **Run > Start debugging** to run the application.

Navigate to the following url: **http://localhost:5000/api/notifications**. This will register a new subscription.

In the Visual Studio Code **Debug Console** window, approximately every 15 seconds, notice the timer checking the subscription for expiration:

```console
Checking subscriptions 12:32:51.882
Current subscription count 1
```

Wait a few minutes and you'll see the following when the subscription needs renewing:

```console
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

This indicates that the subscription was renewed and shows the new expiry time.

## Summary

In this exercise, you extended the existing ASP.NET Core web API application to receive notifications from Microsoft Graph subscriptions. The notifications are sent after a subscription is successfully created, requesting Microsoft Graph to notify an endpoint when specified entities are created, updated, or deleted.
