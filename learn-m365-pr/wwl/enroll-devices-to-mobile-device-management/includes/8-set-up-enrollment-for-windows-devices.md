The purpose of this unit is to help administrators simplify Windows enrollment for their users. Once Intune has been set up, users enroll Windows devices by signing in with their work or school account. As an Intune admin, enrollment can be simplified in the following ways:

 -  Enable automatic enrollment (Azure AD Premium required).
 -  CNAME registration.
 -  Enable bulk enrollment (Azure AD Premium and Windows Configuration Designer required).

Two factors that organizations should consider to help simplify Windows device enrollment:

 -  **Do you use Azure Active Directory Premium?** [Azure AD Premium](/azure/active-directory/active-directory-get-started-premium?azure-portal=true) is included with Enterprise Mobility + Security and other licensing plans.
 -  **What versions of Windows clients will users enroll?** Devices running Windows 10 or 11 can automatically enroll by adding a work or school account. Devices running earlier versions must enroll using the Company Portal app.

|                              | **Azure AD Premium** | **Other AD**    |
| ---------------------------- | -------------------- | --------------- |
| **Windows 10/11**            | Automatic enrollment | User enrollment |
| **Earlier Windows versions** | User enrollment      | User enrollment |

Organizations that use automatic enrollment can also configure [bulk enroll devices](/mem/intune/enrollment/windows-bulk-enroll?azure-portal=true) by using the Windows Configuration Designer app.

Before an administrator can enroll devices to Intune for management, licenses should have already been assigned to the administrator's account. For more information, see [Assigning licenses for device enrollment](/mem/intune/fundamentals/licenses-assign?azure-portal=true).

Organizations can also let unlicensed admins sign in to MEM. For more information, see [Unlicensed admins](/mem/intune/fundamentals/unlicensed-admins?azure-portal=true).

### Multi-user support

Intune supports multiple users on:

 -  Devices that run Windows 10 or 11 Creator's update.
 -  Devices that are Azure Active Directory domain-joined.

When standard users sign in with their Azure AD credentials, they receive apps and policies assigned to their user name. Only the device's [Primary user](/mem/intune/remote-actions/find-primary-user?azure-portal=true) can use the Company Portal for self-service scenarios like installing apps and device actions (like Remove or Reset). For shared Windows 10/11 devices that don't have a primary user assigned, the Company Portal can still be used to install Available apps.

### Enable Windows automatic enrollment

Automatic enrollment lets users enroll their Windows devices in Intune. To enroll, users add their work account to their personally owned devices or join corporate-owned devices to Azure Active Directory. In the background, the device registers and joins Azure Active Directory. Once registered, the device is managed with Intune.

Prerequisites to Windows automatic enrollment include:

 -  Azure Active Directory Premium subscription
 -  Microsoft Intune subscription
 -  Global Administrator permissions

#### Configure automatic MDM enrollment

