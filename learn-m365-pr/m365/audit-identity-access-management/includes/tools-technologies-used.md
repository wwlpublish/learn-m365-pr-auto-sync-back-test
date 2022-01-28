Microsoft 365 uses a variety of tools and technologies to keep service team accounts secure. In this unit, we'll review some of these tools to lay the foundation for discussing how Microsoft enforces Zero Standing Access (ZSA).

## Identity Management Tool (IDM)

Microsoft 365 uses an account management system called Identity Management Tool (IDM) to track service team accounts through their lifecycle. IDM automatically tracks the status of all service team accounts, from the initial account request through eligibility verification, approval, creation, modification, and disablement when the account is no longer necessary.

Before a new service team account can be created, IDM ensures all eligibility requirements have been met. These requirements include personnel screening, security and privacy training, and appropriate manager approval. IDM also notifies managers for approval whenever account modifications are requested. When an employee is transferred, terminated, or fails to complete required training, IDM automatically revokes access for their service team account and notifies their manager.

Automation is at the heart of how we provide security at scale. The bulk of account management is automated by IDM. IDM automatically disables service team accounts after no more than 90 days of inactivity. In addition, service team accounts that exceed the failed sign-in attempt threshold are automatically locked. Service team accounts are audited automatically throughout their lifecycle. Manual access reviews are an exception. Where they do occur, Microsoft 365 service teams carry them out at least quarterly.

## Role-based access control (RBAC)

Microsoft 365 service teams use Role-Based Access Control (RBAC) enforced by Active Directory (AD) and Azure Active Directory (AAD). Service team personnel request access to required roles, subject to management approval. If approved, they’re placed in security groups corresponding to their roles for supporting the system.

Service team account access is managed according to the principle of least privilege. RBAC limits service team accounts to only the access necessary to complete required tasks in environments corresponding to their role. RBAC also helps to enforce separation of duties requirements by limiting service team accounts to roles appropriate for their current responsibilities.

## Remote access

Microsoft 365 system components are housed in datacenters geographically separated from the operations teams. Datacenter personnel have physical access but don’t have logical access to the Microsoft 365 environment. Alternately, service team personnel have logical access, but don’t have physical access. As a result, service team personnel manage the environment through remote access. All approved activities are authorized for execution via remote access to the Microsoft 365 environment. Service team personnel who require remote access to support Microsoft 365 are only granted remote access after approval from an authorized manager. All remote access uses FIPS 140-2 compatible TLS for secure remote connections.

## Secure Access Workstations (SAWs)

Microsoft 365 issues Secure Access Workstations (SAWs) to service team engineers who support production Microsoft 365 environments. SAWs provide increased security by reducing the attack surface of the devices engineers use to perform administrative actions when supporting Microsoft 365 services.

SAWs at Microsoft are specially designed and manufactured laptops with extra protections against hardware and software vulnerabilities. Microsoft partners directly with trusted suppliers to build SAWs, shortening the supply chain to ensure the security of SAW hardware. Hardened operating systems with deliberately limited functionality further mitigate or eliminate common attack vectors. SAW hardening practices include disabling writing to USB drives, enforcing strict application whitelisting, removing productivity suites and email access, limiting internet browsing, forcing use of a hardened browser, routing traffic through a proxy filter, and enforcing inactivity screensaver lockouts through Group Policy.

Microsoft 365 access control systems automatically check the health of an engineer's SAW at time of access and refuse connections from non-compliant SAWs. Device health checks complement other access controls, including IP restrictions, IPsec policies, and user identify verification through multi-factor authentication. SAW usage is strictly monitored and logged to detect and prevent unauthorized use. Non-compliant devices are automatically disabled.

## Multi-factor authentication (MFA)

Microsoft 365 requires multi-factor authentication (MFA) for all service team accounts. MFA increases account security by requiring multiple forms of verification, or factors, to prove an engineer's identity when signing into the system. The types of factors that can be used for MFA fall into three categories:

- Something you know – a password, an answer to a security question, or a Personal Identification Number (PIN)
- Something you have –a security token generator or a mobile app that receives a notification
- Something you are – a biometric property, such as a fingerprint or face scan

Microsoft 365 requires at least two factors for MFA. Using MFA increases the security of Microsoft 365 by limiting the impact of credential exposure. In Microsoft 365, an attacker who compromises a user's password would also need possession of their security token generator to fully authenticate. Authentication with only a single factor is insufficient for access to Microsoft 365, locking out potential attackers and providing time for the user to change their compromised password.

## Learn more

- [Multi-factor authentication for Microsoft 365](/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365?azure-portal=true)
