Windows 10 must be licensed on a device before the device can be used. So what are the options for getting Windows 10 licensed on a device?

 -  If Windows is pre-installed on a device, the license is included with the device.
 -  Windows 10 can be purchased separately from the device.
 -  Windows 10 licenses can be obtained through an agreement with Microsoft.
 -  A Windows 10 Enterprise E3 or E5 license can be assigned to an Azure AD user, and the license will automatically be applied to a device when the user signs in.

### Virtual desktop access

Users sometimes use Remote Desktop to connect to a remote Windows 10 computer. An example of this scenario is when users connect to Virtual Desktop Infrastructure (VDI) desktops or Azure virtual machines. In such cases, they must be licensed to use both devices:

 -  the local device on which they start the Remote Desktop Connection client.
 -  the remote Windows 10 computer to which they connect.

They must have Virtual desktop access rights to be allowed to connect to the remote Windows 10 computer.

Virtual desktop access rights are a benefit of Windows Client Software Assurance (SA). If an organization's Windows 10 devices are covered under Windows Client SA, they can connect to remote Windows 10 computers by using Remote Desktop at no extra cost. But if an organization wants its users to connect from devices that don't qualify for Windows Client SA, such as thin clients, they'll need to license those devices with Windows Virtual Desktop Access (VDA) to access a virtual desktop from such devices.

Virtual machines for which you want to configure VDA for automatic subscription activation must meet following prerequisites:

 -  Must be running Windows 10 Pro, version 1703 (also known as the Creator's Update) or newer.
 -  Must be Active Directory-joined or Azure Active Directory (Azure AD)-joined.
 -  Must be generation 1 virtual machine.

### Virtual machines hosted by another company

If an organization doesn't host its own virtual machines, they must be hosted by a Qualified Multi-tenant Hoster (QMTH).

For example, consider the scenario where a virtual machine is running Windows 10 version 1803 or newer and is hosted in Azure or another Qualified Multi-tenant Hoster. When a user with VDA rights signs in by using their Azure AD credentials, the virtual machine is automatically upgraded to Enterprise and activated.

Both the physical computer and the virtual machine(s) are automatically activated when:

 -  the physical computer with the Hyper-V feature and the virtual machine(s) are running Windows 10 version 1803 or newer

    and

 -  the user has an Enterprise E3 or E5 license assigned

This feature is called Inherited Activation.

If the virtual machine is running Windows 10, version 1703 or 1709, or the hoster isn't an authorized QMTH partner, the organization that owns the device must provide a Windows 10 Pro Generic Volume License Key (GVLK) to the virtual machine. You can find Pro GVK on the Microsoft portal, and you can deploy it to the virtual machine by using a provisioning package.

**Additional reading.** For more information and to get Windows 10 Pro GVLK, see [VDA for Windows 10 subscription activation](/windows/deployment/vda-subscription-activation).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”