The records management solution in Microsoft 365 enables organizations to manage their high-value content for legal, business, or regulatory obligations. These organizations should use the following guidance to get started:

1.  Understand how retention and deletion works in Microsoft 365. Then identify whether you must use retention policies to supplement retention labels that manage documents and emails at the item level. If necessary, create retention policies for baseline governance of data across Microsoft 365 workloads.
2.  Understand the records management solution. Learn how retention labels can be used to allow or block actions when documents and emails are declared records.
3.  Create your file plan for retention and deletion settings and actions. Determine when items should be marked as records by importing an existing plan (if you already have one), or create new retention labels. For more information, see Use file plan to create and manage retention labels.
4.  Publish and apply your retention labels. Retention labels are reusable building blocks that can be used in multiple policies and can be incorporated into user workflows:
     -  Publish retention labels and apply them in apps.
     -  [Apply a retention label to content automatically](/microsoft-365/compliance/apply-retention-labels-automatically?azure-portal=true).

> [!NOTE]
> Retention labels, tags, and policies are covered in a later training module.

### Subscription and licensing requirements

Many different subscriptions support records management. The licensing requirements for users depend on the features you use.

 -  To see the options for licensing your users to benefit from Microsoft Purview features, see the [Microsoft 365 licensing guidance for security &amp; compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance?azure-portal=true).
 -  For records management, see the [Microsoft Purview Records Management](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management?azure-portal=true) section and related PDF download for feature-level licensing requirements.

### Permissions

An organization's compliance team members who are responsible for records management need permissions to the Microsoft Purview compliance portal. By default, the tenant admin (global administrator) has access to this location and can give compliance officers and other people access without giving them all the permissions of a tenant admin.

 -  To grant permissions for this limited administration, it's recommended that organizations add users to the Records Management admin role group. This role group grants permissions for all features related to records management, including [disposition review and verification](/microsoft-365/compliance/disposition?azure-portal=true).
 -  For a read-only role, you can create a new role group and add the View-Only Record Management role to this group.

These permissions are required only to create, configure, and apply retention labels that declare records, and manage disposition. The person configuring these labels doesn't require access to the content.

**Additional reading**. For instructions to add users to the default roles or create your own role groups, see [Permissions in the Microsoft Purview compliance portal](/microsoft-365/compliance/microsoft-365-compliance-center-permissions?azure-portal=true).

### Common records management scenarios and supporting documentation

An organization should use the following table to help map its business requirements to the scenarios that are supported by records management.

> [!TIP]
> Need to comply with a specific industry regulation? Check [Regulatory requirements for data lifecycle management and records management](/microsoft-365/compliance/retention-regulatory-requirements?azure-portal=true) for regulation-specific guidance.

| **I want to ...**                                                                                                                                                                   | **Documentation**                                                                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Declare a record.                                                                                                                                                                   | [Declare records by using retention labels](/microsoft-365/compliance/declare-records?azure-portal=true).                                                                |
| Update a record.                                                                                                                                                                    | [Use record versioning to update records stored in SharePoint or OneDrive](/microsoft-365/compliance/record-versioning?azure-portal=true).                               |
| Let admins and users manually apply retain and delete actions for documents and emails:<br>\- SharePoint<br>\- OneDrive<br>\- Outlook and Outlook on the web                        | [Publish retention labels and apply them in apps](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true).                                            |
| Let site admins set default retain and delete actions for all content in a SharePoint library, folder, or document set.                                                             | [Publish retention labels and apply them in apps](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true).                                            |
| Let users automatically apply retain and delete actions to emails by using Outlook rules.                                                                                           | [Publish retention labels and apply them in apps](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true).                                            |
| Let admins apply retain and delete actions to a document understanding model. By doing so, these actions are automatically applied to identified documents in a SharePoint library. | [Publish retention labels and apply them in apps](/microsoft-365/compliance/create-apply-retention-labels?azure-portal=true).                                            |
| Automatically apply retain and delete actions to documents and emails.                                                                                                              | [Apply a retention label to content automatically](/microsoft-365/compliance/apply-retention-labels-automatically?azure-portal=true).                                    |
| Start the retention period when an event occurs, such as:<br>\- Employees leave the organization.<br>\- Contracts expire.<br>\- End of product lifetime.                            | [Start retention when an event occurs](/microsoft-365/compliance/event-driven-retention?azure-portal=true).                                                              |
| Restrict changes to policies to help meet regulatory requirements or safeguard against rogue administrators.                                                                        | [Use Preservation Lock to restrict changes to retention policies and retention label policies](/microsoft-365/compliance/retention-preservation-lock?azure-portal=true). |
| Manage the lifecycle of different document types in SharePoint.                                                                                                                     | [Use retention labels to manage the lifecycle of documents stored in SharePoint](/microsoft-365/compliance/auto-apply-retention-labels-scenario?azure-portal=true).      |
| Apply a retention label to a file when I receive an alert that content containing personal data is being stored or remains untouched for too long.                                  | [Investigate and remediate alerts in Privacy Risk Management](/privacy/priva/risk-management-alerts?azure-portal=true).                                                  |
| Make sure somebody reviews and approves before content is deleted at the end of its retention period.                                                                               | [Disposition reviews](/microsoft-365/compliance/disposition?azure-portal=true).                                                                                          |
| Have proof of disposition for content that is permanently deleted at the end of its retention period.                                                                               | [Disposition of records](/microsoft-365/compliance/disposition?azure-portal=true#disposition-of-records?azure-portal=true).                                              |
| Monitor how and where retain and delete settings are applied to items.                                                                                                              | [Monitoring retention labels](/microsoft-365/compliance/retention?azure-portal=true#monitoring-retention-labels?azure-portal=true).                                      |

### End-user documentation

If you're using retention policies for baseline data governance, they typically work unobtrusively in the background without user interaction. As a result, they need little documentation for users. Retention policies for Teams inform users when their messages have been deleted with a link to [Teams messages about retention policies](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b?azure-portal=true).

In comparison, retention labels have a UI presence in Microsoft 365 apps. As a result, organizations should ensure they provide guidance for end users and their help desk before these labels are deployed to their production networks. To help users apply retention labels in SharePoint and OneDrive, and information about unlocking records for editing, see [Apply retention labels to files in SharePoint or OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df?azure-portal=true).

However, the most effective end-user documentation will be customized guidance and instructions that organizations provide for the retention label names and configurations they choose. For more information that you can use to help train your users, see [End User Training for Retention Labels](https://microsoft.github.io/ComplianceCxE/enduser/retention?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”