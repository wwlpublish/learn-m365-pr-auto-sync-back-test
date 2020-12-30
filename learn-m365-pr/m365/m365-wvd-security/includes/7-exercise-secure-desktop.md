
As a senior administrator working for Contoso, you've been asked to test Microsoft AppLocker for future deployment in your WVD environment. In an enterprise, this process would normally be done using GPOs, Intune, or Configuration Manager. This exercise doesn't include access to those tools or an Active Directory Domain Controller. 

## Exercise: Enable AppLocker in a Windows Server 2016 VM running in Azure

In this exercise, you'll use a Windows Server 2016 VM running in Azure. Since this isn't a Windows Virtual Desktop environment for the lab, Windows 10 Enterprise was not available. You will:

- Deploy a Windows Server 2016 VM in Azure
- Manually add users
- Manually enable AppLocker
- Disable Internet Explorer Enhanced Security Configuration
- Test AppLocker
- You can view the following video on AppLocker in a Windows Virtual Desktop deployment


 


> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Lt59]


>[!NOTE]
> To complete the Exercise unit, you need to have an active Azure subscription. If you choose to perform the exercise in this module, you might incur costs in your Azure subscription. To estimate the cost, refer to 
[Windows Virtual Machines Pricing](https://azure.microsoft.com/pricing/details/virtual-machines/windows/?azure-portal=true). The steps outlined in this lab are for a Windows server 2016 environment.

#### Pre-requisites

To do this exercise, you require:

- An Azure subscription

- The Remote Desktop app for Windows. If you are using an OS other than Windows you will need to use your favorite Remote Desktop software

You can define and deploy VMs on Azure in several ways. This exercise uses the Azure Command Line Interface in Azure Cloud Shell. The steps outlined here are for Windows server environments.

### Task 1: Create a Windows VM by using the Azure Command Line Interface in the Azure Cloud Shell

1. Sign in to the [Azure portal](https://portal.azure.com/) using your Azure credentials.

1. Select the Cloud Shell icon next to the search box. A **Welcome to Azure Cloud Shell banner** opens.

1. You may also receive a prompt stating you have no storage mounted, prompting you to select a subscription and to create storage. Select your subscription and choose to **Create storage** if prompted.

1. In the Azure Cloud Shell terminal window ensure Powershell is chosen as the the selected environment. Select **PowerShell**.

### Task 2: Create a resource group

You now need to create a resource group. An Azure resource group is a logical container into which Azure resources are deployed and managed. The following example creates a resource group named **myResourceGroup** in the **westus** location. Depending on your location, you might select a different option.

1. Enter the following command in the PowerShell CLI:

	```PowerShell
	az group create -n myResourceGroup -l westus
	```

1. Verify your new resource group by using the following. This command gets the Azure resource group in your subscription named myResourceGroup.
	```PowerShell
	Get-AZResourceGroup -Name myResourceGroup
	``` 

### Task 3: Deploy a Windows Server 2016 VM

1. Enter the following commands into the CLI window:

	```PowerShell
	az vm create --resource-group myResourceGroup --name myVM --image win2016datacenter --admin-username myVMadmin
	```

1. Enter the **Admin Password** and confirm it when prompted.

1. When the **Running** message is shown, the machine is being deployed. The Azure resources should take approximately two to three minutes to deploy.

1. When the process is finished, the following output will be shown:

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

### Task 4: Connect to VM

Use the following steps to create a remote desktop session from your local computer. Replace the IP address with the public IP address of your VM. When prompted, enter the admin username specified in the PowerShell command, and the associated password.

1. On a Windows desktop, enter **mstsc** in your search window and select the Remote Desktop Connection app.

1. Select **Show Options**. Enter the IP address of the VM and your administrator credentials, and then select **Connect**. Don't choose to save the sign-on configuration.

1. If you receive a message that, **The identity of the remote computer cannot be verified. Do you want to connect anyway?**, Select **Yes**

### Task 5: Add a standard user

The next step is to add a standard user to the **myVM** server.

1. The Windows Server Manager dashboard should now be available. If not, select **Start**, and then select **Server Manager**.

1. On the Dashboard, select **Tools**, and then select **Computer Management.**

1. Under **System Tools**, select **Local Users and Groups.** Right-click **Users** or activate its context menu, and then select **New User.**

1. Enter a Username, Full name and Description. Enter and confirm a Password, and clear the **User must change password at next login** check box.

1. Select **Create,** and then select **Close.**

1. Select the **Groups** option, and then search for **Remote Desktop Users**.

1. Right-click **Remote Desktop Users** or activate its context menu, and then select **Add to Group...**.

1. In the **Remote Desktop Users** properties interface dialog box, select **Add...**.

1. Add the standard user you created earlier, to this group.

1. Select **OK**.

1. Close the **Computer Management** console.

### Task 6: Enable the AppIDsrv
The Application Identity service determines and verifies the identity of an app. Stopping this service will prevent AppLocker policies from being enforced.

1. Start **Task Manger** by right-click on the **Taskbar** and select **Task Manager**.

1. Select **More Details**, then select the **Services** tab.

1. Scroll down until you see the **AppIDSvc**. Right-click and select **Start**.

1. The **AppIDSrv** service should now be **Running**.

1. Close **Task Manager**.

### Task 7: Disable Internet Explorer Enhanced Security Configuration
To show the power of AppLocker we need to disable the Enhanced Security Configuration (ESC).This protection is enabled by default in Internet Explorer on Windows Server 2016. With ESC disabled, access to the Internet is not checked.

1. In **Server Manager**, select **Local Server**.

1. In the **Properties** panel, locate the **IE Enhanced Security Configuration**, and select the **On** link.

1. Turn off IE ESC for both **Administrators** and **Users** by selecting the **Off** button for each.

1. Start IE. You should see a message that **Internet Explorer Enhanced Security Configuration is not enabled**.

### Task 8: Download and install Visual Studio code 2019

1. Download and install **Visual Studio Community 2019** edition at https://visualstudio.microsoft.com/downloads/
**Visual Studio Community 2019** is free for students, open-source contributors, and individuals.

1. You will see a prompt to run or save the visual studio .exe, select **Run**.

1. During the install, accept all defaults, and select **Continue** and **Install** when prompted during setup. You do not need to install any additional components for this exercise.

1. Start **Visual Studio** to ensure it can run. There's no shortcut by default on desktop or task bar. **Visual Studio** can be found on the start menu under recently added.

1. Close **Visual Studio**.

### Task 9: Enable AppLocker

1. In **Server Manager** select **Tools**, and then select **Local Security Policy**.

1. Under **Security Setting**, select **Application Control Policies**.

1. Expand the **Application Control Policies**. Select **AppLocker**. The AppLocker configuration interface displays.

1. Select **Configure rule enforcement**. The **AppLocker Properties** interface becomes available.

1. In the **Enforcement** tab, these default rules aren't enabled. Select the **Executable rules: Configured** check box to enable executable rules.

> [!Note] Ensure the setting is set to **Enforce rules**, *not* **Audit only**. 
> The **Audit only** setting  will not block any apps, and you may not experience the exercise as written if this setting is selected.

1. Repeat the previous step for **Windows Installer rules:**, **Script rules:** and **Packaged app Rules:**.

1. Select **OK**.

### Task 10: Enable Default AppLocker Rules

1. In the **Local Security Policy** console under **Security Setting** > **Application Control Policies** > **AppLocker**, select **Packaged app Rules** and right click, select **Create Default Rules**.

1. The **(Default Rule) All signed package apps** should be displayed in the right panel.

1. Repeat the step above for **Executable Rules**. You should see the default rules that are created.

1. Select **Executable Rules** in the left panel, right click, select **Create New Rule**.

1. The **Create Executable Rules** panel is displayed. Select **Next**.

1. Under **Actions**, select **Deny**.

1. Now click on **Select...**

1. The **Select User or Group** panel is displayed. In the **Enter the object name to select** box, enter the standard user name you created previously.

1. Select **Check Names**. You should see **myVM\"your standard users login name"**.

1. Select **OK** button.

1. Select **Next**. Then select **Path**, then select **Next**.

1. Select **Browse Folders**. The **Browse For Folder ** File Explorer is displayed.

1. Select **Program Files (x86)**, then select **Microsoft Visual Studio**, then **2019**. Select **OK**.

1. The Path is now **%PROGRAMFILES%\Microsoft Visual Studio\2019**. Select **Next**.

1. Select **Next** on the **Exceptions** panel.

1. Select **Create** on the **Name and Description** panel. 

1. You should now see a new **Deny** rule in the **Executable Rules** panel.

1. Close the **Local Security Policy** window.

### Task 11: Test the AppLocker configuration on our deployed Windows Server 2016 VM

1. Sign out of the deployed Windows Server VM that you configured, and then sign in using the standard user account you created previously.
The rdp session you had open will close on sign out and you will have to start another rdp session and sign in via the rdp client again as described previously.

1. Select the **Start** menu and click on **Visual Studio 2019**.

1. You should see a message that **This app has been blocked by your system administrator**.

When AppLocker rules are enforced in the production environment, any apps that aren't included in the allowed rules are blocked from running.

### Task 12: Clean up the resources

1. You can use the following command to remove the resource group, VM, and all related resources when you no longer require them. Replace the resource group name with the name of the resource group you created (myResourceGroup) in your own environment. If you choose not to delete them, you may incur costs associated with them.

```PowerShell
az group delete --name myResourceGroup
```
1. This process will take 2 to 3 minutes.
