An organization can use Customer Lockbox requests to control how a Microsoft support engineer accesses the company's data. Sometimes an organization may run into an issue that requires a Microsoft support engineer to help fix it. In some cases, the support engineer will require access to the company's Microsoft 365 data to troubleshoot and fix the issue. Customer Lockbox requests enable an organization to control whether to give the support engineer access to its data. There's also an expiration time on the request, and content access is removed after the support engineer has fixed the issue.

> [!IMPORTANT]
> Customer Lockbox functionality is only used when troubleshooting requires access to an organization's Microsoft 365 content. For most support cases, resolution doesn't require the use of Customer Lockbox access.

Customer Lockbox is included in the Office 365 Enterprise E5 plan.

### Example of Customer Lockbox request

The following steps provide an overview of the Customer Lockbox process:

1.  Someone at Contoso has an issue with their Microsoft 365 mailbox.
2.  After the IT staff has finished troubleshooting, it realizes that it can't fix the issue. At this point, the IT department opens a support request with Microsoft support.
3.  The Microsoft support engineer reviews the service request and determines they need access to Contoso's Exchange Online content to repair the issue.
4.  The Microsoft support engineer logs into the Customer Lockbox request tool and sends an email to Contoso's Enterprise Administrator. The email informs the admin there's a pending Customer Lockbox request. All requests are reviewed and approved by Microsoft support managers before Contoso receives the request.
5.  The Customer Lockbox request tool sends the Enterprise Administrator an email letting them know there's a pending lockbox request. If the Enterprise Admin rejects or doesn't approve the request in 12 hours, access is automatically revoked.
6.  The Enterprise Admin logs into the Microsoft 365 admin center and approves the request. Keep in mind that no links are included in the Customer Lockbox email that require the Enterprise Admin to sign into Microsoft 365.
7.  The Microsoft support engineer gets the approval message, logs into Exchange Online, and fixes the issue. Once the Microsoft support engineer starts the process, they have four hours to fix the issue before access is revoked.
8.  As soon as the issue is fixed, the Customer Lockbox request is closed. The Microsoft support engineer's access is then revoked.
