
Windows Virtual Desktop is easier to deploy and manage than traditional Remote Desktop Services (RDS) or virtual desktop infrastructure (VDI) environments. You don't have to provision and manage servers and server roles like the gateway, connection broker, diagnostics, load balancing, and licensing. 

## What you manage vs Microsoft

The following illustration shows what services are managed by Microsoft and what you manage.

:::image type="content" source="../media/3-wvd-architecture.png" alt-text="Diagram that shows what's managed my Microsoft and what's managed by you.":::

## Multi-session Windows 10 deployment

Windows Virtual Desktop lets you use Windows 10 Enterprise multi-session, the only Windows client-based operating system that enables multiple concurrent users on a single virtual machine (VM). Windows Virtual Desktop also provides a more consistent experience with broader application support compared to Windows Server-based operating systems.


## Performance

The integration of **FSLogix profiles** lets you store user profiles as containers on a separate virtual disk. When the user signs in, their virtual disk dynamically attaches in real time to any Windows Virtual Desktop VM, so the local files in the attached virtual disk feel like they're running from the local C:\ drive.

Windows Virtual Desktop gives you options to load balance users on your VM host pools. **Host pools** are collections of VMs with the same configuration assigned to multiple users. For the best performance, you can configure load balancing to occur as users sign in (breadth mode). With breadth mode, users are sequentially allocated across the host pool for your workload. To save costs, you can configure your VMs for depth mode load balancing where users are fully allocated on one VM before moving to the next. Windows Virtual Desktop provides tools to automatically provision additional VMs when incoming demand exceeds a specified threshold.

## Set up process
Microsoft’s Windows Virtual Desktop solution on Microsoft Azure is a fully managed desktop virtualization solution.

As you progress through the Windows Virtual Desktop training, you’ll notice that the setup process abstracts many of the infrastructure roles you might have deployed for RDS in the past. The initial provisioning is focused on hybrid integration and deploying host pools. The configuration focuses on the day-to-day operations like management of session host, identity, app, and storage. 

  
 
![Prepare Deploy Optimize](../media/wvd-prep-deploy-optimize.png)

Use this information to **Prepare > Deploy > Optimize** your Windows Virtual Desktop environments. 
 
| | |
|-|-|
|Prepare <br>![Prepare icon](../media/prepare.png)|In the **Prepare** module, we’ll discuss the following steps to complete before you deploy Windows Virtual Desktop: <br>- Set up Azure Active Directory (Azure AD) <br>- Integrate with Active Directory Domain Services <br> - Create Azure resources <br>- Assign administrator roles<br>-Assign licenses to Windows Virtual Desktop users <br>-Register the DesktopVirtualization provider with your subscription |
|Deploy <br>![Deploy icon](../media/deploy.png)|In the **Deploy** module, we’ll walk through the steps to: <br>- Create a Windows Virtual Desktop host pool and workspace <br>- Make a desktop and apps available to users by using application groups <br>- Customize the workspace <br>- Connect to the workspace by using the Windows Virtual Desktop client 
|Optimize <br>![Optimize icon](../media/optimize.png)|In the **Optimize** module, we’ll walk through the steps to:  <br>- Set up roaming and stateful user profiles by using Azure File Storage and FSLogix <br>- Configure Azure File Sync to sync on-premises files or user profile data to Azure Storage<br>- Scale session hosts by using the scaling tool built on Azure Automation and Azure Logic Apps| 
