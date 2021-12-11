So far in this module, we’ve explored how to work with content in SharePoint Framework components and work with data within SharePoint lists. In this lesson, you'll learn about another common scenario: how to use the SharePoint Framework API to add files to SharePoint document libraries.

> [!NOTE]
> A previous version of this exercise demonstrated how to use mock data within your web part when testing the component in the SharePoint local workbench. However, the local workbench was removed in the SharePoint Framework release v1.13. The mock data exercise was retired in favor of the common scenario to upload files to document libraries with the SharePoint Framework.

## Differences from document libraries vs SharePoint lists

In a previous unit in this module, you learned how to read and write to SharePoint lists with the SharePoint Framework using the SharePoint REST API. Working with document libraries is similar to working with lists, but there are some differences.

A SharePoint document library is just like a SharePoint list, except that it displays its contents as files instead of a list of items.

When working with a SharePoint REST API, most of the things you learned in working with lists applies to libraries. For example, use HTTP GET calls to retrieve information and HTTP POST, PUT, MERGE, and DELETE calls to make changes to contents.

One difference from lists is that you need to include the folder where the file is, or in the case of creating a file, will be uploaded to. In addition, you also need to use the `Files` endpoint. Finally, the end of the endpoint instructs the REST API what you're trying to do.

For example, the following URL will upload a file to the *root folder* of the *Documents* library. This file is named *sample.png* and will overwrite an existing file with the same name: `https://contoso.microsoft.com/sites/testSite/_api/web/lists/GetByTitle('Documents')/RootFolder/Files/add(overwrite=true,url='sample.png')`.

Developers have two options for uploading files to SharePoint libraries. One option, as shown above, uses the SharePoint REST API.

## Add files using the SharePoint REST API

Developers can use the SharePoint REST API to upload a file to a SharePoint library using the support included in the SharePoint Framework API. To upload a file using the SharePoint REST API, you need to specify the endpoint where you want to upload the file. For example, let's assume you want to upload a file to *Documents* library's root folder in the **testSite** SharePoint site.

You can use the endpoint listed above to do this, but you need to customize the request that's sent to the REST API to provide the file contents as part of the request. By default, the SharePoint Framework API will set all the common properties needed to make a successful call to the SharePoint REST API using the `SPHttpClient.configurations.v1`. Developers can start with that and then override some of the properties.

To override the properties, create an additional request object to override two parts in the request. Specifically, set the `content-length` header to the string value of the length of content we're sending to the REST API, and set the body of the request to the contents of the file:

```typescript
const fileData = /* */;
const options: ISPHttpClientOptions = {
  headers: { 'CONTENT-LENGTH': fileData.byteLength.toString() },
  body: fileData
};
```

Finally, use the endpoint, the default configuration, and this new request object when calling the SharePoint Framework's SharePoint REST API:

```typescript
const response = await this.context.spHttpClient.post(endpoint, SPHttpClient.configurations.v1, options);

if (response.status === 200) {
  alert('File uploaded successfully');
} else {
  throw new Error(`Error uploading file: ${response.statusText}`);
}
```

## Add files using the Microsoft Graph

Another way to upload files to SharePoint libraries is to use the Microsoft Graph support included in the SharePoint Framework SDK.

To upload a file using the Microsoft Graph, you need to specify the endpoint where to upload the file. For example, assuming you want to upload a file to the same URL as listed above, the Microsoft Graph endpoint would be: `https://graph.microsoft.com/v1/sites/{{SITE_ID}}/drive/root:/sample.png:/content`.

Assuming you've read the file into memory as you would using the SharePoint REST API, to upload the file using the SharePoint Framework API for Microsoft Graph, use the following code:

```typescript
const fileData = /* */;
const endpoint = `sites/{{SITE_ID}}/drive/root:/sample.png:/content`
const graphClient = await this.context.msGraphClientFactory.getClient();
const response = await graphClient.api(endpoint).put(fileData);
```

## Summary

In this unit, you learned how to use the SharePoint Framework API to add files to SharePoint document libraries.
