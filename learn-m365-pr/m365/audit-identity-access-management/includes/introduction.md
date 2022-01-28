In this module, you’ll learn how Microsoft 365 controls the access of service team engineers to protect customer data in the Microsoft 365 cloud environment.

The access controls used by Microsoft for operating Microsoft 365 fall into three categories:

| Isolation controls | Personnel controls | Technology controls |
|---|---|---|
| - Customer content isolated from service operations<br>- Task-based execution model with least privilege access<br>- Minimal human touch | - Background check and clearances<br>- Training<br>- Multiple levels of approval | - Zero standing access<br>- Just-In-Time (JIT)<br>- Just-Enough-Access (JEA)<br>- multifactor authentication<br>- Secure access workstations<br>- Logging and auditing |

Isolation controls are built into the architecture of Microsoft 365 Services. They ensure that customer content in a tenant is isolated both from other tenants and from operations and systems data used in the management of Microsoft 365. Isolation supports access control enforcement by preventing access to systems and data without proper authorization. Additionally, Microsoft 365 Services are designed to operate through automated service code. It minimizes the need for engineers to interact directly with production environments.

Personnel controls protect against insider threats and ensure adequate training for Microsoft personnel who support Microsoft 365 Services. The Identity Management Tool (IDM) enforces personnel control requirements before service team accounts can be created or access to any Microsoft 365 resources can be authorized.

Technology controls enable Microsoft to implement the principle of Zero Standing Access (ZSA) using Just-In-Time (JIT) and Just-Enough-Access (JEA). Multifactor authentication (MFA), Secure Access Workstations (SAWs), and centralizing logging and auditing provide extra technology-based protections against unauthorized access.

## Learn more

- [Microsoft 365 Isolation Controls](/microsoft-365/enterprise/microsoft-365-isolation-controls?azure-portal=true)
- [Human resources overview](/office365/Enterprise/office-365-personnel-controls?azure-portal=true)
