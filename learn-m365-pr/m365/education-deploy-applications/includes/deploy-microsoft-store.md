Any device used in a classroom environment needs applications. Some of these will be free, others will need to be purchased. Managing access to applications, distribution and licensing costs can become overwhelming.  Microsoft Store for Education can simplify the selection, deployment, and licensing of apps on your school's PCs.

Here, you'll learn how to configure and use the Microsoft Store for Education.

## Microsoft Store for Education overview

Microsoft Store for Education gives schools a flexible way to find, acquire, manage, and distribute free and paid apps to Windows 10 devices. You can manage Microsoft Store apps and private line-of-business apps in one inventory, plus assign and reuse licenses as needed. You can choose the best distribution method for your organization: directly assign apps to individuals and teams, publish apps to private pages in Microsoft Store, or connect with management solutions for more options.

> [!NOTE]
> The Microsoft Store for Business and Education is a shared destination. Some of the documents refer to the Microsoft Store for Business, however it is also for Education purposes.

## Prerequisites

### Accounts

Before you sign up for Microsoft Store for Education, you'll need an Azure Active Directory (AD) or Office 365 account for your organization, and you'll need to be the global administrator for your organization. If your organization is already using Azure AD, you can go ahead and sign up for Microsoft Store for Education.

- Admins need Azure AD accounts to sign up for Store for Business and Education, and then to sign in, get apps, distribute apps, and manage app licenses. You can sign up for Azure AD accounts as part of signing up for Store for Business and Education.
- Employees need Azure AD account when they access Store for Business content from Windows devices.
- If you use a management tool to distribute and manage online-licensed apps, all employees will need an Azure AD account
- For offline-licensed apps, Azure AD accounts aren't required for employees.
Admins can add or remove user accounts in the Microsoft 365 admin center, even if you don't have an Office 365 subscription. You can access the Office 365 admin portal directly from the Store for Business and Education.

### Software

Administrators working with Microsoft Store for Education need a browser compatible with Microsoft Store running on a PC or mobile device. Supported browsers include: Internet Explorer 10 or later, current versions of Microsoft Edge, Chrome, or Firefox. JavaScript must be supported and enabled.

Employees and students using apps from Store for and Education need at least Windows 10, version 1511 running on a PC or mobile device.

## Sign up for Store for Education

Signing up is the first step in getting started with Store for Education. You can use an existing Office 365, Dynamics 365 Intune, or Azure account. If those accounts have not yet been created, you can create your own Azure AD or Office 365 account.

### Sign up for Microsoft Store for Education

In order to sign in to Microsoft Store for Education, you must be a global administrator for your organization and have an Azure Active Directory for your organization.

- If you do not have an Azure AD account, you can set one up as you sign into the Microsoft Store for Education. See **Crete an Azure AD account through Store for Education** below. If you already have an Azure AD account, see **Sign in to Store for Education** below.

#### Create an Azure AD account through Store for Education

