## Set up Workplace Analytics

Setting up Workplace Analytics is a straightforward process. Here's an overview of the primary steps:

1. Your Microsoft 365 or Azure Active Directory admin assigns the licenses and roles.
2. The designated Workplace Analytics admin sets up the system defaults and privacy settings.
3. The Workplace Analytics admin then prepares and uploads the organizational data.
4. Workplace Analytics validates the upload and then processes the data.

After these steps are complete, your organization has full access to all service features (except for admin-only settings, such as for uploading HR data and the privacy and system default settings).

Organizational data contains effective dates that map to the Microsoft 365 data. This data should be uploaded on a regular (monthly) schedule to reflect changes in your organization. The Microsoft 365 collaboration data updates weekly.

For more information on system requirements and data processing, see [Learn more](#learn-more).

## Workplace Analytics and data privacy

As a Microsoft 365 service, Workplace Analytics resides within the Microsoft 365 trust boundaries as defined by organization for privacy safeguards and protections of individual employees. By default, only metadata is processed for generating metrics that do not include personal information. Your organization has full control over how Workplace Analytics is used, deployed, and the visibility it has in your organization.

The following are user-specific controls.

* Scope of population (with the option to exclude sensitive groups).
* Analyst (role-based) access to Workplace Analytics analysis and to specific population scopes.
* Visibility to meeting subject lines.
* Exclusions set for all meetings and emails based on keywords (in subject lines) that you deem sensitive.
* Specific individuals or domains.
* Organizational attributes loaded.

With Workplace Analytics, the objective is not to examine individual activity, but to recognize group-level trends occurring in your organization. It uses header level metadata and not content, such as body of emails or email attachments.

Features in Workplace Analytics default to non-personal information and a minimum aggregate threshold of five employees, which you can set higher if required.

## Learn more

[Set up Workplace Analytics](/viva/insights/setup/set-up-workplace-analytics)
