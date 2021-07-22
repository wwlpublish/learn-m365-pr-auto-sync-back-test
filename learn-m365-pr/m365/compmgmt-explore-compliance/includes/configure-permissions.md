There are a few steps you need to complete before you can begin using Compliance Manager.

## Set permissions and assign roles

Only users assigned an appropriate role can access Compliance Manager, and the actions allowed by each user are restricted by the role assigned. Start by identifying users that will use Compliance Manager. They should be part of the appropriate role group in the Microsoft 365 compliance center. Identifying other users that will participate in the process can come later. Here are instructions on how to grant users access to Compliance Manager.

1. Sign in to the [**Microsoft 365 compliance center**](https://compliance.microsoft.com?azure-portal=true) using a global administrator account.
2. In the **Microsoft 365 compliance center,** in the left menu, click **Permissions.** 
3. Under **Permissions,** where you see **To view and manage roles in Office 365, please go here,** click **here** to open **Office 365 Security & Compliance.**
4. In the **Name** column, select the role group in the table below that matches desired level of access.
5. Edit the role group to add the appropriate user.

|  User can… |  Role Group |
|---|---|
| Read but not edit data  | Compliance Manager Readers  |
|  Edit data | Compliance Manager Contributors  |
|  Edit data and enter test results |  Compliance Manager Assessors |
|  Manage assessments, templates, and tenant data | Compliance Manager Administrators  |

## Configure automated testing

Microsoft Secure Score is a tool that measures an organization's security posture. Some of the improvement actions monitored in Secure Score are also monitored by Compliance Manager. When you configure automated testing, the results of an action tested and updated in Secure Score are synced with the same action in Compliance Manager. Keeping the two in sync reduces duplication of effort between the security team and compliance team. The recommendation is to configure automated testing for all actions. The default setting for automated testing depends on when you started using Compliance Manager. Make sure Secure Score updates are configured to produce the results you are expecting by taking the following steps.

1. Sign in to the [**Microsoft 365 compliance center**](https://compliance.microsoft.com?azure-portal=true) using a global administrator account or account that is a member of the Compliance Manager Administrators role group.
2. In the **Microsoft 365 compliance center,** in the left menu, click **Compliance Manager.**
3. On the **Compliance Manager page,** in the top-right corner, click **Compliance Manager settings.**
4. On the **Compliance Manager settings page,** click **Automated testing.**
5. Select the desired automated testing option. If you select **Turn on per improvement action,** you will be presented with a list of improvement actions common to Secure Score and Compliance Manager to choose from.
