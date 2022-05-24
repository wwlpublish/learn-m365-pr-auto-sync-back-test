> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OG3j]

In this unit, you'll learn how to manage the notification lifecycle with Microsoft Graph. The key aspect to notification lifecycle is to understand how change notification subscriptions work.

## Create change notification subscriptions

The process to create a subscription to receive change notifications from Microsoft Graph is similar to other requests you submit to Microsoft Graph.

### Register and configure Azure AD app

The first step to receiving change notifications from Microsoft Graph is to register an Azure AD application and configure it with the necessary permissions. The app needs the permissions required to do the query to return a data set that is used in the change notification. For example, if you want to be notified when new emails are received, your app needs to read emails, or the **Mail.Read** permission.

After creating the Azure AD app, the code in your web app must obtain an access token to submit requests to Microsoft Graph. Use the same process to obtain an access token for creating and managing change notification subscriptions that you would for any other type of request to Microsoft Graph.

### Create subscription

Next, create a change notification subscription by submitting an HTTP POST request to the subscriptions endpoint: **https://graph.microsoft.com/v1.0/subscriptions**. The payload of this request will contain the specifics of the subscription (*covered later in this unit*).

### Listen and respond to change notification subscription requests

When a subscription is created, Microsoft Graph immediately submits an HTTP POST to the endpoint registered in our subscription. The endpoint that you specify in the subscription request must respond within five seconds to tell Microsoft Graph that the subscription endpoint is valid and working. This request includes a value in the URL as a query parameter. Your confirmation response must take the value from the query parameter and return it as a string in the body of the response.

### Manage the subscription lifecycle

Change notification subscriptions will be good for a specified amount of time. For most resources, the maximum subscription length is three days, but you should check with each resource for the supported subscription maximum length. After that time, the subscription is automatically purged from Microsoft Graph. This means if your application does nothing after creating the subscription, it will only receive notifications up to the expiration time specified when the subscription is created.

You should have a process that is going to monitor the subscriptions to ensure that it isn't expired or isn't going to expire in a certain amount of time.

If the subscription does expire, you can create a new subscription. However, you can proactively renew existing subscriptions with no interruption in notifications as long as the subscription hasn't expired. Your application just needs to keep track of when the subscription will expire.

One option you can implement is to check the expiration timestamp on the subscription for each change notification your application receives. If the expiration is within a certain time frame, in addition to handling the change notification, your application can also renew the subscription. While this solution will work in scenarios that receive a high number of change notifications, it breaks down if no change notifications are received in the specified subscription window.

To address this, you could have another process on a timer that verifies notifications are received within the subscription window. If not, you can assume the subscription has likely expired and needs to be recreated.

The recommended approach is to have one process that handles the change notifications and a separate process that creates, monitors, manages, and renews change notification subscriptions.

### Create change notification subscription on changes to the `/users` endpoint

Let's look at the process to create a subscription. The following HTTP POST creates a subscription to receive change notifications on the **https://graph.microsoft.com/v1.0/users** endpoint when users are updated:

```http
POST https://graph.microsoft.com/v1.0/subscriptions HTTP/1.1
Authorization: bearer eyJ0eXAiOiJKV1QiLCJub25jZSI6IkFRQUJBQUFBQUFDRWZl<snip>
Content-Type: application/json; charset=utf-8
Host: graph.microsoft.com
Content-Length: 199

{
  "changeType": "updated",
  "clientState": "SecretClientState",
  "notificationUrl": "https://1a3f84c2.ngrok.io/api/notifications",
  "resource": "/users",
  "expirationDateTime": "2020-03-11T04:30:28.2257768+00:00"
}
```

The subscription creation request is submitted ot the **https://graph.microsoft.com/v1.0/subscriptions** endpoint. The body of the request includes the details of where the notifications should be sent (`notificationUrl`), the type of change to trigger the notification (`changeType`) and a timestamp for the expiration of the subscription (`expirationDateTime`).

Notice the `clientState` property in the body of the requests. This value will be included in every change notification to your registered endpoint. You can use this value to validate that the requests your endpoint receives are from your subscription, and not from someone else. The value of this property is of type `string` and can be anything you want it to be.

### Renew change notification subscription

Now let's look at the process for renewing a subscription. This is done by submitting an HTTP PATCH request to the endpoint of the subscription.

In the following example, note the endpoint includes the subscription ID, **47e861c4-2db2-455a-8774-57658ba185a1**, in the address:

```http
PATCH https://graph.microsoft.com/v1.0/subscriptions/47e861c4-2db2-455a-8774-57658ba185a1 HTTP/1.1
Authorization: bearer eyJ0eXAiOiJKV1QiLCJub25jZSI6IkFRQUJBQUFBQUFDRWZleFh
Content-Type: application/json; charset=utf-8
Host: graph.microsoft.com
Content-Length: 134

{
  "expirationDateTime": "2019-03-14T04:33:36.2394526+00:00"
}
```

The body of the request includes a single property, `expirationDateTime`, with the timestamp of the new expiration time.

## Change notification subscription endpoints

Microsoft Graph exposes multiple endpoints for developers to create and manage subscriptions:

- **Create subscriptions**
  - HTTP POST https://graph.microsoft.com/v1.0/subscriptions
  - Include the details of the subscription in the request body
- **List subscriptions**
  - HTTP GET https://graph.microsoft.com/v1.0/subscriptions
  - Retrieve a list of all active, non-expired, subscriptions
- **Get one subscription**
  - HTTP GET https://graph.microsoft.com/v1.0/subscriptions/{GUID}
  - Retrieve the details of a specific subscription using the subscription's ID
- **Update subscription**
  - HTTP PATCH https://graph.microsoft.com/v1.0/subscriptions/{GUID}
  - Update the expiration time of the subscription
- **Delete subscription**
  - HTTP DELETE https://graph.microsoft.com/v1.0/subscriptions/{GUID}
  - Delete an existing subscription

## Summary

In this unit, you learned how to manage the notification lifecycle with Microsoft Graph. The key aspect to notification lifecycle is to understand how change notification subscriptions work.
