At the highest level, a DLP policy contains locations and rules. Locations define where DLP can protect contents. DLP policies are applied to sensitive items across Microsoft 365 locations – you can scope that location as detailed in this table.

|     Location                           |     Include/Exclude by     |
|----------------------------------------|----------------------------|
|     Exchange email                     |     Distribution groups    |
|     SharePoint sites                   |     Sites                  |
|     OneDrive accounts                  |     Accounts               |
|     Teams chat and channel messages    |     Accounts               |
|     Windows 10 devices                 |     User or group          |
|     Microsoft Cloud App Security       |     Instance               |

Rules are conditions and actions that you use to define when and how to protect content.

- Conditions define the content before a rule is enforced. For example, "look for content that contains Social Security numbers and is being shared outside of the organization."
- Actions describe what you want the rule to do when content matching the conditions is found. For example, if someone tries to send content that contains Social Security numbers outside your organization, block access to the document. Also, you can configure the rule to notify the user by email that the email was blocked and why.to explain why this DLP rule was created.
- User notifications/user overrides along with user override you can notify a user of a violation of a policy and point them to documentation that might allow them to override the policy.
- Alerts and Incident reports can notify compliance officers when a rule is matched.

A rule is created to enforce a specific protection requirement. A DLP policy is used to group together common protection requirements.

For example, imagine a set of rules designed to meet the Health Insurance Portability and Accountability Act (HIPAA) across all SharePoint Online sites and all OneDrive for Business sites. The policy looks for any document containing sensitive information that is shared with people outside your organization (the conditions) and then blocks access to document (the actions).

:::image type="content" source="../media/2-data-loss-prevention-policy.png" alt-text="Data loss prevention policy.":::

## Types of sensitive information

DLP policies are designed to protect information that should remain private. Microsoft categorized this information using sensitive information types such as credit card number, bank account numbers, national ID numbers, and passport numbers.

A specific sensitivity information type, for example, a credit card number, isn't defined as simply a 16-digit number. Each sensitivity information type is defined and detected by a combination of:

- Keywords
- Internal function to validate checksums or composition
- Evaluation of regular expressions to find pattern matches
- Other content examination

## Actions and notifications

Actions are applied to protect content when content matches a condition in a rule. You can restrict access to the content in the following ways:

- Restrict access to content for everyone.
- Restrict access to content for people outside the organization.
- Restrict access to "Anyone with the link.

If there is site content (for example, SharePoint sites), the document would be restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document. When access to a document is blocked, the document appears with a special policy tip icon in the library on the site as shown here.

:::image type="content" source="../media/2-blocked-content.png" alt-text="Blocked content.":::

If a user tries to email content with sensitive information, the action blocks the email, and the user sees a policy tip or email notification, depending on how the DLP rule was configured.

:::image type="content" source="../media/2-blocked-email-content.png" alt-text="Blocked e-mail content.":::

## User notifications and user overrides

Policies can be configured such that when they're triggered, a user notification and an option to override the policy can be presented. For example, the user can provide a business justification to override a policy or the user has encountered a false positive.

:::image type="content" source="../media/2-user-notifications-user-overrides-inline.png" lightbox="../media/2-user-notifications-user-overrides-expanded.png" alt-text="User notifications and overrides.":::

Email notifications can be sent to the person who sent, shared, or last modified the content and if there is site content, to the primary site collection administrator and the document owner. You have the option to add or remove anyone from the email notification.

In addition to an email, a user notification displays a policy tip:

- In Outlook and Outlook on the web.
- For the document on a SharePoint Online or OneDrive for Business site.
- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.

The email notification and policy tip provide the user with information about why the content conflicts with the DLP policy. The email notification and policy tip can allow the user to override the rule by reporting a false positive or by providing a business justification. This serves to educate the user about DLP without preventing them from getting work done.

## Grouping and logical operators

Some DLP policies are straightforward, for example, recognizing US Social Security Numbers. At other times, your DLP policy might need to recognize more loosely defined data. For example, if you need to identify content that is subject to the Health Insurance Portability and Accountability Act of 1996 (HIPAA), you would need to look for:

- Content that contains specific types of sensitive information, such as a U.S. Social Security Number or Drug Enforcement Agency (DEA) Number.

AND

- Content that's more difficult to identify, such as communications about a patient's care or descriptions of medical services provided. Identifying this content requires matching keywords from large keyword lists, such as the International Classification of Diseases (ICD-9-CM or ICD-10-CM).

By using logical operators (AND, OR), you more easily identify loosely defined data. You can choose  sensitive information types within a group and between groups.

:::image type="content" source="../media/2-content-contains-inline.png" lightbox="../media/2-content-contains-expanded.png" alt-text="Group conditions.":::

You can select either an operator (AND, OR) between groups to choose whether the conditions in just one or all of the groups must be satisfied for the content to match the rule. In the following example, content being identified comes from both personal data identifiers (at least on SSN OR DEA number) and content from the group Medical Terms (at least one ICD-9-CM keyword OR ICD-10-CM keyword).

:::image type="content" source="../media/2-operator-between-groups-inline.png" lightbox="../media/2-operator-between-groups-expanded.png" alt-text="Operator between groups.":::
