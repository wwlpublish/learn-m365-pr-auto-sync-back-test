In this unit, you'll learn how to use the SharePoint Framework API to retrieve list data from the SharePoint REST API.

## SharePoint REST API

The SharePoint REST API is the primary API for accessing data in a SharePoint site. The API is available to both client-side and server-side solutions. Client-side solutions mean it's available to SharePoint Framework components and server-side solutions are those that run on a server but external to your SharePoint environment, such as an Azure Function or web app.

There are many different SDKs and libraries that developers can use to consume the SharePoint REST API, including the SharePoint client-side object model (CSOM) and the SharePoint Patterns and Practices (PnP) PnPJS library.

The SharePoint REST API enables developers to do CRUD-Q operations on data in SharePoint lists and libraries. CRUD-Q stands for create, read, update, delete, and query operations. The SharePoint REST API implements both the OData v3 and v4 protocol specification, which means you can use an established grammar and parameters to submit your requests that are returned in a predictable format. By default, the SharePoint REST API will expect requests to be submitted, and returned, using the OData v3 format. Developers can change this behavior by overwriting the **odata-version** HTTP request header and setting it to **4** to use the OData v4 format. The SharePoint Framework does this automatically with a default configuration.

### Access the SharePoint REST API

The SharePoint REST API will validate your identity and permissions with each request so you must include authorization details when you submit a request to the SharePoint REST API. Each request is authorized by including an `authorization` HTTP request header that contains an OAuth2 bearer token. This token is provided by Azure AD after a successful authentication and granting the necessary permissions to the app that's accessing the SharePoint REST API. This authorization token is required when you submit a request to the SharePoint REST API from off the SharePoint server.

When you submit a request from a client-side script running on a SharePoint page, the authorization token isn't required. That's because each request from the SharePoint site will include a cookie that was added to your browser session when you logged into the SharePoint site. This cookie is used because the SharePoint REST API is available from the SharePoint site, which is in the same domain as the page that hosts your client-side script is sent from.

HTTP request headers are used not just for authorization, but to control the OData protocol version the SharePoint REST API uses, how much metadata is returned in each request and many other things. For example, when updating or deleting a request, you can include the `if-match` HTTP request header to verify the item you want to update or delete is the same version on the server that your application expects it to be. This header enables developers to ensure they aren't in a "last update wins" scenario.

### OData Query Operators

Here's an example of what an OData request looks like:

```http
https://{{sharepoint-site}}/sites/site/_api/web/lists/getbytitle('Countries')/items?
  $select=Id,Title
  &$filter=Title eq 'United States'
  &$orderby=ID desc
  &$top=1
```

The SharePoint REST API starts with the **_api** endpoint. The rest of the path portion of the URL, **web/lists/getbytitle('Countries')/items** in this example, is used to reference a specific resource. In this example, the items in the **Countries** list in the current SharePoint site are returned.

Notice the parameters prefixed with a `$` in the query string of the URL. These are *OData query operators*. OData query operators are used to control how much data is returned in each query.

The `$select` query operator is used to tell the SharePoint REST API to only return specific fields for the items collection. Without the `$select` operator, a default collection of properties are returned.

The `$filter` query operator is used to include only a subset of items from the list.

The `$orderby` query operator allows developers to specify the field to sort the results on and the direction of the sort operation.

Finally, the `$top` query operator is used to only select a subset of the results in the query.

In this example, the last item in the list that has a title of **United States** is returned in the response and it only includes the **ID** and **Title** properties.

## SharePoint Framework and the SharePoint REST API

The SharePoint Framework includes an API that simplifies submitting request to the SharePoint REST API. The `SPHttpClient` API is available in all SharePoint Framework solutions on the `context` object. The `SPHttpClient` extends the to the `HttpClient` API, which is a wrapper to the Fetch API included in all modern browsers and includes a polyfill for older browsers that don't support the Fetch API.

The `HttpClient` is also included in the SharePoint Framework API. Developers can use it to submit HTTP requests to any REST API.

The `SPHttpClient` API automatically configures the HTTP request with the required HTTP request headers, including setting the SharePoint REST API OData version to v4 and configuring the response to only include minimal metadata for each item returned.

### Get list items with the SharePoint REST API and SharePoint Framework

To submit a request to the SharePoint REST API, use the `spHttpClient` object on the current component's `context` object. You'll use either the `get()` or `post()` method to submit either an HTTP GET or HTTP POST request.

```typescript
private _getListItems(): Promise<ICountryListItem[]> {
  const endpoint: string = this.context.pageContext.web.absoluteUrl
    + `/_api/web/lists/getbytitle('Countries')/items?$select=Id,Title`

  return this.context.spHttpClient.get(
      endpoint,
      SPHttpClient.configurations.v1
    )
    .then(response => {
      return response.json();
    })
    .then(jsonResponse => {
      return jsonResponse.value;
    }) as Promise<ICountryListItem[]>;
}
```

The first parameter of the request is the SharePoint REST API endpoint you want to request. The second parameter is the configuration to use. The configuration is what sets the HTTP request headers previously mentioned. There's an optional third argument you can pass in that enables developers to override the default configuration settings, for example if you want full metadata or no metadata in the response.

The `get()` and `post()` methods return a JavaScript promise that you can examine the HTTP response headers or the status code of the request. If the response body contains JSON, you can call the `json()` method, which also returns a promise containing the parsed body turned as a JSON object.

## Summary

In this unit, you learned how to use the SharePoint Framework API to retrieve list data from the SharePoint REST API.
