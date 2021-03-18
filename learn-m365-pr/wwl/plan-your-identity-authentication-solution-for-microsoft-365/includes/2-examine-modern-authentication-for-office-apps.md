Modern authentication is a Microsoft solution based on the [Microsoft Authentication Library (MSAL)](https://docs.microsoft.com/azure/active-directory/develop/msal-migration?azure-portal=true). It applies the Open Authorization (OAuth) standard when an application or client software tries to obtain access tokens from an authentication provider to access resources. Modern authentication enables sign in features such as Multi-Factor Authentication (MFA), SAML-based third-party Identity Providers with Office client applications, smart card and certificate-based authentication. It also removes the need for Outlook to use the basic authentication protocol.

### Modern Authentication Prerequisites

For the Microsoft 365 services, the default state of modern authentication is:

 *  Exchange Online is **On** by default.
 *  SharePoint Online is **On** by default.
 *  Skype for Business Online is **On** by default.

Modern authentication is automatically **On** for Office 2016 client apps.

To use modern authentication with Office 2013 client apps, prerequisite software must be installed based on whether you have a Click-to-run based installation or a MSI-based installation. To determine whether your Office installation is Click-to-run or MSI-based, you should complete the following steps:

1.  Start Outlook 2013.
2.  On the **File** menu, choose **Office Account**.
3.  For Outlook 2013 Click-to-Run installations, an **Update Options** item is displayed. For MSI-based installations, the **Update Options** item is not displayed.

:::image type="content" source="../media/outlook2013-click-to-run-e8aa57de.png" alt-text="screen shots that compare Outlook 2013 Click-to-Run installations showing the Update Options item versus Outlook 2013 for MSI-based installations that do not show the Update Options item":::


To turn it on for Office 2013 client apps, see [Enable Modern Authentication for Office 2013 on Windows devices](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910?azure-portal=true).

If you are using Active Directory Federation Services (AD FS) 2.0), you should first review the caveats with modern authentication as described in the following article titled [Office 2013 and Office 365 ProPlus modern authentication and client access filtering policies: Things to know before onboarding](https://go.microsoft.com/fwlink/p/?LinkId=717374?azure-portal=true).

### Authentication behavior

The remainder of this unit examines authentication behavior for Office 2013 client apps (or later) when they connect with or without modern authentication to Exchange Online, SharePoint Online, and Skype for Business Online.

#### Exchange Online<br>

The following table describes the authentication behavior for Office 2013 or Office 2016 client apps when they connect to Exchange Online with or without modern authentication.

:::row:::
  :::column:::
    <b>Office client app version </b>
  :::column-end:::
  :::column:::
    <b>Is the Registry key present? </b>
  :::column-end:::
  :::column:::
    <b>Is modern authentication turned on? </b>
  :::column-end:::
  :::column:::
    <b>Authentication behavior with modern authentication turned on for the tenant (default) </b>
  :::column-end:::
  :::column:::
    <b>Authentication behavior with modern authentication turned off for the tenant </b>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    No, or EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then basic authentication is used. Server refuses modern authentication when the tenant is not enabled.
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then basic authentication is used. Server refuses modern authentication when the tenant is not enabled.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then basic authentication is used. Server refuses modern authentication when the tenant is not enabled.
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then basic authentication is used. Server refuses modern authentication when the tenant is not enabled.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    Yes, EnableADAL=0
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Basic authentication
  :::column-end:::
  :::column:::
    Basic authentication
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2013
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Basic authentication
  :::column-end:::
  :::column:::
    Basic authentication
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2013
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then basic authentication is used. Server refuses modern authentication when the tenant is not enabled.
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then basic authentication is used. Server refuses modern authentication when the tenant is not enabled.
  :::column-end:::
:::row-end:::


#### SharePoint Online

The following table describes the authentication behavior for Office 2013 or Office 2016 client apps when they connect to SharePoint Online with or without modern authentication.

:::row:::
  :::column:::
    <b>Office client app version</b>
  :::column-end:::
  :::column:::
    <b>Is the Registry key present?</b>
  :::column-end:::
  :::column:::
    <b>Is modern authentication turned on?</b>
  :::column-end:::
  :::column:::
    <b>Authentication behavior with modern authentication turned on for the tenant (default) </b>
  :::column-end:::
  :::column:::
    <b>Authentication behavior with modern authentication turned off for the tenant </b>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    No, or EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication only.
  :::column-end:::
  :::column:::
    Failure to connect.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication only.
  :::column-end:::
  :::column:::
    Failure to connect.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 0
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2013
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2013
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication only.
  :::column-end:::
  :::column:::
    Failure to connect.
  :::column-end:::
:::row-end:::


#### Skype for Business Online

The following table describes the authentication behavior for Office 2013 or Office 2016 client apps when they connect to Skype for Business Online with or without modern authentication.

:::row:::
  :::column:::
    <b>Office client app version </b>
  :::column-end:::
  :::column:::
    <b>Is the Registry key present?</b>
  :::column-end:::
  :::column:::
    <b>Is modern authentication turned on?</b>
  :::column-end:::
  :::column:::
    <b>Authentication behavior with modern authentication turned on for the tenant </b>
  :::column-end:::
  :::column:::
    <b>Authentication behavior with modern authentication turned off for the tenant (default) </b>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    No, or EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then Microsoft Online Sign in Assistant is used. Server refuses modern authentication when Skype for Business Online tenants are not enabled.
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then Microsoft Online Sign in Assistant is used. Server refuses modern authentication when Skype for Business Online tenants are not enabled.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then Microsoft Online Sign in Assistant is used. Server refuses modern authentication when Skype for Business Online tenants are not enabled.
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then Microsoft Online Sign in Assistant is used. Server refuses modern authentication when Skype for Business Online tenants are not enabled.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2016
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 0
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2013
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    No
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Office 2013
  :::column-end:::
  :::column:::
    Yes, EnableADAL = 1
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Modern authentication is attempted first. If the server refuses a modern authentication connection, then Microsoft Online Sign in Assistant is used. Server refuses modern authentication when Skype for Business Online tenants are not enabled.
  :::column-end:::
  :::column:::
    Microsoft Online Sign in Assistant only.
  :::column-end:::
:::row-end:::
