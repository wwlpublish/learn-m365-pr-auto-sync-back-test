**Windows client** is a comprehensive desktop operating system that allows you to work efficiently and securely. It's important to keep the desktop operating system up to date because it helps devices run efficiently and stay protected. **Windows-as-a-Service (WaaS)** is a new way to work with the Windows desktop. The WaaS model is designed to make life simpler for both users and IT professionals. WaaS maintains a consistent and current Windows client experience for users.

### Release Types

With Windows client, there are two release types:

 -  **Feature updates** add new functionality and are released twice a year. Because these updates are more frequent, they're smaller. There are many benefits:
     -  There's less disruption and effort to apply new features.
     -  Users are more productive with earlier access to new Windows features.
     -  Users take less time to adapt to smaller changes.
     -  The workload and cost impact of updating Windows is reduced.
 -  **Quality updates** provide security and reliability fixes. These updates are issued once a month as **non-security releases** or **combined security + non-security releases.** Non-security releases allow IT admins to do an early validation of content. In addition, a cumulative update is released which includes all previous updates. There are a couple of benefits:
     -  Identified security issues are fixed and deployed quickly, helping to keep devices secure.
     -  Everyone receives security fixes regularly, keeping all devices aligned.

### Servicing channels

**Servicing channels** are the first way to separate users into deployment groups for feature and quality updates. There are three servicing channels. Each channel each provides different levels of flexibility for when these updates are delivered to client computers.

 -  **Windows Insider Program** provides organizations with the opportunity to test and provide feedback on features that will be shipped in the next feature update. These features will be delivered as soon as possible during the development cycle through a process called flighting. This process will allow organizations to see exactly what Microsoft is developing and start their testing as soon as possible. Microsoft recommends that all organizations have at least a few devices enrolled in this program.
 -  **General Availability Channel** provides new functionality with feature update releases annually. Organizations can choose when to deploy updates. This model is ideal for pilot deployments and testing of feature updates. It's also ideal for users such as developers who need to work with the latest features.
 -  **Long-term servicing channel** is designed for specialist devices that don't run Office apps such as medical equipment or ATMs. This channel receives new features every two or three years.

### Deployment rings

**Deployment rings** are a deployment method used to separate devices into a deployment timeline. Microsoft has found that a ring-based deployment works well. Each “ring” comprises a group of users or devices that receive a particular update together. IT administrators set criteria to control delay time or completion that should be met before deployment to the next broader ring of devices or users can occur.

A common ring structure uses three deployment groups:

 -  **Preview** is for planning and development.
     -  The purpose of the preview ring is to evaluate the new features of the update.
 -  **Limited** is for pilot and validation.
     -  The purpose of the limited ring is to validate the update on representative devices across the network.
 -  **Broad** is for wide deployment.
     -  Once the devices in the limited ring have had a sufficient stabilization period, it’s time for broad deployment across the network.

### Deployment methods for Windows

To successfully deploy Windows in your organization, it's important to understand the different ways that it can be deployed. There are three types of deployment categories or methods:

 -  **Modern deployment methods** embrace both traditional on-premises and cloud services to deliver a streamlined, cost effective deployment experience. These methods are recommended and are supported with existing tools such as Microsoft Deployment Toolkit (MDT) and Microsoft Endpoint Configuration Manager.
 -  **Dynamic deployment methods** enable you to configure applications and settings for specific use cases without having to deploy a new custom organization image to the device.
 -  **Traditional deployment methods** use existing tools to deploy operating system images.

#### Modern deployment methods

 -  **Windows Autopilot** allows IT professionals to customize the out-of-box experience (OOBE) to deploy apps and settings that are pre-configured for your organization. Users can go through the deployment process independently, without the need to consult their IT administrator.
 -  **In-place upgrade** provides a simple, automated process that uses the Windows setup process to upgrade from an earlier version of Windows. This process automatically migrates existing data, settings, drivers, and applications. In-place upgrade requires the least IT effort, because there's no need for any complex deployment infrastructure.

#### Dynamic deployment methods

 -  **Subscription activation** uses a subscription to switch from one edition of Windows to another when a licensed user signs into a device. For example, you can switch from Windows 10 Pro to Windows 10 Enterprise.
 -  **Azure Active Directory (Azure AD) joined with automatic mobile device management (MDM) enrollment** automatically joins the device to Azure AD and is configured by MDM. The organization member just needs to provide their work or school user ID and password.
 -  **Provisioning package configuration** uses the Windows Imaging and Configuration Designer (ICD) tool. This tool is used to create provisioning packages that contain all the configuration, settings, and apps that can be applied to devices.

#### Traditional deployment methods

 -  **New computer,** or also called bare metal, is when you deploy a new device or wipe an existing device and deploy with a fresh image.
 -  **Computer refresh,** or also called wipe-and-load, is when you redeploy a device by saving the user state, wiping the disk, then restoring the user state.
 -  **Computer replace** is when you replace an existing device with a new one. You replace the device by saving the user state on the old device and then restoring it to the new device.

### Manage Windows-as-a-Service

In **Configuration Manager**, you can view the state of WaaS in your environment. You can create servicing plans to form deployment rings and ensure that Windows systems are up to date when new builds are released. You can also view alerts when Windows clients are near end of support for the build version.
