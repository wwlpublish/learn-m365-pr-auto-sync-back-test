There are two federation methods in Exchange Server:

 -  Exchange Delegated Federation, otherwise known as Delegated Authentication (DAuth).
 -  Open Authentication (OAuth), which was introduced with Exchange Server 2013.

DAuth uses the Azure AD authentication system for token generation. Organization relationships control which companies you share information with and allows for granular control of what features are available (free busy, mail tips, and so on).

:::image type="content" source="../media/dauth-4329c3d7.jpg" alt-text="Diagram showing basic workflow in Delegated authentication model":::


Open Authentication (OAuth) uses Azure AD authentication server, which provides better resiliency and faster in-forest communications. It uses IntraOrgConnectors / Configuration to control what information you can share with other companies.

:::image type="content" source="../media/open-authorization-88fb3ba5.jpg" alt-text="Diagram showing basic workflow in Open authentication model":::


Both federation methods enable you to share information between two Exchange organizations, such as your local Exchange organization and Exchange Online. The biggest difference between DAuth and OAuth is the granularity of control. When using DAuth, you can configure which information to share, such as MailTips or Free/Busy. If you implement sharing when using OAuth, then you must share everything because OAuth doesn't provide granular control.

### Delegated Federation

Exchange Federated Sharing is also known as Delegated Federation or Delegated Authentication (DAuth). It uses standard federation technologies to allow Exchange organizations to establish trusted relationships with each other.

To establish federation trust, organizations exchange certificates with public keys or with a trusted third party, and then uses those certificates to authenticate and secure all communications between them. Exchange Federated Sharing has been available since Exchange Server 2010. Since Exchange Server 2010 SP1, you'll typically use a self-signed certificate for the federation trust.

In Exchange Server, you use the Azure AD authentication system to establish the federation. The Azure AD authentication system is an identity service that runs over the Internet and works as a trust broker for Federated Sharing. To enable Federated Sharing, the organization must register with the Azure AD authentication system and then configure a Federated Sharing using an organizational relationship with another organization that also registers with the Azure AD authentication system.

### Open Authentication

Open Authentication (OAuth) 2.0 is a framework that includes server-to-server authentication. OAuth is a standards-based framework that is widely used across the web services industry and within other Microsoft products such as Hotmail.

Open Authentication typically involves three components that must communicate with each other using the HTTPS protocol (Port 443):

 -  A trusted authorization server
 -  Two services

The trusted authorization server, or token server, issues security tokens to the two services. These security tokens verify the authenticity of both services. They also ensure that user credentials and passwords don't pass between servers.

The security tokens control authentication and authorization. For example, the trusted authorization server might issue security tokens that verify that:

 -  Users from a specific Skype for Business Server service can access a specific Exchange Server service.
 -  Users from a specific Exchange Server service can access a specific Skype for Business Server service.

In Skype for Business Server, the default SIP domain acts as the OAuth service.

As part of its support within the Microsoft Office family of server products (including Microsoft 365 and the on-premises versions of Exchange 2013 or later, Lync Server 2013 or later, and SharePoint 2013 or later), the OAuth framework supports on-premises and hybrid topologies. In an on-premises topology, there's no requirement to implement a trusted authorization server, as the use of partner applications establishes the trust. By creating the partner application, the server products directly swap security tokens and bypass the need for a third-party token server.

### Functionality OAuth provides to Exchange Server 2016 and later

OAuth is required for some Exchange 2016 and later features, such as cross-premises discovery and automatic archive retention. OAuth enables the following Exchange features:

 -  Message Rights Management (MRM) to move messages from an on-premises mailbox to an archive mailbox located in Microsoft 365.
 -  Exchange In-place eDiscovery, especially cross-premises searches.
 -  Exchange In-place Archiving.
 -  On-premises mailboxes store attachments in OneDrive for Business.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.