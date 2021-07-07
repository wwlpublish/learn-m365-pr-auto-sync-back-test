Computers and digital devices have become common aspects of modern schooling and are used in an ever-increasing number of classrooms.  Each device requires set up and configured to ensure that it meets the needs of the environment where it's installed, be that a library, the science lab, or the classroom, and comply with security and regulatory requirements.  Microsoft provides several tools that can simplify the configuration and deployment process.  As an IT administrator, you need to decide which service or tool will best meet your school's IT needs.

In your role as the IT administrator for your school, you want to explore the various deployment solutions available to you and gain an understanding of the key features and benefits of each.

Here, you'll explore two deployment options, Set up School PCs app and Windows Autopilot.

## What is Set up School PCs app

The Set up School PCs app allows IT administrators to set up and configure school-optimized Windows 10 devices for students and teachers in your school. You'd use the Set up School PCs app to decide which apps and features each device will need and which ones aren't required. The app is free and available in the Microsoft Store for Education.

The Set up School PCs app can work with Azure Active Directory to join a device and enroll it into Intune. The app also enables an administrator to install an initial configuration on devices. You can put the provisioning package for the app on a USB stick and plug it into devices to provision them.

It is recommended that you remove the guest account from the list of features installed by the app.

### Set up School PCs features

Set up School PCs app comes with a number of features:

- Fast sign-in, students can sign in and use the computer in under a minute.
- Custom Start experience, ensures only essential apps are pinned to Start.
- Guest account, no sign-in required, allows the computer to be used without an account.
- School policies, ensure a relevant learning environment with optimal performance.
- Azure AD Join, requires a network connection and an Azure AD subscription. It lets computers join the school Azure AD or Microsoft 365 subscription.
- Single sign-on to Microsoft 365, requires a Microsoft 365 subscription, lets the student use their Microsoft ID to access Office applications.
- Take a Test app, requires an Azure AD Premium subscription, lets the device run quizzes and assessments through test providers.

The app sets up school-optimized defaults for devices. If you need to change any of the customizations installed by the app, you can import a Set up School PCs package into the Windows Configuration Designer and make any changes required.

## What is Windows Autopilot

Windows Autopilot is a cloud-based provisioning tool that lets IT administrators set up and pre-configure new devices ahead of the school year's start.

Windows Autopilot was designed with school IT departments in mind and provides:

- Easy device setup: Windows Autopilot automatically configures each device from the cloud and gets them ready for the classroom when the student signs in for the first time.
- Time and cost savings in large-scale deployments: Students and teachers can provision devices themselves. IT departments no longer need to set up provisioning in large warehouses and hire a fleet of technicians to set up student PCs.
- Always up to date: Custom images and provisioning packages on USBs can quickly become outdated.
- Easy reset: Initiate a remote Windows Autopilot Reset from Intune for Education to quickly reset student PCs that are having issues.

## Choose when to use Set up School PCs or Windows Autopilot

As you can see, both deployment options can be used to set up and deploy Windows devices. They both have strengths, depending on the scenario they're being applied to, making it difficult to know when to use Set up School PCs or Windows Autopilot. The table below identifies the most common deployment scenarios and explains how each of the deployment options best fits it.

| Points to consider                 | Set up School PCs                                            | Windows Autopilot                                            |
| :--------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| IT staff                           | IT staff performs device unboxing, first power-on, and configuration of devices is performed by the IT Staff. | Optimized for limited engagement from IT staff. Students and teachers can perform device unboxing, first power-on, and initial configuration. |
| Device user                        | Best for shared devices and younger students.            | Best for 1:1 devices and older students.                 |
| Apps                               | Best for deploying large apps simultaneously on a slower network. | Works well with apps of all sizes.                           |
| Network                            | Reliable internet connection required; best for low-bandwidth networks. | Reliable internet connection required; network bandwidth consumption based on the number of concurrent device setups and size of required apps. Students can set up devices on their home network. |
| First day of class                 | Devices are ready for sign in and use immediately.           | Students need to unbox and connect to the network; setup completes automatically. |
| Deployment time                    | Can take as little as 1-2 minutes; time increases based on the number of concurrent device setups, network bandwidth, and size of required applications. | Can take as little as 1-2 minutes; time increases based on the number of concurrent device setups, network bandwidth, and size of required applications. |
| OEMs/Partners                      | Not applicable.                                              | Requires registration of device IDs for the Windows Autopilot service by a partner (CSP) or OEM provider. |
| Existing on-premises configuration | Supported with Windows Configuration Designer only.          | Supports Hybrid AD join; the device must be on the same network as Active Directory Domain Controller. |
