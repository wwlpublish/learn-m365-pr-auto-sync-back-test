To deploy Azure Virtual Desktop, we'll start by creating a host pool, specifying our session host VMs, and creating a workspace. This process creates a desktop application group. We'll then assign that application group to a user and verify they can see the virtual desktop in their workspace.

The following steps provide some initial values for you to use to test out Azure Virtual Desktop. Review the available options to plan and customize your deployment to match your organization's needs.

To complete the exercise, you'll need the Azure credentials for:

- A user account that's assigned to the Active Directory Domain administrator role
- A non-administrative user account that's in Active Directory

## Create a host pool by using the Azure portal

### Step 1: Basics

1. [Sign in](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true) to the Azure portal.
1. Use the search box to find **Azure Virtual Desktop**.
1. Select **Create a host pool**.
1. Enter the appropriate information into the **Basics** tab.

   :::image type="content" source="../media/3-create-host-pool.png" alt-text="Screenshot of the Azure Virtual Desktop create host pool basic tab.":::

   |Field  |Value  |
   |---------|---------|
   |Subscription     |  Subscription where you want Azure Virtual Desktop to run       |
   |Resource group     | Resource group you've created for Azure Virtual Desktop resources    |
   |Host pool name     |  wvd-host-pool-1      |
   |Location    | Region where you want the metadata for your host pool stored        |
   |Validation environment|No|
   |Host pool type     |  Pooled  |
   |Load balancing algorithm    | Breadth-first |
   |Max session limit    |Maximum number of users you want load-balanced to a single session host|

1. Select **Next: Virtual Machines**.

### Step 2: Virtual Machines

1. Select **Yes** to add virtual machines.
1. Use the information in the following table to fill out the virtual machine tab.

   :::image type="content" source="../media/3-create-host-pool-vm.png" alt-text="Screenshot of the Azure Virtual Desktop create host pool virtual machine tab.":::

    Field  |Value |
   |---------|---------|
   |Add virtual machines     | Yes        |
   |Resource group    |  Resource group you've created for Azure Virtual Desktop resources       |
   |Name prefix     | wvd-vm-pool        |
   |Virtual machine location     | Region needs to be same location as your virtual network       |
   |Availability options     | Availability zone        |
   |Availability zone     | 2        |
   |Image type     |  Gallery  |
   |Image     |  Windows 10 Enterprise multi-session, Version 1909 |
   |Virtual machine size     | Keep the default size       |
   |Number of VMs     | 2  |
   |OS disk type     | Standard SSD  |
   |Use managed disks     | Yes |
   |Boot diagnostics     |  Enable with managed storage account |
   |Virtual network     |  Virtual network that can connect to the domain controller     |
   |Network security group    | Basic       |
   |Public inbound ports     | No   |
   |Select which directory you would like to join     |Active Directory    |
   |AD domain join UPN     | User name for the user account that's assigned to the Active Directory Domain administrator role      |
   |Specify domain or unit    | No   |
   |Username    | Select a username for your VM administrator       |
   |Password    | Select a password for your VM administrator       |
   |Confirm    | Confirm the password      |
   |ARM template file URL    | Leave blank       |
   |ARM template parameter file URL    | Leave blank       |
1. Select **Next: Workspace**.

### Step 3: Workspace

1. For **Register desktop app group**, select **Yes**.
1. For **To this workspace**, select **Create new**.
1. Enter a name for the workspace.

   :::image type="content" source="../media/3-create-workspace.png" alt-text="Screenshot of workspace tab that shows how to create new workspace.":::
1. Select **Review + create**.
1. Review what you've entered and select **Create**.

## Assign desktop application group to user

Assign the desktop application group to a non-administrative user account that's in Active Directory.

1. Select **Application groups**.
1. Select the desktop application group.
1. Select **Access control (IAM)** > **Add** > **Add role assignment**.
1. For **Role**, select **Desktop Virtualization User** and select **Next**.
1. Beside Members, select **+ Select Members**. Find and select the name of a non-administrative user account that's in Active Directory and select **Select**.
1. Select **Next**.
1. Select **Review + Assign**.

## Verify access to desktop

1. Go to the [Azure Virtual Desktop web client](https://rdweb.wvd.microsoft.com/arm/webclient/index.html).
1. Sign in by using the user credentials for the user you assigned to the desktop application group.
1. You should see a virtual desktop.
