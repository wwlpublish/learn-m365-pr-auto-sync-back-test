Most modern computers now include hardware to support virtualization. Virtualization (in the desktop context) is the ability to install an OS and applications into a logical device (as opposed to a physical machine). The most common use of this technology is to run multiple “instances” of computers on a single computer and it is extensively used in server deployments. However, Windows client includes features that allow clients to take advantage of virtualization as well.

### Client Hyper-V

Client Hyper-V is the virtualization technology built into Windows clients. It is the same virtualization technology previously available only in Windows Server. Client Hyper-V enables you to run one or more operating systems at the same time on the same host computer.

Instead of working directly with the computer’s hardware, the guest operating systems run inside a virtual machine (VM). A virtual machine is a computing environment that is implemented in software and that abstracts the hardware resources of the physical computer so that multiple operating systems can run simultaneously on a single computer. Each operating system runs in its own virtual machine and is allocated logical instances of the computer’s processors, hard disks, network cards, and other hardware resources. An operating system that is running in a virtual machine is unaware that it is executing in a virtual environment and behaves as if it exclusively controls the underlying physical computer’s hardware.

When discussing virtualization, the term *Hypervisors* is often used. A hypervisor is a virtualization platform (like Hyper-V) that enables you to run multiple operating systems on a single physical computer called the host computer. The main function of the hypervisor is to provide isolated execution environments for each virtual machine and to manage access between the guest operating systems running in virtual machines and the underlying hardware resources on the physical computer.

Windows OS and Applications can be deployed to virtual machines running a hypervisor host just like a traditional installation. Client Hyper-V is useful for scenarios such as running an app that may require a different OS or version than the primary OS must be used or scenarios that require an isolated environment, such as driver testing or application compatibility.

### Windows Sandbox

Windows Sandbox is a feature first introduced in Windows 10 that allows Windows clients to set up an isolated environment without the need to configure Hyper-V or create a Windows VM or set up a VHD. This enables the user to quickly start an isolated, pristine Windows environment for temporary use scenarios such as launching a downloaded executable that you may not fully trust. Windows Sandbox is included with Windows Pro and Enterprise editions.

Windows Sandbox includes the following characteristics:

 -  **Pristine**. Every time Windows Sandbox runs, it’s as clean as a brand-new installation of Windows.
 -  **Disposable**. Nothing persists on the device. When Sandbox is closed, everything is discarded.
 -  **Secure**. Uses hardware-based virtualization for kernel isolation, which relies on the Microsoft’s hypervisor to run a separate kernel, which isolates Windows Sandbox from the host.
 -  **Efficient**. Uses the integrated kernel scheduler, smart memory management, and virtual GPU

To use Windows Sandbox, virtualization must be enabled on physical hardware. If using a virtual machine, nested virtualization must be enabled. Windows Sandbox must also be enabled in Windows Features.
