The Windows Assessment and Deployment Kit (Windows ADK) includes a tool called Windows Configuration Designer which you can use to create provisioning packages.

:::image type="content" source="../media/windows-configuration-designer-interface-f5f579a4.png" alt-text="Screenshot of the Windows Configuration Designer. Shows a project called Project1 open with the Computer Account option in the left view, with fields for Account, AccountOU, ComputerName, DomainName, and Password in the right view.":::


You can use the Windows Configuration Designer wizards to configure the following settings:

:::row:::
  :::column:::
    **Step**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Desktop wizard**
  :::column-end:::
  :::column:::
    **Mobile wizard**
  :::column-end:::
  :::column:::
    **Kiosk wizard**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set up device
  :::column-end:::
  :::column:::
    Assign a device name, enter the product key to upgrade Windows, configure shared use, and remove preinstalled software
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Only device name and upgrade key
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set up network
  :::column-end:::
  :::column:::
    Connect to a wireless network
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Account management
  :::column-end:::
  :::column:::
    Enroll the device in Active Directory Domain Services (AD DS), enroll the device in Azure AD, or create a local administrator account
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Bulk enrollment in Azure AD
  :::column-end:::
  :::column:::
    Enroll the device in Azure AD before you use a Windows Configuration Designer wizard
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Add applications
  :::column-end:::
  :::column:::
    Install applications by using the provisioning package
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Add certificates
  :::column-end:::
  :::column:::
    Include a certificate file in the provisioning package
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Configure kiosk account and app
  :::column-end:::
  :::column:::
    Create a local account to run the kiosk mode app, and specify the app to run in kiosk mode
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Configure kiosk common settings
  :::column-end:::
  :::column:::
    Set tablet mode, configure welcome and shutdown screens, and turn off timeout settings
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::


You can apply a provisioning package during Windows 10 or Windows 11 deployment or after the OS installation.

### Azure AD join with automatic MDM enrollment

The Azure AD/MDM dynamic provisioning method is also cloud-driven and is also based on Azure AD Premium and Microsoft Intune. After you enroll a device in Intune MDM, the MDM enforces compliance with your corporate policies, adds or removes apps, and much more. In addition, the MDM can report a device’s compliance to Azure AD; this enables Azure AD to allow access to corporate resources or applications secured by Azure AD only to devices that comply with policies.

Using Azure AD/MDM, you can:

 -  Join devices to Azure AD automatically
 -  Auto-enroll your users’ devices into MDM services
 -  Configure the joined devices by using MDM policies

The requirements for implementing the Azure AD/MDM deployment model are:

 -  Windows 10/11 Pro or Enterprise edition
 -  An instance of Azure AD for identity management
 -  An appropriate MDM, such as Microsoft Intune
