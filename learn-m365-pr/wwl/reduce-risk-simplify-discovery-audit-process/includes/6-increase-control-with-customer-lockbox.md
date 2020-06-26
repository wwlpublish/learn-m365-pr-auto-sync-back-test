Customer Lockbox supports requests to access data in Exchange Online, SharePoint Online, and OneDrive for Business. Customer Lockbox ensures that Microsoft can't access your content to perform a service operation without your explicit approval. Customer Lockbox brings you into the approval workflow for requests to access your content.

Occasionally, Microsoft engineers help troubleshoot and fix customer reported issues in the support process. Usually, issues are fixed through extensive telemetry and debugging tools Microsoft has in place for its services. However, some cases require a Microsoft engineer to access customer content to determine the root cause and fix the issue. Customer Lockbox requires the engineer to request access from the customer as a final step in the approval workflow. Which gives organizations the option to approve or deny these requests and provide direct-access control to the customer.

## Customer Lockbox workflow

The following steps outline the typical workflow when a Microsoft engineer initiates a Customer Lockbox request:

1. Someone at an organization experiences an issue with their Microsoft 365 mailbox. After the user troubleshoots the issue, but can't fix it, they open a support request with Microsoft Support.
1. A Microsoft support engineer reviews the service request and determines a need to access the organization's tenant to repair the issue in Exchange Online.
1. The Microsoft support engineer logs into the Customer Lockbox request tool and makes a data access request that includes the organization's tenant name, service request number, and the estimated time the engineer needs access to the data.
1. After a Microsoft Support manager approves the request, Customer Lockbox sends the designated approver at the organization an email notification about the pending access request from Microsoft.
1. The approver signs-in to the Microsoft 365 admin center and approves the request. This step triggers the creation of an audit record available by searching the audit log. If the customer rejects the request or doesn't approve the request within 12 hours, the request expires, and no access is granted to the Microsoft engineer.
1. After the approver from the organization approves the request, the Microsoft engineer receives the approval message, logs into the tenant in Exchange Online, and fixes the customer's issue. Microsoft engineers have the requested duration to fix the issue after which the access is automatically revoked.

:::image type="content" source="../media/6-lockbox-workflow.png" alt-text="Diagram showing the lockbox workflow: customer, Microsoft engineer, lockbox system, Microsoft manager, customer, and Microsoft engineer":::

All actions performed by a Microsoft engineer are logged in the audit log. You can search for and review these audit records.
