> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OG3i]

In this unit, you'll learn how you can track changes to entities in a collection over time without writing code to detect which items have changed. This capability is provided as part of the *delta query* feature in Microsoft Graph.

## Tracking changes to entities with Microsoft Graph

Many custom applications have a need to track and replicate changes between two systems. For example, updates to user information in the master Azure AD directory for an organization, such as office addresses, manager, and contact phone numbers need to be recorded in time reporting systems or other back-office platforms. One way developers can monitor a source system for changes is by polling the system to detect changes.

As you learned in a previous unit, an alternative to the polling pattern, developers can leverage change notifications in Microsoft Graph to be notified when entities change. While this addresses one part of the problem, what happens in the case where a change notification subscription expires? In this case, your application may miss changes to entities when the subscription was not active. In addition, what happens if a change notification wasn't fired by Microsoft Graph because of a system error? In these cases, your application would have to temporarily rely on the polling pattern.

There's another option that developers can leverage for certain endpoints in Microsoft Graph that, when combined with change notifications, enables applications to avoid the polling pattern in a robust and fault tolerant way. This is done using the track changes capability, also known as the delta query.

### Introducing delta query / track changes

Delta query is supported on email messages, groups, users, and the events object in Microsoft Graph.

The way it works is that an application submits an HTTP GET request to a particular endpoint, `/users` for example. In the request, the endpoint has the `/delta` function added to the end of the URL.

Microsoft Graph will respond with a list of all the users in the collection just like a normal HTTP GET request. However, it will include a new property, `odata.deltaLink`, in the response. The value of this property is a link that your application should save for future use. At some point in the future, your application can use this delta link URL to submit the same request to the `/users` endpoint, except the response will only include those items that have changed since the first call was submitted.

This second response will include a new delta link that your application should save, replacing the previous delta link. The application can then use this new value to retrieve all changed items since the second request was submitted. Each time you make a new request, the delta link will change, allowing your application to only retrieve those items that have changed since the previous request.

### Submitting a delta query request

Let's look at a sample request. The following request will get a list of all users from Microsoft Graph.

```http
HTTP GET https://graph.microsoft.com/v1.0/users/delta HTTP/1.1
Authorization: bearer eyJ0eXAiOiJKV1QiLCJub25jZSI6IkFRQUJBQUFBQUFDRWZl<snip>
Host: graph.microsoft.com
```

This first time this is submitted, you'll receive a list of all users in the directory. Notice the response includes the `odata.deltaLink` property.

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users",
  "@odata.deltaLink": "https://graph.microsoft.com/v1.0/users/delta?$skiptoken=moXwmvoHW4B2uevGNLf2<snip>",
  "values": [ ..<users>.. ]
}
```

If there are multiple pages of data returned, the delta link will be present in the last page of the results.

## Combine change notifications and track changes for a robust application

Your apps can use change notifications and track changes both together to create a robust, reliable, and performant experience.

Change notifications are going to notify your app when something changes with a collection supported by Microsoft Graph. When Microsoft Graph notifies your application that something changed, instead of your app requesting all the information from Microsoft Graph on the entity that triggered the notification, instead it can use the delta query retrieve all changes that have happened since the last request.

With this pattern, your app could first, create a change notification subscription for changes to the `/users` endpoint in Microsoft Graph. Then, immediately after creating the subscription, the application can request all users from Microsoft Graph as a delta query. After processing all the users in the response, your app would save the delta query link.

In the future, change notifications are used to notify your application that something changed. You can use this as a trigger to resubmit the delta query for all changes that have happened since the first request, or one of the later requests. This way, your application can be assured to not miss any changes that happen even if there's when a subscription expires or there's an unforeseen error in the processing of, or sending, the change notification.

To make the application as fault tolerant as possible, it's recommended to have a scheduled process check for a valid subscription and renew it if the expiration time is coming up soon. It's also recommended to schedule a delta query request to occur on regular intervals to cover the scenario where there was a gap in an active subscription and or where a notification of a change wasn't received for some unknown reason.

## Summary

In this unit, you learned how you can track changes to entities in a collection over time without writing code to detect which items have changed. This capability is provided as part of the *delta query* feature in Microsoft Graph.
