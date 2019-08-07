(introductory sentence)

## Locate ‘Windows Virtual Desktop – Provision a host pool’ in Azure Marketplace 
Now that your Windows Virtual Desktop tenant is available and other pre-requisites are in place, we’ll build our first host pool and then move on to provisioning both full desktops and remote apps to users.   

To get started, log in to the Azure portal at [https://portal.azure.com](https://portal.azure.com). 

- In the upper left corner, click **Create a Resource.**
- In **Search the Marketplace**, type "Windows Virtual Desktop." 
- Click on **Windows Virtual Desktop – Provision a host pool**. 
- Now click **Create** to open a 6-step wizard. 

## Provisioning a Windows Virtual Desktop host pool 
This process uses an Azure Resource Manager template to build out Windows Virtual Desktop environments in repeatable way.

- First, we’ll give the host pool a name – such as "My first host pool." 
- Now, we’re presented with our first choice – a **personal** or **pooled** desktop. 
   - A **personal desktop** is where each user has their own personal virtual machine. This is useful if the virtual machines need to be dedicated to one user each and those users are local administrators.
   - A **pooled desktop** allows multiple user accounts to log into the same virtual machine at the same time. Pooled desktops are more efficient and less expensive to run from a cost per user perspective. Because several users share the same virtual machine, the users will not be local admins, so you’ll need another process to install applications and configure the virtual machine. 
- Select **pooled** to maximize resource utilization; and later we’ll select a corresponding Windows 10 Enterprise multi-session image for the host pool. 
- Next, define the **Default desktop users**. This is a comma-separated list of user email accounts from your Azure Active Directory. You can add an email address – also known as a User Principal Name (UPN) – or several UPNs with commas between them.  
- Now, select the same **Azure subscription** we used when working on the pre-requisites 
- Next for **Resource Group**, be sure to create a new one. Give it a name without spaces or special characters. 
- In the **location** field, we recommend selecting **East US 2** during preview.

Now with the basics out of the way, we can move on to **Step 2**. 

- The first choice here is the **Usage Profile** – as you make changes, the **Total Users** value will change, indicating what is **Light** vs. **Medium** vs. **Heavy**. 
- Now specify the number of **total users** – the default is 100 users, but as you change the number, you’ll see the recommend VM count change. By entering 25 with a Medium usage profile, you’ll see the VM count go to 1 
- If you want to change the recommended VM size, click change size 
- Now you can select your VM size. If you want to save costs or are using free Azure credits with a trial, you can select a less powerful virtual machine.  
- Now provide a **Virtual Machine name prefix**, for example **WVD** and click **OK**. 

Now we have the basics and VM settings configured, let’s move on to **Step 3**. 

- Here’s where we select the Windows image we want to use. The **image source** can be: 
   - One of your own images stored in Azure blob storage – which will let you input an **imageURI** – this is a fully qualified path including the VHD filename  
   - A **managed image** is one you’ve customized and defined as managed. Here you’ll specify the image name and the Resource Group 
   - A **gallery** image, is a pre-configured image from Microsoft for the WVD service. You’ll see images for: 
      - Windows 10 Enterprise Multi-session with Office 365 ProPlus
      - Windows 10 Enterprise Multi-session
      - Windows Server 2016 
   - Choose **Windows 10 Enterprise multi-session with Office 365 ProPlus**. 
- Select the disk type, it’s recommended to keep **Premium SSD**. 
- Next enter the credentials used for automated domain join – this is for ADDS – usually your on-premises domain. Optionally you can input a different domain or organizational unit 
- Now in the **virtual network**, we need to select a VNET where the virtual machines can communicate with the domain and directory services.
   - Select the virtual network you created to connect your virtual machines to ADDS. 
   - Now select the subnet to complete step 3. 

Next in **Step 4**, we’ll configure authentication to your WVD environment. This what we created in the PowerShell steps in module 1. 

- In **Windows Virtual Desktop tenant group name** – you’ll want to keep this as Default Tenant Group.
- The **Windows Virtual Desktop tenant name** needs to be the one you added in PowerShell in module 1.
- Now we can use a **User Principal Name (UPN)** or **service principal** account. Service principals are recommended for automated scenarios and if you’re using multi-factor authentication, you’ll need to use a service principal.  
- To keep this simple, use a UPN from your Azure AD and if you’re using Azure ADDS, remember this should be an ADDS administrator account. 
- Enter the password and confirm. 
- Now, click **OK** and move on to Steps 5 and 6; your configuration steps are complete. 

Step 5 is simply a confirmation page, and Step 6 is where you’ll click **Create** to start the provisioning process. In most cases, this will complete in a few minutes and when you’re finished, you’ll have a full desktop environment to log into. Azure will notify you once provisioning is complete. 

## Validating the basic Windows Virtual Desktop environment 
Now after the deployment completes successfully, we’ll sign into Windows Virtual Desktop via the browser to validate the deployment. 

- Open an InPrivate or Incognito browser window and go to [http://aka.ms/wvdweb](http://aka.ms/wvdweb). 
- Use the account specified in **Step 1 > Default desktop users** before. 
- You’ll see the **Windows desktop** option for the image we deployed. 
- Open it and enter the credentials again for the ADDS authentication and you’ll see a full desktop Windows 10 Enterprise multi-session with Office 365 ProPlus environment. 
- Open the Windows 10 Start or click on apps in the Taskbar to make sure everything is working. 
- Now close the session simply by closing the browser window.  