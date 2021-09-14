As soon as users obtain their own personal devices, they typically use them not only for personal leisure, but also for work. This situation poses two problems for companies:

 -  Until the devices are enrolled to an MDM solution, the organization doesn’t have control over them, nor can it manage them.
 -  Device enrollment is usually a manual process and users often forget to do it.

As a result, most companies have resorted to making enrollment of personal devices mandatory if users want to use them for work. Organizations also put rules and policies in place to help manage these personal devices. For example:

 -  Users can only access company resources from enrolled devices that follow company policy.
 -  Compliance policies are used to define how devices should be configured.
 -  Conditional access policies are used for controlling access to company resources.

To control access to company resources, organizations can configure either a Security policy in Microsoft 365 or a Conditional access policy in Intune. These policies can be configured to only allow access to company resources from enrolled devices.

For example, if such a policy is in place and a user tries to access company resources, such as their Exchange Online mailbox, the user will be denied access and redirected to enroll their device first. After the user enrolls the device, they can access their mailbox.<br>

The following diagram shows what happens when a user with a new personal device tries to access Microsoft 365. The user is blocked from accessing Microsoft 365 resources in the app until they enroll the device.

:::image type="content" source="../media/basic-mobility-security-access-control-flow-0f850383.jpg" alt-text="diagram showing what happens when a user with a new personal device tries to access Microsoft 365. The user is blocked from accessing Microsoft 365 resources in the app until they enroll the device.":::


The following sections examine how Windows 10, Android, and iOS devices are enrolled to MDM.

### Automatic enrollment of Windows 10 devices

Organizations can configure automatic enrollment to MDM for Windows 10 devices only.

 -  If a Windows 10 device is already joined to an on-premises AD DS that is synced to Azure AD, the **Enable automatic MDM enrollment using default Azure AD credentials** Group Policy setting can be configured to enroll devices to MDM.
 -  If Azure AD is integrated with MDM, then any Windows 10 devices that users join to Azure AD are automatically enrolled to MDM.

> [!NOTE]
> Azure AD users can enroll devices to Azure AD by default. However, they must have an Intune license to use this feature.

**Additional reading.** For more information, see the following resources:

 -  [Enrolling Windows 10 devices by using Group Policy](/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy?azure-portal=true).
 -  [Integrating Azure AD with MDM](/windows/client-management/mdm/azure-ad-and-microsoft-intune-automatic-mdm-enrollment-in-the-new-portal?azure-portal=true).

### Manual enrollment of Windows 10 devices

Organizations can manually enroll Windows 10 devices to Intune by using any of the following methods:

 -  **Settings app.** Use the **Access work or school** option in the **Account** section to manually enroll a Windows 10 device to MDM.
 -  **Provisioning package.** Use Windows Configuration Designer to create a provisioning package that enrolls devices to MDM. Provisioning packages are typically used for bulk enrollment.
 -  **Company Portal app.** This app is available for free in the Microsoft Store. It can be installed and used for enrolling devices to MDM.

### Manual enrollment of Android and iOS devices

Organizations can enroll Android and iOS devices by using the Company Portal app. The app isn't included on those devices by default. Organizations must install it from the Google Play store or the Apple app store first. To enroll an iOS device, an organization must ensure that its MDM is configured with an APNS certificate.

:::image type="content" source="../media/company-portal-sign-in-page-041d875a.jpg" alt-text="screenshot of the company portal sign-in page":::


**Additional reading.** For more information, see [Enrolling Android and iOS devices to MDM](/intune-user-help/enroll-your-device-in-intune-all?azure-portal=true).

### 
