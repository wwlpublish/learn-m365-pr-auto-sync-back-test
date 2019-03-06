In the past when you managed an organization that ran Windows PCs you could expect to update those PCs every 2 to 3 years, when the next major version of Windows was released. In between you might also need to deploy service packs to address known issues or security updates. With Windows 10 that cadence – 2 to 3 years between deployments – collapses down from years to months. Windows 10 introduces the idea of Windows as a service, where updates become maintenance tasks instead of major, systematic projects. Updates are smaller and more frequent, making them less disruptive.  

Let’s discuss the different types of updates and how best to deploy them in your organization, based on your specific needs. 
  
## Types of updates 
There are two types of updates in the Windows as a service model: 
 
- **Feature updates** – new functionality, released twice a year. Deploy these updates using your existing tools. Because these new features come out more often, the individual updates themselves are smaller, making it easier to deploy across your organization. It also introduces less change per update – less for your users to get used to with each update. 
- **Quality updates** – Security updates and fixes, usually released one a month. On the second Tuesday of the month (“patch Tuesday”), Microsoft releases a cumulative update that includes all the past quality updates. This helps make sure your devices are up to date and, to make our own testing more effective, more closely aligned to the devices we use for testing at Microsoft.

## Choose the right update channel 
You determine which devices in your environment get which updates when by using channels. There are three servicing channels in Windows as a service: 
 
- **Windows Insider Program** – Get early access to pre-release Windows 10 builds, updated as often as weekly. Use Insider builds to explore and test new and changed features before you deploy them. You can also provide direct feedback to Microsoft on these updates. 
- **Semi-Annual Channel** – Updated twice a year with new features. Devices in the semi-annual channel get updates as soon as Microsoft releases them. You can further control the timing of when specific devices get updated by using the deferral feature (available with Windows Update for Business, Configuration Manager, or Windows Server Update Services) to delay installation. 
- **Long-term Servicing Channel** – Designed to be used only with specialized devices, like ATMs or a PC that runs medical equipment, that can’t be regularly updated or that don’t need to be updated.  The long-term servicing channel is released every two to three years. (Note that the LTSC is updated with security fixes as needed – your devices will be secure.) Office 365 ProPlus isn’t supported on the LTSC. 
 
## Choose the right deployment ring 
Windows 10 uses deployment rings with update channels to control how and when updates are applied to your devices. At its most basic, a deployment ring is a group of devices to update at the same time. The number of rings you need depends on many different considerations, including the number of devices you have, how many different update channels you need to use, or even how many organizations you have in your company. No one can tell you how many rings you should have or which (and how many) devices should go in each ring – that all depends on your org and you’re the expert there.  

By defining and using deployment rings, you can effectively control how feature and quality updates are deployed through your organization. You should start to think about using Windows as a service as an ongoing process, rather than a specific project to update Windows builds. 

Here’s an example deployment ring strategy. These ring names are examples and aren’t related to specific builds. (For example, unlike Office 365 ProPlus, Windows as a service doesn’t have a release called “Targeted.”) Choose ring names that make sense for you. These deployment rings also have different settings for deferring updates – use Windows Update for Business, Configuration Manager, or Windows Server Update Services to control deferral periods. 

|Ring name|Microsoft Channel|Defers feature updates?|Defers quality updates?|Description|
|-|-|-|-|-| 
|Preview|Windows Insider Program|No|No|A small group of devices that can test pre-release builds without affecting productivity. |
|Test|Semi-Annual Channel|No|No|Another group of devices to test the update before you deploy it to the majority of your devices. |
|Organization|Semi-Annual Channel|120 days|7 to 14 days|Most of your users. Use the deferment period to make sure you‘ve thoroughly tested the updates before you deploy them. 
Note: You can pause an update if you run into issues. |
|Line of Business|Semi-Annual Channel|180 days|30 days|Devices that are mission-critical and are only updated once all other devices have successfully updated.  |
|LTSC|Long-term servicing channel|n/a|n/a|Isolated devices that can’t use the Semi-annual Channel. |
