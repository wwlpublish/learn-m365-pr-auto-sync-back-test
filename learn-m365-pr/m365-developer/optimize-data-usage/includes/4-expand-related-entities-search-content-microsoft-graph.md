In this unit, we'll explore how you can use two query parameters to search and include related data in Microsoft Graph requests.

## Microsoft Graph exposes relationships between entities

Many Microsoft Graph resources expose both declared properties of the resource and its relationships with other resources. These relationships are also called reference properties or navigation properties, and they can reference either a single resource or a collection of resources. For example, mail folders, manager, and direct reports of a user are all exposed as relationships.

Normally, you can query either the properties of a resource or one of its relationships in a single request, but not both. You can use the `$expand` query string parameter to include the expanded resource or collection referenced by a single relationship (navigation property) in your results.

## Expanding related entities in queries to limit requests

The `$expand` operator, can be used to expand a collection of items, saving you from issuing additional requests.

```http
https://graph.microsoft.com/v1.0/me/drive/root?$expand=children
```

In this example, you've requested Microsoft Graph to automatically include the children collection from the drive/root endpoint. The response will include all the default properties for the collection of files and folders within the root folder of the user’s OneDrive.

You can further optimize this query by including a `$select` query operator to only include the specific properties from the children collection.

```http
https://graph.microsoft.com/v1.0/me/drive/root?$expand=children($select=id,name)
```

Consider the scenario where you want to get the members of 10 groups. Without using the `$expand` operation, you can retrieve the members with one query for the first 10 groups, then as you enumerate through the results, you would create 10 more requests, one for each group, to get each group's members. The query results in 11 round trips of Microsoft Graph requests. However with the `$expand` operator, these 11 requests can be cut down to a single request.

```http
https://graph.microsoft.com/v1.0/groups?$expand=members
```

## Limit query results by filtering

Another optimization option supported by Microsoft Graph is use of the `$filter` query parameter. Filtering enables developers to limit the size of the response by filtering on specific content. Filtering isn't to be confused with search.

The syntax of the `$filter` query parameter follows the format of passing in an equality function with two parameters. The first parameter is the field to filter while the second parameter is the value to filter on.

```http
https://graph.microsoft.com/v1.0/users?$filter=displayName eq 'Megan Bowen'
```

Most logical operators are supported, such as:

- **equal** (`eq`)
- **not equal** (`ne`)
- **and**
- **or**
- **not**
- **greater than** (`gt`)
- **greater than or equal** (`ge`)
- **less than** (`lt`)
- **less than or equal** (`le`)

The operator `startswith()` is supported by most endpoints in Microsoft Graph, but not all. Refer to the documentation for Microsoft Graph for full details.

```http
https://graph.microsoft.com/v1.0/users?$filter=startswith(displayName,'J')
```

## Find entities with search

Developers can also use the `$search` query parameter to search for content against the people & message endpoints.

```http
https://graph.microsoft.com/v1.0/me/contacts?$search="wilke"
https://graph.microsoft.com/v1.0/me/messages?$search="body:Northwind"
```

Search is limited to returning 250 results.

Search can't be combined with the `$filter` or `$orderby` operators.

When searching against the messages endpoint, if no property is specified, it defaults to searching the **from**, **subject**, and **body** property. You can search on specific fields as well, such as the **cc** property:

```http
https://graph.microsoft.com/v1.0/me/messages?$search="cc:wilke"
```

Like the `$filter` query parameter, the `$search` query parameter can be combined with the `$select` query parameter to limit the data returned.

```http
https://graph.microsoft.com/v1.0/me/messages?$search="cc:wilke"&$select=subject,toRecipients
```
