The following table provides an overview of the Enterprise Mobility + Security components included with Microsoft 365 Enterprise. It also introduces the core concepts necessary to understand how to best use Microsoft 365 component services for your organizational needs. These services provide capabilities that enable Microsoft cloud enterprise administrators to not just protect company employees’ identities and devices, but also control access to company data itself - both in transit and at rest.

:::row:::
  :::column:::
    <p><b>Service</b></p>
  :::column-end:::
  :::column:::
    <p><b>Description</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-whatis?azure-portal=true">Microsoft Azure Active Directory</a></p>
  :::column-end:::
  :::column:::
    <p>Azure AD provides a full suite of identity management capabilities including multi-factor authentication, device registration, self-service password management, self-service group management, role-based access control, application usage monitoring, rich auditing, and security monitoring and alerting. Azure AD includes the following premium editions:</p>  
  - **Azure AD Premium P1.** This enterprise-level edition provides identity management for on-premises users, remote users, and hybrid users accessing applications both locally and over the cloud. This edition includes support for self-service identity, access management, administration of dynamic groups including self-service group management, and Microsoft Identity Manager, which is a suite of on-premise identity and access management tools.
  - **Azure AD Premium P2.** This edition includes all of the features of Azure AD Premium P1, plus Azure AD Identity Protection and Azure AD Privileged Identity Management, each of which is described below.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection?azure-portal=true">Azure AD Identity Protection</a></p>
  :::column-end:::
  :::column:::
    <p>This service enables you to detect potential vulnerabilities affecting your organization's identities and configure automated responses through conditional access policies to low, medium, and high sign-in risk and user risk.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><a href="https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure?azure-portal=true">Azure AD Privileged Identity Management</a></p>
  :::column-end:::
  :::column:::
    <p>Azure AD Privileged Identity Management enables organizations to minimize the number of people who have persistent access to privileged operations. This service introduces the concept of an eligible administrator. Eligible admins should be users that need privileged access now and then, but not every day. The role is inactive until the user needs access, at which point they must complete an activation process and become an active admin for a predetermined amount of time.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><a href="https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection?azure-portal=true">Azure Information Protection</a></p>
  :::column-end:::
  :::column:::
    <p>Azure Information Protection (AIP) is a cloud-based solution that is delivered as part of the Mobility + Security E3 and E5 subscriptions. AIP helps organizations classify, label, and protect their documents and emails, all of which can be done automatically by administrators who define rules and conditions, manually by users, or a combination where users are given recommendations. You use Azure Information Protection labels to apply classification to documents and emails. When using AIP labels, the classification is always identifiable, regardless of where the data is stored or with whom it’s shared. AIP policy settings are protected by <a href="https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms?azure-portal=true">Azure Rights Management</a>. Protection that's applied by using Rights Management is similar to how the labels are applied; that is, it stays with the documents and emails independently of the location—inside or outside your organization, networks, file servers, and applications.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><a href="https://www.microsoft.com/en-us/microsoft-365/enterprise-mobility-security/microsoft-intune?azure-portal=true">Microsoft Intune</a></p>
  :::column-end:::
  :::column:::
    <p>Intune is a cloud-based Enterprise Mobility Management (EMM) service that enables an organization’s workforce to be productive while keeping its corporate data protected. Intune integrates closely with Azure AD for identity and access control and is used for device and application management. <a href="https://docs.microsoft.com/mem/intune/fundamentals/what-is-device-management?azure-portal=true">Intune's device management</a> capabilities are used to configure and protect user's devices, including Windows PCs. Intune device management capabilities support both <a href="https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-byod?azure-portal=true">Bring Your Own Device (BYOD)</a> enrollment, which lets users enroll their personal phones, tablets, or PCs, and <a href="https://docs.microsoft.com/enterprise-mobility-security/solutions/issue-corp-devices?azure-portal=true">Corporate-owned Device (COD)</a> enrollment, which enables management scenarios like automatic enrollment, shared devices, and pre-authorized enrollment requirement configurations. For added security, organizations can even require Multi-Factor Authentication to enroll a device. Once enrolled into management, Intune can configure device features and settings to enable secure access to company resources.</p>
  :::column-end:::
:::row-end:::

Choose the best response for the following question. Then select “Check your answers.”