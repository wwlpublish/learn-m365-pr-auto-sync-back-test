When you don't already have co-management enabled, you can use the **Configure co-management** wizard to enable device upload. You can upload your devices without enabling automatic enrollment for co-management or switching workloads to Intune. If needed, you can limit upload to a single [device collection](/mem/configmgr/core/clients/manage/collections/introduction-to-collections.md).

> [!NOTE]
> If co-management is already enabled in your environment, you must [edit the co-management properties](/mem/configmgr/tenant-attach/device-sync-actions.md#bkmk_edit) to enable device upload.

When co-management isn't enabled in your environment, use the instructions below to enable device upload:

1. In the Configuration Manager admin console, select **Administration** > **Overview** > **Cloud Services** > **Co-management**.
2. In the ribbon, select **Configure co-management** to open the wizard.
3. On the **Tenant onboarding** page, select **AzurePublicCloud** for your environment. Azure Government Cloud and Azure China 21Vianet aren't supported.
4. Select **Sign In**. Use your *Global Administrator* account to sign in.
5. Ensure the **Upload to Microsoft Endpoint Manager admin center** option is selected on the **Tenant onboarding** page.
   - Make sure the option **Enable automatic client enrollment for co-management** isn't checked to avoid enabling co-management now.

   [ ![Co-management Configuration Wizard](../media/set-up-tenant-attach-using-confirmation-manager-01.png) ](../media/set-up-tenant-attach-using-confirmation-manager-01.png#lightbox)

6. Choose **Next** and then **Yes** to accept the **Create AAD Application** notification. This action provisions a service principal and creates an Azure AD application registration to facilitate the sync. Service principals define who can access the application, and what resources the application can access.
7. On the **Configure upload** page, select the recommended device upload setting for **All my devices managed by Microsoft Endpoint Configuration Manager**. If needed, you can limit upload to a single device collection. 

    > [!NOTE]
    > Starting in Configuration Manager version 2010, when a single collection is selected, its child collections are also uploaded.

8. Check the option to **Enable Endpoint analytics for devices uploaded to Microsoft Endpoint Manager**, so that later you can get insights into optimizing the end-user experience using [Endpoint Analytics](/learn/modules/compliance-endpoint-manager).
9. Select **Summary** to review your selection, then choose **Next**.
10. When the wizard is complete, select **Close**.  
