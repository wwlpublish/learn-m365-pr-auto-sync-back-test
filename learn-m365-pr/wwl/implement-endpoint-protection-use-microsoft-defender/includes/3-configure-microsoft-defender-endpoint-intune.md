Organizations can integrate Microsoft Defender for Endpoint with Microsoft Intune as a Mobile Threat Defense solution. Integration can help prevent security breaches and limit the effect of breaches within an organization.

Microsoft Defender for Endpoint works with devices that run:

 -  Android
 -  iOS/iPadOS
 -  Windows 10
 -  Windows 11

To be successful, you'll use the following configurations in concert:

 -  **Establish a service-to-service connection between Microsoft Intune and Microsoft Defender for Endpoint**. This connection lets Microsoft Defender for Endpoint collect data about machine risk from supported devices an organization manages with Intune.
 -  **Use a device configuration profile to onboard devices with Microsoft Defender for Endpoint**. An organization onboards devices to configure them to communicate with Microsoft Defender for Endpoint. By doing so, data is provided to help the organization assess its risk level.
 -  **Use a device compliance policy to set the level of risk you want to allow**. Risk levels are reported by Microsoft Defender for Endpoint. Devices that exceed the allowed risk level are identified as noncompliant.
 -  **Use a conditional access policy to block users from accessing corporate resources from devices that are noncompliant**. Conditional access policies can also block devices that exceed an organization's expected risk levels.

When an organization integrates Microsoft Intune with Microsoft Defender for Endpoint, it can take advantage of Microsoft Defender for Endpoint's Threat and Vulnerability Management (TVM) module. It can also [use Intune to remediate endpoint weakness identified by TVM](/mem/intune/protect/atp-manage-vulnerabilities?azure-portal=true).

### Example of using Microsoft Defender for Endpoint with Microsoft Intune

The following example helps explain how Intune and Microsoft Defender for Endpoint work together to help protect organizations. For this example, Microsoft Defender for Endpoint and Intune are already integrated.

Consider an event where someone sends a Word attachment with embedded malicious code to a user within your organization.

 -  The user opens the attachment, which enables the embedded code.
 -  An elevated privilege attack starts. An attacker from a remote machine has admin rights to the victim's device.
 -  The attacker then remotely accesses the user's other devices. This security breach can affect the entire organization.

Microsoft Defender for Endpoint can help resolve security events like this scenario.

 -  In this example, Microsoft Defender for Endpoint detects each of the actions that occurred:
     -  The device executed abnormal code.
     -  The device experienced a process privilege escalation.
     -  Malicious code was injected into the device.
     -  A suspicious remote shell was issued.
 -  Based on the actions from the device, Microsoft Defender for Endpoint [classifies the device as high-risk](/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity?azure-portal=true). It also includes a detailed report of suspicious activity in the Microsoft Defender Security Center portal.

For this example, assume your organization has an Intune device compliance policy that classifies devices with a **Medium** or **High** level of risk as **noncompliant**. As such, the compromised device in this example is classified as noncompliant. This classification allows your conditional access policy to kick in and block access from that device to your corporate resources.

For devices that run Android, you can use Intune policy to modify the configuration of Microsoft Defender for Endpoint on Android. For more information, see [Microsoft Defender for Endpoint web protection](/mem/intune/protect/advanced-threat-protection-manage-android?azure-portal=true).

### Prerequisites to integrating Microsoft Defender for Endpoint and Microsoft Intune

