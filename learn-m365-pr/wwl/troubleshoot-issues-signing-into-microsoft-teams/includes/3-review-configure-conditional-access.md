Conditional Access is a feature of Azure AD that provides an additional layer of security before allowing authenticated users to access data or other assets, such as apps like Microsoft Teams. Conditional Access analyses signals such as user, device, and location to automate decisions and enforce policies for accessing apps or resources. 

## How Conditional Access policies work

A Conditional Access policy brings signals together, to make decisions, and enforce organizational rules. A conditional access policy might state that:

- **IF** a user belongs to a certain group 
- **THEN** they are required to provide multifactor authentication (MFA) to sign in to an application

### Conditional Access signals

Conditional Access can use the following signals when deciding whether to grant access:

- **User or group membership**. Policies can be targeted to specific users and groups, giving administrators fine-grained control over access.
- **IP Location information**. Trusted IP address ranges can be created, then used when making policy decisions. Also, Administrators can opt to block or allow traffic from an entire country/region's IP range.
- **Device**. Users with devices of specific platforms or marked with a specific state can be used/
- **Application**. Users attempting to access specific applications can trigger different Conditional Access policies.
- **Real-time sign in risk detection**. Signals integration with Azure AD Identity Protection allows Conditional Access policies to identify risky sign in behavior. Policies can then force users to perform password changes or multifactor authentication. This reduces their risk level and may prevent them from being blocked from access until an administrator takes manual action.
- **Microsoft Cloud App Security**. Enables user application access and sessions to be monitored and controlled in real-time, increasing visibility and control over access to and activities performed within your cloud environment.

This means that Conditional Access policies can be created to allow or block specific users or groups access to certain applications. You can create trusted IP address ranges and block other countries/regions or IP address ranges. You might prevent a legacy device being used to access sensitive data. 

Sign in risk represents the probability that a given authentication request is *not* authorized by the identity owner. Sign in risk can be calculated in real-time or offline using Microsoft's internal and external threat intelligence sources. Policies can then force users to perform password changes or enter multifactor authentication, or the policy might block access until an administrator takes manual action.

### Access controls

Once the conditional access policy has been applied, an informed decision is reached whether to grant access, block access, or require additional verification. Common decisions are:

- Grant access
- Require one or more of the following options before granting access:

   - Require MFA.
   - Require device to be marked as compliant.
   - Require hybrid Azure AD joined device.
   - Require approved client app.
   - Require app protection policy (preview).

- Block access

## Verify conditional access policy settings

Your Azure AD administrator might have created a conditional access policy to control access to Teams, or all Microsoft 365 apps. To verify these settings, you must sign in to the Azure Active Directory admin center, and then access **Azure AD Conditional Access** from **All services**. All policies will be listed. You’ll only be interested in policies that display a State of **On**. 

Open the appropriate policies, and then review the conditions and access controls. In the screenshot below, the Teams Policy is:

- Assigned to all users
- Applies when users connect to Microsoft Teams
- Applies when the users have no or low sign security risks
- Grants access as long as the device is marked as compliant

:::image type="content" source="../media/conditional-access.png" alt-text="A screenshot displays the Teams Policy page. The Name is displayed, and a number of other settings are visible that relate to settings described in the preceding text.":::

## Configure conditional access policies

Watch the following video for a demonstration of how to set up a conditional access policy:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWHb8R]