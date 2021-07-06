When don't already have co-management enabled, you can use the **Configure co-management** wizard to enable device upload. You can upload your devices without enabling automatic enrollment for co-management or switching workloads to Intune. If needed, you can limit upload to a single device collection. 

> [!NOTE]
> If co-management is already enabled in your environment, you must [edit the co-management properties](/mem/configmgr/tenant-attach/device-sync-actions.md#bkmk_edit) to enable device upload.

When co-management isn't enabled, use the instructions below to enable device upload:

1. In the Configuration Manager admin console, go to **Administration** > **Overview** > **Cloud Services** > **Co-management**.
1. In the ribbon, select **Configure co-management** to open the wizard.
1. On the **Tenant onboarding** page, select **AzurePublicCloud** for your environment. Azure Government Cloud and Azure China 21Vianet aren't supported.
1. Select **Sign In**. Use your *Global Administrator* account to sign in.
1. Ensure the **Upload to Microsoft Endpoint Manager admin center** option is selected on the **Tenant onboarding** page.
   - Make sure the option **Enable automatic client enrollment for co-management** isn't checked if you don't want to enable co-management now. If you do want to enable co-management, select the option.
   - If you enable co-management along with device upload, you'll be given additional pages in the wizard to complete. For more information, see [Enable co-management](/mem/configmgr/comanage/how-to-enable.md).

   [ ![Co-management Configuration Wizard](../media/setup-tenant-attach-using-confirmation-manager-03.png) ](../media/setup-tenant-attach-using-confirmation-manager-03.png#lightbox)

1. Choose **Next** and then **Yes** to accept the **Create AAD Application** notification. This action provisions a service principal and creates an Azure AD application registration to facilitate the sync.
1. On the **Configure upload** page, select the recommended device upload setting for **All my devices managed by Microsoft Endpoint Configuration Manager**. If needed, you can limit upload to a single device collection.
    - Starting in Configuration Manager version 2010, when a single collection is selected, its child collections are also uploaded. 

1. Check the option to **Enable Endpoint analytics for devices uploaded to Microsoft Endpoint Manager** if you also want to get insights to optimize the end-user experience in [Endpoint Analytics](/learn/modules/compliance-endpoint-manager).
1. Select **Summary** to review your selection, then choose **Next**.
1. When the wizard is complete, select **Close**.  
