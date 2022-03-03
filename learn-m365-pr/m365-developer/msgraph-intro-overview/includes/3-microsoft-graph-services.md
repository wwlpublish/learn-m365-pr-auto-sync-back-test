Microsoft Graph services are centered on users and groups.

A user's data is the core of Microsoft 365 cloud services. Think about a salesperson planning to create a calendar event with a customer. The salesperson can schedule the meeting invitation by using the user's protected identity with any device or platform that the salesperson chooses. As the meeting is scheduled, the calendar event will be accessible across all platforms and applications to act upon if needed.

The following image shows the types of information that Microsoft Graph can access for a user.

:::image type="content" source="../media/3-user.png" alt-text="Diagram that shows the types of information that Microsoft Graph can access for a user.":::

Groups are the base environment for a user's collaboration and teamwork in Microsoft 365. Imagine a group of users in a sales team. They can use Microsoft 365 services to collaborate with their colleagues, have conversations, and share files, calendar events, and notes.

Accessing that type of functionality is key to the sales application scenario, because multiple salespeople might have reached out to a customer over time. Having access to group information enables salespeople across the organization to make better decisions.

:::image type="content" source="../media/3-group.png" alt-text="Diagram that shows the types of information that Microsoft Graph can access for groups.":::

Microsoft Graph services support scenarios related to identity, security, productivity, collaboration, workspace intelligence, and more. For example, to access a specific user's profile, the application can use the following Microsoft Graph REST API call:

```http
GET /users/michellec@M365x214355.OnMicrosoft.com
```

That REST API call returns profile information about Michelle that can be displayed in the application.

```json
{
  ...
  "displayName": "Michelle Caruana",
  "givenName": "Michelle",
  "jobTitle": "Development Manager",
  "mail": "michellec@M365x214355.OnMicrosoft.com",
  "mobilePhone": "425-555-0132",
  "officeLocation": null,
  "preferredLanguage": "en-US",
  "surname": "Caruana",
  "userPrincipalName": "michellec@M365x214355.OnMicrosoft.com",
  "id": "4cdd269d-559f-4360-a12a-92525f712d8c"
}
```

The application can get information about Michelle's direct reports by using the following REST API call:

```http
GET /users/michellec@M365x214355.OnMicrosoft.com/directReports
```

This call returns the following data:

```json
{
...
  "value": [
    {
      "displayName": "Pradeep Gupta",
      "givenName": "Pradeep",
      "jobTitle": "Project Manager",
      "mail": "PradeepG@M365x214355.onmicrosoft.com",
      ...
    },
    {
      "displayName": "Jordy Smith",
      "givenName": "Jordy",
      "jobTitle": "Accountant",
      "mail": "Jordy@M365x214355.onmicrosoft.com",
      ...
    },
    {
      "displayName": "Bridgette Johnson",
      "givenName": "Bridgette",
      "jobTitle": "Designer",
      "mail": "BridgetteJ@M365x214355.onmicrosoft.com",
      ...
    }
  ]
}
```

In addition to making direct calls to Microsoft Graph REST APIs, you can use the Microsoft Graph SDK (software development kit) and client libraries to simplify the process of calling an API. The next modules in this learning path give examples of using the SDK.

Many services can be called via Microsoft Graph, as mentioned earlier. Let's look at three specific areas where Microsoft Graph can help you integrate Microsoft 365 data into your apps.

## Identity and access management

Imagine a large sales company with hundreds of employees. Everyone in the company needs to access many apps, devices, and services throughout the day. The company requires a secure identity and access flow in place across the entire organization.

The Microsoft Graph API for Azure Active Directory (Azure AD) helps organizations build a secure identity and access foundation. Developers can use Microsoft Graph to connect to Azure AD identity management services and automate administrative workflows. It can be a time saver for admins if processes like profile maintenance, employment onboarding/termination, or tracking assignments are automated through Microsoft Graph.

## Productivity and collaboration

In the salesperson application scenario, salespeople need solutions to increase their productivity throughout the day.

Developers can enhance the app experience by adding a chatbot that can schedule meetings between colleagues and customers, check calendar availability, and remind salespeople about the to-do list for the day.

You can build a chatbot that consumes the Microsoft Graph Outlook calendar API and to-do API as a productivity solution.

:::image type="content" source="../media/3-bot.png" alt-text="Screenshot showing a chatbot that consumes the Microsoft Graph Outlook calendar API as a productivity solution.":::

The same chatbot idea can be used for collaboration purposes. A sales team can store its files on a SharePoint site and add its tasks to Microsoft Planner in the group. If the team needs to access any file or task, a chatbot can get the required data by using the Microsoft Graph API for SharePoint and Planner.

Microsoft Graph collaboration APIs can be used for automation as well. For example, every time a new salesperson is hired, a new salesperson's profile can be generated in Azure AD. The new salesperson can then be added to the related team in Microsoft Teams. The following scenarios can be automated through the Microsoft Graph Teams APIs.

:::image type="content" source="../media/3-bot-flow.png" alt-text="Diagram that shows Microsoft Graph automation scenarios in the workflow process.":::

## People and workspace intelligence

Microsoft Graph services for people and workplace intelligence can help you access many insights about users and groups in Microsoft 365. For instance, a salesperson participates in meetings, reads emails, and collaborates with colleagues and customers through different channels in an ordinary workday. Hundreds of documents can be shared during collaboration, and a salesperson needs to quickly locate the files to make effective decisions.

By using the Microsoft Graph API for insights, you can get trending, shared, and frequently used files across the organization. This API improves productivity and makes relevant content much more accessible to users.

:::image type="content" source="../media/3-shared-documents.png" alt-text="Diagram that shows trending documents around a user.":::
