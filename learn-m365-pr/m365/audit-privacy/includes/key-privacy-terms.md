Let's start by reviewing some key privacy terms.

**Data controller:** A legal person, public authority, agency, or other body which, alone or jointly with others, determines the purposes and means of the processing of personal data.

The customer is the data controller for their use of Microsoft online services and professional services. Microsoft is the data processor (except in those cases where the customer is the data processor, in which case Microsoft is the subprocessor). Microsoft is an independent data controller for data used to provide a limited set of legitimate business operations (LBOs) needed to support the use of Microsoft online services and professional services.

**Personal data and data subject:** Any information relating to an identified or identifiable natural person (data subject). An identifiable natural person is one who can be identified, directly or indirectly. There are two types of data subjects in enterprise services: end users within a tenant and users that are external to a tenant.

**Data processor:** A natural or legal person, public authority, agency, or other body, which processes personal data on behalf of the controller. In enterprise services, Microsoft acts as a data processor, which processes data in accordance with a customer's documented instructions to provide the online services or professional services. Microsoft will only process data based on your documented instructions. The volume licensing agreement, including the Data Protection Terms, and the way in which a customer configures and uses the service form a customer's documented instructions.

The diagram below describes the relationship between data controllers, data processors, data subjects, and personal data in more detail. In the following examples, C1 is a direct customer of an enterprise service, and C2 is a customer of C1.
:::image type="content" source="../media/relationship-diagram.png" alt-text="Data processor is microsoft when delivering online and professional services. Data controller is C1 admin (license holder). An example would be Contoso tenant admin. Both C1 user and C2 user can be data subject. An example of C1 user is contoso employee, and an example of C2 user would be contoso external users." border="false":::

There are two types of C1 roles and one type of C2 role:

- A C1 admin, who is a license holder - typically the tenant administrator who has signed up for a Microsoft service subscription. C1 administrators are considered data controllers because they sign up for the services on behalf of their enterprises. They configure the tenant's settings and policies in the services, decide who gets a license in the Microsoft service, and assign a license to that user.
- A C1 user is a licensed user to whom the tenant administrator has assigned a license. Typically, C1 users are employees of an enterprise, who we often refer to as the enterprise end users. C1 users are considered data subjects.
- C2 users are the customers of C1. C2 users are external to an enterprise. For example, when a C1 user invites an external business partner to Contoso's SharePoint site, this business partner is a C2 user. C2 users are also considered data subjects.

## Categories of data processed by Microsoft

Data that is used throughout the lifecycle of a customer account to provide Microsoft online services or professional services falls within one of four separate and distinct data categories:

- **Customer data** is all data, including text, sound, video or image files, and software that the customer provides to Microsoft or that is provided on a customer's behalf through use of Microsoft enterprise online services, excluding Microsoft professional services. It includes customer content, which is the data a customer uploads for storage or processing and apps a customer uploads for distribution through a Microsoft enterprise service.

    For example, customer content includes Exchange Online email and attachments, Power BI reports, SharePoint Online site content, or instant messaging conversations.

- **Service-generated data** includes all data "generated" or "derived" by Microsoft through the operation of an online service. Microsoft aggregates this data from our online services and uses it to make sure performance, security, scaling, and other services that impact the customer experience are operating at the levels our customers require.

    For example, to understand how to ramp up datacenter capacity as a customer's use of Microsoft Teams increases, we process log data of their Teams usage. We then review the logs for peak times and decide which data centers to add to meet this capacity.

- **Diagnostic data** includes all data "collected" or "obtained" from software that is installed locally for use in connection with the Microsoft enterprise online service. It is used to help Microsoft ensure the client software is secure and performing properly.

    For example, Microsoft collects information about how long it takes to launch an app, whether an add-in has crashed, and how many times a sign-in has been attempted. Diagnostic data can also be referred to as telemetry data. It does not include names, email addresses, or file content.

- **Professional services data** means all data provided to Microsoft, or processed by Microsoft, upon authorization and through an engagement with Microsoft to obtain professional services. Professional services data includes support data that is provided to Microsoft during technical support for an online service.

    For example, professional services data includes text, sound, video, image files, or software provided to Microsoft during troubleshooting.

When a customer uses Microsoft online services, three of the above four data categories are processed - customer data, service-generated data, and diagnostic data. When a customer uses professional services, we only process professional services data and any other data that a customer authorizes us to access in order to perform the service requested. Data from each of these four data categories is also used to perform a limited set of legitimate business operations (LBOs) needed to support our ability to provide the Microsoft online services and professional services. We limit our use of personal data for LBOs by using only pseudonymized data originating from diagnostic data and aggregate personal data prior to using it for LBOs such that it is no longer linkable back to users.

Microsoft acts as an independent data controller in our use of data to perform LBOs. The use is limited to the following functions:

- billing and account management
- compensation (for example, calculating employee commissions)
- internal reporting and modeling (for example, forecasting, revenue, capacity planning, product strategy)
- combatting fraud, cybercrime, or cyber-attacks that may affect Microsoft or Microsoft Products
- improving the core functionality of accessibility, privacy, or energy efficiency
- financial reporting or compliance with legal obligations

## Learn more

- [How Microsoft categorizes data for online services](https://www.microsoft.com/trust-center/privacy/customer-data-definitions?azure-portal=true)
