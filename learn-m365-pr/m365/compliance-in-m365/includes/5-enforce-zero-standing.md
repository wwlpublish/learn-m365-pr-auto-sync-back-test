Organizations are twice as likely to get breached through compromised credentials than through any other threat vector. All that's needed to expose data and inflict damage is perpetual or standing privileged access to an application. Increasingly regulators and customers expect you to carefully document (including an audit trail) when you grant privileged access. One way to address this is by adopting *zero standing access* - users don't get permissions by default to perform privileged tasks or access sensitive data on their own. 

## Customer Lockbox for Office 365
Microsoft runs organizations and datacenters on the principle of zero standing **admin** access. When required, all access requests go through a privileged access workflow, allowing users just-in-time and just-enough access for the specific task they need to perform. These  requests require approvals and significant oversight.

Another tool Microsoft offers to control access is Customer Lockbox. Customer Lockbox requires the tenant admin (or a custom role like the compliance manager) to approve a request before access to your datacenter is granted to Microsoft engineers. The transparency, control, and security rigor provided through this Customer Lockbox workflow is above and beyond what other major SaaS vendors offer today. 

![Access request flow for Customer Lockbox](../media/5-customer-lockbox.png)
*Customer Lockbox workflow*

Together, these controls enable you and Microsoft engineers to enforce zero standing access by default for service provider access, which is a significant leap in keeping our datacenters and your data secure and compliant. 

## Privileged access management in Office 365
Taking all the learnings from how Microsoft manages its own datacenter, Office 365 has built a similar privileged access management system to help you manage privileged admin access to your users, typically the tenant admins. This system requires your users to request just-in-time and just-enough access to perform the tasks at hand. 

With privileged access management in Office 365, access requests must be approved by an authorized set of approvers. You can configure whether access requests are automatically or manually approved. Either way, all the activity is logged and auditable, so that both requests and approvals can be reviewed and documentation provided for internal reviews and auditor requests.


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrzxn]
