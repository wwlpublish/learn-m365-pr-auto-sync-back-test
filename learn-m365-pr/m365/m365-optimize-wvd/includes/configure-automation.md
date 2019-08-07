(Introductory sentence)
 
## Automated scaling with Windows Virtual Desktop 
Windows Virtual Desktop provides tools and approaches to automate scaling virtual machine resources within host pools. A primary benefit of hosting your remote desktop service in the cloud is that you can shut down compute resources to save costs during off-peak hours, then restart them on schedule or dynamically based on session host utilization. 

The scaling scripts include logic to periodically determine activity levels in virtual machines before draining underutilized user session hosts and shutting them down. This can be performed on schedule after hours to reduce the number of running virtual machines and the inverse scenario where additional virtual machines are provisioned dynamically as user density within virtual machines exceeds pre-defined thresholds to trigger scaling. 

You can download the scaling scripts from GitHub at [https://aka.ms/WVDscaling](https://aka.ms/WVDscaling). They currently run in the context of a connected virtual machine using scheduled tasks. In the future, scaling operations will use Azure Automation.