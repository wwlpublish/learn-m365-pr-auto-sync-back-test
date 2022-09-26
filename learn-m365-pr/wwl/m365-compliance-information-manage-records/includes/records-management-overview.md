Many principles of the solution for Data Lifecycle Management also apply for Microsoft Purview Records Management, but there are some differences. Those differences include file plan, record declaration, and record versioning.

> [!NOTE]
> Records management is included with Microsoft 365 E5/A5/G5, Microsoft 365 E5/A5/G5/F5 Compliance and F5 Security & Compliance, Microsoft 365 Information Protection and Governance E5/A5/G5, and Office 365 E5/A5/G5.
>
> Please review Microsoft 365 licensing guidance for security and compliance to identify the required licenses for your organization.

## File plan

Records management introduces the concept of a file plan. A file plan specifies how your records are organized and their retention schedule. You can create your own retention labels or import them into your file plan, and author policies to publish or auto-apply the labels to your content.

## Record declaration

How you declare an item as a record  is at the heart of Microsoft Purview Records Management. You can determine where, when, and how your records are retained, and attend to new and pending disposition alerts. An item declared as a record becomes immutable and cannot be modified (except for the name and metadata in SharePoint Online and OneDrive), or deleted until after the retention period.

## Record versioning

Record versioning in SharePoint Online and OneDrive lets you work on a document, even after it has been declared as a record. For example, you might want to declare a specific revision of a document as a record but then make additional modifications. Record versioning is automatically available for any document with a retention label that declares the item as a record.

## Customer scenarios

Here are some common scenarios that Microsoft Purview Records Management can address:

- Delete employee reviews 10 years after the employee has left the organization.
- Declare a contract as a record to prevent it from being changed.  

## Getting started with Microsoft Purview Records Management

Careful planning should be a part of each information protection and governance solution, and this is especially true of Microsoft Purview Records Management. This section includes general guidance on where to start with records management. It isn't meant to be a substitute for developing a more thorough plan that involves subject matter experts and stakeholders.

Many organizations already have a file plan that includes a retention schedule. They'll make this   the first step to get started with Microsoft Purview Records Management. Organizations that don't have a file plan should start by developing one. Microsoft includes a template and wizard that simplifies the process of importing your file plan into Microsoft 365.

Here are some common items a typical file plan includes:

- Content your organization needs to declare as records for legal, regulatory, compliance, business, or other reasons.
- Format of the content to be kept as records.
- Sorting of the documents into broad categories based on business requirements.
- Locations where records are stored.
- Create a records retention period.
- How records should be disposed of after a retention period.
- Responsible party for managing different types of records.

## Learn more

- [Microsoft Purview Records Management](/microsoft-365/compliance/records-management)
- [Overview of records](/microsoft-365/compliance/records-management)
- [Microsoft 365 security & compliance licensing guidance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)
- [Records management licensing guidance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management)
