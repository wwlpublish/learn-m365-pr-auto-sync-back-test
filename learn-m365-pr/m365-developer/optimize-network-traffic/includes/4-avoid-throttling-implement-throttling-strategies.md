> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OIAy]

## Options for addressing throttling

If an application relies on external services that implement some request throttling or rate-limiting, the developers of the application should incorporate it into the application design.

There are two approaches to consider when building an application that relies on Microsoft Graph to address throttling scenarios.

### Consider how to avoid requests from being throttled

First, consider avoiding scenarios where requests could be throttled. Avoiding the issue completely is the best approach.

### Consider how to address when requests are throttled

The application should also assume that while developers try to avoid throttling situations, it still may happen. As such, the application should address what happens in those cases.

The application should always assume the request will be throttled and developers should do what they can avoid them from hitting the throttling limits.

One way to think of throttling is like exceptions, or errors in your code. Developers always strive to avoid errors in their code, but they happen… there’s a reason why “try-catch-finally” constructs exist. While you should strive to avoid them, you should also incorporate logic in your code that accounts for when they happen.

## Avoid Common Throttling Scenarios

Let’s look at the first approach to addressing throttling issues: avoiding situations where requests are throttled.

### Avoid requests from being throttled

The best approach is to try to avoid any scenario where your application’s requests to Microsoft Graph will be throttled. To avoid throttling scenarios, you need to understand what causes requests to be throttled. This was covered in more detail in the previous section.

Fundamentally, requests are throttled when they put too much of a demand on the target service. This happens when a high volume of requests is received over a short amount of time. However, there's no set number on how many requests can be submitted over this time. The reason is because not all requests are equal. A write operation is more expensive than a read operation. However, a complex read operation that includes many child collections using the `$expand` query parameter or complex `$filter` query parameters may be much more expensive than a write operation.

### Strategies for avoiding requests from being throttled

There are two strategies you can implement in your applications to avoid requests from being throttled.

First, limit the number of requests to Microsoft Graph over a short time period.

Another option is to limit the number of operations per request. A query that includes multiple `$expand` and `$filter` query parameters is much more expensive than a simple read operation that limits the data set using the `$select` query parameter.

Keep in mind these aren't perfect strategies where you can ensure your applications are never throttled. Your application could experience a burst in traffic and usage that makes it impossible to completely avoid some requests from being throttled.

It's a good practice to collect detailed telemetry from your application for all instances of throttled requests. You should log enough detail to let you identify in what cases throttling occurred so you can use that information to change the calling patterns to avoid or reduce such instances in the future. You'll then be able to optimize and adjust your application to operate within the service limits applicable to your scenarios.

## Implement throttling strategies

Avoiding scenarios where your application’s requests to Microsoft Graph will be subjected to throttling is a good first approach. But your application should incorporate logic for situations when requests are throttled.

### Understand how to identify when requests are throttled

The first step is to identify when requests are throttled. Identifying throttling instances can easily be done by inspecting the HTTP status code in the response. The status code 429 indicates too many requests and is how Microsoft Graph tells the client their requests are being throttled.

## HTTP header Retry-After

Many responses include an HTTP header `Retry-After` that specifies the number of seconds the client should wait before submitting another request. This includes repeating the same request, or more requests.

Consider that not all endpoints in Microsoft Graph include the `Retry-After` header value. Your application should have a default delay number it uses. Also consider implementing an exponential back-off strategy for later requests.

Consider the situation where a response of 429 comes back with no `Retry-After` header and you delay for two seconds. If your requests continue to be throttled, maybe the two-second delay isn’t long enough. If a replayed request continues to be throttled, consider doubling the next request, and so on, to improve the chances of a future request succeeding. The application should also have an upper limit of how long an exponential delay could be and if exceeded, it should trigger an exception.
