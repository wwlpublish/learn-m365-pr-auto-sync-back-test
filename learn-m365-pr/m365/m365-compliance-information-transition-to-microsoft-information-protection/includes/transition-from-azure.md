Transitioning from Azure Information Protection to Microsoft Information Protection consists of the following steps:

- Activate unified labeling and migrate labels to the Microsoft 365 compliance center.
- Copy existing Azure Information Protection policies or create new policies in Microsoft 365 compliance center.
- Manage labels with label policies from the Microsoft 365 compliance center.
- Download and install the latest unified labeling client if necessary.

:::image type="content" source="../media/transition-to-microsoft-information-protection.png" alt-text="Transition to Microsoft Information Protection." border="false":::

## Activate unified labeling and migrate labels to the Microsoft 365 compliance center

If you create labels in the Microsoft 365 compliance center with the same name as your existing Azure Information Protection labels, you won't be able to migrate those labels later. To avoid conflicts, we recommend you first migrate your labels from Azure Information Protection. Activation migrates the labels from the Azure Information Protection store to the Microsoft Information Protection unified labeling store. Once activated, both services use the unified store for **labels**. This transition has no impact on users with the Azure Information Protection client (classic). It only makes the policies originally defined in Azure Information Protection visible and configurable in the Microsoft 365 compliance center. Unified labeling clients do not see any labels until you **publish** a label policy, which does not happen during unified labeling activation.

If you create labels in the Microsoft 365 compliance center with the same name as your existing Azure Information Protection labels, you won't be able to migrate those labels later. To avoid conflicts, we recommend you first migrate your labels from Azure Information Protection.

Here is the path to activate unified labeling: **Azure Information Protection > Unified Labeling > Activate**. The graphic below shows the Azure Information Protection unified labeling properties page after unified labeling has been activated. This step should only take a few moments but is dependent on the number of labels defined.

:::image type="content" source="../media/azure-information-protection-unified-labeling-properties.png" alt-text="Azure Information Protection unified labeling properties page after unified labeling has been activated." border="false":::

Once labels are migrated, you will see the same labels in Azure information Protection and the Microsoft 365 compliance center.

The image below shows the labels in Azure Information Protection.

:::image type="content" source="../media/sensitivity-label-aip.png" alt-text="labels in Azure Information Protection." border="false":::

The image below slows the successfully migrated labels in the Microsoft 365 compliance center.

:::image type="content" source="../media/sensitivity-label-compliance-center.png" alt-text="Successfully migrated labels in the Microsoft 365 compliance center." border="false":::

Here is an image of the service architecture **before** unified labeling activation. When the "Get policy" action is executed from the classic client, the source of the labels is the Azure Information Protection store.

:::image type="content" source="../media/service-architecture-before-unified-labeling-activation.png" alt-text="Service architecture before unified labeling activation." border="false":::

Here is an image of the service architecture **after** unified labeling activation. When the "Get policy" action is executed from the classic client, the source of the labels is now the Microsoft 365 compliance center unified labeling store. Note that **policies** and **conditions** are still sourced from the Azure Information Protection store for the classic client, even after migration. **Just the label source changes.**

:::image type="content" source="../media/service-architecture-after-unified-labeling-activation.png" alt-text="Service architecture after unified labeling activation." border="false":::

## Copy existing Azure Information Protection policies or create new policies in Microsoft 365 compliance center

Once your labels have been migrated to the Microsoft 365 compliance center, determine if you want to copy your existing policies or start over with new ones.

Here are some considerations before electing to copy policies:

- **All or nothing**. All policies from Azure Information Protection will be copied. You cannot select which policies to copy.
- **Immediate publishing**. Once policies are copied, they are **immediately published* to all unified labeling supported clients. All users with applications that support unified labeling will see any sensitivity labels associated with those policies. This may be what you intend, but do not copy your policies if you do not want the sensitivity labels associated with them to be visible to users.
- **Policies not synchronized**. Unlike labels, **policies do not synchronize* between the Microsoft 365 compliance center and the Azure Information Protection pane. Once copied, each platform's policies are independent. Classic client users will still access the Azure Information Protection store for policies. Unified labeling clients will access the Microsoft 365 compliance center store.

