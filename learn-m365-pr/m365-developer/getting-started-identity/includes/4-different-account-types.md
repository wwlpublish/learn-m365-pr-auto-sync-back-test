This unit will cover the different account types that are used within the Microsoft identity platform. You'll also learn about the differences and relationships between applications and service principals.

Developers that use the Microsoft identity platform within custom apps begin with registering an application in Azure AD. It doesn’t matter if the app runs on a mobile device or in the cloud. If it runs in the cloud, it doesn't matter which cloud provider hosts it. The app can even be a PowerShell script. The Azure AD application is the control point for how you access the identity and the information it protects.

You as the developer have many choices to make and the choices you make are driven by the requirements for your application. Developers have to decide:

- how will customers get the app
- should the app do work on behalf of a user, or as the app itself
- what resources are required by the app, and when are they needed
- when should the app ask the user for permissions to a resource

The first decision is: are you going to trust the Microsoft identity platform? Once you have made the decision to trust the Microsoft identity platform, the next step is to register an application with Azure AD. A key part of creating an Azure AD application is what are the permissions the app requires.

Another key decision you'll make when registering the app is what type of accounts will it support? The Microsoft identity platform supports the following types of accounts:

- single organization
- multiple organizations
- personal Microsoft accounts

## Single Tenant Apps

If you're writing a Line of Business (LOB) application, you can sign in users in your own organization. Applications that sign in users only from the app’s home tenant are called single tenant applications.​

​Administrators decide who can register applications in the tenant. These could be every user, only administrators, or users with the Application administrator, Cloud application administrator, or application developer Azure AD administrative roles.  Only users within your organization can sign in and use the application; no one outside the organization can use this application.​

## Multi-Tenant Apps

The other type of application is one that allows users from more than just your organization to sign in and use the application. For example, if you're an independent software vendor (ISV), you can write an application which signs-in users from any organization.

These applications can also allow users to sign in using their personal Microsoft account. Maybe you want to give users the choice of signing into the application using either their work or school account or their personal Microsoft account.

### Guidelines for building multi-tenant apps

Building great multi-tenant apps can be challenging because of the number of different policies that IT administrators can set in their tenants. When building multi-tenant apps, you should keep a few guidelines in mind.​

Test your app in a tenant that has configured Conditional Access policies. The Conditional Access feature in Azure AD offers one of several ways that IT Pros can use to secure your app and protect a service. Conditional Access enables enterprise customers to protect services in a multitude of ways including multi-factor authentication, allowing only Intune-enrolled devices to access specific services, and restricting user locations and IP ranges. Your application may, or may not, acquire access tokens due to various Conditional Access Policies. Your app must gracefully handle not obtaining an access token.​

Your apps should also follow the principle of least user access to ensure that your app only requests permissions it actually needs. Avoid requesting permissions that require admin consent as it may prevent users from acquiring your app at all in some organizations.​

Finally, provide appropriate names and descriptions for any permissions you expose as part of your app. This helps users and admins know what they are agreeing to when they attempt to use your app's APIs.​

## Applications and service principals

An application that has been integrated with Azure AD has implications that go beyond the software aspect. "Application" is frequently used as a conceptual term, referring to not only the application software, but also its Azure AD registration and role in authentication/authorization "conversations" at runtime.

When you register an Azure AD application in the Azure portal, two objects are created in your Azure AD tenant:

- application object
- service principal

### Application object

The Application object is where developers specify how the app works. This includes parameters for authentication, secrets, or certificates, what permissions the app will use, any APIs the app exposes. ​

Azure AD applications are defined by exactly one application object. The application object resides in the Azure AD tenant where it was registered.​

### Service principal object

IT Pros use the Service Principal to determine how the application operates within their tenant. The IT PRO can limit the app to specific users and/or groups, review permissions and grant consent, assign users and/or groups to roles, or configure app provisioning.​

For a multi-tenant application, when an application is given permission to access resources in a tenant, a service principal object is created in that tenant​

### Application and service principal relationship

Consider the application object as the *global* representation of your application for use across all tenants, and the service principal as the *local* representation for use in a specific tenant.

The application object serves as the template from which common and default properties are derived for use in creating corresponding service principal objects. Application objects therefore have a 1:1 relationship with the software application, and a 1:many relationships with its corresponding service principal object(s).

Service principals must be created in each tenant where the application is used, enabling it to establish an identity for sign-in and/or access to resources being secured by the tenant.

A Single-tenant application has only one service principal (in its home tenant), created and consented for use during application registration.

Multi-tenant web applications or APIs also have a service principal created in each tenant where a user from that tenant has consented to its use.

## Summary

In this unit, you learned about the different account types that are used within the Microsoft identity platform. You also learned about the differences and relationships between applications and service principals.
