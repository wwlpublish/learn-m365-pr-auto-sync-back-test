Data is at the core of most apps, including those apps that are built in Power Apps. Data is stored in a data source, and app creators bring that data into their apps by creating a connection. The connection uses a specific connector to talk to the data source. Connectors act as a bridge from the data source to the app or workflow. This design enables information to be transported back and forth. Connectors are essentially wrappers around the APIs provided by cloud and on-premises services. These connectors enable Power Apps to easily interact with those services.

Power Apps supports over 275 connectors for popular services and on-premises data sources, including SharePoint, SQL Server, Microsoft 365, Salesforce, and Twitter. Power Platform also provides the option to build custom connectors. Custom connectors enable an app to call a publicly available API, or a custom API hosted by a cloud provider. Custom connectors are defined in the context of an environment; that is, they serve as containers to separate apps that may have different roles, security requirements, or target audiences, and they're only available within that environment.

Canvas apps aren't limited to connecting to just one data source. Microsoft Power Platform easily supports multiple data connections, which enable applications to bring data together from many platforms and services.

In the context of Power Apps, connectors access the data in an organization's data sources through tables and actions. For example, some data sources, such as Common Data Service, SharePoint, and SQL Server provide data in a structured table.

Other data sources, such as the Microsoft 365 Users Connection or Project Online, are action-based. For example, with the Microsoft 365 Users Connection an action may be “Update my profile”.

> [!NOTE]
> When using Excel as a data source, the data must be formatted as a table.

**Additional reading.** For more information on connectors and data access, see the [connector index](/connectors/index?azure-portal=true).

### On-premises data sources

Connections to on-premises data sources, such as an on-premises SharePoint service, require the use of an on-premises data gateway. The on-premises data gateway acts as a bridge to provide quick and secure data transfer between on-premises data and Microsoft cloud services, including Power Apps, Power Automate, and Power BI. By using a gateway, organizations can keep databases and other data sources on their on-premises networks, yet securely use that on-premises data in cloud services.

An on-premises data gateway enables multiple users to connect to multiple on-premises data sources. A single installation of an on-premises data gateway can also be used with all supported services.

**Additional reading.** For more information, see the [On-premises data gateway architecture](/data-integration/gateway/service-gateway-onprem-indepth?azure-portal=true) documentation.

### Data source authentication

When an app or workflow creates a connection to a data source, the connector typically requires some form of authentication. The specific connection’s credentials and associated service entitlements determine permissions when apps use the connector. Depending on the type of authentication, some connectors are shared automatically when the app is shared. Other connectors require that the users to which the app is shared must create their own connections. For example, the SQL Server connector allows an organization to use Azure AD Integrated, SQL Server Authentication, and Windows Authentication.

Each type of authentication has different levels of security associated with it. It's important to understand what information and rights authors share with users who run their applications. The following list provides examples of different methods of authentication:

 -  **Azure AD-integrated authentication.** The author of an application can connect and work with the data source using their credentials. When an author publishes their application and the application user logs in, they do so with their credentials. If the data is appropriately secured on a back end, the user can only see what they're authorized to see based on their credentials. This type of security allows authors to change rights for specific application users on the back-end data source after the application has been published. For example, you can grant access, deny access, or refine what a user or set of users can see all on the back-end data source.
 -  **Open-standard authorization (OAuth).** This type of connection is also secure because it requires you to enter your username and password when you connect. Twitter is a good example of an OAuth connection that uses this type of authentication. The author of an application connects and works with the data source with their credentials. When the author publishes their application and the application user logs in, they must also supply their credentials. This type of connection is secure as users must use their own credentials to access the data source service.
 -  **SQL Server authentication.** SQL Server authentication provides limited security because it doesn't rely on end-user authentication. When an author publishes their application, users don't need to supply a unique username and password. Instead, they use the username and password the author supplies when they authored the application. The connection authentication to the data source is implicitly shared with the users. Once the application is published, the connection is also published and available to the users. End users can also create applications using any connection that's shared with them that uses SQL Server authentication. Users can't see the username or password, but the connection will be available to them.
 -  **Widows authentication.** As with SQL Server authentication, Windows authentication provides limited security because it also doesn't rely on end-user authentication. Windows authentication is used when an author needs to connect to a data source that is on-premises, such as an on-premises server that has a SQL Server. The connection must go through a gateway that gives the connector access to all the data on that data source. As a result, any information that can be accessed with the Windows credentials the author supplies are available to the connector. Once the application is published, the connection is also published and available to users. As a result, end users can also create applications using this same connection and access the data on that machine. Connections to the data source are implicitly shared with the users to which the app is shared.

### Common Data Service

The Common Data Service is a type of data source that lets an organization securely store and manage data that's used by business applications. The Common Data Service can also integrate data from multiple sources into a single store. This design provides an easier app building experience and a single set of logic to maintain and operate over the data.

Data within the Common Data Service is stored within a set of entities. An entity is a set of records used to store data, which is similar to how a table stores data within a database. While the Common Data Service includes a base set of standard entities that covers typical scenarios, an author can also create custom entities specific to their organization and populate them with data the author imports from lists in SharePoint, from Excel, or from PowerQuery. App makers can then use Power Apps to build rich applications using this data.

:::image type="content" source="../media/apps-built-on-common-data-service-ba3d719a.png" alt-text="diagram shows how the Power Platform components and Microsoft apps are built on top of the Common Data Service":::


For most organizations, it's a good idea to use the standard entities and attributes as they were intended. But to meet its business needs, an organization can extend the functionality of standard entities by creating one or more custom entities to store information that's unique to the company.

The Common Data Service is so powerful and ideal for Power Apps (and other Microsoft Power Platform products) because it's the underlying data platform. Every environment can have zero or one Common Data Service database. The Common Data Service is a premium connector that's built into Power Apps. As a result, apps can natively connect to its data entities.

Entities within Common Data Service can use rich server-side logic and validation to ensure data quality. Repetitive code can also be reduced in each app that creates and uses data within an entity.‎

 -  **Business rules.** Business rules validate data across multiple fields and entities. They also provide warning and error messages, regardless of the app that's used to create the data.
 -  **Business process flows.** Business process flows guide users to ensure they enter data consistently and follow the same steps every time. Business process flows are currently supported only for model-driven apps.
 -  **Workflows.** Workflows automate business processes without requiring user interaction.
 -  **Business logic with code.** Business logic supports advanced developer scenarios that extend the application directly through code.

Data in Common Data Service is securely stored so that users can see it only if you grant them access. Role-based security allows an organization to control access to entities for different users.

## **Exercise – Interactive demonstration**

Select the following link to complete an interactive demonstration titled: [Create a Power App from a data source](https://edxinteractivepage.blob.core.windows.net/edxpages/MS-100/M4-L3-E6-T2/index.html?azure-portal=true).

This simulation guides you through the steps to create a Power app from a data source for the fictitious company known as Adatum Corporation.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”