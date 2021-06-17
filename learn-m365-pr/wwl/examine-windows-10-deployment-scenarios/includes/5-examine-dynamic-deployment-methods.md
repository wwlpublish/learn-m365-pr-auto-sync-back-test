In the past, when companies upgraded devices to newer versions of Windows, they typically wiped the devices and deployed their own custom Windows image. Before Windows 10, that was the recommended way in which businesses upgraded the Windows OS. Deploying a custom image was often faster and easier than using the preinstalled version, even if both versions of Windows were the same.

However, all that changed with the release of Windows 10. It includes dynamic provisioning capabilities that aren't available in older versions of Windows. Dynamic provisioning enables organizations to transform the existing version of Windows 10, which is included on a device, to a customized version that's used within the company. This transformation can be completed without reinstalling Windows 10, which saves organizations time and reduces network traffic.

> [!IMPORTANT]
> The goal of dynamic provisioning is to take a new device right from the vendor, turn it on, and transform it into a productive company device, with minimal time and effort.

Dynamic provisioning achieves this goal by enabling a company to:

 -  modify the Windows 10 edition.
 -  add more content such as apps and certificates.
 -  remove unwanted software that's included on the device.
 -  join devices to the company's domain or Azure AD.

By joining devices to its domain or Azure AD, an organization can use compliance policies to ensure its devices follow company standards.

 -  Joining devices to an on-premises Active Directory domain enables companies to use Group policies.
 -  Joining devices to Azure AD enables companies to use Mobile Device Management (MDM) policies.

Organizations implement Group policies and MDM policies to ensure device compliance with company's standards.

There are three different dynamic provisioning options available with Windows 10. You can select one of them based on the size of your company and on the infrastructure the company is using. These options include:

 -  Provisioning package.
 -  Windows 10 subscription activation.
 -  Integrating Azure AD with automatic MDM enrollment.

Each of these options is examined in detail in the following sections.

### Provisioning package

Using the Windows Configuration Designer, organizations can create a self-contained provisioning package. The package can contain the configuration and all the settings and apps that must be applied for devices to follow company policy.

For example, organizations can use a provisioning package to:

 -  configure the Windows 10 user interface.
 -  add more drivers, files, or applications.
 -  adjust connectivity settings to meet mobile network requirements and follow security policies.

> [!IMPORTANT]
> A provisioning package can be installed without having to reinstall Windows.

Organizations can achieve the same result by deploying a new, customized Windows 10 image. However, the benefit of a provisioning package is that it's much smaller and installs faster.

:::image type="content" source="../media/windows-configuration-designer-cff6b714.jpg" alt-text="screenshot of the Windows Configuration Designer":::


**Additional reading.** For more information, see [Provisioning packages](/windows/configuration/provisioning-packages/provisioning-packages).

### Windows 10 subscription activation

Windows 10 Enterprise E3 and E5 are available as online services through subscription. If a company is using Azure AD, it can assign a Windows 10 license to users and groups. When a licensed user signs in to a device by using the Azure AD credentials associated with a Windows 10 Enterprise E3 or E5 license:

 -  the operating system turns from Windows 10 Pro to Windows 10 Enterprise with no keys and no reboots.
 -  and all the Windows 10 Enterprise features are unlocked.

Sometimes a user’s subscription expires or is transferred to another user. When this occurs, the Windows 10 Enterprise device reverts seamlessly to the Windows 10 Pro edition after a grace period of up to 90 days.

Windows 10 version 1803 and newer also supports inherited activation. Inherited activation enables Windows 10 virtual machines to inherit the activation state from their Windows 10 Enterprise E3 or E5 host.

**Additional reading.** For more information, see [Windows 10 subscription activation](/windows/deployment/windows-10-enterprise-subscription-activation).

### Integrating Azure AD with automatic MDM enrollment

Organizations can integrate Azure AD with a Mobile Device Management (MDM) solution, such as Microsoft Intune. By doing so, Windows 10 devices are automatically enrolled to MDM when they're joined to Azure AD. Once a device is enrolled in an MDM solution, the MDM solution can:

 -  enforce compliance with corporate policies.
 -  add or remove apps.
 -  turn Windows 10 Pro to Windows 10 Enterprise.
 -  configure the device as needed.
 -  report a device’s compliance.

Reporting a device's compliance can be used to enable access to company resources or apps only by devices that follow company policies.

**Additional reading.** For more information, see [Integrating Azure AD with MDM](/windows/client-management/mdm/azure-active-directory-integration-with-mdm).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”