The following table provides an overview of the Enterprise Mobility + Security components included with Microsoft 365 Enterprise. It also introduces the core concepts necessary to understand how to best use Microsoft 365 component services for your organizational needs. These services provide capabilities that enable Microsoft cloud enterprise administrators to not just protect company employees’ identities and devices, but also control access to company data itself - both in transit and at rest.

:::row:::
  :::column:::
    

**Service**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

[Microsoft Azure Active Directory](/azure/active-directory/active-directory-whatis)


  :::column-end:::
  :::column:::
    

Azure Active Directory (Azure AD) provides a full suite of identity management capabilities including multi-factor authentication, device registration, self-service password management, self-service group management, role-based access control, application usage monitoring, rich auditing, and security monitoring and alerting. Azure AD includes the following premium editions:

 -  **Azure AD Premium P1.** This enterprise-level edition provides identity management for on-premises users, remote users, and hybrid users accessing applications both locally and over the cloud. This edition includes support for self-service identity, access management, administration of dynamic groups including self-service group management, and Microsoft Identity Manager, which is a suite of on-premise identity and access management tools.
 -  **Azure AD Premium P2.** This edition includes all of the features of Azure AD Premium P1, plus Azure AD Identity Protection and Azure AD Privileged Identity Management, each of which is described below.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

[Azure AD Identity Protection](/azure/active-directory/active-directory-identityprotection)


  :::column-end:::
  :::column:::
    

This service enables you to detect potential vulnerabilities affecting your organization's identities and configure automated responses through conditional access policies to low, medium, and high sign-in risk and user risk.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

[Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure)


  :::column-end:::
  :::column:::
    

Azure AD Privileged Identity Management enables organizations to minimize the number of people who have persistent access to privileged operations. This service introduces the concept of an eligible administrator. Eligible admins should be users that need privileged access now and then, but not every day. The role is inactive until the user needs access, at which point they must complete an activation process and become an active admin for a predetermined amount of time.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

[Azure Information Protection](/information-protection/understand-explore/what-is-information-protection)


  :::column-end:::
  :::column:::
    

Azure Information Protection (AIP) is a cloud-based solution that is delivered as part of the Mobility + Security E3 and E5 subscriptions. AIP helps organizations classify, label, and protect their documents and emails, all of which can be done automatically by administrators who define rules and conditions, manually by users, or a combination where users are given recommendations. You use Azure Information Protection labels to apply classification to documents and emails. When using AIP labels, the classification is always identifiable, regardless of where the data is stored or with whom it’s shared. AIP policy settings are protected by [Azure Rights Management](/information-protection/understand-explore/what-is-azure-rms). Protection that's applied by using Rights Management is similar to how the labels are applied; that is, it stays with the documents and emails independently of the location—inside or outside your organization, networks, file servers, and applications.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

[Microsoft Intune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune?azure-portal=true)


  :::column-end:::
  :::column:::
    Intune is a cloud-based Enterprise Mobility Management (EMM) service that enables an organization’s workforce to be productive while keeping its corporate data protected. Intune integrates closely with Azure AD for identity and access control and is used for device and application management. [Intune's device management](/mem/intune/fundamentals/what-is-device-management) capabilities are used to configure and protect user's devices, including Windows PCs. Intune device management capabilities support both [Bring Your Own Device (BYOD)](/enterprise-mobility-security/solutions/enable-byod) enrollment, which lets users enroll their personal phones, tablets, or PCs, and [Corporate-owned Device (COD)](/enterprise-mobility-security/solutions/issue-corp-devices) enrollment, which enables management scenarios like automatic enrollment, shared devices, and pre-authorized enrollment requirement configurations. For added security, organizations can even require Multi-Factor Authentication to enroll a device. Once enrolled into management, Intune can configure device features and settings to enable secure access to company resources.
  :::column-end:::
:::row-end:::


## Knowledge check<br>

Choose the best response for the following question. Then select “Check your answers.”