Now that your Windows Virtual Desktop tenant is available and you've set up the other prerequisites, you're ready to build your first host pool. You can use your host pool to provision full desktops and remote apps for users.   

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
   |Resource group     | Create a new resource group or select an existing resource group.    |
   |Host pool name     |  Enter a unique name for your host pool.       |
   |Location    | Azure region where Metadata will be stored        |
   |Host pool type     |  Pooled  or personal. Pooled is where several users sign in and share a VM. Typically, none of those users would be a local administrator on the pooled VM. Personal is where each user has their own dedicated VM and they'd typically be a local administrator for that VM. Select personal where you're using Windows 10 single session. If you select personal, you select the assignment type: automatic or direct. |
   |Max session limit    | Enter the maximum number of users you want load-balanced to a single session host.|
   |Load balancing algorithm    | Choose either breadth-first or depth-first, based on your usage pattern. |
1. Select **Next: Virtual Machines**.

### Step 2: Virtual Machines

1. Select **Yes** to add virtual machines. 
1. Use the information in the following table to fill out the virtual machine tab.

   :::image type="content" source="../media/2-create-host-pool-vm.png" alt-text="Screenshot of the Windows Virtual Desktop create host pool virtual machine tab.":::


    Field  |Description  |
   |---------|---------|
   |Add virtual machines     | if you've already created virtual machines and want to use them with the new host pool, select No. If you want to create new virtual machines and register them to the new host pool, select Yes.        |
   |Resource group    |  Choose the resource group where you want to create the virtual machines. This can be a different resource group than the one you used for the host pool.       |
   |Virtual machine location     | Region where you want to create the virtual machines. The location can be same or different from the region you selected for the host pool.        |
   |Virtual machine size     | Choose the size of the virtual machine you want to create. You can either keep the default size as-is or select Change Size to pick a size more suitable for your workload.        |
   |Number of VMs     |  Provide the number of VMs you want to create for your host pool. The setup process can create up to 400 VMs while setting up your host pool, and each VM setup process creates four objects in your resource group. The creation process doesn't check your subscription quota. So make sure the number of VMs you enter is within the Azure VM and API limits for your resource group and subscription. You can add more VMs after you finish creating your host pool.      |
   |Name prefix     |  Name the virtual machines the setup process creates. The process adds numerical suffixes to each VM starting with 0.       |
   |Image type     |  Choose the image type Azure uses to create the virtual machine. You can choose either Gallery or Storage blob.  Gallery allows you to pick a recommended image like Windows 10 Enterprise multi-session + Office 365. Storage blob allows you to use your own image built through Hyper-V or on an Azure VM.  |
   |Image     |  For Gallery, select one of the recommended images from the drop-down menu. If you don't see the image you want, select Browse all images and disks. Browse lets you select another image in your gallery or an image provided by Microsoft and other publishers.        |
   |Image URI    |   For Storage blob, add the URL to the generalized VHD from your Azure Storage account. |
   |OS disk type     | Choose what kind of OS disks you want your VMs to use: Standard SSD, Premium SSD, or Standard HDD.     |
   |Use managed disks     | For Storage blob image type, we recommend you choose yes for most VM configurations. You'd choose no where you want to use unmanaged disks for classic scenarios or to manage VHDs in your storage account.  |
   |Storage account     | For Storage blob image type, select the Azure storage account that contains your image.       |
   |Virtual network     |  Select virtual network you've created that can connect to the domain controller. You'll need to join the virtual machines inside the virtual network to the domain.       |
   |Public IP     | Select whether or not you want a public IP for the virtual machines. We recommend you select No, because a private IP is more secure.        |
   |Network security group    | Select what kind of security group you want: Basic, Advanced, or None. If you choose Advanced, select an existing network security group that you've already configured.        |
   |Public inbound ports     | If you select Basic, select yes or no to specify whether you want inbound ports open.        |
   |inbound ports to allows     | For public inbound ports, choose from the list of standard ports like HTTP (80), HTTPS (443), SSH (22), RDP (3389).      |
   |Specific domain or unit     | Select yes to have the virtual machines joined to a specific domain or organizational unit. If you choose Yes, specify the full Active Directory domain name to join like contoso.com. You can also add a specific organizational unit for the virtual machines to be in.        |
   |AD domain join UPN     | Enter the credentials for the Active Directory Domain administrator for the virtual network you selected.  This account is used to join the VMs to your domain.      |
   |Password    | Enter the password for the Active Directory Domain administrator's account.   |
   |Confirm password    | Confirm the password for the Active Directory Domain administrator's account.      |
1. Select **Next: Workspace**.

### Step 3: Workspace

1. For **Register desktop app group**, select **Yes**.
1. For **To this workspace**, select **Create new**.
1. Enter a name for the workspace.

   :::image type="content" source="../media/2-create-workspace.png" alt-text="Screenshot of workspace tab that shows how to create new workspace.":::
1. Select **Next: Tags**.

### Step 4: Tags (Optional)

We recommend that you use tags to logically organize your Azure resources, resource groups, and subscriptions into a taxonomy. You might use tags to organize by workload, environment, ownership, or other important criteria. Tags aren't unique to Windows Virtual Desktop and aren't crucial to our scenario, so you can skip this step.

## Validate the basic Windows Virtual Desktop environment 
