> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWKmWP]

## Understand throttling in Microsoft Graph

Microsoft Graph is designed to handle a high volume of requests. If an overwhelming number of requests occurs, throttling helps maintain optimal performance and reliability of the Microsoft Graph service. Throttling limits the number of concurrent calls to a service to prevent overuse of resources.

Throttling limits vary based on the scenario. For example, if you're doing a large volume of writes, its more likely they'll be throttled than if you're only doing reads.

Many developers ask: *“what are the throttling limits per hour or per day”*. This question isn't easy to answer. Microsoft Graph is a proxy service that provides access to multiple Microsoft resources. Each of these services has their own process for calculating when requests should be throttled.

Not all requests are treated equally. A read request isn't as demanding on the services as a write operation. Furthermore, not all read or write operations can be treated equally. A read request for the ID and name of 50 groups isn't the same as including the `$expand` query operator to include the ID, name, email, and phone number for members in the groups.

## What happens when requests are throttled?

What does Microsoft Graph do when it determines that requests by a specific client should be throttled? First, consider what it means when a request is throttled.

When Microsoft Graph throttles a request, the service is telling the requesting client: *“your requests have been determined to be negatively impacting the service that can impact the health, responsiveness, and reliability of the service for others.”*

In throttling requests, Microsoft Graph is telling the requesting client *“don't issue any more requests until a specific time”*. This time frame is commonly just a few seconds, but some services may require a longer delay.

### Any future requests before the time period specified will continue to be throttled

Any requests made before this delay time have elapsed will continue to be throttled by Microsoft Graph. In some cases, it can also cause the delay to be extended.

### Not all requests are throttled when limits are exceeded

While some requests are throttled, other requests by the same client to the same endpoint may be allowed. For instance, a high volume of write requests could trigger Microsoft Graph to throttle future write requests, but read requests would still be allowed.

## Identifying throttled requests

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OO3D]

The first step to understanding throttling is knowing how to identify Microsoft Graph is throttling requests.

In HTTP APIs, the result of a request is indicated by the HTTP status code returned. HTTP status codes are classified in groups.

For example, successful status codes are in the range of 200-299. Common successful status codes include:

- 200: used when requesting a resource or
- 201 and 204: used on write operations for creating, updating, or deleting resources

Error status codes are in the ranges of 400-499 & 500s. Common failed status codes include:

- 400: bad request
- 401 and 403: usually a permission or auth issue
- 404: used for a not found request

Another status code you may receive is 503, service unavailable. Microsoft Graph returns the service unavailable code when the service is unhealthy and isn't related to throttling or traffic from a specific application or request. It is recommended your application handle this response code, but there is no action your application can take to avoid it.

### Throttled requests = HTTP 429

The status code returned for throttled requests is **429**, indicating **too many requests**. All requests that are throttled by Microsoft Graph will return 429 when they're throttled.

Keep in mind, Microsoft Graph is a proxy service to multiple Microsoft services. These include Azure AD for users and groups, Exchange for calendar, contacts and messages, OneDrive, OneNote, SharePoint, Microsoft Teams, and many more services.

Each of these services has their own rules and calculations for when limits are exceeded and future requests will be throttled.

Many, but not all, of these endpoints will also return an additional value in the response’s HTTP headers that the requester can use to determine how long they should wait before submitting another request.

### Inspect the Retry-After HTTP header

The header value, ***Retry-After***, is an integer that represents the number of seconds the client should wait before submitting the request again. Any requests sent before this time will continue to be throttled and may cause the **Retry-After** value to increase as well.

Not all services include the **Retry-After** value so your applications should have a default number to rely on when this HTTP header isn't included.

Some services have hard-coded **Retry-After** values while other services have dynamic numbers that are calculated based on the type of request and the current conditions. So, you shouldn't treat one **Retry-After** as a universal or uniform number across all services and for all future requests.

## Explain common throttling scenarios

Now that we've covered what throttling is, why requests can be throttled, and what it means, let’s look at some common scenarios that can cause requests to be throttled.

Determining if a request will be throttled isn't an exact science. You won't find reliable metrics that can be applied or assumed across all applications, endpoints, and request types. Rather, consider what goes into determining when requests should be throttled.

As a general rule, you can think of it like this: how expensive a request is on a particular endpoint is the determining factor.

What's used to determine how expensive a request is? That's the part that depends on different situations: which endpoint is the request targeting, is the request a read operation or is it writing (creating, updating, or deleting) data, and how complex is the request.

### Example throttling scenarios

Here are a few examples of scenarios that can experience throttled requests:

A large number of requests across multiple endpoints in a tenant or a large number of requests from a specific application across all tenants.

A large number of requests for large data responses. Consider a request that uses the `$expand` query operator. `$expand` tells Microsoft Graph to get additional data and include it in the request. If the request isn't using data limiting query parameters such as `$select`, `$top`, or `$skip` for instance, the service must work harder to retrieve and include larger data sets in the response. The request would be much more expensive than asking for the names, emails, and IDs of users.

A large number of complex requests. Similar to the previous example, consider a request that is forcing Microsoft Graph to not only retrieve additional data (such as the case when the `$expand` query operator is used), but also to do conditional checks on the data, such as using the `$filter` query parameter to limit the data results.

Consider how expensive a request is: the more expensive its and the more of these requests you send, the more likely its these requests will eventually be throttled.
