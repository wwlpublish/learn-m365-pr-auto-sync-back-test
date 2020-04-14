Administrators often carry out privileged operations in Azure AD, Office 365, or in other SaaS apps. As a result, many organizations grant administrators permanent privileged access in Azure AD. This creates a security risk for cloud resources because organizations have difficulty monitoring how these administrators use their access privileges. Additionally, if a privileged access account is compromised, the organization's overall cloud security is at risk.

Consider this example. As a Contoso executive, Christina, has administrator privileges. She occasionally needs to access the HR database to review the personnel records of her direct reports. If someone steals her credentials, that information is at risk. You must increase security measures on Christina’s account to protect employee data against unauthorized access.

### Methods for enhancing security

![Concentric circles represent security layers surrounding administrator account.](../media/layered-approach-to-secure-admin-accounts.png)

*The Microsoft 365 layered approach to securing administrator accounts*

Microsoft 365 enables you to manage, control, and monitor access to privileged accounts. Its security architecture provides an integrated and layered approach to access management. The following are best practices.

- **Protect at the role level.** Use Azure AD Privileged Identity Management to apply protection at the role level while allowing administrators to perform multiple tasks.
- **Protect at the task level.** Use privileged access management to control access to data at the task level.
- **Secure devices.** Set Conditional Access policy to require that devices that administrators use are compliant and patched with the most recent software and antivirus definitions.
- **Isolate identities.** Create dedicated accounts for users with administrative privileges that are separate from those users’ information worker identities.

The remainder of this module looks at each of these methods in more detail.