Selecting *Azure Information Protection > Unified labeling > Copy policies (Preview)** performs a one-time copy from the Azure Information Protection policy store to the Microsoft 365 compliance center policy store. The policies copied to compliance center use the naming convention "AIP_\<policyname>".

Examples of the copy policies summary in Azure Information Protection and resulting policy in the Microsoft 365 compliance center are shown below. Notice the "AIP_" prefix to indicate this policy was copied from Azure Information Protection.

The image below shows Unified labeling status in Azure Information Protection.

:::image type="content" source="../media/unified-label-status-aip.png" alt-text="Unified labeling status in Azure Information Protection." border="false":::

The image below shows Unified labeling status in the Microsoft 365 compliance center.

:::image type="content" source="../media/unified-label-status-compliance-center.png" alt-text="Unified labeling status in the Microsoft 365 compliance center." border="false":::

Some advanced policy settings are not available in the Microsoft 365 compliance center but accessible via PowerShell. This is also true of policies copied using Azure Information Protection's Copy policies (preview). The policy settings are copied, but not visible in the compliance center. Instead, use the Security & Compliance PowerShell module [to update these policy settings. Here are few examples of these settings:

- For email messages with attachments, apply a label that matches the highest classification of those attachments.
- Implement pop-up messages in Outlook that warn, justify, or block emails being sent.
- Add "Report an Issue" for users.

> [!NOTE]
> These advanced settings (both for policies and labels) are supported only by the Azure Information Protection unified labeling client and not the Office 365 built-in labeling client.

## Manage labels and label policies from the Microsoft 365 compliance center

Any policies copied in the previous step will already be published. However, you may want to edit those existing policies or create new ones. Remember, labels are not visible until they are published. You must edit policies for clients using unified labeling in the Microsoft 365 compliance center.

Organizations with Azure Information Protection clients (classic) installed should be aware of the following:

- Policy changes and additions made in the Microsoft 365 compliance center must also be made in Azure Information Protection.
- Label changes made in Microsoft 365 compliance center will be visible in Azure Information Protection, but those labels must be published in Azure Information Protection to become visible to clients.

## Download and install the latest unified labeling client if necessary

The services are now in place for clients to use the unified sensitivity labels and label policies from the Microsoft 365 compliance center. Users still need a client with awareness of the unified sensitivity labels and policies. Windows users will either use the built-in client or install the unified labeling client following the selection guidance covered earlier in this module.

There are two options for installing the Azure Information Protection unified labeling client, if necessary:

Running the executable (EXE) version of the client is the recommended installation method. It can be configured to run in interactive mode or silent mode. It has the most flexibility and it is recommended because the installer checks for many of the prerequisites and can install any that are missing.

Deploying the Windows installer (MSI) version of the client is supported for silent installs that use a central deployment mechanism, such as group policy, Configuration Manager, and Microsoft Intune. This method is necessary for Windows 10 PCs managed by Intune and mobile device management (MDM) because installation via executable files is not supported. When you use this installation method, you must manually check and install or uninstall the software the executable would typically perform.

## Summary

Transition to unified labeling is complete and you can manage labels in the Microsoft 365 compliance center once you perform the steps above. Once all your clients are using unified labeling, the only reason you may still need to use the Azure portal for Azure Information Protection or to manage the Azure Information Protection scanner and to monitor label activities using Azure Information

## Learn more

- [What label policies can do](/microsoft-365/compliance/sensitivity-labels?what-label-policies-can-do?azure-portal=true)
- [Choose which labeling client to Windows computers](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers?azure-portal=true)
- [Apply sensitivity labels to your files and email in Office](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?azure-portal=true)
- [Compare the labeling clients for Windows computers](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?azure-portal=true)
- [Azure Information Protection unified labeling client for Windows](/azure/information-protection/rms-client/aip-clientv2?azure-portal=true)
