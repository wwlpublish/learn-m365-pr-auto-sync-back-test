## Avoid Polling Microsoft Graph for Changes

One common scenario that custom applications implement is polling Microsoft Graph on scheduled intervals. Typically this strategy is used to keep the application’s local data store in sync with data exposed in Microsoft Graph. However, polling Microsoft Graph for changes usually requires multiple GET requests for numerous data to submit in succession, a scenario that commonly triggers requests to be throttled.

## Microsoft Graph: Delta Query

One way to mitigate throttling when polling Microsoft Graph for large data sets is to use the delta query feature of Microsoft Graph. Delta query, also known as “track changes” allows developers to request only data that has been added, updated, or deleted since the last request. This pattern will allow the application to reduce the amount of data requested by the application that will reduce the cost of the request and therefore likely limit the chances of the requests being throttled.

Delta query works using the concept of a state token. An application will issue an initial request to Microsoft Graph the same way it normally does, except it will include the delta link function in the request.

Microsoft Graph will respond with the requested data as normal, except the last page of data will include an extra property deltaLink. This contains the endpoint with the state token of the delta query.

To request the changes that happened in the resulting data set from the time the previous query was submitted, the application uses the endpoint from the previous request’s deltaLink endpoint. This tells Microsoft Graph to execute the same query, but only return the items that have changed since the first request, as indicated using the state token included in the deltaLink property. The last page of results on this second request will include a new deltaLink property value that can be used for the next request, and so on.

### Delta Query Supported by Many Microsoft Graph Resources

Delta query is supported by most Microsoft Graph resources, including directory roles, drive items, events in the primary calendar view, groups, mail folders and messages in a folder, personal contact folders and contacts in a folder, and users.

## Combine Delta Query with Change Notifications

Delta query, when combined with another feature of Microsoft Graph, can be used to significantly reduce the number of requests to Microsoft Graph. Change notifications are another feature of Microsoft Graph that enables an application to be notified when changes occur to specific data.

### Microsoft Graph Change Notifications

An application can subscribe to be notified when a specific resource changes, such as the users. When a user is added, updated, or deleted, the application is notified something changed in the users endpoint by Microsoft Graph via an HTTP POST. The application can then use delta query to request all changes since the last time it made the request.

Using this strategy, applications can nearly eliminate the need to frequently poll Microsoft Graph and process those changes to keep a local data store in sync, greatly reducing the chances for their requests to be throttled.

### Recommendation: Schedule one Delta Query Requests on a Long Interval

To ensure no changes are missed, it is recommended to schedule at least one long-interval delta query request and not rely entirely on the subscription notifications to request changes from the Microsoft Graph resource. This will return all changed data can be processed by the application in the case a change notification was missed.
