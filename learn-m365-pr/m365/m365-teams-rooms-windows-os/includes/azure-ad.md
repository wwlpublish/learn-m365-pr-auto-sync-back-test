Azure AD is Microsoft's cloud-based identity and access management service. Azure AD requires no physical infrastructure and can be accessed anywhere with an internet connection. Organizations deploying Microsoft Teams will already have Azure AD configured and in use. This makes it a natural fit for managing Windows on Teams Rooms.

There are two primary methods to join Windows to Azure AD. The first one is *direct Azure AD join* and the second one is *Hybrid Azure AD*, which works with on-premises Active Directory.

You can create a dynamic security group that automatically populates with Teams Rooms devices. If you set the computer name of Teams Rooms devices to begin with **TR-** or end with **-TR**, a dynamic security group can be created to automatically add Teams Rooms devices to it. You can then use this dynamic security group to exclude Teams Rooms devices from any policy that may interfere with its operation. Azure AD also allows you to dynamically enroll Teams Rooms devices in Intune.
  
> [!NOTE]
> Dynamic security groups and Intune auto-enrollment require Azure Active Directory Premium P1.
>

## Learn more

- [What is Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis?azure-portal=true)
