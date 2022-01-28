>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xda3]

Customer Lockbox ensures that Microsoft cannot access an organization's tenant to perform a service operation without the customer's explicit approval. service team engineers at Microsoft often help troubleshoot and fix technical issues reported by customers. Our engineers are sometimes able to resolve issues through the extensive telemetry and debugging tools Microsoft has in place for its services. However, some issues may require a service team engineer to access the customer's tenant to determine the root cause and fix the issue. Customer Lockbox requires the service team engineer to request access from the customer and provides customers with the option to approve or deny these access requests. This puts access control directly in the hands of the customer.

The following diagram illustrates the Customer Lockbox workflow when a customer experiences an issue in Microsoft 365 that requires a service team engineer to access the customer's tenant.

:::image type="content" source="../media/customer-lockbox-diagram.png" alt-text="Customer Lockbox workflow diagram, explanation to follow":::

1. When a customer troubleshoots an issue but is unable to fix it, the customer can open a support request with Microsoft Support.

2. A service team engineer reviews the support request and determines if the request requires access to the customer's tenant to resolve the issue.

3. If access to the customer tenant is necessary, the service team engineer logs into the Customer Lockbox request tool and makes a data access request. The request includes the customer's tenant name, service request number, and the estimated time the engineer needs access to the data. Currently, the maximum period allowed for access permissions granted through Customer Lockbox is 4 hours. The engineer can request a shorter period.

4. If a Microsoft Support manager approves the request, Customer Lockbox sends the customer's designated approver an email notification about the pending access request from Microsoft. Customer accounts with the global administrator role or the Customer Lockbox access approver admin role in the Microsoft 365 admin center can approve Customer Lockbox requests. The default duration for a customer to respond to a Customer Lockbox request is 12 hours. If the customer does not respond to a request within this period, the request expires without granting access to the service team engineer.

5. If the customer approver decides to grant access, they sign into the Microsoft 365 admin center and approve the request. This step triggers the creation of an audit record, which is made available to the customer in the audit log if the customer has enabled audit logging. Actions performed by the service team engineer are also logged in the audit log.

6. After receiving approval from the customer approver, the service team engineer is granted access. The engineer can then log into the customer's tenant in Microsoft 365 Services and resolve the customer's issue. When the period approved for access expires, access is automatically revoked.

## Learn more

- [Customer Lockbox FAQ](/microsoft-365/compliance/customer-lockbox-requests?azure-portal=true)