1. Open a browser and go to [education store](https://www.microsoft.com/education-store) and then select **Sign-up**.
1. On the **Welcome, Let's get to know you screen**, type in the required information and then select **Next**
1. On the **Create your user ID** screen, examine the information that was created from the first screen, and then select **Next**.
1. On the **Prove. You're. Not. A. Robot.** screen, select either the **Text me** or **Call me** buttons, enter a phone number, and then select either **Text me** or **Call me**.
1. Enter your verification code, and then select **Create my account**.
1. On the **Save this info.** screen, make note of your Business store sign-in URL and your user ID.

At this point, you'll have an Azure AD directory created with one user account and that account is the global administrator. You can use this account to sign in to Store for Education.

#### Sign in to Store for Education

1. Open a browser and go to [education store](https://www.microsoft.com/education-store) and then select **Sign-up**.
1. Sign in with your Azure AD account credentials.
1. Read and accept Microsoft Store for Business and Education terms.

### Setting up Store for Education

Once your administrator has signed up into Store for Education, they can assign roles to other employees in your school. The set of roles within Microsoft Store for Education help administrators and employees manage applications and tasks. The following describes the differences between a global and billing administrator.

- **Global Administrator** - IT Pros with this account have full access to Microsoft Store. They can do everything allowed in the Microsoft Store Admin role, plus they can sign up for Microsoft Store.
- **Billing Administrator** - IT Pros with this account have the same permissions as Microsoft Store Purchaser role.

The following lists the global user accounts and permissions.

| Task | Global Administrator | Billing Administrator |
|--------------------------------------------------------|----------------------|-----------------------|
| Sign up for Microsoft Store for Business and Education | X                    |                       |
| Modify company profile settings                        | X                    |                       |
| Purchase apps                                          | X                    | X                     |
| Distribute apps                                        | X                    | X                     |
| Purchase subscription-based software                   | X                    | X                     |

### Billing account roles and permissions

There are several roles for billing account management. This table lists the roles and their permissions.

| Role                        | Buy from  Microsoft Store | Assign  roles | Edit  account | Sign  agreements | View  account |
|-----------------------------|---------------------------|---------------|---------------|------------------|---------------|
| Billing account owner       | X                         | X             | X             | X                | X             |
| Billing account contributor |                           |               | X             | X                | X             |
| Billing account reader      |                           |               |               |                  | X             |
| Signatory                   |                           |               |               | X                | X             |
|                             |                           |               |               |                  |               |

There are two roles for the management of purchases. This table lists the roles and their permissions

| Role            | Buy from  Microsoft Store | Manage all items | Manage items  I buy |
|-----------------|---------------------------|------------------|---------------------|
| Purchaser       | X                         | X                |                     |
| Basic purchaser | X                         |                  | X                   |

### How to assign roles

1. Sign in to Microsoft Store for Education
    > [!NOTE]
    > You need to be a Global Administrator, or have the Billing account owner role to access Permissions.
1. Select **Manage**, and then select **Permissions**.
1. On **Roles**, or **Purchasing roles**, select **Assign roles**.
1. Enter a name, choose the role you want to assign, and select **Save**. If you don't find the name you want, you might need to add people to your Azure AD directory.

For more information, see **Manage user accounts** in the Learn more section.

## Get apps and content

You can browse and search for all products in the Store for Education catalog. There are both free and paid-for applications. Applications are added to the Store for Education so you should check back from time to time. Currently, you can pay for apps with a credit card, and some items can be paid for with an invoice. 

There are two applications types in the Store for Education

- Universal Windows Platform applications
- Universal Windows applications by device: Phone, Surface Hub, IOT devices, and HoloLens

Applications purchased from the Store for Education only work on Windows 10 devices.

Line-of-business (LOB) apps are also supported through Microsoft Store. You can invite IT developers or ISVs to be LOB publishers for your organization. This allows them to submit apps via the developer center that are only available to your organization through Store for Education. These apps can be distributed using the distribution methods discussed in this topic. For more information, see **Working with Line-of-Business applications** in the Learn more section.

## Application licensing model

There are two licensing options in Store for Education; online and offline. The default is online and is similar to the licensing model for Microsoft Store. Online licensed apps require users and devices to connect to Microsoft Store services to acquire an app and its license. Offline licensing is a new licensing option for Windows 10. With offline licenses, organizations can cache apps and their licenses to deploy within their network. ISVs or devs can opt in their apps for offline licensing when they submit them to the developer center.

## Distribute applications

The distribution of applications is done through two channels:

- Microsoft Store for Education
- Using a management tool.

You can use either, or both distribution methods in your organization.

### Distribute with Store for Education

- Email link – After purchasing an app, Admins can send employees a link in an email message. Employees can select the link to install the app.
- Curate private store for all employees – A private store can include content you've purchased from Microsoft Store for Business, and your line-of-business apps that you've submitted to Microsoft Store for Business. Apps in your private store are available to all of your employees. They can browse the private store and install apps when needed.
- To use the options above users must be signed in with an Azure AD account on a Windows 10 device. Licenses are assigned as individuals install apps.

### Using a management tool

For larger organizations that want a greater level of control over how apps are distributed and managed, a management tool provides other distribution options:

- Scoped content distribution – Ability to scope content distribution to specific groups of employees.
- Install apps for employees – Employees are not responsible for installing apps. Management tool installs apps for employees.

Management tools can synchronize content that has been acquired in the Store for Education. If an offline application has been purchased this will also include the app package, license and metadata for the app (like, icons, count, or localized product descriptions). Using the metadata, management tools can enable portals or apps as a destination for employees to acquire apps.

## Distribute apps to your employees from Microsoft Store for Education

Distribute apps to your employees from Microsoft Store for Education. You can assign apps to employees, or let employees install them from your private store.

### Distribute apps using your private store

The private store was created when you signed up for Microsoft Store. Applications in the private store can viewed and downloaded. Your private store is available as a tab in Microsoft Store app, and is usually named for your company or organization. Only apps with online licenses can be added to the private store. You can make an app available in your private store when you acquire the app, or you can do it later from your inventory.

#### To acquire an app and make it visible in your private store

1. Sign in to Microsoft Store for Education.
1. Select an application, choose the license type, and then select **Get the app** to acquire the application for your organization.
1. Microsoft Store adds the app to **Products and services**.
1. Select **Manage, Apps & software** for app distribution options.

#### To make an app in Apps & software available in your private store

1. Sign in to Microsoft Store for Business or Microsoft Store for Education.
1. Select Manage, and then choose Products and services.
1. Select on the application to open the application settings, then select Private store availability.
1. Select Everyone to make application available for all people in your organization.

> [!NOTE]
> If you are working with a new Line-of-Business (LOB) app, you have to wait for the app to be available in Products & services before adding it to your private store. For more information, see **Working with line-of-business apps** in the Learn more section.

#### Private store availability

On the details page for each app, you can directly assign an app to a user, or for apps in your private store, you can set Private store availability.

Private store availability allows you to choose which groups of people can see an app in the private store:

- No one - The app isn't in your private store
- Everyone - The app is available to anyone in your organization
- Specific groups - The app is available to all users in assigned security groups

To assign security groups to an app

1. Sign in to the Microsoft Store for Business or Microsoft Store for Education.
1. Select Manage, and then choose Products & services.
1. Find an app, choose the ellipses, and then choose View license details.
1. Select Private store availability, select Specific groups, and then select Assign groups.
1. Enter a name or email address for the security group you want to use, and then select Add groups.

#### Manage application licenses

For each app in your inventory, you can view and manage license details. This gives you another way to assign apps to people in your organization. It also allows you to reclaim app licenses after they've been assigned to people, or claimed by people in your organization.

To view license details

1. Sign in to Microsoft Store for Education.
1. Select **Manage**, and then choose **Products & services**.
1. Select an app you want to manage.
1. On the app details page, you'll see the names of people in your organization who have installed the app and are using one of the licenses. From here, you can:
    - Assign the app to other people in your organization.
    - Reclaim app licenses.
    - View app details.
    - Add the app to your private store, if it isn't in the private store.

You can assign the app to more people in your organization, or reclaim licenses.

To assign an app to more people

- On the app page, select **Assign users**, type the email address for the person that you're assigning the app to, and select **Assign**.

To reclaim licenses

- On the app page, choose the person you want to reclaim the license from, select the ellipses, and then select **Reclaim licenses**.

Microsoft Store updates the list of assigned licenses.

#### Purchase additional licenses

You can purchase additional licenses for apps in your Inventory.

To purchase additional app licenses

1. Sign in to Microsoft Store for Education.
1. Select **Manage**, and then choose **Apps & software**.
1. From **Apps & software**, select an app.
1. On the app page, select **Buy more** for additional licenses, or select **Assign users** to manage your current licenses.

You'll have a summary of current license availability.

#### Download offline-licensed app

Offline licensing is a new feature in Windows 10 and allows apps to be deployed to devices that aren't connected to the Internet. This means organizations can deploy apps when users or devices don't have connectivity to the Store.

You can download offline-licensed apps from your inventory. You'll need to download these items:

- App metadata
- App package
- App license
- App framework

For more information about online and offline licenses, see **Apps in the Microsoft Store for Business** in the Learn more section.

For more information about downloading offline-licensed apps, see **Download offline apps** in the Learn more section.

#### Manage products programmatically

Microsoft Store for Education provides a set of Admin management APIs. If your organization develops scripts or tools, these APIs allow Admins to programmatically manage items in **Apps & software**. For more information, see **REST API reference for Microsoft Store for Business** in the Learn more section.

You can download a preview PowerShell script that uses REST APIs. The script is available from PowerShell Gallery. You can use to the script to:

- View items in inventory (Apps & software)
- Manage licenses - assigning and removing
- Perform bulk options using .csv files - this automates license management for customers with large numbers of licenses

> [!NOTE]
> The Microsoft Store for Business and Education Admin role is required to manage products and to use the MSStore module. This requires advanced knowledge of PowerShell.
