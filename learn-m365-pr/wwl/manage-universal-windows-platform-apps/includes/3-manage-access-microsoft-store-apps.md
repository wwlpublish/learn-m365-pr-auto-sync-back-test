While it might be convenient to enable users to search for and install applications themselves, this method poses potential problems for system administrators who want to control application installation, or impose a rigid desktop standard on network-connected computers. For these reasons, you can prevent users from accessing the Microsoft Store.

> [!NOTE]
> This functionality requires Windows Enterprise edition.

### Preventing users from installing applications from the Microsoft Store

To disable user access to the Microsoft Store, perform the following procedure:

1.  Run **regedit.exe**.
2.  Navigate to **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Policies\\Microsoft\\WindowsStore**. (If the WindowsStore key is not there, you will need to create it.)
3.  Create a new **DWORD** value named **RemoveWindowsStore**, and change the value to **1**.
4.  Before this setting can take effect, you must restart the computer and sign back in.

In Windows 8 and Windows 8.1, you can configure this setting via a Group Policy setting, but the WinStoreUI.admx and .adml files are not present in Windows 10. Because Windows 10 introduces the Microsoft Store for Business, preventing access to the Microsoft Store app is not as relevant in Windows 10 as it is in Windows 8.1. However, you can prevent users from signing in with a Microsoft account by using Group Policy, and thereby preventing users from downloading apps from the Microsoft Store.

Users will receive the following message when access to the Microsoft Store is blocked:

:::image type="content" source="../media/store-denied-access-d318fe57.jpg" alt-text="Screenshot showing the store app is blocked.":::


#### Controlling the applications that users can install

Windows 10 Enterprise and Windows 10 Education editions enable you to use AppLocker to control which Universal Windows apps users can install and run. In AppLocker, you configure which Universal Windows apps to allow or deny, under the category Packaged Apps.

### Managing updates

IT administrators have limited control over updates for installed Universal Windows apps. You cannot control which updates are available. By default, applications installed from the Microsoft Store update automatically.
