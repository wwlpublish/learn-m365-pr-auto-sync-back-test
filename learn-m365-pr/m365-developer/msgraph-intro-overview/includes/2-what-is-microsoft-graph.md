Organizations store vast amounts of data and intelligence across Microsoft cloud services, but how accessible is the data to users?

For example, if a salesperson is setting up a meeting with a customer, can they easily access files and previous meetings and notes? Are emails and chats between a salesperson and customer easy to find? What people within the organization can the customer contact for support?

By using Microsoft Graph, you can take advantage of a secured, unified API to connect to data located in various Microsoft 365 services. Gaining access to this data will give users the information that they need to make timely decisions and give the company a competitive advantage. Developers can get started with Microsoft Graph quickly and access data across an organization without having to learn about how individual Microsoft 365 services work.

Data and intelligence like the following types can be accessed through the Microsoft Graph REST APIs and client libraries:

- Users and groups
- Teams data
- Tasks
- Files
- Mail
- Meetings and calendars
- Organizational charts

:::image type="content" source="../media/2-microsoft-graph.png" alt-text="Diagram that shows an overview of the connections in Microsoft Graph.":::

> [!NOTE]
> Microsoft Graph is used to access Microsoft 365 data and isn't related to other graph technologies, such as graph databases or GraphQL.

## Benefits of using Microsoft Graph in your application

To better understand the benefits of Microsoft Graph, let's revisit the customer application scenario. The application needs the following functionality to enable salespeople to work with customers more effectively:

- Get a history of interactions between salespeople and customers
- See messages that a salesperson sent to a customer (Microsoft Teams chat or email)
- Access information about prior meetings and notes
- Identify key people within the organization who can help with customer questions
- Review files related to a customer

:::image type="content" source="../media/2-sales-app-summary.png" alt-text="Diagram of the components of the sales application.":::

If the members of your development team didn't use Microsoft Graph, they would need to learn the Outlook mail API for mail, calendar, and meetings. To access files, they would need to learn the OneDrive and SharePoint APIs. Finally, they would need Active Directory queries to gain access to people in the organization, the organizational chart, and individual skills. That's a few APIs to learn, which is further complicated when you factor in management and maintenance of the application over time.

By using Microsoft Graph, your development team can use a single endpoint and unified API to get all the customer interaction data that the application needs. This data retrieval ranges from accessing customer messages sent by different salespeople to viewing relevant files. Developers can securely access this information by using the Microsoft Graph REST APIs. Client libraries are also available for various languages.

As the salesperson application grows, it can include data from other services:

- Microsoft 365 services: Delve, Excel, Microsoft Bookings, Microsoft Teams, OneDrive, OneNote, Outlook/Exchange, Planner, SharePoint, Workplace Analytics
- Enterprise Mobility + Security services: Advanced Threat Analytics, Advanced Threat Protection, Azure Active Directory, Identity Manager, Intune
- Windows 10 services: activities, devices, notifications
- Dynamics 365 Business Central

Security is a critical part of any organization. Microsoft Graph provides built-in security to control access to services.
