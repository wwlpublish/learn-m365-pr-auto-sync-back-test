Teams Rooms devices aren't "just another Windows computer." Because Teams Rooms devices aren't used for general purpose computing, how you think about managing and securing them needs to be approached differently than how you manage and secure typical servers and workstations.

Microsoft has several tools for managing Windows on Teams Rooms devices such as Microsoft Endpoint Configuration Manager, Group Policy, and Azure Active Directory (Azure AD).

While many of the common management tools you are familiar with are supported, answering the question "which tool is right for my organization" may not have an obvious answer.
The tool that works best for one organization may not work best for other ones. For example, your organization may have robust processes and procedures in place for managing Windows 10 using Endpoint Configuration Manager. Because Teams Rooms devices don't support many of the common configuration settings used in general computer environments, leveraging Configuration Manager as a management tool may lead to situations where Teams Rooms devices are inadvertently misconfigured.

You may find it perfectly acceptable operating Teams Rooms devices without Windows 10 management.

The question as to which tools to use to manage Teams Rooms devices ultimately is answered by each individual use case. You may have a robust set of Active Directory processes and procedures. In that case, Active Directory and Group Policy would be a viable option for managing the underlying operating system. Or you may have adopted a cloud first, mobile first strategy and have processes and procedures in place for Intune. In that case, Azure AD and Intune make the most sense.

> [!IMPORTANT]
> You should exclude both Teams Rooms resource accounts and compute modules from common policies that may be in place in your environment. This includes things like requiring passwords and password complexity for local user accounts, idle time outs which lock or sign-out the logged in user, power management policies which place computers into hibernate mode, multi-factor authentication, and most Intune Conditional Access Policies.
>

**Create new dedicated security groups**. Whichever management tools you use, you should create new dedicated security groups that only contain Teams Rooms devices and resource accounts. These security groups can be used to exclude Teams Rooms devices and resource accounts from your existing management policies. Then you can assign new policies to them. These security groups can be dynamic or static. If static groups are used, be sure you have a process for ensuring all Teams Rooms devices and resource accounts are added to these groups.

Create dedicated:

- Active Directory organizational units (OU) for the accounts and Teams Rooms devices.
- Active Directory/Azure AD security groups for accounts and Teams Rooms devices.
- Intune device configuration policies.
- Conditional access policies.

Block inheritance on Active Directory OUs for Teams Rooms accounts and devices. Exclude from:

- Conditional access policies.
- Mobile device management (MDM) configuration policies.
- Multifactor authentication policies.
