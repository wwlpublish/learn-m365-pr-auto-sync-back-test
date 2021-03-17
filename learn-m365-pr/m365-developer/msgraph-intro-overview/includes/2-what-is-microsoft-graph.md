Organizations store vast amounts of data and intelligence across different Microsoft cloud services but how accessible is the data to users? For example, if a salesperson is setting up a meeting with a customer, can they easily access files and previous meetings and notes? Are emails and chats between a salesperson and customer easily accessible? What people within the organization can they contact for support? 

By using Microsoft Graph, you can take advantage of a secured, unified API that can be used to connect to data located in various Microsoft 365 services. Gaining access to this data will give users the information they need to make timely decisions and provide the company with a competitive advantage. Developers can get started with Microsoft Graph quickly and access data across an organization without having to learn about how individual Microsoft 365 services work. 

Data and intelligence can be accessed using Microsoft Graph’s REST APIs and client libraries. A few types of data and information that can be accessed include: 

- Users and groups 
- Teams data 
- Tasks 
- Files
- Mail
- Meetings and calendars 
- Org charts 
- More...

:::image type="content" source="../media/2-microsoft-graph.png" alt-text="Microsoft Graph overview":::

It's important to mention that Microsoft Graph is used to access Microsoft 365 data and isn't related to other graph technologies such as graph DB or GraphQL. 
 

## Benefits of using Microsoft Graph in your application  

To better understand the benefits of Microsoft Graph, let’s revisit the customer application scenario mentioned earlier. As a quick review, the application needs the following functionality to enable salespeople to work with customers more effectively: 

- Provide a history of interactions between salespeople and customers
- See prior messages sent to the customer by a salesperson (Teams chat or email)
- Access information about prior meetings and notes
- Identity key people within the organization that can help with customer questions
- Review files related to a customer 

:::image type="content" source="../media/2-sales-app-summary.png" alt-text="Sales application summary":::

If your development team didn’t use Microsoft Graph, they would need to learn the Outlook mail API for mail, calendar, and meetings. To access chat, they would need to learn the Microsoft Teams APIs and for files they would need to learn the OneDrive and SharePoint APIs. Finally, Active Directory queries would be needed to gain access to people in the organization, the org chart, and individual skills. That is many APIs to learn which is further complicated when you factor in management and maintenance of the application over time. 

By using Microsoft Graph, your development team can use a single endpoint and unified API to retrieve all the customer interaction data needed by the application. This ranges from accessing customer messages sent by different salespeople to viewing relevant files. Developers can securely access this information using Microsoft Graph’s REST APIs. Client libraries are also available for a variety of languages.  

As the salesperson application grows, data from other services can be accessed as well: 

- Microsoft 365 services: Delve, Excel, Microsoft Bookings, Microsoft Teams, OneDrive, OneNote, Outlook/Exchange, Planner, SharePoint, Workplace Analytics
- Enterprise Mobility and Security services: Advanced Threat Analytics, Advanced Threat Protection, Azure Active Directory, Identity Manager, and Intune
- Windows 10 services: activities, devices, notifications
- Dynamics 365 Business Central

Security is a critical part of any organization and Microsoft Graph provides built-in security to control access to various services.
 