To create your identity infrastructure, you'll designate a primary identity provider. This service stores user accounts and attributes, groups and memberships, and supports their ongoing administration. 

  ![Identity Lifecycle](../media/icon10.png)

With Microsoft 365, your primary identity provider is either: 

- Active Directory Domain Services (AD DS), an intranet identity provider hosted on computers running Windows Server. This is typically used by organizations that have an existing on-premises identity provider. 

 ![Identity Lifecycle](../media/icon11.png)

- Azure Active Directory (Azure AD), a cloud-based Identity as a Service (IDaaS) that provides a broad range of capabilities for managing and protecting your environment. This is typically used by organizations that have no existing on-premises infrastructure. Azure AD is also used by Enterprise customers with on-premises infrastructure. You use Azure AD Connect to manage this hybrid identity environment. 

Use the following steps to plan your identity governance infrastructure in a cloud or hybrid environment. 

1. *Plan for users and groups.* Identify users, groups, and group memberships and their corresponding Azure AD accounts. 

2. *Secure your privileged identities.* Plan how to secure your global administrator accounts and determine which users will have global admin roles and dedicated global admin accounts.   

3. *Configure hybrid identity.* For hybrid environments, determine which on-premises identities in AD DS you want to sync with the Azure AD tenant used by your Microsoft 365 subscription. Plan how you will configure Azure AD Connect to implement the synchronization. 

4. *Configure secure user authentication.* Plan to set up multi-factor authentication as a second level of security for user sign-ins. Determine how you will configure the second authentication method on a per-user account basis. 

5. *Simplify access for users.* Plan to use Azure AD to enable self-service password reset (SSPR). This permits users to reset or unlock their passwords without help desk intervention. For hybrid environments, plan to implement password writeback, which allows users to update their passwords through Azure AD SSPR even when their accounts and attributes are stored on-premises. 

6. *Use groups for easier management.* Identify Azure AD groups that group owners can manage on their own. Self-service group management enables group leaders who understand the business use for the group to have day-to-day control of membership. 
