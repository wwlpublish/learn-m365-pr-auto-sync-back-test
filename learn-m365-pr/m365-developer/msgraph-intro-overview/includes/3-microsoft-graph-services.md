Microsoft Graph services are centered around users and groups.  

A user’s data is the core of Microsoft 365 cloud services. Think about a salesperson planning to create a calendar event with a customer. Any device or platform the salesperson chooses to use, the meeting invite can be scheduled using the user’s protected identity. As the meeting invite is scheduled, the calendar event will be accessible across all platforms and applications to act upon if needed. The following image shows the types of information that Microsoft Graph can access for a user.

:::image type="content" source="../media/3-user.png" alt-text="Diagram showing the types of information that Microsoft Graph can access for a user.":::

Groups are the base environment for user’s collaboration and teamwork in Microsoft 365. Imagine a group of users in a sales team. They can use Microsoft 365 services to collaborate with their colleagues, have conversations, share files, calendar events, and notes. 

Accessing that type of functionality is key to the sales application scenario as multiple salespeople may have reached out to a customer over time. Having access to a group information enables salespeople across the organization to make better decisions.

:::image type="content" source="../media/3-group.png" alt-text="Diagram showing the types of information that Microsoft Graph can access for groups.":::

Graph services support scenarios related to identity, security, productivity, collaboration, workspace intelligence, and more. 

For example, to access a specific user’s profile based on their alias, you can consume the Graph REST API below: 

```http
GET /users/michellec
```

Graph REST API call above will return profile information about Michelle that can be displayed in the application.

```json
{ 
  ...   
    "displayName": "Michelle Caruana", 
    "givenName": "Michelle", 
    "jobTitle": "Development Manager", 
    "mail": "michellec@M365x214355.OnMicrosoft.com", 
    "mobilePhone": "425-882-1032", 
    "officeLocation": null, 
    "preferredLanguage": "en-US", 
    "surname": "Caruana", 
    "userPrincipalName": "michellec@M365x214355.OnMicrosoft.com"", 
    "id": "4cdd269d-559f-4360-a12a-92525f712d8c" 

} 
```

Information about Michelle’s direct reports can be retrieved using the API call shown below:

```http
GET /users/michellec/directReports
```

This call will return data as shown below:

```json
{ 

... 
    "value": [ 
        { 
        "displayName": "Pradeep Gupta", 
        "givenName": "Pradeep",         
        "jobTitle": "Project Manager",        
        "mail": PradeepG@M365x214355.onmicrosoft.com, 
         ...         
        }, 
        { 
        "displayName": "Jordy Smith",
        "givenName": "Jordy",         
        "jobTitle": "Accountant",        
        "mail": Jordy@M365x214355.onmicrosoft.com, 
        ... 
        }, 
        { 
        "displayName": "Bridgette Johnson", 
        "givenName": "Bridgette", 
        "jobTitle": "Designer", 
        "mail": PradeepG@M365x214355.onmicrosoft.com, 
        ... 
        }     
    ] 
} 
```

In addition to making direct calls to Microsoft Graph REST APIs, you can also use the Microsoft Graph SDK (Software Developer Kit) client libraries to simplify the process of calling an API. Next modules in this Learn path provide examples of using the SDK. 

There are many different services that can be called using Microsoft Graph as mentioned earlier. Let’s look at three specific areas where Microsoft Graph can help you integrate Microsoft 365 data into your apps. 

## Identity and Access Management

Imagine a large sales company with hundreds of employees. Everyone in the company needs to access many apps, devices, and services throughout the day. So that, the company requires a secure identity and access flow in place across the entire organization.  

Microsoft Graph API for Azure AD (Azure Active Directory) help organizations build a secure identity and access foundation. Developers can use Microsoft Graph to connect to Azure AD identity management services and automate administrative workflows. It can be a time saver for admins if processes like profile maintenance, employment onboarding/termination, or tracking assignments are automated using Microsoft Graph. 

## Productivity and Collaboration 
 
In the salesperson application scenario mentioned earlier, a salesperson needs solutions to increase their productivity throughout the day. 

Developers can enhance the app experience by adding a chatbot that can schedule meetings between colleagues and customers, check calendar availability, and remind salespeople about the to-do list for the day. 

You can build a chatbot that consumes the Microsoft Graph Outlook calendar API and To-Do API as a productivity solution.  

:::image type="content" source="../media/3-bot.png" alt-text="Screenshot showing a chatbot that consumes Microsoft Graph Outlook calendar API as a productivity solution.":::

The same chatbot idea can be used for collaboration purposes as well. A sales team can store their files on a SharePoint site and add their tasks to Microsoft Planner in the group. If they need to access any file or task, a chatbot can get the required data using Microsoft Graph API for SharePoint and Planner. 

Microsoft Graph collaboration APIs can be used for automation as well. For example, every time a new salesperson gets hired, new salesperson's profile can be generated in Azure AD and the new salesperson can be added to the related team in Microsoft Teams. The following scenario can be automated using the Microsoft Graph Teams APIs. 

:::image type="content" source="../media/3-bot-flow.png" alt-text="Diagram showing Microsoft Graph for automation scenarios work flow process.":::

## People and Workspace Intelligence 

Microsoft Graph people and workplace intelligence services can help you access many insights about users and groups in Microsoft 365. For instance, a salesperson participates in meetings, reads e-mails, collaborates with colleagues and customers through different channels in an ordinary workday. Hundreds of documents may be shared while collaborating and a salesperson needs to quickly locate the files to make effective decisions. By using the Microsoft Graph API for Insights, you can get trending, shared, and frequently used files across the organization. It improves productivity and makes relevant content much more accessible to users. 

:::image type="content" source="../media/3-shared-documents.png" alt-text="Diagram showing the trending documents around the user.":::

