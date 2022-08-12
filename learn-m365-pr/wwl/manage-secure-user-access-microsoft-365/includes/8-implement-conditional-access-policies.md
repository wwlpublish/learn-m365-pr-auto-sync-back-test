Conditional Access is the protection of regulated content in a system by requiring certain criteria to be met before granting access to the content. Conditional Access brings signals together to make decisions and enforce organizational policies. Azure Active Directory Conditional Access is at the heart of the new identity-driven control plane.

:::image type="content" source="../media/conditional-access-signal-decision-enforcement-36ecaa3c.png" alt-text="Graphic showing how conditional access brings signals together to make decisions and enforce organizational policies.":::


Conditional Access policies at their simplest are if-then statements. If a user wants to access a resource, then they must complete an action. For example, consider a payroll manager who wants to access the company's payroll application. The manager is required to do multifactor authentication to access it.

Administrators are faced with two primary goals:

 -  Empower users to be productive regardless of location or time.
 -  Protect their organization's assets.

By using Conditional Access policies, you can apply the right access controls when needed to keep your organization secure and stay out of your user's way when not needed.

Organizations can use Conditional Access with Microsoft Intune compliance policies. This combination can control the devices and apps that connect to your email and company resources. When integrated, you can gate access to keep your corporate data secure. This design gives users an experience that allows them to do their best work from any device, and from any location.

Conditional Access is an Azure Active Directory capability that's included with an Azure Active Directory Premium license. Through Azure Active Directory, Conditional Access brings signals together to make decisions, and enforce organizational policies. Intune enhances this capability by adding mobile device compliance and mobile app management data to the solution. Common signals include:

 -  User or group membership.
 -  IP location information.
 -  Device details, including device compliance or configuration status.
 -  Application details, including requiring use of managed apps to access corporate data.
 -  Real-time and calculated risk detection, when you also use a mobile threat defense partner.

:::image type="content" source="../media/conditional-access-overview-cd55cc68.png" alt-text="Graphic showing how conditional access policies apply access controls to secure apps and data.":::


> [!IMPORTANT]
> Conditional Access policies are enforced after first-factor authentication is completed. Conditional Access isn't intended to be an organization's first line of defense for scenarios like denial-of-service (DoS) attacks. However, it can use signals from these events to determine access.

> [!NOTE]
> Conditional Access also extends its capabilities to Microsoft 365 services.

### Conditional Access integrated with Microsoft Intune

Conditional Access works with Intune device configuration and compliance policies, and with Intune Application protection policies.

 -  **Device-based Conditional Access**. Intune and Azure Active Directory work together to make sure only managed and compliant devices can access email, Microsoft 365 services, Software as a service (SaaS) apps, and on-premises apps. You can also set a policy in Azure Active Directory to enable only domain-joined computers or mobile devices that have enrolled in Intune to access Microsoft 365 services. These policies include:
    
    
     -  Conditional Access based on network access control
     -  Conditional Access based on device risk
     -  Conditional Access for Windows PCs (both corporate-owned and bring your own device (BYOD))
     -  Conditional Access for on-premises Exchange Server
    
    For more information, see [device-based Conditional Access with Intune](/mem/intune/protect/create-conditional-access-intune?azure-portal=true).
 -  **App-based Conditional Access**. Intune and Azure Active Directory work together to make sure only managed apps can access corporate e-mail or other Microsoft 365 services. For more information, see [app-based Conditional Access with Intune](/mem/intune/protect/app-based-conditional-access-intune?azure-portal=true).

### Common signals

Common signals that Conditional Access can take into account when making a policy decision include:

 -  User or group membership
     -  Policies can be targeted to specific users and groups giving administrators fine-grained control over access.
 -  IP Location information
     -  Organizations can create trusted IP address ranges that can be used when making policy decisions.
     -  Administrators can specify entire countries/regions IP ranges to block or allow traffic from.
 -  Device
     -  Users with devices of specific platforms or marked with a specific state can be used when enforcing Conditional Access policies.
     -  Use filters for devices to target policies to specific devices like privileged access workstations.
 -  Application
     -  Users attempting to access specific applications can trigger different Conditional Access policies.
 -  Real-time and calculated risk detection
     -  Signals integration with Azure AD Identity Protection allows Conditional Access policies to identify risky sign-in behavior. Policies can then force users to change their password, do multifactor authentication to reduce their risk level, or block access until an administrator takes manual action.
 -  Microsoft Defender for Cloud Apps
     -  Enables user application access and sessions to be monitored and controlled in real time. This feature increases visibility and control over access to and activities done within your cloud environment.

### Common decisions

Common decisions built into conditional access policies include:

 -  Block access
     -  Most restrictive decision
 -  Grant access
     -  Least restrictive decision. It can still require one or more of the following options:
         -  Require multifactor authentication.
         -  Require a device to be marked as compliant.
         -  Require a device to be Hybrid Azure AD-joined.
         -  Require an approved client app.

### Common Conditional Access policies

Many organizations have common access concerns that Conditional Access policies can help with. These common conditional access policies include:

 -  Require multifactor authentication for users with administrative roles.
 -  Require multifactor authentication for Azure management tasks.
 -  Block sign-ins for users attempting to use legacy authentication protocols.
 -  Require Azure AD Multi-Factor Authentication for all users.
 -  Require Azure AD Multi-Factor Authentication for Azure management.
 -  Require Azure AD Multi-Factor Authentication for risky sign-in.
 -  Require password change for risky users.
 -  Require compliant or hybrid-joined devices.
 -  Require organization-managed devices for specific applications.
 -  Require approved app or app protection policy.
 -  Block or granting access from specific locations.
 -  Block risky sign-in behaviors.

### Assign a Conditional Access policy for Cloud PCs

Conditional Access policies aren't set for your tenant by default. You can target Conditional Access policies to the cloud PC first-party app by using either Azure or Microsoft Endpoint Manager. No matter which method you use, the policies will be enforced on the Cloud PC End-user portal and the connection to the Cloud PC.

The following steps describe how to create conditional access policies using Microsoft Endpoint Manager:

1. Sign in to the Microsoft Endpoint Manager admin center, select **Endpoint Security &gt; Conditional Access &gt; New Policy.**
1. Provide a **Name** for your specific Conditional Access policy.
1. On the **New Policy** tab, under **Users and groups**, choose **Specific users included**. Select the specific user or group you want to target with the conditional access policy. You can also Exclude certain users or groups to fine-tune the assignment.
1. Under **Cloud apps or actions**, select **No cloud apps, action, or authentication contexts selected**.
1. Select **Cloud apps &gt; Include &gt; Select apps**.
1. In the **Select** pane, search for and select both the following apps:
    
    
     -  **Windows 365** (you can also search for "cloud" to find this app).
     -  **Windows Virtual Desktop** (this option may also appear as Azure Virtual Desktop)
    
    By choosing both apps, you ensure the policy applies to the Cloud PC End-user portal and the connection to the Cloud PC. If you want to exclude apps, you must also choose both apps.
1. If you want to fine-tune your policy, under **Access controls**, choose **0 controls selected**. Under **Grant**, choose the options that you want to apply to all objects assigned to this policy.
1. If you want to test your policy first, under **Enable Policy**, set **Report-only** to **Off**. If you set it to **On**, the policy will be applied as soon as you create it.
1. Select **Create** to create the policy.

You can see your list of active and inactive policies in the **Policies** view in the Conditional Access UI.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”