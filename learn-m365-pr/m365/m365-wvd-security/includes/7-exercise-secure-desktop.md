In this exercise, you’ll learn how to enable AppLocker. In an enterprise, this process would normally be done using GPOs, Intune, or Configuration Manager. This exercise does not include access to those tools or an Active Directory Domain Controller. In this exercise, you'll use a Windows Server 2016 VM running in Azure. Given that this is not a Windows Virtual Desktop environment for the lab, Windows 10 Enterprise was not available. You can also review the following video on AppLocker in a Windows Virtual Desktop deployment.

> [!NOTE] 
> If you choose to perform the exercise in this module, you might incur costs in your Azure subscription. To estimate the cost, refer to [Windows Virtual Machines Pricing](https://azure.microsoft.com/pricing/details/virtual-machines/windows/?azure-portal=true). The steps outlined in this lab are for a Windows server 2016 environment.

[The following video shows AppLocker working in a WVD enviroment](https://www.microsoft.com/en-us/videoplayer/embed/RE4Lt59)

### Prerequisites

To perform this exercise, you require:

- An Azure subscription

- The Remote Desktop app

You can define and deploy VMs on Azure in several ways. This exercise uses the Azure Command Line Interface in Azure Cloud Shell.

### Task 1: Create a Windows VM by using the Azure Command Line Interface in the Azure Cloud Shell

1. Sign in to the [Azure portal](https://portal.azure.com/) using your Azure credentials.

1. You may also receive a prompt stating you have no storage mounted, prompting you to select a subscription and to create storage. Select your subscription and choose to **Create storage** if prompted.

1. The **ProvisioningState : Succeeded** message should confirm successful creation of your storage.

1. Select the Cloud Shell icon next to the search box. A **Welcome to Azure Cloud Shell banner** opens.

1. In the Azure Cloud Shell terminal window ensure Powershell is chosen as the the selected environment. Select **PowerShell**.

### Create a resource group

You now need to create a resource group. An Azure resource group is a logical container into which Azure resources are deployed and managed. The following example creates a resource group named **myResourceGroup** in the **westus** location. Depending on your location, you might select a different option.

1. Enter the following command in the PowerShell CLI:

	```PowerShell
	az group create -n myResourceGroup -l westus
	```

1. Verify your new resource group by using the following. This command gets the Azure resource group in your subscription named myResourceGroup.
	```PowerShell
	Get-AZResourceGroup -Name "myResourceGroup"
	``` 

### Deploy a Windows Server 2016 VM

1. Enter the following commands into the CLI window:

	```PowerShell
	az vm create --resource-group myResourceGroup --name myVM --image win2016datacenter --admin-username myVMadmin
	```

1. Enter the **Admin Password** and confirm it when prompted.

1. When the **Running** message is depicted, the machine is being deployed. The Azure resources should take approximately two to three minutes to deploy.

1. When the process is finished, the following output will depict completion:

    ```PowerShell
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

### Task 2: Connect to VM

Use the following steps to create a remote desktop session from your local computer. Replace the IP address with the public IP address of your VM. When prompted, enter the admin username you specified in the PowerShell command, and the password you entered when the VM was created.

1. On a Windows desktop, enter **mstsc** in your search window and select the Remote Desktop Connection app.

1. Select **Show Options**. Enter the IP address of the VM and your administrator credentials, and then select **Connect**. Do not choose to save the sign-on configuration.

### Task 3: Add a standard user

1. The next step is to add a standard user to the **myVM** server.

1. The Windows Server Manager dashboard should now be available. If not, select **Start**, and then select **Server Manager**.

1. On the Dashboard, select **Tools**, and then select **Computer Management.**

1. Under **System Tools**, select **Local Users and Groups.** Right-click **Users** or activate its context menu, and then select **New User.**

1. Enter a Username, Full name and Description, enter and confirm a Password, and clear the **User must change password on next login** check box.

1. Select **Create,** and then select **Close.**

1. Select the **Groups** option, and then search for **Remote Desktop Users**.

1. Right-click **Remote Desktop Users** or activate its context menu, and then select **Add to Group...**.

1. In the **Remote Desktop Users** properties interface dialog box, select **Add...**.

1. Add the standard user you created earlier, to this group.

1. Select **OK**.

1. Close the **Computer Management** console.

### Task 4: Enable AppLocker

1. In **Server Manager** select **Tools**, and then select **Local Security Policy**.

1. Under **Security Setting**, select **Application Control Policies**.

1. Select **AppLocker**. The AppLocker configuration interface displays.

1. Select **Configure rule enforcement**. The **AppLocker Properties** interface becomes available.

1. In the **Enforcement** tab, these default rules are not enabled. Select the **Executable rules Configured**check box. to enable executable rules.

1. Repeat the previous step for **Windows Installer rules...**, **...Script rules,** and **Packaged app Rules...**.

1. Select **OK**.

### Task 5 Disable Internet Explorer Enhanced Security Configuration
To show the power of AppLocker we need to disable the Enhanced Security Configuration which is enabled by default in Internet Explorer on Windows Server 2016.

1. In **Server Manager** select **Local Server**.

1. In the **Properties** panel locate the **IE Enhanced Security Configuration**, and select the **On** link.

1. Turn off IE Enhanced Security for both **Administrators** and **Users** by selecting the **Off* button for each.

1. Start IE. You should see a message that **Internet Explorer Enhanced Security Configuration is not enabled**.


### Task 6 Test the applocker configuration on our deployed Windows Server 2016 VM by using the following steps

1. Sign out of the deployed Windows Server VM that you just configured, and then sign in using the standard user account you created previously.

1. Access the internet using IE. 

1. Try to download Visual Studio Code at https://code.visualstudio.com/Download or you favorite app.

1. You should not be allowed to install the app. The default **access denied** message should be displayed.

### Task 7 Clean up the resources

1. You can use the following command to remove the resource group, VM, and all related resources when you no longer require them:

```PowerShell
az group delete --name myResourceGroup
```
1. This process will take 2 to 3 minutes.
