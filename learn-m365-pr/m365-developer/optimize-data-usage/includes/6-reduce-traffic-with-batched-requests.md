In this unit, you'll learn how to optimize applications that have complex or numerous interactions with Microsoft Graph.

## Common scenarios require multiple requests

Many complex scenarios can involve complex interactions with the data exposed via Microsoft Graph. For instance, consider an application needs to display three different types of data from Microsoft Graph. The `$expand` operator may not be sufficient as the data is not directly relatable, or the queries would get too complex.

Another scenario may involve multiple write operations such as:

- preparing for an event by saving resources to a shared OneDrive folder
- creating a shared OneNote notebook for the event
- sending meeting invites out to the participants

Applications can get chatty quickly, and that can also introduce potential throttling issues.

One way to avoid any issues and to introduce an optimization is to group multiple requests into a single request to Microsoft Graph. This support, called batching, instructs Microsoft Graph to execute multiple requests and return the grouped results for each request in a single response. Batching does not reduce the number of requests, but it does reduce the number of HTTP round trips your application requests to Microsoft Graph.

## Microsoft Graph endpoints support batched requests

The requests within a batch are not special requests; they are just like any other request you would submit. Therefore, all endpoints and resources exposed by Microsoft Graph can support batching.

When submitting batch requests, all URLs within the requests should be relative to the root of the version of the Microsoft Graph REST endpoint.

One important point to keep in mind: batching doesn't introduce transactional support to your grouped requests.

Furthermore, a batch that contains five requests, for example, can have three requests succeed and two fail. These mixed results are still considered a “successful” batch request as the request and response are not malformed.

## Submitting batch requests

All batch requests must be submitted as an HTTP POST to the https://graph.microsoft.com/v1.0/ endpoint and include the `$batch` query operator

The requests in a batch are submitted within a JSON collection of requests within the batch request body.

Unless the `dependsOn` property is defined within a request that references the ID of a previous request, the requests aren't guaranteed to be executed in any order. Microsoft Graph determines when they are executed which may be simultaneously.

Each request within the batch request body contains properties that define the request. Include the HTTP method and URL in addition to unique ID number you assign to each request.

You can include optional headers and body properties in the request for specific HTTP POST requests.

## Handling batch responses

A batch request results in a single response that includes a collection of individual results for each request.

Each response object in the response collection has an ID that matches the corresponding request ID in the original request. This way you can check the status of each request once you receive the responses.
