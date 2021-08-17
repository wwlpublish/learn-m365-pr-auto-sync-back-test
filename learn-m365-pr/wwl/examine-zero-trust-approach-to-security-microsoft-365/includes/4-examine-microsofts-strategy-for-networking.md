Today, employees access their organization’s resources from anywhere using various devices and apps. Access control policies that focus only on who can access a resource aren't sufficient. To master the balance between security and productivity, security admins must also factor in how a resource is being accessed.

Microsoft has a story and strategy around Zero Trust networking. Azure Active Directory conditional access is the foundational building block of how customers can implement a Zero Trust network approach. Conditional access and Azure Active Directory Identity Protection make dynamic access control decisions based on user, device, location, and session risk for every resource request. They combine:

 -  Confirmed runtime signals about the security state of a Windows device.
 -  The trustworthiness of the user session and identity to arrive at the strongest possible security posture.

Conditional access provides a set of policies that can be configured to control the circumstances in which users can access corporate resources. Considerations for access include:

 -  user role
 -  group membership
 -  device health and compliance
 -  mobile applications
 -  location
 -  sign-in risk

These considerations are used to decide whether to:<br>

 -  allow access
 -  deny access
 -  control access

Access can be controlled with extra authentication challenges (for example, multi-factor authentication), Terms of Use, or access restrictions. Conditional access works robustly with any application configured for access with Azure Active Directory.

:::image type="content" source="../media/zero-trust-networking-f5b48506.png" alt-text="Diagram showing the relationship of Azure AD to devices for Zero Trust networking.":::


To accomplish the Zero Trust model, Microsoft integrates several components and capabilities in Microsoft 365, including:

 -  Windows Defender Advanced Threat Protection
 -  Azure Active Directory
 -  Windows Defender System Guard
 -  Microsoft Intune

**Additional reading.** For more information on Zero Trust networking, see [Building Zero Trust networks with Microsoft 365](https://www.microsoft.com/security/blog/2018/06/14/building-zero-trust-networks-with-microsoft-365/?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”