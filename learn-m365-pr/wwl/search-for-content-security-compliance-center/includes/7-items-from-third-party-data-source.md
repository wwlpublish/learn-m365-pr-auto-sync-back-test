The Content search feature in the Microsoft 365 compliance center enables you to search for items that were imported into mailboxes in Microsoft 365 from a third-party data source. This feature enables you to complete the following tasks:

 -  Create a query to search all imported third-party items.
 -  Create a query to only search specific third-party items.
 -  Create a query-based Preservation Policy.
 -  Create a query-based eDiscovery Hold to preserve third-party data in Microsoft 365.

To search or place a hold on any type of third-party data that you've imported into Microsoft 365, you can use the **kind:externaldata** message property-value pair in the keyword box for a Content search or when creating a query-based hold. For example, you would use the following query to search for items that were imported from any third-party data source that contains the word "contoso" in the Subject property of the imported item:

```
kind:externaldata AND subject:contoso
```

Instead of searching all types of third-party data, you can create queries that only search for a specific type of third-party data. This type of search can be created by using the following message property-value pair in the keyword box for a Content search:

```
itemclass:ipm.externaldata.&lt;third-party data type&gt;*
```

For example, you would use the following query to only search Facebook data that contains the word "contoso" in the Subject property:

```
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

**Additional reading.** For more information, including a table that lists the third-party data types that can be searched, see [Use Content Search to search third-party data that was imported to Office 365.](/microsoft-365/compliance/use-content-search-to-search-third-party-data-that-was-imported)