To use Microsoft Defender for Endpoint with Microsoft Intune, an organization must have the following subscriptions:

 -  **Microsoft Defender for Endpoint**. This subscription provides you access to the Microsoft Defender Security Center (ATP portal). For Defender for Endpoint licensing options, see Licensing requirements in [Minimum requirements for Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements?azure-portal=true) and [How to set up a Microsoft 365 E5 Trial Subscription](/microsoft-365/security/defender/setup-m365deval#enable-microsoft-365-trial-subscription?azure-portal=true).
 -  **Microsoft Intune**. This subscription provides access to Intune and the Microsoft Endpoint Manager admin center. For Intune licensing options, see [Microsoft Intune licensing](/mem/intune/fundamentals/licenses?azure-portal=true).

The following platforms are supported for Microsoft Intune with Microsoft Defender for Endpoint:

 -  Android
 -  iOS/iPadOS
 -  Windows 10/11 (Hybrid Azure Active Directory Joined or Azure Active Directory Joined)

### Enable Microsoft Defender for Endpoint in Intune

To set up the service-to-service connection between Intune and Microsoft Defender for Endpoint, you only need to enable Microsoft Defender for Endpoint a single time per tenant.

Complete the following steps to enable Microsoft Defender for Endpoint with Microsoft Intune:

1.  You must begin by navigating to the **Microsoft Endpoint Manager admin center**. To do so, on the **Microsoft 365 admin center**, select **Show all** in the navigation pane. Under the **Admin centers** group, select **Endpoint Manager**.
2.  In the **Microsoft Endpoint Manager admin center**, select **Endpoint security** in the navigation pane.
3.  On the **Endpoint security \| Overview** page, under the **Setup** section in the navigation pane, select **Microsoft Defender for Endpoint**.
4.  On the **Endpoint security \| Microsoft Defender for Endpoint** page, select the **Open the Microsoft Defender for Endpoint admin console**. This step opens the **Microsoft 365 Defender** portal.
    
    > [!TIP]
    > If the **Connection status** at the top of the page is already set to **Enabled**, the connection to Intune has already been made. In this event, you can select **Open the Microsoft Defender for Endpoint admin console** to open the **Microsoft Defender Security Center**. Then use the guidance in the following steps to confirm that the **Microsoft Intune connection** is set to **On**.

5.  In the **Microsoft 365 Defender** portal, select **Settings &gt; Endpoints &gt; Advanced features**.
6.  Set the toggle switch for the **Microsoft Intune connection** setting to **On**.
    
    :::image type="content" source="../media/security-center-intune-toggle-3a1d7a0a.png" alt-text="Screenshot of the Microsoft Intune connection setting.":::
    
7.  Select **Save preferences**.
    
    > [!NOTE]
    > Once the connection between Microsoft Defender for Endpoint and Microsoft Intune is established, the services are expected to sync with each other **at least** once every 24 hours. The number of days without sync until the connection is considered unresponsive can be configured in the Microsoft Endpoint Manager admin center. Select **Endpoint security &gt; Microsoft Defender for Endpoint &gt; Number of days until partner is unresponsive**.

8.  At this point, you have enabled Microsoft Defender for Endpoint with Microsoft Intune. You'll now configure Microsoft Defender for Endpoint to use compliance and app protection policies. To do so, you must begin by returning to the **Microsoft Defender for Endpoint** page in the **Microsoft Endpoint Manager admin center**.
9.  To use Microsoft Defender for Endpoint with compliance policies, configure the following options under **MDM Compliance Policy Settings** for the platforms you support:
     -  Set **Connect Android devices to Microsoft Defender for Endpoint** to **On**.
     -  Set **Connect iOS devices to Microsoft Defender for Endpoint** to **On**.
     -  Set **Connect Windows devices to Microsoft Defender for Endpoint** to **On**.When these configurations are set to **On**, the following devices are connected to Microsoft Defender for Endpoint for compliance:
     -  Applicable devices that you manage with Intune.
     -  Devices you enroll in the future.
10. To use Microsoft Defender for Endpoint with app protection policies, configure the following options under **App Protection Policy Settings** for the platforms you support. These capabilities are available for Android and iOS/iPadOS.
     -  Set **Connect Android devices to Microsoft Defender for Endpoint for app protection policy evaluation** to **On**.
     -  Set **Connect iOS devices to Microsoft Defender for Endpoint for app protection policy evaluation** to **On**.
11. Select **Save**.

When you integrate a new application to Intune Mobile Threat Defense and enable the connection to Intune, Intune creates a classic conditional access policy in Azure Active Directory. Each MTD app you integrate, including Microsoft Defender for Endpoint or any of Microsoft's [MTD partners](/mem/intune/protect/mobile-threat-defense#mobile-threat-defense-partners?azure-portal=true), creates a new classic conditional access policy. These policies can be ignored; however, they shouldn't be edited, deleted, or disabled.

If the classic policy is deleted, you must delete the connection to Intune that was responsible for its creation. Once you delete the connection, you must then set it up again. Doing so recreates the classic policy. Migrating classic policies for MTD apps to the new policy type for conditional access isn't supported.

Classic conditional access policies for MTD apps:

 -  Are used by Intune MTD to require that devices are registered in Azure AD. Doing so ensures they have a device ID before communicating to MTD partners. The ID is required so that devices can successfully report their status to Intune.
 -  Have no effect on any other Cloud apps or resources.
 -  Are distinct from conditional access policies you can create to help manage MTD.
 -  By default, don't interact with other conditional access policies you use for evaluation.

To view classic conditional access policies, in Azure, go to **Azure Active Directory &gt; Conditional Access &gt; Classic policies.**
