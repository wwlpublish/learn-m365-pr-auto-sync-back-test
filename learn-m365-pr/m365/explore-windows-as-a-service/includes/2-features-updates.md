Feature Updates and quality updates work together to ensure you are up to date with the latest Windows enhancements and features.

> [!VIDEO https://www.youtube.com/embed/qSAsiM01GOU]

In the Windows as a service (WaaS) model Microsoft no longer provides major operating system revisions every few years, with significant servicing updates (known as service packs) between these major revisions. Instead, consider Windows updates as an ongoing maintenance task rather than a periodic operating system upgrade project. The Windows operating system receives revisions and updates more frequently, and they are applied with less disruption and effort. These updates fall into two categories: 

- **Feature updates**. These add new functionality and are released twice a year. You can deploy these updates using existing management tools. Because the updates are more frequent, they are smaller, so users take less time to adapt to changes. Consequently, the workload and cost impact on organizations is reduced. 
- **Quality updates**. These are security updates and fixes, usually issued once a month. On the second Tuesday of each month (“patch Tuesday”), a cumulative update is released that includes all previous updates. This helps to ensure that devices are fully up to date and more closely align to those used for testing in Microsoft. 

You can control how and when updates are applied with servicing channels and deployment rings:

**Servicing channels**: There are three Windows as a service servicing channels: 
- Windows Insider Program: Updated as often as weekly with the latest builds. Use Insider builds to test updates before you deploy them in your organization. You can also provide feedback on the updates.
- Semi-Annual Channel (SAC): Updated twice a year with feature udpates.
- Long Term Servicing Channel (LTSC). Designed to use only on specialized devices that don't need regular updates, updated every two to three *years*. Generally if you have a device that doesn't run Office but does run custom line-of-business apps, that's a good candidate for the LTSC.

**Deployment rings**: Groups of devices used to test and deploy Windows releases. You assign devices to deployment rings based on which servicing channel works best.

Next, let's learn when to use the different servicing channels and how deployment rings help with that.