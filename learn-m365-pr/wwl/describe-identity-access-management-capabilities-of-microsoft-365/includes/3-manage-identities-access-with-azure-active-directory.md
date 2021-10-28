The modern security perimeter now extends beyond an organization's network to include user and device identity. Organizations can utilize these identity signals as part of their access control decisions. Microsoft 365 uses Azure AD Conditional Access to manage access and control to all your organization's assets and resources.

Conditional Access is at the heart of the new identity-driven control plane. It spans Microsoft 365 services, including Intune, Microsoft 365, and Windows 10. It provides granular access to keep your corporate data secure while allowing users to do their best work from any device and from any location. Conditional Access helps protect sensitive data by evaluating users, devices, apps, location, and assessing the risk before granting access. This helps ensure that only approved users and devices can access critical company resources.

:::image type="content" source="../media/3-conditional-access-overview-how-it-works.png" alt-text="Diagram showing the Conditional Access model":::

Conditional Access policies at their simplest are if-then statements. If a user wants to access a resource, then they must complete an action, for example, a payroll manager wants to access the payroll application and is required to perform multi-factor authentication to access it.

### Conditional Access signal assessment

When an access request is received, Conditional Access uses signal information from the source of the request to build a context for determining the overall risk, which is used to make an informed decision as to whether the session request should be granted or revoked. Common signals that Conditional Access can take into account when making a policy decision include:

| **Signal Type**                          | **Use case**                                                 |
| ---------------------------------------- | ------------------------------------------------------------ |
| User  or group membership                | Policies  can be targeted to specific users and groups, giving administrators  fine-grained control over access. |
| IP  Location information                 | Organizations  can create trusted IP address ranges that can be used when making policy  decisions. Also, Administrators can  opt to block or allow traffic from an entire countries IP range. |
| Device                                   | When  enforcing Conditional Access policies, users with devices of specific  platforms or marked with a specific state can be used |
| Application                              | Users attempting to access  specific applications can trigger different Conditional Access policies. |
| Real-time  and calculated risk detection | Signals integration with Azure  AD Identity Protection allows Conditional Access policies to identify risky  sign-in behavior. Policies can then force users to perform password changes  or multi-factor authentication to reduce their risk level or be blocked from  access until an administrator takes manual action. |
| Microsoft  Cloud App Security (MCAS)     | Enables user application  access and sessions to be monitored and controlled in real-time, increasing  visibility and control over access to and activities performed within your  cloud environment. |

### Conditional Access decision

Once you've established that the signal request passes the risk assessment, it's time to apply a policy to the request based on your organization’s security posture and risk appetite. Conditional Access provides a flexible set of policies that can be configured to provide granular control over the circumstances in which users can access an organization’s resources.

The decision outcome from Conditional Access will be:

- **Block Access** – This is the most restrictive decision.
- **Grant Access** – The least restrictive decision. It can still require one or more of the following checks:

  - Require multi-factor authentication
  - Require device to be marked as compliant
  - Require Hybrid Azure AD joined device
  - Require approved client app
  - Require app protection policy (preview)

### Enforcement through applied policies

Many organizations have [common access concerns that Conditional Access policies can help with](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common) such as:

- Requiring multi-factor authentication for users with administrative roles
- Requiring multi-factor authentication for Azure management tasks
- Blocking sign-ins for users attempting to use legacy authentication protocols
- Requiring trusted locations for Azure Multi-Factor Authentication registration
- Blocking or granting access from specific locations
- Blocking risky sign-in behaviors
- Requiring organization-managed devices for specific applications

### Licensing for identity and Conditional Access

Azure AD is a cloud-based identity service that centralizes identity and access management across cloud and on-premises environments. It has built in support for synchronizing with your existing on-premises Active Directory or can be used stand-alone. This means that all your applications, whether on-premises, in the cloud, or even mobile can share the same credentials.

Azure AD has several tiers of service, including Free, Microsoft 365, and Premium editions P1 and P2. Premium editions might require additional cost depending upon your Microsoft cloud subscription levels. Azure AD Premium P1 is included as part of Microsoft 365 E5, E3, and F3 plans. Azure AD Premium P2 is included with Microsoft 365 E5.

Here are some of the key features from each tier:

- Free – includes single sign-on, self-service password change, multi-factor authentication, basic security/usage reports, and business-to business collaboration
- Microsoft 365 Apps – includes all the free features plus identity, self-service password reset, and device write-back (two-way synchronization between on-premises directories and Azure)
- Premium P1 – includes free, Office 365, and premium features including Conditional Access based on group, location, and device status, Microsoft Cloud App Discovery, Advanced security and usage reports, advanced group access management, and hybrid identities
- Premium P2 – includes all the above plus Azure Identity protection, which includes risk based Conditional Access policies, risky accounts detection, risk event investigations and Identity governance capabilities, including Privileged Identity Management (PIM)

Azure Active Directory is a feature rich service offering that scales to meet your needs. You can see the complete feature list by visiting the [Active Directory Pricing Guide](https://azure.microsoft.com/pricing/details/active-directory/) page. The table below shows a summarized version of the content, with only the identity and access management features for each tier.

| **Feature**                                                  | **Azure AD Free** | **Microsoft 365** | **Premium P1** | **Premium P2** |
| ------------------------------------------------------------ | ----------------- | ----------------- | -------------- | -------------- |
| Single Sign-on across Azure  and Microsoft 365               | Yes               | Yes               | Yes            | Yes            |
| Cloud Authentication  (Pass-Through Auth, Password Hash sync, Seamless SSO) | Yes               | Yes               | Yes            | Yes            |
| Azure AD Connect sync (extend  on-premises directories to Azure AD) | Yes               | Yes               | Yes            | Yes            |
| Self-Service Password Change  for cloud users                | Yes               | Yes               | Yes            | Yes            |
| Azure AD Join: desktop SSO  & administrator BitLocker recovery | Yes               | Yes               | Yes            | Yes            |
| Password Protection (global  banned password)                | Yes               | Yes               | Yes            | Yes            |
| Multi-Factor Authentication                                  | Yes               | Yes               | Yes            | Yes            |
| Self-service password reset  for cloud users                 |                   | Yes               | Yes            | Yes            |
| Device write-back (two-way  synchronization between on-premises directories and Azure) |                   | Yes               | Yes            | Yes            |
| Password protection (custom  banned password)                |                   |                   | Yes            | Yes            |
| Self-service password  reset/change/unlock with on-premises write-back |                   |                   | Yes            | Yes            |
| Conditional Access based on  group, location, and device status |                   |                   | Yes            | Yes            |
| Multi-Factor Authentication  with Conditional Access         |                   |                   | Yes            | Yes            |
| Microsoft Identity Manager                                   |                   |                   | Yes            | Yes            |
| Group access and management                                  |                   |                   | Yes            | Yes            |
| Identity Protection                                          |                   |                   |                | Yes            |
| Risk based Conditional Access  policies                      |                   |                   |                | Yes            |
| Privileged Identity Management  (PIM)                        |                   |                   |                | Yes            |
| Entitlement Management                                       |                   |                   |                | Yes            |