1.  Sign in to the Azure portal.
2.  In the **Azure Active Directory admin center**, select **Azure Active Directory** in the navigation pane.
3.  On the **Azure Active Directory** page, select **Mobility (MDM and MAM)** in the middle navigation pane.
4.  On the **Mobility (MDM and MAM)** page, select **Microsoft Intune**.
5.  On the **Microsoft Intune** page, select **Configure** in the navigation pane.
6.  On the **Configure** page, update the **MDM User scope field**. Select one of the following options that specifies which users' devices should be managed by Microsoft Intune. These Windows 10 and 11 devices can automatically enroll for management with Microsoft Intune.
     -  **None**. MDM automatic enrollment disabled.
     -  **Some**. Select the Groups that can automatically enroll their Windows 10 devices.
     -  **All**. All users can automatically enroll their Windows 10 devices.
    
    For Windows BYOD devices, the **MAM user scope** takes precedence if both the **MAM user scope** and the **MDM user scope** (automatic MDM enrollment) are enabled for all users (or the same groups of users). The device won't be MDM enrolled, and Windows Information Protection (WIP) Policies will be applied if you've configured them.
    
    If your intent is to enable automatic enrollment for Windows BYOD devices to an MDM: configure the **MDM user scope** to **All** (or **Some**, and specify a group) and configure the MAM user scope to **Non**e (or **Some**, and specify a group – ensuring that users aren't members of a group targeted by both MDM and MAM user scopes).
    
    For [corporate devices](/mem/intune/enrollment/enrollment-restrictions-set#blocking-personal-windows-devices?azure-portal=true), the **MDM user scope** takes precedence if both MDM and MAM user scopes are enabled. The device will get automatically enrolled in the configured MDM.

    > [!NOTE]
    > **MDM user scope** must be set to an Azure AD group that contains user objects.

7.  Use the default values for the following MDM URLs:
     -  MDM Terms of use URL
     -  MDM Discovery URL
     -  MDM Compliance URL
8.  Select **Save**.

By default, multi-factor authentication (MFA) isn't enabled for the service. However, MFA is recommended when registering a device. To enable MFA, an organization should configure a multi-factor authentication provider in Azure AD. It should then configure its user accounts for MFA. For more information, see [Getting started with the Azure Active Directory Multi-Factor Authentication Server](/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud?azure-portal=true).

### Simplify Windows enrollment without Azure AD Premium

To simplify enrollment, organizations can create a domain name server (DNS) alias (CNAME record type) that redirects enrollment requests to Intune servers. Otherwise, users trying to connect to Intune must enter the Intune server name during enrollment. The following two sections identify the steps required to CNAME DNS record.

#### Step 1: Create CNAME (optional)

The first step in this process is to create CNAME DNS resource records for the company's domain. For example, if a company's website is contoso.com, it would create a CNAME record in DNS that redirects **EnterpriseEnrollment.contoso.com** to **enterpriseenrollment-s.manage.microsoft.com**.

Although creating CNAME DNS entries is optional, CNAME records make enrollment easier for users. If no enrollment CNAME record is found, users are prompted to manually enter the MDM server name, **enrollment.manage.microsoft.com**.

| **Type** | **Host name**                              | **Points to**                               | **TTL**  |
| -------- | ------------------------------------------ | ------------------------------------------- | -------- |
| CNAME    | EnterpriseEnrollment.company\_domain.com   | EnterpriseEnrollment-s.manage.microsoft.com | One hour |
| CNAME    | EnterpriseRegistration.company\_domain.com | EnterpriseRegistration.windows.net          | One hour |

If the company uses more than one UPN suffix, it must create one CNAME for each domain name and point each one to **EnterpriseEnrollment-s.manage.microsoft.com**. For example, users at Contoso could use the following formats as their email/UPN:

 -  name@contoso.com
 -  name@us.contoso.com
 -  name@eu.contoso.com

The Contoso DNS admin should create the following CNAME records:

| **Type** | **Host name**                       | **Points to**                               | **TTL**  |
| -------- | ----------------------------------- | ------------------------------------------- | -------- |
| CNAME    | EnterpriseEnrollment.contoso.com    | EnterpriseEnrollment-s.manage.microsoft.com | One hour |
| CNAME    | EnterpriseEnrollment.us.contoso.com | EnterpriseEnrollment-s.manage.microsoft.com | One hour |
| CNAME    | EnterpriseEnrollment.eu.contoso.com | EnterpriseEnrollment-s.manage.microsoft.com | One hour |

> [!NOTE]
> **EnterpriseEnrollment-s.manage.microsoft.com** supports a redirect to the Intune service with domain recognition from the email's domain name.

Changes to DNS records can take up to 72 hours to propagate. An organization can't verify the DNS change in Intune until the DNS record propagates.

#### Step 2: Verify CNAME (optional)

1.  In the **Microsoft Endpoint Manager admin center**, select **Devices** in the navigation pane.
2.  On the **Devices** page, select **Windows** in the navigation pane.
3.  On the **Windows** page, select **Windows enrollment**.
4.  On the **Windows enrollment** page, select **CNAME Validation**.
5.  On the **CNAME validation** page, in the **Domain** field, enter the company website and then select **Test**.

### Endpoints that aren't supported

**EnterpriseEnrollment-s.manage.microsoft.com** is the preferred FQDN for enrollment. There are two other endpoints that have been used previously and still work. However, they're no longer supported:

 -  EnterpriseEnrollment.manage.microsoft.com (without the -s)
 -  manage.microsoft.com

Both work as the target for the auto-discovery server, but the user will have to select **OK** on a confirmation message. If you point to **EnterpriseEnrollment-s.manage.microsoft.com**, the user won't have to do another confirmation step. As such, using **EnterpriseEnrollment-s.manage.microsoft.com** is the recommended configuration.

### Alternate methods of redirection aren't supported

Using a method other than the CNAME configuration isn't supported. For example, using a proxy server to redirect enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc to either enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc or manage.microsoft.com/EnrollmentServer/Discovery.svc isn't supported.

### Tell users how to enroll Windows devices

Organizations must tell their users how to enroll their Windows devices and what to expect after they're brought into management.

> [!NOTE]
> End users must access the Company Portal website through Microsoft Edge to view Windows apps that they've assigned for specific versions of Windows. Other browsers, including Google Chrome, Mozilla Firefox, and Internet Explorer don't support this type of filtering.

For end-user enrollment instructions, see:

 -  [Enroll Windows 10/11 device](/mem/intune/user-help/enroll-windows-10-device?azure-portal=true).
 -  [Enroll Windows 8.1 or Windows RT 8.1 device](/mem/intune/user-help/enroll-your-w81-or-rt81-windows?azure-portal=true).

Organizations can have their end-users to see [What can my IT admin see on my device](/mem/intune/user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune?azure-portal=true).

> [!IMPORTANT]
> If you don't have Auto-MDM enrollment enabled, but you have Windows 10/11 devices that have been joined to Azure AD, two records will be visible in the Intune console after enrollment. You can avoid this situation by verifying that users with Azure AD joined devices go to **Accounts &gt; Access work or school** and **Connect** using the same account.

**Additional reading**. For more information about end-user tasks, see [Resources about the end-user experience with Microsoft Intune](/mem/intune/fundamentals/end-user-educate?azure-portal=true).

### Configure Registration CNAMEs

Azure Active Directory has a different CNAME that it uses for device registration for iOS/iPadOS, Android, and Windows devices. Intune conditional access requires devices to be registered, also called "workplace joined". If you plan to use conditional access, you should also configure the EnterpriseRegistration CNAME for each company name you have.

| **Type** | **Host name**                              | **Points to**                      | **TTL**  |
| -------- | ------------------------------------------ | ---------------------------------- | -------- |
| CNAME    | EnterpriseRegistration.company\_domain.com | EnterpriseRegistration.windows.net | One hour |

**Additional reading**. For more information about device registration, see [Manage device identities using the Azure portal](/azure/active-directory/devices/device-management-azure-portal?azure-portal=true).
