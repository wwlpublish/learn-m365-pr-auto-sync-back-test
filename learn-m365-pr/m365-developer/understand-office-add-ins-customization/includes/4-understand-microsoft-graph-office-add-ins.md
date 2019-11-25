Your add-in can connect to Microsoft Graph and access the user's data so they can accomplish more useful and productive scenarios. Example tasks are:

- Read files from OneDrive
- Fetch email attachments
- Get the user's profile

## Why use Microsoft Graph

Microsoft Graph REST APIs provide a way for your add-in to access the user's data in services like:

- Azure Active Directory
- Office 365 services
- Enterprise Mobility and Security services
- Windows 10 services
- Dynamics 365

![Microsoft Graph](../media/microsoft-graph.png)

*Microsoft Graph*

## How to authorize to Microsoft Graph

To connect to and use Microsoft Graph, your add-in needs to:

- Authenticate the user
- Be authorized to act on the user's behalf

### Authentication

The add-in can get an access token from Azure Active Directory (AAD) when the user has signed in. AAD doesn't allow its sign-in page to open in an iframe, and the add-in task pane is an iframe when the add-in is launched in Office on the Web. So, use the Office JavaScript Dialog API to display the AAD login form. If your add-in includes custom functions that need authorization to Microsoft Graph, use the custom functions Dialog API to display the login form.

### Authorization

After the user signs in, your add-in gets an access token to use in subsequent API calls to Microsoft Graph. The access token can never give the add-in more or greater permissions than the user has. Users typically only have permissions to data about themselves, their own files and email, and objects that have been shared with them. If your add-in gets Microsoft Graph data about multiple users, then it can be used successfully only by users with admin-level permissions.

### Recommended libraries

Depending on your development choices, you can use one of the following libraries for authentication and authorization as appropriate.

- Your server-side is on a .NET-based framework (for example, .NET Core or ASP.NET): use MSAL.NET
- Your server-side is node.js-based: use Passport Azure AD
- Your add-in uses Implicit flow: use msal.js
