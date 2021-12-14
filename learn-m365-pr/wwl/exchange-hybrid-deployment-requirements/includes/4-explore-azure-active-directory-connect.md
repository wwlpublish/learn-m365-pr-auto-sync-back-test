The Azure AD Connect tool, formerly known as DirSync, is the primary supported directory synchronization tool for Microsoft 365. An organization can configure Azure AD Connect once, after which it automatically runs in the background without user interaction. For Microsoft 365, the purpose of the tool is to enable coexistence between an organization's on-premises Active Directory Domain Services (AD DS) environment and Microsoft 365 in the cloud.

Azure Active Directory Connect is made up of three parts:

 -  Synchronization services
 -  An optional authentication service that consists of one of the following authentication solutions:
    
     -  Pass-Through Authentication (PTA)
     -  Password hash synchronization (PHS)
     -  Seamless Single Sign On (SSO)
     -  Active Directory Federation Services)
 -  The Azure AD Connect Health monitoring service

### Directory synchronization

Azure AD Connect is the primary supported tool to provide synchronization of objects between on-premises Active Directory and Azure Active Directory.

:::image type="content" source="../media/azure-active-directory-connect-8f07eae2.jpg" alt-text="diagram showing Azure AD Connect providing synchronization of objects between on-premises AD and Azure AD":::


Azure AD Connect also supports the following scenarios:

 -  Synchronization of multiple Active Directory forest environments
 -  Synchronization for multiple Exchange organizations to one Microsoft 365 tenant
 -  Synchronization of third-party on-premises LDAP directory services

When using Azure AD Connect for directory synchronization:

 -  New user, group, and contact objects in on-premises AD DS are added to Microsoft 365. However, Microsoft 365 licenses aren't automatically assigned to these objects.
 -  Attributes of existing user, group, or contact objects that are modified in on-premises AD DS are modified in Microsoft 365. However, not all on-premises AD DS attributes are synchronized to Microsoft 365.
 -  Existing user, group, and contact objects that are deleted from on-premises AD DS are deleted from Microsoft 365.
 -  Existing user objects that are disabled on-premises are disabled in Microsoft 365. However, licenses aren't automatically unassigned.

In a cloud-only Microsoft 365 deployment, all Azure AD objects are created in the cloud, and they must be edited using cloud-based tools (either using the Office 365 portal or the Microsoft 365 admin center, or by using Windows PowerShell cmdlets). In this scenario, Azure AD is referred to as the source of authority for all Active Directory objects.

Azure AD requires a single source of authority for every object. As such, it’s important to understand that when you deploy Azure AD Connect for Active Directory synchronization, you're mastering objects from within your on-premises AD DS by using tools such as Active Directory Users and Computers or Windows PowerShell. The source of authority in this scenario is the on-premises AD DS. This process is known as establishing Hybrid Identity.

After the first synchronization cycle has completed, the source of authority is transferred from the cloud to the on-premises AD DS. Later changes to cloud objects (except for licensing) are then mastered from the on-premises AD DS tools. The corresponding cloud objects are read-only, and Microsoft 365 administrators can't edit cloud objects if the source of authority is on-premises.

Email address matching is used to identify the on-premises AD DS user object that relates to a Microsoft 365 user:

 -  If a user exists in your on-premises AD DS and no matching user exists in Microsoft 365, Azure AD Connect will create a new Microsoft 365 user with the same email address as the on-premises account.
 -  If a user already exists in both your on-premises AD DS and in Microsoft 365 and these objects have the same email address, then during the first synchronization these objects will become joined, or linked.

By synchronizing user, contact, and group objects, Azure AD Connect provides a unified GAL experience between Microsoft 365 and the on-premises AD DS or Exchange environment. Using the filtering features in Azure AD Connect, objects hidden from the GAL on-premises are also hidden from the GAL in Exchange Online.

Azure AD Connect supports the following mailbox migration scenarios:

 -  Microsoft 365 replaces on-premises Exchange Server.
 -  Both on-premises and Exchange Online mailboxes exist in a hybrid deployment scenario.

In hybrid scenarios, Azure AD Connect allows mail routing between on-premises and Microsoft 365 with a shared SMTP domain namespace or to use archive mailboxes stored in Exchange Online for on-premises mailboxes. This scenario allows on-premises/cloud coexistence for both Exchange Server 2019 or later, Skype for Business Server 2015, or Lync Server 2013.

**Additional reading.** For more information, see [Hybrid identity documentation](/azure/active-directory/hybrid?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.