## Prerequisites & permissions

Before you can begin creating insider risk policies, there are several requirements that need to be met.

### Turn on audit logging

Insider risk management uses audit logs for user insights and activities configured in policies. The audit logs are a summary of all activities associated with an insider risk management policy or anytime a policy is modified. For step-by-step instructions to turn on auditing, see [Turn Office 365 audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off?azure-portal=true). After you turn on auditing, a message is displayed that says the audit log is being prepared and that you can run a search in a couple of hours after the preparation is complete.

### Assign permissions

A global administrator will need to assign you and other compliance officers to the **Insider Risk Management** or **Insider Risk Management Admin** role group by using the **Permissions** module in the Microsoft 365 compliance center. Once you have been assigned to one of these roles, you have the ability to assign additional users to specific role groups to manage different sets of insider risk management features.

Depending on the structure of your compliance management team, you have options to assign users to specific role groups to manage different sets of insider risk management features. You have the ability to choose from the following role group options when configuring insider risk management:

- **Insider Risk Management.** Use this role group to manage insider risk management for your organization in a single group. By adding all user accounts for designated administrators, analysts, and investigators, you can configure insider risk management permissions in a single group. This role group contains all the insider risk management permission roles. This is the easiest way to quickly get started with insider risk management and is a good fit for organizations that do not need separate permissions defined for separate groups of users.
- **Insider Risk Management Admin.** Use this role group to initially configure insider risk management and later to segregate insider risk administrators into a defined group. Users in this role group can create, read, update, and delete insider risk management policies, global settings, and role group assignments.
- **Insider Risk Management Analysts.** Use this group to assign permissions to users that will act as insider risk case analysts. Users in this role group can access all insider risk management alerts, cases, and notices templates. They cannot access the insider risk Content Explorer.
- **Insider Risk Management Investigators.** Use this group to assign permissions to users that will act as insider risk data investigators. Users in this role group can access all insider risk management alerts, cases, notices templates, and the Content Explorer for all cases.

## Potential dependencies

Two of the insider risk management templates have dependencies that must be configured for policy indicators to generate relevant activity alerts. This step might be optional depending on the policy you plan to configure for your organization.

### Departing employee data theft template

If you configure a policy using the Departing employee data theft template, you'll need to configure a Microsoft 365 Human Resources (HR) data connector so that you can import user and log data from 3rd-party risk management and human resources platforms. HR connectors allow you to pull in human resources data from CSV files, including user termination and last employment dates. This data helps drive alert indicators in insider risk management policies and is an important part of configuring full risk management coverage in your organization.

The following requirements must be met before you can set up an HR connector:

- A global administrator will need to consent to allow the Office 365 Import service to access data in your organization.
- The user who creates the HR connector will need to be assigned the Mailbox Import Export role in Exchange Online. 
- You have to have a system in place for retrieving and exporting the data from your organization's HR system and add it to a CSV file.
  Once the requirements have been met, you can set up your HR connector.
  
  Briefly, the steps for creating the connector involve the following:
  1. Creating an app in Azure Active Directory.
  1. Generating the CSV file from your organization's HR system.
  1. Creating an HR connector in the Microsoft 365 compliance center.
  1. Running a script that will upload the HR data in the CSV file to the Microsoft cloud.

  For more details, see the [Set up a connector to import HR data](/microsoft-365/compliance/import-hr-data?azure-portal=true) topic.

### Data leaks template

Insider risk management supports using DLP policies to help identify the intentional or accidental exposure of sensitive information to unwanted parties. When configuring an insider risk management policy with the Data leaks template, you have to assign a specific DLP policy. This policy helps drive the alert indicators for sensitive information and is an important part of configuring full risk management coverage in your organization.

> [!NOTE]
> To reduce noise, alerts will only fire when a high volume DLP policy qualifying event is triggered. For example, an alert will fire if the policy detects 10 or more credit card numbers in an email or document, but not less. See the [Create, test, and tune a DLP policy](/microsoft-365/compliance/create-test-tune-dlp-policy?azure-portal=true) topic to learn how to configure DLP policies for your organization.

## Creating a new insider risk policy

Insider risk management policies include assigned users and define which types of risk indicators are configured for alerts. Before activities can trigger alerts, a policy must be configured.

To create a new insider risk management policy, you use the policy wizard in the **Insider risk management** solution in the Microsoft 365 compliance center. Briefly, you create a new policy by stepping through the policy wizard and policy settings to configure the following items:

- **Policy template**
- **Users or groups** the policy will apply to (optionally, assign higher risk scores to detected activity based on where the related content is located, what sensitive info is included, and what sensitivity labels are applied)
- **Alert indicators** (**Indicators** need to be enabled under **Policy Settings** before they can be selected when creating a policy)
- **Duration** (time frame) for monitoring

For more information, see [Create an insider risk policy](/microsoft-365/compliance/insider-risk-management-configure?step-5-required-create-an-insider-risk-management-policy?azure-portal=true).

## Learn more

- [Compare Microsoft 365 Enterprise Plans](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1?azure-portal=true)
- [Enable permissions for insider risk management](/microsoft-365/compliance/insider-risk-management-configure?step-1-required-enable-permissions-for-insider-risk-management?azure-portal=true)
- [Create, test, and tune a DLP policy](/microsoft-365/compliance/create-test-tune-dlp-policy?azure-portal=true)
