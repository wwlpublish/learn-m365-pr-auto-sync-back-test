In this exercise, you’ll learn how to enable AppLocker. In an enterprise, this process would normally be done using GPOs, Intune, or Configuration Manager. This exercise does not include access to those tools or an Active Directory Domain Controller. In this exercise, you'll use a Windows Server 2016 VM running in Azure. Given that this is not a WVD environment for the lab, Windows 10 Enterprise was not available. You can also review the following video on AppLocker in a WVD deployment.

<!--Video:here -->

## Prerequisites

To perform this exercise, you require:

- An Azure subscription

- The Remote Desktop app

You can define and deploy VMs on Azure in several ways. You can use the Azure portal, a script (using the Azure Command Line Interface [CLI] or Azure PowerShell), or through an Azure Resource Manager template. This exercise uses the Azure CLI.

## Subtask 1: Create a Windows VM by using the Azure Command Line Interface

1. Sign in to the [Azure portal](https://portal.azure.com/) using your Azure credentials.

1. Select the PowerShell icon next to the search box. A **Welcome to Azure Cloud Shell banner** opens.

1. Select **PowerShell**.

1. If prompted, select **Create storage** and wait for the command prompt. A **Welcome to Cloud Shell** message and a command prompt window should become available.

### Create a resource group

You now need to create a resource group. An Azure resource group is a logical container into which Azure resources are deployed and managed. The following example creates a resource group named **myResourceGroup** in the **westus** location. Depending on your location, you might select a different option.

1. Enter the following command in the PowerShell CLI:

	```az group create -n myResourceGroup -l westus```

1. Verify your new resource group by using the **Get-AZResourceGroup** cmdlet. The **ProvisioningState : Succeeded** message should confirm successful creation.

### Create a Windows Server 2016 VM

1. Enter the following commands into the CLI window:

	```az vm create --resource-group myResourceGroup --name myVM --image win2016datacenter --admin-username myVMadmin```

1. You'll be prompted for an administrator password. When the **Running** message is depicted, the machine is being deployed. When the process is finished, the following output will depict completion:

    ```
    {- Finished ..

     "fqdns": "",

    "id":"/subscriptions/************/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM",

     "location": "westus",

     "macAddress": "00-0D-3A-5A-75-FA",

     "powerState": "VM running",

     "privateIpAddress": "10.0.0.4",

     "publicIpAddress": "65.52.124.71",

     "resourceGroup": "myResourceGroup",

     "zones": ""

    }
    ```
1. The public address is the address to use in your RDP connection. Note the address with your administrator password.

## Subtask 2: Connect to VM

Use the following steps to create a remote desktop session from your local computer. Replace the IP address with the public IP address of your VM. When prompted, enter the credentials used when the VM was created.

1. On a Windows desktop, enter **mstsc** in your search window and select the Remote Desktop Connection app.

1. Select **Show Options**. Enter the IP address of the VM and your administrator credentials, and then select **Connect**. The next step is to add a standard user to the **myVM** server. Do not choose to save the sign-on configuration.

## Subtask 3: Add a standard user

1. The Windows Server Manager dashboard should now be available. If not, select **Start**, and then select **Server Manager**.

1. On the Dashboard, select **Tools**, and then select **Computer Management.**

1. Under **System Tools**, select **Local Users and Groups.** Right-click **Users** or activate its context menu, and then select **New Users.**

1. Enter your details in the **New User** dialog box and clear the **User must change password on next login** check box.

1. Select **Create,** and then select **Close.**

1. Select the **Group** option, and then search for **Remote Desktop Users**.

1. Right-click **Remote Desktop Users** or activate its context menu, and then select **Add to Group**.

1. In the **Remote Desktop Users Properties interface** dialog box, select **Add**.

1. Add the standard user you created to this group.

1. Select **OK**.

1. Close the Computer Management console.

## Subtask 4: Enable AppLocker

1. Select **Tools**, and then select **Local Security Policies**.

1. Under **Security Setting**, select **Application Control Policies**.

1. Select **AppLocker**. The AppLocker interface is in the **details** pane.

1. Select **Configure rule enforcement**. The AppLocker Properties interface becomes available.

1. In the **Enforcement** tab, these default rules are not enabled. Select the check boxes to enable the **Executable rules.**

1. Repeat the previous step for **Windows Installer Rules**, **Script Rules,** and **Package app Rules**.

1. Select **OK**.

## Results

Test the deployment by using the following steps:

1. Sign out as an administrator and sign in using the non-administrative user account you created previously.

1. Access the internet and try to download your favorite app.

1. You should not be allowed to install the app.

## Clean up the resources

You can use the following command to remove the resource group, VM, and all related resources when you no longer require them:

```az group delete --name myResourceGroup```
