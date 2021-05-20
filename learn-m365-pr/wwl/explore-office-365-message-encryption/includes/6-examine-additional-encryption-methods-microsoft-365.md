The primary focus of this module has been message encryption, and specifically OME. However, it’s important to note that Microsoft 365 provides other forms of data encryption that can protect your content from being read by unauthorized users. Because encryption in Microsoft 365 can be accomplished using various technologies and methods, there isn't one single place where encryption is set up. So, let’s examine the various ways you can set up or configure encryption as part of your information protection strategy.

With Microsoft 365, several encryption capabilities are available by default for meeting certain compliance or legal requirements. The following table describes several encryption methods for addressing common business scenarios.

:::row:::
  :::column:::
    

**Scenario**


  :::column-end:::
  :::column:::
    

**Encryption Methods**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Files are saved on Windows computers.


  :::column-end:::
  :::column:::
    

Encryption at the computer level can be done using BitLocker on Windows devices. As an enterprise administrator or IT Pro, you can set this up using the Microsoft Deployment Toolkit (MDT). See [Set up MDT for BitLocker](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Files are saved on mobile devices.


  :::column-end:::
  :::column:::
    

Some kinds of mobile devices encrypt files that are saved to those devices by default. With [Capabilities of built-in Mobile Device Management for Office 365](https://support.office.com/article/a1da44e5-7475-4992-be91-9ccec25905b0?azure-portal=true), you can set policies that determine whether to allow mobile devices to access data in Microsoft 365. For example, you can set a policy that allows only devices that encrypt content to access Microsoft 365 data. See [Create and deploy device security policies](https://support.office.com/article/d310f556-8bfb-497b-9bd7-fe3c36ea2fd6?azure-portal=true).
For more control over how mobile devices interact with Microsoft 365, you can consider adding Microsoft Intune. See [Device management overview](https://docs.microsoft.com/mem/intune/fundamentals/what-is-device-management#simplify-it-tasks-using-the-device-management-dashboard?azure-portal=true) for an explanation on the differences between MDM for Office 365 and Microsoft Intune.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

You need control over the encryption keys used to encrypt your data in Microsoft's data centers.


  :::column-end:::
  :::column:::
    

As a Microsoft 365 administrator, you can control your organization's encryption keys and then configure Microsoft 365 to use them to encrypt your data at rest in Microsoft's data centers.

For more information, see [Controlling your data in Office 365 using Customer Key](https://docs.microsoft.com/office365/securitycompliance/controlling-your-data-using-customer-key?azure-portal=true) and [Customer Key for Office 365 FAQ](https://docs.microsoft.com/office365/securitycompliance/service-encryption-with-customer-key-faq?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

People are communicating via email (Exchange Online).


  :::column-end:::
  :::column:::
    

As an Exchange Online administrator, you have several options for configuring email encryption. These options include:

 -  Using Office 365 message encryption (OME) with Azure Rights Management (Azure RMS) to enable people to send encrypted messages inside or outside your organization.
 -  Using [S/MIME for message signing and encryption](https://docs.microsoft.com/microsoft-365/security/office-365-security/s-mime-for-message-signing-and-encryption?azure-portal=true) to encrypt and digitally sign email messages.
 -  Using TLS to [set up connectors for secure mail flow with another organization](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner?azure-portal=true).

For more information, see [Email encryption in Office 365](https://docs.microsoft.com/microsoft-365/compliance/email-encryption?azure-portal=true).



  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Files are accessed from team sites or document libraries (OneDrive for Business or SharePoint Online).


  :::column-end:::
  :::column:::
    

When people are working with files saved to OneDrive for Business or SharePoint Online, TLS connections are used. This feature is automatically built into Microsoft 365.

For more information, see [Data Encryption in OneDrive for Business and SharePoint Online](https://docs.microsoft.com/microsoft-365/compliance/data-encryption-in-odb-and-spo?azure-portal=true).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Files are shared in online meetings and IM conversations (Skype for Business Online).


  :::column-end:::
  :::column:::
    

When people are working with files using Skype for Business Online, TLS is used for the connection. This feature is automatically built into Microsoft 365.

For more information, see [Security and Archiving (Skype for Business Online)](https://docs.microsoft.com/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features?azure-portal=true).


  :::column-end:::
:::row-end:::
