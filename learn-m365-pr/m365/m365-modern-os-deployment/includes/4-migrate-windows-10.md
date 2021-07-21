If you're changing from Windows 7, Windows 8, or Windows 8.1 x86 to Windows 10 x64, you'll be migrating to new computers. Upgrades can't change from a 32-bit operating system to a 64-bit operating system, because of possible complications with installed applications and drivers.

## Migrate with the User State Migration Tool

You can use the User State Migration Tool (USMT) to automate migration during large deployments of the Windows operating system. USMT uses configurable migration rule files (.xml) to control exactly which user accounts, user files, operating system settings, and application settings are migrated and how they are migrated. You can use USMT for both side-by-side migrations, where one piece of hardware is being replaced, or wipe-and-load (or refresh) migrations, when only the operating system is being upgraded.

## Migrate with Windows Autopilot

Windows Autopilot is a modern migration option for devices that already have Windows 10 installed. Unlike the imaging process that wipes the PC and redeploys Windows, Autopilot enables you to customize the default Windows Out of Box Experience (OOBE) with options such as eliminating licensing agreements. By working with hardware vendors, devices can also be shipped directly to the user from the vendor, without the need for IT to physically touch the device at all, including switching from Pro to Enterprise or Education.

There are no images to deploy, no drivers to inject, and no infrastructure to manage. When a user signs into the PC during setup using their Azure AD credentials, Microsoft Intune takes over the deployment process and applies applications, software update configurations, and compliance policies.

Windows Autopilot is cloud-driven and based around Azure AD Premium and Microsoft Intune. Intune leverages the unique device IDs provided by the manufacturer or identified using PowerShell.

Using Windows Autopilot, you can:

- Join devices to Azure AD automatically.
- Auto-enroll your users' devices into MDM services.
- Restrict the creation of the administrator account.
- Customize the OOBE content specifically to your organization.
- Apply applications, software update configurations, and compliance policies.
- Reset, repurpose, or recover devices.
