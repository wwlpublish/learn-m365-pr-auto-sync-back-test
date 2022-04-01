Deployments consist of the activities that make a computer device available for use. The general deployment process consists of several interrelated activities with possible transitions between the build and deployment phases.

The desktop deployment life cycle provides a framework for the tasks required to successfully deploy a software application or operating system. Understanding the life cycle phases to properly plan for the resources and tools that are required for an effective implementation. The key phases of the desktop deployment life cycle are Building and Deploying.

#### Building

The building phase provides the opportunity to improve efficiencies when developing a strategy for a base OS configuration. Its key steps include:

 -  **Streamlining the deployment process**. This step includes developing automated solutions and procedures that you can use for deployment.
 -  **Developing the deployment process.** If using traditional imaging, this may consist of a baseline OS image. When using newer features such as Windows Autopilot, this might involve creating a base device configuration.
 -  **Testing**. Without a test system, you may fail to identify and correct errors before deployment. Virtual machines are commonly used to simulate deployment and validate configurations quickly and effectively, however, a testing plan should include testing deployments to physical devices prior to deployment.
 -  **Configuration**. This step includes developing an automation solution, testing and configuring standardized images or device configurations, accounting for IT labor to configure computers, and planning for network access configuration.
 -  **Managing the logistics**. This step includes storing computers, deploying and setting up physical hardware, and communicating to end users. This step can also include providing the hardware vendor with configuration requirements to be done by the vendor before shipping the device to the organization.

#### Deployment

After you build and test your baseline OS, you can begin deploying them and ensure they are stable and usable. A typical deployment takes place in phases throughout the networking environment. The deployment team stabilizes each phase before progressing to performing upgrades or installations. Early phases can be used to validate scenarios such as device configuration profiles, image configurations, the end-user experience, application deployment success, and so forth.

#### Enrollment

With enrollment, there's no operating system deployment. The existing device becomes a recognized entity within the organization and is then allowed to access resources. With devices that already have Windows 10 and later, modern methods don't require the OS to be re-deployed to configure the device. Instead, by enrolling the device and using Windows Autopilot, the device is reconfigured to the organization's requirements.

Enrollment can also be used for mobile devices, as well as supporting bring-your-own-device (BYOD) scenarios. The scenarios supported can range from accessing e-mail using the user's personal device, to deploying organizational applications and complete management of the device.

The requirements for each organizational group within each use-case scenario. You might have different sets of requirements for each of your use-case and sub-use-case scenarios, and their associated organizational groups and mobile device platforms. You may define which devices you are willing to support and the minimum required configurations to access a resource. For example, your organizational device requirements might require devices to enroll with a more restrictive set of device settings, like a PIN of 6 characters or disabled cloud backup. BYOD scenarios may be less restrictive and allow a four character PIN and cloud backup.

#### Data Migration

Even with a successful deployment, loss of data is almost always an unacceptable result. Many organizations are moving to cloud solutions such as Microsoft 365 or OneDrive to minimize or even eliminate the need for data migration. Organizations should ensure users are aware of and using the supported options available to them. Considerations must be made for scenarios where cloud solutions aren't available or feasible. There are several solutions available that this course will cover, but it's important to understand that data is a critical part of the process. When planning for data during a deployment, some best practices are:

 -  **Migrate important data to a cloud or non-local solution prior to deployment.** It is generally easier and safer than trying to continue the risk and solving the problem after a migration. Tools like *Known Folder Move* can help with seamless migrations of local data to the cloud. When cloud solutions aren't feasible, consider migrating data to network file shares or Work folders. Use features like *Enterprise State Roaming* to migrate common settings.
 -  **Use in-place upgrades when possible.** This is the recommended practice for deploying upgrades. While re-imaging devices were historically recommended in the past, this isn't the case today, unless there's a scenario where in-place upgrades aren't supported.
 -  **Use the User State Migration tool** when local data or application settings migration is necessary. USMT captures and migrates user accounts, user files, operating system settings, and application settings.
