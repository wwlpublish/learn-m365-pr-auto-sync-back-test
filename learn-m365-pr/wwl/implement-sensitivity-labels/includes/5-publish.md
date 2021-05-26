Once an organization has finished creating and configuring its sensitivity labels, it must publish the labels by creating a label policy. Complete the following steps to create a label policy that contains your sensitivity labels, and then publish the policy:

1.  Whether you're using the Microsoft 365 compliance center or the Security and Compliance Center, navigate to sensitivity labels:
    
     -  In the Microsoft 365 compliance center, navigate to **Solutions &gt; Information protection.** If you don't immediately see this option, first select **Show all.**
     -  In the Security &amp; Compliance Center, navigate to **Classification &gt; Sensitivity labels.**<br>
2.  Select the **Label policies** tab, and then select **Publish labels** to start the **Create policy** wizard. The following image shows this step in the Microsoft 365 compliance center.<br><br>:::image type="content" source="../media/publish-sensitivity-labels-full-80bc98e3.png" alt-text="screenshot of the Label policies page with the Publish labels button highlighted":::
    <br>

    > [!NOTE]
    > By default, Microsoft 365 tenants don't have any label policies. As a result, you must create at least one policy to publish your sensitivity labels

3.  In the wizard, select **Choose sensitivity labels to publish**. Select the labels that you want to make available in apps and to services, and then select **Add**.
4.  Review the selected labels. To make any changes, select **Edit**. If no changes are needed, select **Next**.
5.  Follow the prompts to configure the policy settings.<br><br>The policy settings that you see match the scope of the labels that you selected. For example, if you selected labels that have just the **Files &amp; emails** scope, you won't see the policy settings titled "**Apply this label by default to groups and sites"** and "**Require users to apply a label to their groups and sites**."<br><br>Labels configured for Azure Purview assets (preview) won't have any associated policy settings.
6.  Repeat these steps if you need different policy settings for different users or scopes. For example, different settings are needed in the following scenarios:
    
     -  You want more labels for a group of users.
     -  You want a different default label for a subset of users.
     -  You've configured labels to have different scopes.
7.  If you create more than one label policy that may result in a conflict for a user, review the policy order and if necessary, move them up or down. To change the order of a label policy, select the ellipsis icon (**...)** for **More actions**, and then select **Move up** or **Move down**.

> [!IMPORTANT]
> Multiple label policies are needed only if users need different labels or different policy settings. Aim to have as few label policies as possible. It's not uncommon to have just one label policy for the entire organization.

Completing the wizard automatically publishes the label policy. To make changes to a published policy, you just need to edit it. There's no specific publish or republish action for you to select.

### Edit a label policy

To edit an existing label policy, select it, and then select the **Edit Policy** button, as seen in the following image.

:::image type="content" source="../media/edit-sensitivity-label-policy-full-d2c90935.png" alt-text="screen shot of the label policy window with the Edit policy button circles":::


This button starts the **Create policy** wizard, which lets you edit the label settings and which labels are included in the policy. When you complete the wizard, any changes are automatically replicated to the selected users and services.

> [!CAUTION]
> When you use built-in labeling for Office apps on Windows, macOS, iOS, and Android, users see new labels within four hours. They'll see these new labels within one hour for Word, Excel, and PowerPoint on the web when you refresh the browser. However, allow up to 24 hours for changes to replicate to all apps and services.

### Edit more label policy settings with SCC PowerShell

You can now use Security &amp; Compliance Center PowerShell to create and configure all the settings you see in your labeling admin center, plus any extra settings that aren't available in the labeling admin centers. You can also fully script the creation and maintenance of sensitivity labels and sensitivity label policies.

Other label policy settings are available with the Set-LabelPolicy cmdlet from Security &amp; Compliance Center PowerShell.

The Azure Information Protection unified labeling client supports many [advanced settings](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations?azure-portal=true) that include migrating from other labeling solutions, and pop-up messages in Outlook that warn, justify, or block emails being sent. For the full list, see [Available advanced settings for label policies](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies?azure-portal=true) from this client's admin guide.

**Additional reading.** For more information, see the following documentation for supported parameters and values:

 -  [New-Label](https://docs.microsoft.com/powershell/module/exchange/new-label?azure-portal=true)
 -  [New-LabelPolicy](https://docs.microsoft.com/powershell/module/exchange/new-labelpolicy?azure-portal=true)
 -  [Set-Label](https://docs.microsoft.com/powershell/module/exchange/set-label?azure-portal=true)
 -  [Set-LabelPolicy](https://docs.microsoft.com/powershell/module/exchange/set-labelpolicy?azure-portal=true)

You can also use [Remove-Label](https://docs.microsoft.com/powershell/module/exchange/remove-label?azure-portal=true) and [Remove-LabelPolicy](https://docs.microsoft.com/powershell/module/exchange/remove-labelpolicy?azure-portal=true) if you need to script the deletion of sensitivity labels or sensitivity label policies. However, before you delete sensitivity labels, make sure you read the following unit on removing and deleting sensitivity labels.
