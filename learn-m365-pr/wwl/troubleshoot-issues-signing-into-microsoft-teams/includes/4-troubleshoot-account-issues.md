Microsoft Azure AD is an online directory service that provides similar capabilities to the on-premises Active Directory Domain Services (AD DS). Azure AD provides authentication and authorization for most Microsoft cloud services, including Microsoft Azure, Microsoft 365, and Microsoft Intune. 

AD DS is not designed to work with Internet applications or services. One way to address this shortcoming is to extend the capabilities of AD DS by using an intermediary system that handles translation of AD DS on-premises constructs and protocols (such as tokens and the Kerberos protocol) into their Internet-ready equivalents. 

> [!NOTE]
> The Active Directory Federation Services (AD FS) server role and Web Application Proxy server feature of Windows Server provide this functionality. 

The primary feature that AD FS and Web Application Proxy facilitate is federation support. A federation resembles a traditional trust relationship, but relies on:

- Claims (contained within tokens) to represent authenticated users or devices.
- Certificates to establish trusts and to facilitate secure communication with an identity provider.
- Web-friendly protocols such as HTTPS, Web Services Trust Language (WS-Trust), Web Services Federation (WS-Federation), or OAuth to handle transport and processing of authentication and authorization data.

Authentication through Azure AD can be on a cloud-only basis or through directory synchronization from on-premises AD DS. 

## What are your hybrid authentication options?

Authentication options when using Azure AD fall into one of the categories described in the following table.

| Category                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Cloud-only                                                   | Cloud-only  identities exist only in the cloud, so all password management and policy  control is done through Azure AD. Each user has two entirely separate  identities. |
| Directory  synchronization with optional password synchronization | With  directory synchronization, you set up a directory synchronization server or  appliance that provides either one- or two-way synchronization of users,  groups, and attributes from on-premises AD DS to Azure AD. But it’s important  to remember that even with password synchronization, there are still two sets  of security credentials; it is just that directory synchronization and  password sync are keeping them aligned. Users still authenticate to Azure AD  to access Microsoft 365 online services, such as Teams. |
| SSO with  AD FS                                              | The SSO  option gives authentication control to your directory service. Therefore,  users no longer authenticate against Azure AD but against AD FS.  Consequently, when a user enters `user@contoso.com` into the sign-in page of a  cloud service such as Teams, the user receives a message telling them that  they have been redirected to their organization’s sign-in page. They now  enter their on-premises identity and authenticate to the online services by  using a delegated token that verifies that the user has been successfully  authenticated by their on-premises directory service. |
| Pass-through  authentication                                 | Azure AD  pass-through authentication helps you ensure that password validation for  services that rely on Azure AD is always performed against an on-premises AD  DS. Unlike the solution using AD FS, this solution is easier to implement and  maintain. You configure Azure AD pass-through authentication by using Azure  AD Connect. It works by using an on-premises agent that listens for external  password validation requests. You can deploy this agent to one or more  servers to provide high availability. |

If your users experience sign-in problems, and your organization operates in a hybrid environment, it’s possible that the sign in problems relate to your directory synchronization architecture.

## Verify synchronization configuration

The first place to start is to determine how your organization is configured to integrate AD DS with Azure AD:

1. Open the **Azure Active Directory admin center**, and then select **Azure AD Connect**.
2. Under the **USER SIGN-IN** heading, verify the configured option: 

   - Federation
   - Seamless single sign-on
   - Pass-through authentication

   :::image type="content" source="../media/azure-ad-connect.png" alt-text="A screenshot displays the Azure AD Connect page for Contoso. The Azure AD cloud sync option is enabled and active.":::

## Verify Azure AD Connect functionality

Depending on what you see, you’ll need to verify that synchronization is occurring, and that there are no errors displayed. You might also need to check Azure AD Connect health.

### Verify synchronization status

For example, if your organization is configured for Azure AD Connect sync, verify that the Sync Status is Enabled, and that sync occurred recently. 

If it did not, you’ll need to sign-in at the computer hosting Azure AD Connect, and ensure the sync service is running: 

1. Open **Services**.
2. Locate the **Microsoft Azure AD Sync** service.
3. Start it, if necessary. 

### Verify Azure AD Connect health

You should also check the Azure AD Connect health. In the Azure Active Directory admin center. Navigate to **Azure AD Connect**, and then, under the **HEALTH AND ANALYTICS** heading, select **Azure AD Connect Health**. From here, you can review the options described in the following table. 

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Quick Start                     | Enables you to download various tools,  provide feedback, and access additional documentation. |
| Sync errors                     | Enables you to review sync errors by type,  and to configure notification settings. |
| Sync services                   | Enables you to review any alerts about the  synchronization service. You can click through to discover more about any  identified issues. |
| AD FS services                  | Provides service alert information for AD  FS issues.        |
| AD DS services                  | Provides service alert information for AD DS  issues.        |
| Settings                        | Enables you to change the update settings  for your Azure AD Connect configuration. |
| Role based access control (IAM) | Enables you to review or configure the  role assignments for your configuration. |


:::image type="content" source="../media/ad-connect-health.png" alt-text="A screenshot displays the Azure Active Directory Connect Health Quick Start page.":::

## Troubleshoot synchronization

Important troubleshooting tasks for directory synchronization include analyzing logs for errors and remediating synchronization errors with Azure AD Connect. Typical issues that can lead to problems include:

- Installation errors, such as using incorrect on-premises or Azure AD credentials
- Inadvertently deactivating directory synchronization in the Azure portal or through Windows PowerShell
- Unexpected changes in AD DS that affect OU scoping or attribute filtering
- Corrupted AD DS requiring directory recovery

### Deactivating directory synchronization 

It’s vital that you understand what happens when you deactivate and then reactivate synchronization in the Azure portal. When directory synchronization is deactivated, the source of authority is transferred from the on-premises AD DS to Azure AD. 

Deactivation is needed when on-premises AD DS is no longer being used to create and manage users, groups, contacts, and mailboxes, such as after a staged Exchange migration to the cloud, when the organization no longer wants to manage objects from the on-premises environment. 

Problems can subsequently arise if directory synchronization is then reactivated, with the source of authority transferred back from Azure AD to the on-premises AD DS.

#### Example

For example, assume that an organization activated directory synchronization in January and then created new users on-premises, which synchronized to Azure AD. 

In this case, the source of authority is the on-premises AD DS. 

In July, the organization deactivated directory synchronization, resulting in transfer of the source of authority to Azure AD; from this point on, objects were edited in Azure AD. 

In September, the organization decided to deploy AD FS and SSO. To meet this requirement, directory synchronization was reactivated, transferring the source of authority back to the on-premises AD DS. 

In this example, when you reactivate and run directory synchronization, any changes made to the Azure AD objects from July through to September would be overwritten and lost.

### Upgrading directory synchronization

It’s important to use the latest version of the directory synchronization tool. When upgrading to a new version of the directory synchronization tool, some existing filters and other management agent customizations might not automatically import into the new installation. 

If you are upgrading to a newer version of directory synchronization, you must always manually reapply filtering configurations after you upgrade but before you run the first synchronization cycle.