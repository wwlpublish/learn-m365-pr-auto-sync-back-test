## Set up Workplace Analytics

Setting up Workplace Analytics is a straightforward process. Here's an overview of the primary steps.

1. Your Office 365 or Azure Active Directory administrator assigns the licenses and roles.
1. The designated Workplace Analytics administrator enters system defaults and privacy settings.
1. The Workplace Analytics administrator prepares and uploads the organizational data.
1. Workplace Analytics validates the upload and then processes the data.

Once these steps are complete, your organization has full access to all service features (except Upload and administrative settings). 

Organizational data contains effective dates which map to the Office 365 data. This data should be uploaded on a regular monthly schedule to reflect changes in your organization. The Office 365 collaboration data will update weekly.

For more information on system requirements and data processing, see the **Learn more** section below.

## Workplace Analytics and data privacy

As an Office 365 service, Workplace Analytics sits in your organization’s trust boundaries with privacy safeguards and protections for individuals. By default, only metadata is processed for metric generation and personally identifiable information is not included. Your organization has full control over how Workplace Analytics is used, deployed, and the visibility it has in your organization.

These are the customer-specific controls.

![Customer-specific controls](../media/customer-specific-controls.png)

- Scope of population (with the option to exclude sensitive groups)
- Analyst access to Workplace Analytics and access to specific population scopes
- Access to email and meeting subject lines
- Rule out all meetings and emails by keywords (in subject lines) that you deem sensitive
- Specific individuals or domains
- Organizational attributes loaded

With Workplace Analytics, the objective is not to examine individual activity, but to recognize group level trends happening in your organization. The app looks at header level metadata—no content, such as body of emails, email attachments, or anything considered sensitive in nature. 

Features in Workplace Analytics default to non-personally identifiable data. Out-of-the-box insights default to a minimum aggregate threshold of five employees.

## Learn more

- [Set up Workplace Analytics](https://docs.microsoft.com/workplace-analytics/setup/set-up-workplace-analytics?azure-portal=true)
