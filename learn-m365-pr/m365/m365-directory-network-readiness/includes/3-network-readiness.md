## Planning for bandwidth considerations and requirements

When it comes to preparing your network for a deployment, you need to take into consideration any and all components that have an impact on bandwidth. The most important considerations are:

- PC imaging and app installations
- Software updates
- User personalization

**PC imaging and app installations.** For Windows images with no customization you should plan typically for 3GB per PC, while for customized images with apps you may need to allow 6GB or more. You may also need to consider driver packages; these can be a few hundred megabytes per PC, sometimes up to 1GB.

Other installations (as opposed to updates, which are discussed below) can also impact your network bandwidth, including the initial installation of Office apps and any language support for deployments (of Office or Windows) that use multiple languages.  

**Software updates.** Windows 10 and Office 365 ProPlus use a new servicing model delivering monthly and semi-annual updates, covered later in this learning path. The new servicing model includes feature updates for Windows twice a year, Office semi-annual channel updates, and monthly Windows and Office quality updates.

Feature updates are typically 2 – 4GB in size, and Office semi-annual channel updates are 300 – 400 MB per update. Monthly quality updates may range from a few hundred megabytes to over a gigabyte because monthly updates are cumulative -  these increase in size over the servicing lifetime for each Windows 10 version. (Microsoft offers tools to help reduce the amount of data that must pass over the network to implement updates, which we'll talk about later in this module.)

**User personalization.** You'll need to plan network bandwidth to accommodate the restoring of user files, their settings, and their applications as part of the PC refresh or replacement process. Together, these items often exceed 20 GB per PC; for some users these may exceed 100 GB.