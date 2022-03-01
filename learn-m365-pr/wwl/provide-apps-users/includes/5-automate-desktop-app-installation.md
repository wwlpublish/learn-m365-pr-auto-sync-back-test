A single, user-directed installation process works for scenarios in which a desktop app will be installed only once or twice. However, for larger and more complex installations, you should plan and perform an automated desktop-app deployment. Several options exist for automating desktop-app deployment to Windows computers.

### Automating installation by using Group Policy

Group Policy software deployment enables you to deploy desktop apps in the Windows Installer .msi file format to computers that belong to an Active Directory Domain Services (AD DS) environment. Group Policy software deployment offers the most basic form of automated app deployment. To perform Group Policy software deployment, you configure a GPO. Use Group Policy as a software-deployment method in small organizations where the desktop apps that you want to deploy already are packaged in the Windows Installer format. Group Policy software deployment has the following requirements and properties:

 -  The target computers must belong to an AD DS domain.
 -  You must package the software in the Windows Installer .msi file format.
 -  User and computer accounts can be the targets of an app deployment.
 -  You can target a deployment at the domain level, the site level, or the organizational unit (OU) level.

Group Policy software deployment supports the following deployment types:

 -  **Assign**. You can assign apps to users or computers. When you assign an app to a user, the app installs when the user signs in. When you assign an app to a computer, the app installs when the computer starts.
 -  **Publish**. You can publish apps to users. Doing so makes an app available through the Programs and Features item in Control Panel. You cannot publish apps to computers.

Group Policy software deployment has the following drawbacks:

 -  **It can be difficult to determine whether a deployment is successful**. Group Policy software deployment does not include reporting functionality. The only way to determine whether an app has installed correctly is to check it manually.
 -  **There is no prerequisite checking**. Group Policy software deployment does not enable you to perform prerequisite checks directly. You can use Windows Management Instrumentation (WMI) queries to perform these checks. However, this complex operation requires significant expertise and time.
 -  **There is no installation schedule**. Deployment will occur the next time a Group Policy refresh occurs. You cannot schedule Group Policy software deployment to occur at a specific date and time.

### Automating installation by using MDT

Microsoft Deployment Toolkit (MDT) is a solution accelerator that you can use to automate the deployment of operating systems and apps to devices. You can use MDT to perform lite-touch installation (LTI). LTI requires that you trigger an operating system deployment or app installation on each computer, but it requires minimal intervention after the deployment begins. You can use MDT to perform automated app and operating-system deployment without deploying Configuration Manager. However, you can use MDT when you integrate it with Configuration Manager to perform zero-touch installation (ZTI). ZTI enables app and operating-system deployment and migration without requiring any intervention.

The LTI process requires only the tools that are available in MDT. You do not need to deploy Configuration Manager in your environment to perform LTI. To perform LTI by using MDT, perform the following steps:

1.  Deploy MDT on a computer that will function as the management computer, create a deployment share on this computer, and then import the image files that you will use.
2.  Create a task sequence and a boot image for the computer that will function as the reference computer.
3.  Start the reference computer by using the medium that contains MDT. The task sequence files, task sequence, and boot image transfer to the reference computer.
4.  Use the **Windows Deployment Wizard** to deploy the operating system and required apps. After deployment, capture the reference computer as an image.
5.  Transfer the captured image to the management computer.
6.  Create a new boot image and task sequence for deployment to the target computers.
7.  Start the deployment target computers by using the medium that contains MDT. The task sequence files, task sequence, and boot image transfer to the reference computer.
8.  Run the **Windows Deployment Wizard** to deploy the prepared image.

### Automating installation by using Microsoft Intune

With Windows, organizations can use Microsoft Intune to manage Windows PCs either as mobile devices with mobile device management (MDM) or as computers with the Intune software client. Windows 8.1 and later, macOS, iOS, and Android can be managed using Intune’s MDM management capabilities.

Microsoft recommends that customers use the MDM management solution whenever possible. For more information on the differences between managing Windows as a computer or as a mobile device with Intune, see [http://aka.ms/AA3tzmy](http://aka.ms/AA3tzmy).

Once clients are enrolled in Intune, administrators can:

 -  Make software available as an optional installation or configure it as a required installation.
 -  Use reporting features of Microsoft Intune. This provides reporting on the success and failure of targeted app deployment, and it means that you can determine how many clients out of the target group successfully installed the deployed app.
 -  Remove apps that previously were deployed to client computers.
 -  Setup app protection policies for installing or launching an app. An example would be requiring the devices PIN locking be enabled before it can use Outlook with the organization’s Exchange server.

> [!NOTE]
> You must upload apps to Microsoft Intune before you can deploy them.

### Installation by using Endpoint Configuration Manager

Endpoint Configuration Manager provides a comprehensive platform for app deployment and management, and it supports deploying apps in the .exe, .msi, .appv, and .appx file formats. Configuration Manager enables administrators to target deployments to groups of users and computers, and to configure deployments to occur at specific dates and times. Computers must have the Configuration Manager client installed to receive software that Configuration Manager deploys. Using Configuration Manager provides you with a number of benefits, including:

 -  **Collections**. Configuration Manager enables you to create collections that consist of manually created groups of users or computers, or collections based on the results of queries of user or computer properties. You then can target app deployment to these collections. For example, you can create a collection that includes only the computers that are located at a specific site with a certain deployed app and a specific piece of installed hardware.
 -  **Multiple deployment type**s. Configuration Manager enables you to use multiple deployment types. With this feature, you can configure a single app deployment but make it possible for that deployment to occur in different ways, depending on the conditions that apply to the target computer or user. For example, you can configure an app to install locally if a user is logged on to his or her primary device, but to stream as an App-V app if the user is logged on to another device.

> [!NOTE]
> App V, which is included in the Enterprise and Education editions of Windows. It is a Microsoft solution that allows users to run virtualized applications on their computers without having to install or configure them locally.

 -  **Reporting**. This feature enables you to determine how successful an app deployment was after its completion. Configuration Manager also enables you to simulate app deployments before performing them, enabling you to determine if any factors that you have not considered might block a successful app deployment.
 -  **Wake on LAN (WOL)**. Instead of interrupting a user with an app installation that might require a restart, which could disrupt his or her current productivity WOL functionality allows you to schedule app deployment to occur after normal business hours. Typically, users are done working during this time, and compatible computers are in a low power state.
 -  **Software inventory, software metering, and Asset Intelligence**. A software inventory provides you with a list of which apps are installed on your organization’s computers. You can use software metering to monitor how often particular apps are used. You can use the Asset Intelligence feature to check software-licensing compliance. This helps you ensure that the number of apps deployed in your organization equals the number of software licenses that you have available.
