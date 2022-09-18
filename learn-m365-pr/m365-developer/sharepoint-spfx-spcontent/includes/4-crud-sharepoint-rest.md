In this unit, you'll extend what you learned in a previous unit from just reading SharePoint list data to writing data using the SharePoint REST API. You'll learn how to create, update, and delete data in SharePoint lists and libraries in SharePoint Framework components with the SharePoint REST API.

## Write operations in SharePoint Framework projects with the SharePoint REST API

The operations referred to when reading and writing data is simplified to CRUD operations. CRUD stands for **create, read, update, and delete**. A previous unit covered reading data from SharePoint lists. To request data from SharePoint's REST API, you use the `get()` method on the `SPHttpClient` API from the SharePoint Framework API.

When writing data to SharePoint lists and libraries, you most submit HTTP POST requests. This is done using the `post()` method on the `SPHttpClient` API. The `get()` and `post()` methods have the exact same arguments, although each scenario may require more steps.

For example, when updating or deleting an item in a SharePoint list, you should include the `IF-MATCH` HTTP request header. You should also include the `X-HTTP-METHOD` when updating and deleting SharePoint list items as well. These two request headers are covered in more detail in the sections on updating and deleting items later in this unit.

When creating or updating a SharePoint list item, you must submit the data for the new or updated item. This is done by including a JSON object that represents the new or updated item as a string in the body of the request. This object should also indicate what type of data its using the `@odata.type` property. This is covered in more detail in the sections on creating and updating list items later in this unit.

## Create SharePoint list items with the SharePoint REST API

You must tell the SharePoint REST API the data type of the item submitted in the request payload when you create a new list item. To do this, specify the data type in the `@odata.type` property in the payload of the request.

This is required as SharePoint lists can support multiple content types. Each content type can have unique or shared fields, but each field can have different settings, such as if they're required or not. So, when creating an item, you must tell SharePoint the type of data so SharePoint knows which content type rules to enforce.

You can obtain a list of all the data types supported on a list using the lists `ListItemEntityTypeFullName` property. It will return the data type supported by the list.

Let's look at an example. This TypeScript method requests the data type for the **Countries** list. It does this by requesting the `ListItemEntityTypeFullName` property on the list and returning it back as a string in a JavaScript promise:

```typescript
private async _getItemEntityType(): Promise<string> {
  const endpoint: string = this.context.pageContext.web.absoluteUrl + 
    `/_api/web/lists/getbytitle('Countries')/items?$select=Id,Title`;

  const response = await this.context.spHttpClient.get(
    endpoint,
    SPHttpClient.configurations.v1);

  if (!response.ok) {
    const responseText = await response.text();
    throw new Error(responseText);
  }

  const responseJson = await response.json();

  return responseJson.ListItemEntityTypeFullName;
}
```

Call this method before creating a new list item. The following TypeScript method calls the `_getItemEntityType()` method to first get the data type supported by the list. It then creates a JSON object for the new item, setting the `Title` property of the item and the `@odata.type` property:

```typescript
private async _addListItem(): Promise<SPHttpClientResponse> {
  const itemEntityType = await this._getItemEntityType();

  /* eslint-disable @typescript-eslint/no-explicit-any */
  const request: any = {};
  request.body = JSON.stringify({
    Title: new Date().toUTCString(),
    '@odata.type': itemEntityType
  });
  /* eslint-enable @typescript-eslint/no-explicit-any */

  const endpoint = this.context.pageContext.web.absoluteUrl + 
    `/_api/web/lists/getbytitle('Countries')/items`;

  return this.context.spHttpClient.post(
    endpoint,
    SPHttpClient.configurations.v1,
    request);
}
```

Once the item is created, the object is converted to a JSON string using the `JSON.stringify()` method, which is set to the `body` property of the request. Notice in the `SPHttpClient.post()` method, the third argument passed into the method is the request.

## Update SharePoint list items with the SharePoint REST API

Updating list items with the SharePoint REST API is similar to creating items with a few small differences.

To update an item, you can submit an HTTP PUT or HTTP MERGE operation to the SharePoint REST API. The difference between the two is that PUT will update all properties on the specified item while MERGE will only update those properties included in the body of the request. This means that any properties omitted when submitting an HTTP PUT will be nulled out because no value was submitted.

If this isn't the behavior you want, you can use the HTTP MERGE method, which will ignore any properties not included in the body of the payload.

The challenge with the HTTP MERGE method is that not all networking equipment and libraries support it. To get around this limitation, specify the wanted method in an HTTP POST with the HTTP request header `X-HTTP-METHOD`. Set the `X-HTTP-METHOD` to `MERGE` when you submit an HTTP POST using the `SPHttpClient.post()` method when you want the SharePoint REST API to treat the HTTP POST as an HTTP MERGE.

