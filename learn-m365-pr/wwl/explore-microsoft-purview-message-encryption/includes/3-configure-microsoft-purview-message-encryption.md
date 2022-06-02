Microsoft Purview Message Encryption enables organizations to share protected email with anyone on any device. Users can exchange protected messages with other Microsoft 365 organizations, and with third-parties using Outlook.com, Gmail, and other email services.

Follow the steps below to ensure that Microsoft Purview Message Encryption is available in your organization.

### Verify that Azure Rights Management is active

Microsoft Purview Message Encryption applies the protection features in Azure Rights Management Services (Azure RMS). Azure RMS is the technology used by Azure Information Protection to protect emails and documents through encryption and access controls.

> [!IMPORTANT]
> The only prerequisite for an organization to use Microsoft Purview Message Encryption is that Azure RMS must be activated in its tenant. If Azure RMS is activated, Microsoft 365 activates message encryption automatically and you don't need to do anything.

Azure RMS is also activated automatically for most eligible plans, so you probably don't have to do anything in this regard either. For more information, see [Activating Azure Rights Management](/azure/information-protection/activate-service?azure-portal=true).<br>

> [!IMPORTANT]
> If you use Active Directory Rights Management service (AD RMS) with Exchange Online, you must [migrate to Azure Information Protection](/azure/information-protection/migrate-from-ad-rms-to-azure-rms?azure-portal=true) before you can use message encryption. Microsoft Purview Message Encryption isn't compatible with AD RMS.

**Additional reading**. For more information, see:

 -  [Message Encryption FAQ](/microsoft-365/compliance/ome-faq?azure-portal=true) to check whether your subscription plan includes Azure Information Protection (which includes Azure RMS functionality).
 -  [Azure Information Protection](https://azure.microsoft.com/services/information-protection/?azure-portal=true) for information about purchasing an eligible subscription.

#### Manually activating Azure Rights Management

If you disabled Azure RMS, or if it wasn't automatically activated for any reason, you can manually activate it in either of the following portals:

 -  **Microsoft 365 admin center**. See [How to activate Azure Rights Management from the admin center](/azure/information-protection/activate-office365?azure-portal=true) for instructions.
 -  **Azure portal**. See [How to activate Azure Rights Management from the Azure portal](/azure/information-protection/activate-azure?azure-portal=true) for instructions.

#### Configure management of your Azure Information Protection tenant key

This step is optional. Allowing Microsoft to manage the root key for Azure Information Protection is the default setting. It's also the recommended best practice for most organizations. For these organizations, they don't need to do anything.

However, there are many reasons, such as compliance requirements that may necessitate an organization generating and managing its own root key (also known as bring your own key, or BYOK). In this situation, it's recommended that organizations complete the required steps to generate its own key before setting up Microsoft Purview Message Encryption. This scenario is outside the scope of this training. For more information, see [Planning and implementing your Azure Information Protection tenant key](/information-protection/plan-design/plan-implement-tenant-key?azure-portal=true).

An organization can use Exchange Online PowerShell to verify that its Microsoft 365 tenant is properly configured to use Microsoft Purview Message Encryption. To do so, they should complete the following steps:

1.  Connect to Exchange Online PowerShell using an account with global administrator permissions in your Microsoft 365 tenant.
2.  Run the **Get-IRMConfiguration** cmdlet.
    
    You should see a value of **$True** for the **AzureRMSLicensingEnabled** parameter. This value indicates that Microsoft Purview Message Encryption is configured in your tenant.
    
    If it isn't, use **Set-IRMConfiguration** to set the value of **AzureRMSLicensingEnabled** to **$True** to enable Microsoft Purview Message Encryption.
3.  Once Microsoft Purview Message Encryption is enabled, run the **Test-IRMConfiguration** cmdlet using the following syntax:
    
    ```powershell
    Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
    ```
    
    For example, see the following command that tests Microsoft Purview Message Encryption at Contoso:
    
    ```powershell
    Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
    ```
    
    
     -  For sender and recipient, use the email address of any user in your Microsoft 365 tenant. Your results should be similar to the following example:
        
        ```Raw
        Results:
        Acquiring RMS Templates ...
        - PASS: RMS Templates acquired. Templates available: Contoso - Confidential View Only, Contoso - Confidential, Do Not Forward.
        Verifying encryption ...
        - PASS: Encryption verified successfully.
        Verifying decryption ...
        - PASS: Decryption verified successfully.
        Verifying IRM is enabled ...
        - PASS: IRM verified successfully.
        
        OVERALL RESULT: PASS
        ```
     -  In this example, your organization name will replace **Contoso**.
     -  The default template names may be different from those names displayed above. For more information, see [Configuring and managing templates for Azure Information Protection](/azure/information-protection/configure-policy-templates?azure-portal=true).
4.  Run the **Remove-PSSession** cmdlet to disconnect from the Rights Management service.
    
    ```powershell
    Remove-PSSession $session
    ```


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”