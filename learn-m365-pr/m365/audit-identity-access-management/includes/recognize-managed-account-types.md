At Microsoft, we mitigate the risks associated with privileged accounts through the principle of Zero Standing Access (ZSA). It enables Microsoft to operate its services without persistent privileged user accounts. Combined with Just-In-Time (JIT) and Just-Enough-Access (JEA), ZSA provides a robust framework for safeguarding customer data.
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xq8i]

Microsoft 365 has identified three categories of accounts to support organizational missions and business functions: service team accounts, service accounts, and customer accounts. Two of these categories, service team accounts and service accounts, are managed by Microsoft and enable us to operate and support our products and services. The third category, customer accounts, are managed by the customer and give customers the flexibility to meet their internal access control requirements.

> [!div class="centered"]
> :::image type="content" source="../media/shared-responsibility-accounts.png" alt-text="A visual representation of shared responsibility in managing accounts. Two account types: service team accounts and service accounts are managed by Microsoft. Customer accounts are managed by customers." border = "false":::

## Microsoft-managed accounts

Microsoft directly manages two categories of accounts: service team accounts and service accounts.

**Service team accounts** are used by individual Microsoft personnel charged with developing, maintaining, and repairing core Microsoft 365 services. Access rights are granted to service team accounts using Role-Based Access Control (RBAC). RBAC enforces separation of duties and ensures team members have only the minimum access required to perform specific activities approved by an authorized approver.

**Service accounts** are also managed by Microsoft but aren’t assigned to individual Microsoft personnel. Instead, service accounts are used by Microsoft 365 services to authenticate to servers and other services within the Microsoft cloud environment. These accounts cannot be accessed by Microsoft personnel and are only used by automated processes to operate our products and services.

## Customer-managed accounts

In cloud environments, customers and cloud service providers share the responsibility for achieving a compliant and secure computing environment. Microsoft uses [a shared responsibility model](/azure/security/fundamentals/shared-responsibility?azure-portal=true) to define security and operational accountability in Microsoft 365 services. While Microsoft 365 secures the underlying cloud infrastructure and services, customers need to be aware of their responsibilities for ensuring a secure tenant environment for their users and data. In the context of privileged access management, customers are responsible for provisioning and managing customer accounts within their Microsoft 365 tenant.

Customers manage access control within their Microsoft 365 tenant using **customer accounts**. Customer accounts allow customer-defined users to access Microsoft 365 services. These accounts can be provisioned by the customer in Azure Active Directory (AAD) or federated with on-premises Active Directory (AD). Customer-managed accounts provide customers with the flexibility to meet their organization's access control requirements for their users. Customer accounts can’t be used to access data outside the customer's tenant.

Let's explore how Microsoft manages service team accounts to protect Microsoft 365 services and customer data.
