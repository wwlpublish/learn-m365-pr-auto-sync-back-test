In this unit, you'll learn how to call anonymous third-party REST APIs using the SharePoint Framework API.

## Consume REST APIs in SharePoint Framework projects

A common requirement for SharePoint Framework projects is that they display or interact with data external to the web part. This data can reside in SharePoint lists and libraries, or it may be accessible via Microsoft Graph. Maybe the data is external to SharePoint and Microsoft 365 and your project will need to request data from a third-party REST API that may support anonymous requests or only support authorized requests because it's protected with Azure AD.

The SharePoint Framework includes multiple APIs you can use that address the different scenarios depending where the data is and the specifics around the HTTP API you'll need to call. There are three different APIs you'll use for specific scenarios.

The `HttpClient` API is the cornerstone for most HTTP requests in SharePoint Framework projects. You'll use the `HttpClient` API to primarily submit anonymous requests to third-party APIs. The `SPHttpClient` API extends the `HttpClient` to include necessary HTTP request headers used by the SharePoint REST API. For example, the `SPHttpClient` automatically includes an `odata-version` HTTP request header set to `4` to configure the SharePoint REST API from the default OData v3 protocol to OData v4.

The `MSGraphClient` API is used to call the Microsoft Graph REST API in the same tenant as the current SharePoint Online tenant. Unlike the other HTTP APIs in the SharePointFramework, the `MSGraphClient` API is used to obtain a configured instance of the Microsoft Graph JavaScript SDK client.

The `AADHttpClient` API extends the `HttpClient` API that is used to call Azure AD secured APIs. You'll use the Azure AD HTTP client API to obtain an instance of the `HttpClient` that includes an `authorization` HTTP request header with the value set to an access token used to authorize calls to an Azure AD secured HTTP endpoint.

None of these related HTTP request APIs require developers to install more clients or libraries; the default SharePoint Framework project includes everything you'll need in your project to submit requests to REST APIs.

## Call third-party APIs with the `HttpClient` API

The `HttpClient` API is available from the SharePoint Framework component's `context` object. You'll primarily use this API to submit HTTP request to anonymous REST APIs, but you aren't limited to anonymous APIs or REST APIs. The client is optimized for REST APIs, but it can be used to submit HTTP requests to other types of endpoints. You have full control to override any parts of the request before sending it, including adding or modifying HTTP request header values.

Most modern browsers implement the Fetch API, which provides an interface for fetching resources across a network. The `HttpClient` API wraps the Fetch API and automatically includes the polyfill **whatwg-fetch** for older browsers that don't implement the Fetch API, such as Internet Explorer 11.

Previously we said you'd primarily use the `HttpClient` API for calling anonymous APIs. You aren't limited to anonymous APIs. The SharePoint Framework includes APIs that are based off the `HttpClient` for calling Microsoft-secured APIs, such as the SharePoint REST API, Microsoft Graph and other APIs secured with Azure AD. You can use the `HttpClient` if you need to call an API secured with another solution, but you'll need to implement any authorization specifications in your project.

### Call anonymous REST APIs

To use the `HttpClient` API, first import it into your TypeScript file:

```typescript
import {
  HttpClient,
  HttpClientResponse
} from '@microsoft/sp-http';
```

In the code above, we're also importing the `HttpClientResponse` object to cast the object returned from an HTTP request into a typed object.

Next, submit a request using either the `get()` or `post()` method on the `this.context.httpClient` object from a SharePoint Framework component. These two methods have three arguments:

- **endpoint** (*required*): The first argument is the endpoint of the HTTP request you want to call.
- **configuration** (*required*): The second argument is the configuration to use for the request. Always use the `HttpClient.configurations.v1` configuration. This will set the HTTP request headers to the common values such as setting the `accept` header to `application/json` to request the data as JSON.
- **request options** (*optional*): The last argument is optional. It enables developers to pass in a custom request object that overrides any of the configuration settings before submitting the request.

The `get()` and `post()` methods return a JavaScript promise with the response as a `HttpClientResponse` object. To parse the body of the response as a JSON object, call the `json()` method that will return a JavaScript promise object containing the response:

```typescript
return this.context.httpClient.get(
  `http://[rest-endpoint]`,
  HttpClient.configurations.v1
)
.then((response: HttpClientResponse) => {
  return response.json();
})
.then(jsonResponse => {
  return jsonResponse;
}) as Promise<any>;
```

## Summary

In this unit, you learned how to call anonymous third-party REST APIs using the SharePoint Framework API.
