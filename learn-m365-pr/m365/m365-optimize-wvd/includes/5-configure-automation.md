Azure Virtual Desktop provides tools and approaches to automate scaling virtual machine (VM) resources in your host pools. One of the primary benefits to hosting Remote Desktop Service in the cloud is that you can shut down compute resources to save costs during off-peak hours, and then restart them either on a schedule or dynamically, based on session host utilization.

## Scale session hosts using Azure Automation

The scaling tool used for Azure Virtual Desktop is built with Azure Automation and Azure Logic Apps. It will automatically scale session host virtual machines in your Azure Virtual Desktop environment.

Use the scaling tool to:

- Schedule VMs to start and stop based on Peak and Off-Peak business hours.
- Scale out VMs based on number of sessions per CPU core.
- Scale in VMs during Off-Peak hours, to leave the minimum number of session host VMs running.

The scaling tool can manage:

- Only to pooled session host VMs
- VMs in any region, but can only be used in the same subscription as your Azure Automation account and Azure Logic Apps

The following steps describe the high-level process you use to set up the scaling tool for Azure Virtual Desktop session hosts.

1. *Create an Azure Automation account*: Download and run the Azure PowerShell script createazureautomationaccount.ps1 from the [scaling script repository](https://aka.ms/WVDscaling) in GitHub.
1. *Create an Azure Automation Run As account*: In the Azure portal, from the Automation account you've created, add an Azure Run As Account. This process creates an asset named AzureRunAsConnection in the Automation account. The connection asset holds the application ID, tenant ID, subscription ID, and certificate thumbprint.
1. *Create a role assignment in Azure Virtual Desktop*: Use the Azure Virtual Desktop PowerShell module to create a role assignment so that AzureRunAsConnection can interact with Azure Virtual Desktop.
1. *Create the Azure Logic App and run schedule*: Download and run the Azure PowerShell script createazurelogicapp.ps1 from the [scaling script repository](https://aka.ms/WVDscaling) in GitHub.

For step-by-step instructions and to learn more about this tool, review the links at the end of this module.
