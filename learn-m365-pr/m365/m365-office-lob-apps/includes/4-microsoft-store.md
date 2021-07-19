**Microsoft Store for Business** provides a flexible way to discover, acquire, manage, and distribute free and paid apps to Windows 10 devices at scale. You can publish selected Microsoft Store apps and custom organizational apps to your own private store while assigning and reusing licenses as needed. End users are directed to this private store and can only find and install approved apps with online licenses.

## Package your business app for the Microsoft Store

You can build store apps as Universal Windows Platform (UWP) apps or repackage existing apps for the store and add modern experiences for Windows 10. Your apps remain unchanged and continue to run in full-trust user mode.

A new option for application packaging used by the Microsoft Store is MSIX, which applies the containerization technology available in Windows. Containerization means clean uninstall and removal of packages. It also means users only need standard user credentials to install applications – you don't have to have administrator credentials to install MSIX containers.

Before you package your desktop app for the store, be sure to review any requirements for the application and address any of the issues that come up. In most cases, we recommend you use the [MSIX Packaging Tool](/windows/msix/packaging-tool/create-app-package-msi-vm), available from the Microsoft Store, to repackage an existing desktop app to the MSIX format. It has both an interactive UI and a command line for conversions and it gives you the ability to convert an application without having the source code.

### Distribute your apps using your private store

Your private store is available as a tab in the Microsoft Store app and is named for your company or organization. You can make an app available in your private store when you acquire the app, or you can do it later from your inventory. Once the app is in your private store, employees may claim and install the app.

## Learn more

- [Plan for the Microsoft Store for Business](/microsoft-store/prerequisites-microsoft-store-for-business?azure-portal=true)
- [Configure access to Microsoft Store](/windows/configuration/stop-employees-from-using-microsoft-store?azure-portal=true)
- [Manage apps in Microsoft Store for Business](/microsoft-store/manage-apps-microsoft-store-for-business-overview?azure-portal=true)
- [Windows 10 sideloading](/intune/apps/app-sideload-windows?azure-portal=true)
- [Plan for device and app monitoring](/configmgr/desktop-analytics/health-status-monitoring?azure-portal=true)
- [Manage kiosk settings](/intune/configuration/kiosk-settings-windows?azure-portal=true)
