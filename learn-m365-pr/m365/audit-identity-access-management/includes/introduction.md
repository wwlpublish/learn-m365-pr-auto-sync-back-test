In this module, you will learn how Microsoft 365 controls Service Team engineers’ access to protect customer data in the Microsoft 365 cloud environment.

The access controls used by Microsoft for operating Microsoft 365 fall into three categories:

| Isolation controls | Personnel controls | Technology controls |
|---|---|---|
| - Customer content isolated from service operations<br>- Task-based execution model with least privilege access<br>- Minimal human touch | - Background check and clearances<br>- Training<br>- Zero standing access<br>- Multiple levels of approval | - Just-In-Time (JIT)<br>- Just-Enough-Access (JEA)<br>- Multi-factor authentication<br>- Secure access workstations<br>- Logging and auditing |

Isolation controls are built into the architecture of Microsoft 365 Services. They ensure that customer content in a tenant is isolated both from other tenants and from operations and systems data used in the management of Microsoft 365. Isolation supports access control enforcement by preventing access to systems and data without proper authorization. In addition, Microsoft 365 Services is designed to be operated through automated service code. This minimizes the need for engineers to interact directly with production environments.

Personnel controls protect against insider threats and enforce separation of duties. They also ensure adequate training for Microsoft personnel who support Microsoft 365 Services. The Identity Management Tool (IDM) enforces personnel control requirements before allowing creation of service team accounts or authorizing access to any Microsoft 365 resources.

Technology controls enable Microsoft to implement the principle of Zero Standing Access (ZSA) using Just-In-Time (JIT) and Just-Enough-Access (JEA). Multi-factor authentication (MFA), Secure Access Workstations (SAWs), and centralizing logging and auditing provide additional technology-based protections against unauthorized access.

## Learn more ##

- [Office 365 Technology Controls](https://docs.microsoft.com/office365/Enterprise/office-365-technology-controls?azure-portal=true)
- [Office 365 Personnel Controls](https://docs.microsoft.com/office365/Enterprise/office-365-personnel-controls?azure-portal=true)
