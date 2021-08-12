Azure Active Directory (Azure AD) is an online instance like Active Directory. Azure AD provides authentication and authorization for Microsoft 365 and for other Microsoft cloud offerings, including Azure. Azure AD can authenticate cloud-only identities or identities synchronized with an on-premises directory.

There are different ways in which identities can be authenticated. Authentication can optionally use password hash synchronization. Or, you can enable user authentication with on-premises user accounts through Active Directory Federation Services (AD FS) or other single sign-on (SSO) providers.

Authentication options in Microsoft 365 fall into one of the following categories:

 -  **Cloud-only.** Cloud-only identities are exactly as the name suggests; the user identity only exists in the cloud, so all password management and policy control are done through Azure AD. The following graphic shows the logon of a Windows client to Azure AD to get access to the Microsoft 365 services.

    :::image type="content" source="../media/windows-client-logon-to-aad-d644dd38.jpg" alt-text="picture symbolizes the logon of a windows client to Azure AD to get access to the Office 365 services.":::


 -  **Directory synchronization with Pass-Through authentication (PTA).** This authentication option provides a simple password validation for Azure AD authentication services. PTA uses a software agent running on one or more on-premises servers to validate an organization's users directly with its on-premises Active Directory. With PTA, on-premises Active Directory user account objects are synchronized with Microsoft 365 and users are managed on-premises. PTA enables users to sign in to both on-premises and Microsoft 365 resources and applications using their on-premises account and password. The following graphic symbolizes the logon of a windows client to Azure AD when using PTA, where the logon request is redirected to an on-premises infrastructure.

    :::image type="content" source="../media/windows-client-logon-to-aad-using-pta-7847117c.jpg" alt-text="picture symbolizes the logon of a windows client to Azure AD when using PTA, where the logon request is redirected to an on-premises infrastructure":::


 -  **Single Sign-On (SSO) with AD FS.** The SSO option hands over authentication control to an organization's directory service. As such, users no longer authenticate against Azure AD but against AD FS. So, when a user types their login credentials (for example, **user@adatum.com)** into the Microsoft 365 sign-in page, the user receives a message telling them that they've been redirected to their organization’s sign-in page. They now enter their on-premises credentials and authenticate to the Microsoft 365 online services by using a delegated token that verifies to Microsoft 365 that the user has been successfully authenticated by their on-premises directory. In the following graphic, the logon arrows and processes are similar to PTA. However, another proxy is required for AD FS because the AD FS Server hosting the farm isn't allowed to accept connections from the public network.

    :::image type="content" source="../media/windows-client-logon-to-aad-using-adfs-5653d60f.jpg" alt-text="graphic symbolizes the logon of a windows client to Azure AD when using ADFS":::
