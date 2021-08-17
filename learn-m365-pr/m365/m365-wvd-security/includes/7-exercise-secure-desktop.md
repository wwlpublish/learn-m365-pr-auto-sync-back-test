As a senior administrator working for Contoso, you've been asked to test Microsoft AppLocker for future deployment in your Azure Virtual Desktop environment. In an enterprise, this process is normally done through Group Policy objects, Intune, or Configuration Manager. This exercise doesn't include access to those tools or an Active Directory domain controller.

In this exercise, you'll use a Windows Server 2016 VM running in Azure. Because this isn't an Azure Virtual Desktop environment for the lab, Windows 10 Enterprise is not available. You will:

- Open Azure Cloud Shell.
- Create a resource group.
- Deploy a Windows Server 2016 VM.
- Connect to the VM.
- Add a standard user.
- Enable the AppIDsrv service.
- Disable Internet Explorer Enhanced Security Configuration.
- Download and install Visual Studio Code 2019.
- Enable AppLocker.
- Enable default AppLocker rules.
- Test the AppLocker configuration on our deployed Windows Server 2016 VM.
- Clean up resources.
- Try a demo about using AppLocker.

>[!NOTE]
> To complete this exercise unit, you need to have an active Azure subscription. If you perform the exercise, you might incur costs in your Azure subscription. To estimate the costs, see
[Windows Virtual Machines pricing](https://azure.microsoft.com/pricing/details/virtual-machines/windows/?azure-portal=true). The steps outlined in this lab are for a Windows Server 2016 environment.

You can define and deploy VMs on Azure in several ways. This exercise uses the Azure CLI in Azure Cloud Shell.

## Open Azure Cloud Shell

1. Sign in to the [Azure portal](https://portal.azure.com/) by using your Azure credentials.
1. Select the **Cloud Shell** icon next to the search box. A **Welcome to Azure Cloud Shell** banner opens.
1. You might receive a prompt that says you have no storage mounted, and that asks you to select a subscription and create storage. Select your subscription and choose **Create storage** if you're prompted.
1. In the Azure Cloud Shell terminal window, select **PowerShell** as the environment.

## Create a resource group

You now need to create a resource group. An Azure resource group is a logical container into which Azure resources are deployed and managed. The following example creates a resource group named *myResourceGroup* in the *westus* location. Depending on your location, you might select a different option.

1. Enter the following command in the PowerShell CLI:

  ```PowerShell
  az group create -n myResourceGroup -l westus
  ```

1. Verify your new resource group by using the following command. This command gets the Azure resource group in your subscription named myResourceGroup.

  ```PowerShell
  Get-AZResourceGroup -Name myResourceGroup
  ```

## Deploy a Windows Server 2016 VM

3. Enter the following commands in the CLI window:

  ```PowerShell
  az vm create --resource-group myResourceGroup --name myVM --image win2016datacenter --admin-username myVMadmin
  ```

1. Enter the admin password and confirm it when you're prompted.
1. When the **Running** message appears, the machine is being deployed. The Azure resources should take 2 to 3 minutes to deploy.

   When the process is finished, the following output appears:

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

1. Use the public address in your Remote Desktop connection. Note the address with your administrator password.

## Connect to the VM

Use the following steps to create a Remote Desktop session from your local computer. Replace the IP address with the public IP address of your VM. When you're prompted, enter the admin username specified in the PowerShell command and the associated password.

1. On a Windows desktop, enter **mstsc** in your search window and select the **Remote Desktop Connection** app.
1. Select **Show Options**. Enter the IP address of the VM and your administrator credentials, and then select **Connect**. Don't choose to save the sign-on configuration.
1. If you receive a message that says **The identity of the remote computer cannot be verified. Do you want to connect anyway?**, select **Yes**.

## Add a standard user

The next step is to add a standard user to the **myVM** server.

1. The Windows Server Manager dashboard should now be available. If not, select **Start**, and then select **Server Manager**.
1. On the Dashboard, select **Tools**, and then select **Computer Management**.
1. Under **System Tools**, select **Local Users and Groups**. Right-click **Users** or activate its shortcut menu, and then select **New User**.
1. Enter a username, full name, and description. Enter and confirm a password, and clear the **User must change password at next login** check box.
1. Select **Create**, and then select **Close**.
1. Select the **Groups** option, and then search for **Remote Desktop Users**.
1. Right-click **Remote Desktop Users** or activate its shortcut menu, and then select **Add to Group**.
1. In the **Remote Desktop Users** properties dialog box, select **Add**.
1. Add the standard user that you created earlier to this group.
1. Select **OK**.
1. Close the **Computer Management** console.

## Enable the AppIDsrv service

The Application Identity service (AppIDsrv) determines and verifies the identity of an app. Stopping this service will prevent AppLocker policies from being enforced.

1. Start Task Manger by right-clicking the taskbar and then selecting **Task Manager**.
1. Select **More Details**, and then select the **Services** tab.
1. Scroll down until you see **AppIDSvc**. Right-click it, and then select **Start**.

   The AppIDSrv service should now have a status of **Running**.

1. Close Task Manager.

## Disable Internet Explorer Enhanced Security Configuration

To show the power of AppLocker, we need to disable Enhanced Security Configuration. This protection is enabled by default in Internet Explorer on Windows Server 2016. With Enhanced Security Configuration disabled, access to the Internet is not checked.

1. In Server Manager, select **Local Server**.
1. On the **Properties** panel, find **IE Enhanced Security Configuration** and select the **On** link.
1. Turn off Enhanced Security Configuration for both **Administrators** and **Users** by selecting the **Off** button for each.
1. Start Internet Explorer. You should see the message **Internet Explorer Enhanced Security Configuration is not enabled**.

## Download and install Visual Studio Code 2019

1. Download and install Visual Studio 2019 Community edition on the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/) page. This edition is free.
1. When you're prompted to run or save the Visual Studio .exe file, select **Run**.
1. During the installation, accept all defaults. Select **Continue** and **Install** when you're prompted during setup. You don't need to install any additional components for this exercise.
1. Open Visual Studio to ensure that it can run. There's no shortcut by default on the desktop or the taskbar. You can find **Visual Studio** on the **Start** menu, under **Recently added**.
1. Close Visual Studio.

## Enable AppLocker

1. In Server Manager, select **Tools**, and then select **Local Security Policy**.
1. Under **Security Setting**, select **Application Control Policies**.
1. Expand **Application Control Policies**, and then select **AppLocker**. The AppLocker configuration interface appears.
1. Select **Configure rule enforcement**. The **AppLocker Properties** interface becomes available.
1. On the **Enforcement** tab, these default rules aren't enabled. Select the **Executable rules: Configured** check box to enable executable rules.

    >[!NOTE]
    >Ensure that the setting is set to **Enforce rules**, *not* **Audit only**. The **Audit only** setting won't block any apps, and you might not experience the exercise as written if this setting is selected.

1. Repeat the previous step for **Windows Installer rules**, **Script rules**, and **Packaged app Rules**.
1. Select **OK**.

## Enable default AppLocker rules

1. In the **Local Security Policy** console, under **Security Setting** > **Application Control Policies** > **AppLocker**, right-click **Packaged app Rules**. Then select **Create Default Rules**.

   **(Default Rule) All signed package apps** should appear on the right panel.

1. Repeat the previous step for **Executable Rules**. You should see the default rules that are created.
1. On the left panel, right-click **Executable Rules**, and then select **Create New Rule**.
1. The **Create Executable Rules** panel appears. Select **Next**.
1. Under **Actions**, select **Deny**.
1. Click **Select**.
1. The **Select User or Group** panel appears. In the **Enter the object name to select** box, enter the standard username that you created previously.
1. Select **Check Names**. You should see **myVM\\"your standard users login name"**.
1. Select the **OK** button.
1. Select **Next**, select **Path**, and then select **Next**.
1. Select **Browse Folders**. The **Browse For Folder** file explorer appears.
1. Select **Program Files (x86)** > **Microsoft Visual Studio** > **2019**. Then select **OK**.
1. The path is now **%PROGRAMFILES%\Microsoft Visual Studio\2019**. Select **Next**.
1. Select **Next** on the **Exceptions** panel.
1. Select **Create** on the **Name and Description** panel.

   You should now see a new **Deny** rule on the **Executable Rules** panel.

1. Close the **Local Security Policy** window.

## Test the AppLocker configuration on a Windows Server 2016 VM

1. Sign out of the deployed Windows Server VM that you configured, and then sign in by using the standard user account that you created previously.

   The Remote Desktop session closes on sign-out. You'll have to start another Remote Desktop session and sign in via the Remote Desktop client again, as described earlier.

1. On the **Start** menu, select **Visual Studio 2019**.

   You should see the message **This app has been blocked by your system administrator**.

When AppLocker rules are enforced in the production environment, any apps that aren't included in the allowed rules are blocked from running.

## Clean up resources

You can use the following command to remove the resource group, VM, and all related resources when you no longer need them. Replace the resource group name with the name of the resource group that you created in your own environment (myResourceGroup). If you choose not to delete these resources, you might incur costs associated with them.

```PowerShell
az group delete --name myResourceGroup
```

This process takes 2 to 3 minutes.

## Demo: Use AppLocker in an Azure Virtual Desktop environment

The following video shows how you can use AppLocker to help secure your Azure Virtual Desktop deployment.

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4M709]
