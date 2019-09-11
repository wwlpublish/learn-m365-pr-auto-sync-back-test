In this unit, let's look at the endpoint characteristics of Microsoft Graph and how you can use query parameters to manipulate requests.

## Accessing the Microsoft Graph

Developers can create all sorts of applications that will communicate with the Microsoft Graph. To support as many developers and platforms as possible, the Microsoft Graph has two options for developers to choose from when integrating the Microsoft Graph into their applications.

### Microsoft Graph REST API

At its core, the Microsoft Graph is a REST API which means that developers can use any platform, any framework, and any programming language they're most comfortable with. The only requirement is that they issue common HTTP requests and process HTTP responses. All recent platforms, frameworks and languages have these capabilities.

### Microsoft Graph Native SDKs

The Microsoft Graph also provides multiple native SDKs for developers who want to use a rich programming model within their applications. These SDKs are available for multiple platforms and simplify the process of interacting with the Microsoft Graph’s REST API. They abstract away the tasks of constructing, submitting, and processing the REST requests and responses with the Microsoft Graph REST API.

You'll find an existing SDK for the platform and language you are working on as all the popular platforms covered, including .NET, iOS, Android, Java, PhP, Ruby, JavaScript, and many more.

## Authentication Options

The Microsoft Graph supports two styles of authentication. One option supports users to authenticate using either an Azure AD account, also known as a Work & School account, or a Microsoft Account. The former account is typically used to access content and resources within Office 365 and Microsoft 365. The latter account type, a Microsoft Account, is used to access consumer resources such as OneDrive Consumer, Outlook.com, and other related services.

## Microsoft Account + Azure AD

What’s nice about the Microsoft Graph supporting both styles of authentication, is that the same API and endpoints can be used to create applications that will expose business data in Microsoft 365 or consumer data within Microsoft’s consumer services. Native support for different authentication options makes it easy for developers to learn a single API and can configure their application to support both business and consumer data that is driven strictly by the user and what type of account they sign in with.

## Manipulating Microsoft Graph Requests with Query Parameters

Microsoft Graph’s REST API confirms to the OData v4 protocol. One aspect of this is that the REST API supports many query parameters. These query parameters enable developers to specify & control the amount of data returned in the responses.

Each endpoint exposed by the Microsoft Graph has varying support for different query parameters. For example, the `$count` query parameter is supported by the /contacts endpoint, but it isn’t supported for directory objects like users and groups.

Query parameters are added to the query string portion of a URL and have a `$` prefix. Each parameter has a different syntax for usage. For example, the `$count` query parameter, when set to TRUE, will tell the Microsoft Graph to only report the number of items in the collection instead of returning all the data in the collection. This `$count` parameter dramatically reduces the amount of data returned by the service, reducing the work on Microsoft Graph and bandwidth consumed by your application.

## Control the Amount of Information Returned in Queries

One of the most powerful uses of query parameters is to control how much data is returned in the response to a request.

### Limit the Number of Returned Results

The `$top` parameter enables you to limit the response to only include a specific number of records.

### Skip Results

The `$skip` parameter enables you to skip the first # of results in the response.

### Requesting Paged Results

You can combine the `$top` and `$skip` parameters to implement paging solutions. For example, consider the scenario where you want to display five items at a time. Page one would only include `$top=5` while page two would include `$top=5&$skip=5` to skip the first five results that were shown on page one, but get the next five records to display.

### Limiting Data Fields in Results

Microsoft Graph responses will include a set of default properties when no result set is defined. Including default properties means if you only want the display name & email address of numerous users, you will actually receive a lot more data that isn’t going to be used. To optimize the request and speed up the response, you can use the `$select` parameter to specify a comma-delimited list of properties you want to receive in the response.

## Manipulating the Order and Format of Data Returned

Another powerful uses of query parameters are to control how the data is returned in the response to a request.

The `$orderby` parameter enables developers to let data from Microsoft Graph be pre-sorted. By default data is returned in ascending order, but you can add the `desc` keyword after the property to sort in descending order. It also supports sorting by multiple fields, separating each field with a comma.

Complex fields can also be sorted. Complex types, such as the from field in an email message is a complex type of an email address that contains a name & address property. To sort by name, use `from/emailAddress/name`.

By default, responses from Microsoft Graph are returned in the JSON format. However, you can request data in two other formats, ATOM & XML, by adding the `$format` parameter.
