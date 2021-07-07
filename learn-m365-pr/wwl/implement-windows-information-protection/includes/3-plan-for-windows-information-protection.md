Given the importance of Windows Information Protection (WIP) in protecting against potential data leakage, you must carefully plan the WIP implementation process to take advantage of its security benefits.

### **Prerequisites**

Implementing WIP requires the following prerequisites:

 -  Windows 10 version 1607 (Anniversary Edition) or later
 -  An MDM or MAM solution that supports an “Enterprise Data Protection” configuration service provider (CSP) such as Microsoft Intune, Configuration Manager, or third-party solutions that support WIP.
 -  Windows Client must be enrolled in MDM or registered for MAM.

Once you've satisfied your prerequisites, you should plan for the following issues related to your WIP implementation:

 -  Planning considerations.
 -  Determine which Encryption key to use.
 -  Determine which Policy protection mode to use.
 -  Configure your intelligent network boundaries.

### **Planning considerations**

WIP settings are delivered through WIP policies. These policies contain an organization's required Windows settings. WIP settings must be configured with your preferred MDM or MAM solution for Windows 10 devices to send them to your users’ devices.

When planning your WIP implementation, you should consider the questions in the following table.

:::row:::
  :::column:::
    

**Planning Step**


  :::column-end:::
  :::column:::
    

**Consideration**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Which Windows 10 versions exist in your company?


  :::column-end:::
  :::column:::
    

Windows Home edition only supports WIP for MAM-only; upgrading to an MDM policy on the Home edition will revoke WIP-protected data access.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Will you use MDM or MAM?


  :::column-end:::
  :::column:::
    

WIP policies are created for MDM or MAM, but they don't support both at the same time. For example, a WIP policy configured for MDM but scoped for a group of users with MAM won't work.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

How many policies are required?


  :::column-end:::
  :::column:::
    

WIP policies are assigned to Azure AD security groups, and you can assign policies to multiple groups. By creating multiple policies for different user groups, you can differentiate, for example, between MDM and MAM users. You can also differentiate between users with higher security needs and developers that must conduct tests.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Which apps do you need to include or trust for protection?


  :::column-end:::
  :::column:::
    

Select from a list of predefined and fully supported apps that can differentiate between corporate and personal data to be protected. You can also select trusted apps that can bypass the WIP policy.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Which apps are trusted or untrusted?


  :::column-end:::
  :::column:::
    

Apps that aren't fully supported can be declared as either trusted (to access corporate data) or untrusted (to be blocked from corporate data access).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Which websites and networks are trustful?


  :::column-end:::
  :::column:::
    

Websites and networks are untrusted by default, including OWA. Define which websites are trusted to access your corporate data.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Which protection mode for what group of users do you require?


  :::column-end:::
  :::column:::
    

Decide which users require the restrictive protection mode, which users must be allowed to override, and which users are monitored.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

How to monitor the use of WIP policies?


  :::column-end:::
  :::column:::
    

Monitor or collect the local machines’ event logs to audit the use of WIP. You can also use the Reporting configuration service provider (CSP).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Where are the limitations and interdependencies of WIP?


  :::column-end:::
  :::column:::
    

Consider the limitations of WIP. For example, the Windows feature known as Direct Access (DA) is incompatible with WIP. WIP is designed for use only by a single user per device. For more information, see the following article on [the limitations of WIP](/windows/security/information-protection/windows-information-protection/limitations-with-wip).




  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Use an Encrypting File System (EFS) Data Recovery Agent (DRA) certificate or AIP?


  :::column-end:::
  :::column:::
    

When Azure RMS is activated in your tenant, you can use the Azure RMS certificate by default, or you can choose an EFS certificate. Without AIP and an EFS DRM certificate in your WIP policy, you can possibly lose data because local certificates are used for encryption.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

WIP standalone or use Azure RMS templates?


  :::column-end:::
  :::column:::
    

Use RMS templates from AIP to protect documents and files. You can also use WIP standalone.


  :::column-end:::
:::row-end:::


All apps that fully support the data separation between company and personal data are called “Enlightened.” Apps that aren't fully compatible are called “Non-Enlightened” (or Unenlightened); these apps consider all files and resources as work-related only. Those differences in detail will be covered in a later lesson.

### **Determine which encryption key to use**

There are three different methods of using encryption keys to protect documents and files:

 -  If you use Azure RMS, the encryption key from your Azure Vault is used for encryption.
 -  If you specify an EFS DRM certificate in a WIP policy, the certificates public key is used for encryption.
 -  If you don’t use Azure RMS, the local machine’s EFS DRM certificate is used for encryption.

> [!IMPORTANT]
> *If you decide not to use the Azure RMS or centralized EFS DRM key, you can't access protected content if the local machine’s private key is lost.*

### **Determine which policy protection mode to use**

For any WIP policy you can configure a protection mode that enforces the WIP policy, allows user overrides, or silently monitors all WIP-related user actions. The following protection modes are available.

:::row:::
  :::column:::
    

**Mode**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Block


  :::column-end:::
  :::column:::
    

Blocks corporate work data from leaving protected apps.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Allow Overrides.


  :::column-end:::
  :::column:::
    

User is prompted when attempting to move data from a protected app to a non-protected app. If the user chooses to override this prompt, the action will be logged.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Silent


  :::column-end:::
  :::column:::
    

User is free to move data off of protected apps. The actions are logged.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Off


  :::column-end:::
  :::column:::
    

User is free to move data off of protected apps. No actions are logged.


  :::column-end:::
:::row-end:::


> [!NOTE]
> Changing the scope or removing a policy will decrypt all data.

### **<br>Configure your intelligent network boundaries**

When working with local apps, the interaction between processes that contain work or personal data stays inside the local system, in contrast to online apps such as Outlook Web Access or Office Online. To offer your users a seamless work experience, you must define trusted online apps and network locations or prepare your users that certain online services won't be available when working with protected files anymore.

All required networks should be added to the list of trusted locations. For example:

 -  On-premises SharePoint servers, on-premises OWA sites, and intranet websites.
 -  Trusted Office Online apps of your tenant (for example, yourdomain.sharepoint.com).
 -  Trusted Office Online apps (for example, teams.microsoft.com, outlook.office.com, and so on).

> [!NOTE]
> If you configure Outlook on the web (OWA) as a trustful networking place, all logins to **https://outlook.office.com** will be treated as trusted. In contrast to SharePoint Online, where your tenant name is a part of your web address (**&lt;tenant name&gt;.sharepoint.com**), Outlook on the web is available as a shared web address. If a user signs in to **https://outlook.office.com** using a login name from another tenant, they'll also be fully trusted in your environment.

**Additional reading.** For more information, see [How to add custom apps for protection](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#add-store-apps?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”