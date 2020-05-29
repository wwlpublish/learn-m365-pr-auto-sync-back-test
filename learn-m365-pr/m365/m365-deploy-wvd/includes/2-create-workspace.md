With all prerequisite steps complete, you're ready to create a Windows Virtual Desktop workspace. The workspace is used to group your host pools and to identify your resources in later provisioning and customization steps.

## Register the DesktopVirtualization provider

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Subscriptions**.
1. Select the subscription you want to use with Windows Desktop Virtualization.
1. Under **Settings**, select **Resource provider**.
1. In the filter box, search for and then select **Microsoft.DesktopVirtualization**.
1. Select **Register**.

   :::image type="content" source="../media/2-register-provider.png" alt-text="Screenshot of resource provider listed and register button highlighted.":::

   It may take a minute for the status to change to **Registered**.



## Create a host pool by using the Azure portal


### Step 1: Basics

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Windows Virtual Desktop**.
1. Select **Create a host pool**.
1. Enter the appropriate information into the **Basics** tab.

   :::image type="content" source="../media/2-create-host-pool.png" alt-text="Screenshot of the Windows Virtual Desktop create host pool basic tab.":::


   |Field  |Description  |
   |---------|---------|
   |Subscription     |  Subscription where you want Windows Virtual Desktop to run.       |
   |Resource group     | Resource group that contains the other Azure resources needed to support Windows Virtual Desktop.      |
   |Host pool name     |  Enter a unique name for your host pool.       |
   |Location    | Azure region where Metadata will be stored        |
   |Host pool type     |  Pooled  or personal. If you select personal, you select the assignment type: automatic or direct. |
   |Max session limit    | Enter the maximum number of users you want load-balanced to a single session host.|
   |Load balancing algorithm    | Choose either breadth-first or depth-first, based on your usage pattern. |
1. Select **Next: Virtual Machines**.

### Step 2: Virtual Machines

1. Select **Yes** to add virtual machines. 
1. Use the information in the following table to fill out the virtual machine tab.

   :::image type="content" source="../media/2-create-host-pool-vm.png" alt-text="Screenshot of the Windows Virtual Desktop create host pool virtual machine tab.":::


    Field  |Description  |
   |---------|---------|
   |Add virtual machines     |         |
   |Resource group    |         |
   |Virtual machine location     |         |
   |Virtual machine size     |         |
   |Number of VMs     |         |
   |Name prefix     |         |
   |Image type     |         |
   |Image     |         |
   |OS disk type     |         |
   |Use managed disks     |         |
   |Virtual network     |         |
   |Public IP     |         |
   |Network security group    |         |
   |Public inbound ports     |         |
   |inbound ports to allows     |         |
   |Specific domain or unit     |         |
   |AD domain join UPN     |         |
   |Password    |         |
   |Confirm password    |         |
1. Select **Next: Workspace**.

### Step 3: Workspace

1. For **Register desktop app group**, select **Yes**.
1. For **To this workspace**, select **Create new**.
1. Enter a name for the workspace.

   :::image type="content" source="../media/2-create-workspace.png" alt-text="Screenshot of workspace tab that shows how to create new workspace.":::
1. Select **Next: Tags**.

### Step 4: Tags (Optional)

We recommend that you use tags to logically organize your Azure resources, resource groups, and subscriptions into a taxonomy. You might use tags to organize by workload, environment, ownership, or other important criteria. Tags aren't unique to Windows Virtual Desktop and aren't crucial to our scenario, so you can skip this step.
<!--
This is done in the UI now. Need to mention PS module and cmds. 
Az.DesktopVirtualization
-->
<!--
All steps are different now. It's on docs. https://docs.microsoft.com/en-us/azure/virtual-desktop/create-host-pools-azure-marketplace 
"Also, make sure you've registered the Microsoft.DesktopVirtualization resource provider. "
https://techcommunity.microsoft.com/t5/windows-it-pro-blog/getting-started-windows-virtual-desktop-arm-based-azure-portal/ba-p/1374466
-->

## Create the workspace by using Azure PowerShell