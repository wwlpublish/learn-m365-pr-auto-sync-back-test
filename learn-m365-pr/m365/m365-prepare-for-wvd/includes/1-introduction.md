Before you can deploy your first Windows Virtual Desktop virtual machines (VMs), there are some prerequisite steps to take care of in the Microsoft Azure portal. You also need to connect to your existing directory service. We’ll go through the exact steps and PowerShell cmdlets you need to get your environment ready for Windows Virtual Desktop. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3Jhf9]

If you’ve ever provisioned a large-scale Remote Desktop Services (RDS) environment, you’ll be familiar with the components, complexity, and time required to get everything up and running, as well as the operational steps needed to right-size the infrastructure. With Windows Virtual Desktop, deployment is much faster and easier, since most steps go away - the RDS infrastructure roles are now managed Platform as a Service (PaaS) components that you don’t need to provision or manage. This new architecture helps simplify both initial setup and day-to-day operations. You only need to manage OS images, apps, users, and the scale of the environment, not the physical hardware.

That said, there are still a few prerequisites you should be aware of – especially if you’ve historically run everything in your datacenters.

## Learning objectives

At the end of this module, you should be able to:

- Describe the steps involved and resources you need to prepare for Windows Virtual Desktop deployment.

## Prerequisites

- Familiarity with server and client management concepts and tools
- Familiarity with Windows virtualization technologies, like Remote Desktop Services