When you update an item, you need to be sure that you're updating same version of the item that is on the server. In other words, you don't want to update an item that has changed since you previously retrieved it, otherwise you would overwrite another user's changes.

To protect against this scenario, use the `IF-MATCH` HTTP request header and set its value to the **etag** of the current item. The etag is a unique string for the specific version of the item. If the etag matches the etag of the item on the server, the update is applied. If the etags don't match, the SharePoint REST API will return an HTTP error code 419 indicating the expected etag didn't match.

The following TypeScript method demonstrates how to update an item in a SharePoint list. After first obtaining an item from a list, it then modifies the returned object's `Title` property. Next, the two HTTP request headers `IF-MATCH` and `X-HTTP-METHOD` are added as previously discussed.

Finally, the `request` object's `body` property is set with the JSON string version of the object. Notice that unlike creating an item, the endpoint of the request includes the unique endpoint of the item to be updated:

```typescript
private async _updateListItem(): Promise<SPHttpClientResponse> {
  const getEndpoint: string = this.context.pageContext.web.absoluteUrl + 
    `/_api/web/lists/getbytitle('Countries')/items?` +
    `$select=Id,Title&$filter=Title eq 'United States'`;

  const getResponse = await this.context.spHttpClient.get(
    getEndpoint,
    SPHttpClient.configurations.v1);

  if (!getResponse.ok) {
    const responseText = await getResponse.text();
    throw new Error(responseText);
  }

  const responseJson = await getResponse.json();
  const listItem: ICountryListItem = responseJson.value[0];

  listItem.Title = 'USA';
  /* eslint-disable @typescript-eslint/no-explicit-any */
  const request: any = {};
  request.headers = {
    'X-HTTP-Method': 'MERGE',
    'IF-MATCH': (listItem as any)['@odata.etag']
  };
  /* eslint-enable @typescript-eslint/no-explicit-any */
  request.body = JSON.stringify(listItem);

  const postEndpoint: string = this.context.pageContext.web.absoluteUrl + 
    `/_api/web/lists/getbytitle('Countries')/items(${listItem.Id})`;

  return this.context.spHttpClient.post(
    postEndpoint,
    SPHttpClient.configurations.v1,
    request);
}
```

## Delete SharePoint list items with the SharePoint REST API

Deleting list items with the SharePoint REST API is similar to updating items with a few small differences.

The `SPHttpClient` API doesn't include a `delete()` method like the `get()` and `post()` methods. Instead, to submit an HTTP DELETE request, you'll use the `X-HTTP-METHOD` HTTP request header and set it to `DELETE`. Similar to how you update an item, this will tell the SharePoint REST API to treat the HTTP POST as an HTTP DELETE request.

You can also use the `IF-MATCH` HTTP request header to be sure you're deleting same version of the item that is saved in the SharePoint list. The other option is to ignore the version by setting the value of the `IF-MATCH` header to `*`, which you don't care what version is on the server.

The following TypeScript method demonstrates how to delete an item in a SharePoint list. After first obtaining an item from a list, it then modifies the request using the HTTP request headers `IF-MATCH` and `X-HTTP-METHOD` are added as previously discussed.

```typescript
private async _deleteListItem(): Promise<SPHttpClientResponse> {
  const getEndpoint = this.context.pageContext.web.absoluteUrl + 
    `/_api/web/lists/getbytitle('Countries')/items?` +
    `$select=Id,Title&$orderby=ID desc&$top=1`;

  const getResponse = await this.context.spHttpClient.get(
    getEndpoint,
    SPHttpClient.configurations.v1);

  if (!getResponse.ok) {
    const responseText = await getResponse.text();
    throw new Error(responseText);
  }

  const responseJson = await getResponse.json();
  const listItem: ICountryListItem = responseJson.value[0];

  /* eslint-disable @typescript-eslint/no-explicit-any */
  const request: any = {};
  request.headers = {
    'X-HTTP-Method': 'DELETE',
    'IF-MATCH': '*'
  };
  /* eslint-enable @typescript-eslint/no-explicit-any */
  request.body = JSON.stringify(listItem);

  const postEndpoint = this.context.pageContext.web.absoluteUrl + 
    `/_api/web/lists/getbytitle('Countries')/items(${listItem.Id})`;

  return this.context.spHttpClient.post(
    postEndpoint,
    SPHttpClient.configurations.v1,
    request);
}
```

## Summary

In this unit, you extended what you learned in a previous unit from just reading SharePoint list data to writing data using the SharePoint REST API. You learned how to create, update, and delete data in SharePoint lists and libraries in SharePoint Framework components with the SharePoint REST API.
