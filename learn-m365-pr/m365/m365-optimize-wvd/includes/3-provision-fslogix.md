To use FSLogix to separate user profiles from the session host virtual machines (VM), we'll need to configure Azure Storage and create an FSLogix profile. These steps vary depending on the storage type and whether you're using Azure Active Directory Domain Services (Azure AD DS) or Active Directory Domain Services (AD DS) on premises. The following steps cover how to configure Azure Files with Azure AD DS. The steps for AD DS on premises are the same except for the "Enable Azure Active Directory authentication" section. The differences are called out in that section.

## Create the storage account

1. Sign in to the [Azure portal](https://portal.azure.com?azure-portal=true).
1. Search for **Storage accounts** by using the Azure portal search box.
1. In **Storage accounts** command bar, select **Create**. The **Create a storage account** page appears.
1. Under *Project Details* select the **Subscription**, and then select or create a **Resource group** to contain your storage resources.
1. Under *Instance details*, enter a unique name for your Storage account, and accept the defaults for the rest of the values.

   :::image type="content" source="../media/3-create-storage-account.png" alt-text="Screenshot of the create storage account experience with resource group selected and a storage account name entered.":::

1. Select **Review + create** to validate your inputs, and then select **Create**.
1. Wait for the deployment to complete. This may take a minute.
1. Select **Go to resource**. The **Storage account** page displays details about your storage account.

## Enable Azure Active Directory authentication

The following steps cover how to enable authentication for Azure file shares with Azure AD DS. If you're using AD DS on premises, you need to register your Azure storage account with AD DS, and then set the required domain properties on the storage account. Use the AzFilesHybrid Azure PowerShell module on a device that is domain joined to your on-premises AD DS. The `Join-AzStorageAccountForAuth` cmdlet performs the equivalent of an offline domain join on behalf of the Azure storage account. For the step-by-step instructions to enable authentication with AD DS on-premises, see the related Docs article at the end of this module.

### Enable authentication for Azure file shares with Azure AD DS

1. In the Storage account menu, scroll to **Settings**, and then select **Configuration**.
1. Under **Identity-based access for file shares**, enable the **Azure Active Directory Domain Services (AAD DS)** option.

    :::image type="content" source="../media/3-enable-storage-account-aadds.png" alt-text="Screenshot that shows the storage account configuration page with the Azure Active Directory Domain Services (AAD DS) option enabled.":::
1. Select **Save**.

## Assign roles to access storage data

You need to assign roles to the AAD DC Administrators group and to your Azure Virtual Desktop users.

### Assign role to AAD DC Administrators

Give the administrators the ability to modify NTFS permissions by assigning an elevated contributor role for the file share.

1. In the storage account you created, select **Access control (IAM)**.
1. Select **Add** > **Add role assignment**.
1. For **Role**, select **Storage File Data SMB Share Elevated Contributor**.
1. Select **AAD DC Administrators**.

    :::image type="content" source="../media/3-add-role-file-data-elevated.png" alt-text="Screenshot that shows the role and AAD DC Administrators selected.":::

1. Select **Save**.

### Assign role to non-administrator Azure Virtual Desktop users

Assign users a contributor role so they have permission to read and write file data in the SMB file share where the user profile virtual disks are stored.

1. Select **Add** > **Add role assignment**.
1. For **Role**, select **Storage File Data SMB Share Contributor**.
1. Select each Azure Virtual Desktop user.

    :::image type="content" source="../media/3-add-role-file-data-contributor.png" alt-text="Screenshot that shows the role and Azure Virtual Desktop user selected.":::

1. Select **Save**.

## Create a file share to store the user profile virtual disks

1. In your storage account, in the left navigation, scroll down to **File service**.
1. Select **File shares** > **File share** to create a new file share.
1. Enter a **Name**.
1. Enter a value for **Quota** in Gibibytes (GiB), up to 5120 GiB.

   :::image type="content" source="../media/3-new-file-share.png" alt-text="Screenshot that shows the new file share page with a name and quota entered.":::

1. Click **Create**.

This file share will use SMB 3.0 protocol with your session hosts.

## Get the access key and file share path

You'll need the storage account access key and file share path to configure FSLogix on the VMs.

### Get storage account access key

1. In your storage account, under **Settings**, select **Access keys**.
1. Copy the value from one of the key fields to use it later.

### Get the file share path

1. In your storage account, in the left navigation, scroll down to **File service** and select **File shares**.
1. Select the file share you created.
1. Under **Settings**, select **Properties**.
1. Copy the URL.
1. Convert it from an HTTP path to an SMB path to use it later.

## Install FSLogix software for non-gallery images

Any virtual machine (VM) you create by using a gallery image has the FSLogix software preinstalled. So you can skip this section. If you used an image that's not from the gallery, you need to install FSLogix by completing the following steps.


1. For each VM registered to the host pool, [download the FSLogix agent](https://go.microsoft.com/fwlink/?linkid=2084562).
1. Go to either \\Win32\Release or \\X64\Release in the .zip file.
1. Run FSLogixAppsSetup to install the FSLogix agent.

## Configure FSLogix

Add a registry key to each VM registered to the host pool.  You'll need the storage account access key and the file share path.

1. From the start menu, run RegEdit as an administrator.
1. Go to **Computer\HKEY_LOCAL_MACHINE\software\FSLogix**.
1. Create a key for the VMs called **Profiles**.  
1. Under **Profiles**, add the following data type entries:

   | Type  | Name   | Data/Value  
   |----|---|----|
   | DWORD | Enabled           | 1     |
   | Multi-String Value | VHDLocations| File share location from Azure Files, in SMB path format    |
1. Open an elevated command prompt.
1. Run the following commands where you replace placeholder values with the SMB file share path, the storage account access key, and the user's Azure AD User Principal Name (UPN). The UPN would look something like kaicarter@contoso.onmicrosoft.com.

   ```cmd
   net use Z: [SMB path used in VHDLocations in the registry] /u:Azure\[storage account name] [storage access key] 

   Icacls Z: /grant [user UPN]:(f)
   ```

## Create the FSLogix profile

To create the FSLogix profile, the VM can't already have a user profile established for the user.

1. Go to [https://aka.ms/wvdwebarm](https://aka.ms/wvdwebarm).
1. Sign in to a VM that you haven't signed into yet.

The initial sign-in will take a little longer than usual. It's a one-time delay while the process creates the virtual disk file in the background. This file will be used each time you sign in.  

## Verify disk are created

1. Go back to your **Storage Account** in Azure.
1. Go to the **File Share**.
1. You'll see the new virtual disk.

   :::image type="content" source="../media/3-profile-files.png" alt-text="Screenshot that shows the user profile disk in the Azure file share..":::

The next time the user signs in, the VM will connect to their virtual disk. For the user, it will feel like any apps that use %localappdata% are using a locally stored profile.
