If you’re changing from Windows 7, Windows 8, or Windows 8.1 x86 to Windows 10 x64, you’ll migrate to new computers. The upgrade process can’t change from a 32-bit operating system to a 64-bit operating system, because of possible complications with installed applications and drivers.

## Migrate with the User State Migration Tool

You can use the User State Migration Tool (USMT) to automate migration during large deployments of the Windows operating system. USMT uses configurable migration rule  files (.xml) to control exactly which user accounts, user files, operating system settings, and application settings are migrated and how they are migrated. You can use USMT for both side-by-side migrations, where one piece of hardware is being replaced, or wipe-and-load (or refresh) migrations, when only the operating system is being upgraded

## Migrate with Windows Autopilot

A modern migration option with Windows 10 is to configure new PCs as part of a hardware refresh cycle using Windows Autopilot. You can work with hardware vendors to customize the default Windows Out of Box Experience (OOBE) with options such as eliminating licensing agreements or telemetry settings. There are no images to deploy, no drivers to inject, and no infrastructure to manage. When a user signs in to the PC during setup using their Azure AD credentials, Microsoft Intune takes over the deployment process and applies applications, software update configurations, and compliance policies.
