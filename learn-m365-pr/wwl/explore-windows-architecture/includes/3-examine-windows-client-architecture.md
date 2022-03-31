It is important to understand the differences between software applications, operating system services, and hardware devices and their associated device drivers in the operating system kernel. The Windows operating system architecture comprises the operating system kernel, system services, and applications.

:::image type="content" source="../media/windows-architecture-ccd0d952.jpg" alt-text="Diagram showing the architecture of Windows 10.":::


#### Operate system kernel

At the lowest level of the operating system, the core of the operating system consists of the Windows kernel itself and low-level device drivers. The kernel is responsible for taking operating system requests from system services. The kernel then translates those requests into instructions for the computer hardware, including the central processing unit (CPU), memory, and hardware devices.

When the operating system starts up, the kernel and its related low-level device drivers initialize first, followed by the operating system services.

#### System services

Operating system services are part of the operating system rather than components that you install after the operating system deploys. Additionally, operating system services function with no user action. In fact, they start before a user signs in to the computer.

Both operating system services and device drivers are software. However, the difference between them is that device drivers interact directly with hardware devices or components. Generally, a system service interacts with other software components in the operating system.

> [!NOTE]
> From a management perspective, the difference between device drivers and services is more obvious. You can use the Device Manager tool to manage device drivers, and you use the services Microsoft Management Console (MMC) snap-in tool to manage system services.

System services include various executive services that provide distinct functions within the operating system, including:

 -  The I/O Manager manages I/O.
 -  The virtual memory manager controls virtualization of memory within the operating system.
 -  Other components within the executive control other aspects of the operating system.
 -  The application programming interface (API) sets enable Windows to support different types of apps. The Windows Runtime (RT) APIs enable the operating system to run Microsoft Store apps, whereas Win32 and related API sets enable the operating system to run traditional desktop apps.

#### Understand apps

At the upper level of the operating system, apps operate by interacting with the computer user, and at a lower level by integrating with the operating system services. You install apps after you install the operating system, and you must start apps manually to use them.

Starting with Windows 8.1, Microsoft engineered Windows to support two different styles of apps. This involved modifying the architecture of the Windows operating system to provide dual stacks of APIs as follows:

 -  Traditional desktop apps, such as Office apps, use the Win32 APIs and Microsoft .NET Framework.
 -  Microsoft Store apps use the Windows RT APIs.

The benefit of this dual stack approach is that the same operating system can support these two different application platforms.

Windows 10 introduced the Universal Windows Platform (UWP), which is an evolution of the Windows Runtime model that provides a common app platform across every device that is capable of running Windows 10 or later. Apps that are designed for the UWP can call both the Win32 APIs and Microsoft .NET Framework, and can call the Windows RT APIs. This means developers can create a single app that can run across all devices.
