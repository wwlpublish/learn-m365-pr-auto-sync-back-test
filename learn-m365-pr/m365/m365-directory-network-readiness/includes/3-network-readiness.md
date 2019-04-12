When it comes to preparing your network, you need to open specific ports and protocols, so the installation and update tools can make the connections they need, and plan for increased demand on the network, which can impact day-to-day performance.

## Ports and protocols
When looking at the network requirements for your Microsoft 365 deployment, you need to make sure that the right ports and protocols are open. Microsoft created a web service to publish the Office 365 endpoints - this helps you identify which network traffic is related to Office 365 ProPlus. You can learn more about the ports, protocols, and endpoints at [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) in the Office 365 ProPlus technical library. (This link opens in the same window, so be sure to come back here to finish the module.)

## Increased network demand
There are three main components in a deployment that will have an impact on your network: PC imaging, software updates, and user personalization. Between them, this can mean in excess of 20 GB per PC for the initial migration, and often 1 GB or more per month per PC to stay up-to-date. 

### PC imaging and app installations
For Windows images with no customization you should plan typically for 3GB per PC, while for customized images with apps you may need to allow 6GB or more. You may also need to consider driver packages; these can be a few hundred megabytes per PC, sometimes up to 1GB.

Other installations (as opposed to updates, which are discussed below) can also impact your network bandwidth, including the initial installation of Office apps and any language support for deployments (of Office or Windows) that use multiple languages.  

## Software updates
Windows 10 and Office 365 ProPlus use a new servicing model delivering monthly and semi-annual updates, covered later in this learning path. The new servicing model includes feature updates for Windows twice a year, Office Semi-Annual Channel updates, and monthly Windows and Office quality updates.

Feature updates are typically 2 – 4GB in size, and Office Semi-Annual Channel updates are 300 – 400 MB per update. Monthly quality updates may range from a few hundred megabytes to over a gigabyte because monthly updates are cumulative -  these increase in size over the servicing lifetime for each Windows 10 version. (Microsoft offers tools to help reduce the amount of data that must pass over the network to implement updates, which we'll talk about later in this module.)

### User personalization
The third component to consider is user personalization. Here you’ll need to plan network bandwidth to accommodate the restoring of user files, their settings, and their applications as part of the PC refresh or replacement process. Together, these items often exceed 20 GB per PC; for some users these may exceed 100 GB.