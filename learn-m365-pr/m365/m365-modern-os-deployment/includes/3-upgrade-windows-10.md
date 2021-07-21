If you have existing computers running Windows 7, Windows 8, or Windows 8.1, x64, use one of the upgrade methods, unless your inventory and testing revealed blocking issues, like antivirus or disk encryption apps that are incompatible with the upgrade process.

## Upgrade considerations

When you upgrade to a new version of Windows, be aware of the following:

**Application compatibility.** Most of your applications, drivers, and add-ins will work as-is. Both Upgrade Readiness and the Readiness Toolkit help assess items in your org that might have compatibility issues. They also provide you with known information about compatibility, including where to find version updates to resolve them. Test these updates before you roll them out.

**Multilingual Windows image upgrades.** The User State Migration tool (USMT) doesn't support cross-language upgrades. If you need to upgrade multilingual Windows devices, upgrade or migrate only the system default user interface language. For example, if English is the default but you have a Spanish language pack installed, you can upgrade only to English.

**Errorhandler.cmd.** If you want to use Errorhandler.cmd during your upgrade, copy the file into the %WINDIR%\Setup\Scripts directory on the old installation. This ensures that if there are errors during the down-level phase of Windows Setup, the commands in Errorhandler.cmd still run.

**Data drive ACL migration.** During the configuration pass of Windows Setup, the root access control list (ACL) on drives formatted for NTFS without an installed OS are changed to the default Windows XP ACL format. This change enables authenticated users to modify access on folders and files. Because this change may affect performance, you can [change the relevant registry value](/windows/deployment/upgrade/windows-upgrade-and-migration-considerations?azure-portal=true) to disable this feature if needed.

## In-place upgrades

For existing Windows 7, Windows 8, or Windows 8.1 x64 PCs, the recommended path uses the Windows installation program (setup.exe) to perform an in-place upgrade, automatically preserving all data, settings, applications, and drivers. In-place upgrades run several small pre-installation checks to look for known compatibility issues. It also preserves the user state and applications while removing what isn't compatible with the version of Windows 10 you're installing.

The in-place upgrade process supports manually or automatically rolling back to the previous OS if you encounter issues either during or after deployment.

In-place upgrades are typically faster than traditional deployments because applications don't need to be reinstalled as part of the process.

## In-place upgrades using task sequence automation

You can have more control over the upgrade process by using tools like Configuration Manager to completely automate the upgrade process through task sequences. When task sequences run, they run the actions of each step at the command-line level in the Local System context. This means the task sequence is fully automated with no user intervention.

Previous versions of Windows didn't require a task sequence for in-place upgrades, but we do recommend it when deploying Windows 10 at enterprise scale. And while an in-place upgrade doesn't let you apply a custom image with applications, you can update the default install.wim by, for example, installing the latest Windows updates in your task sequence prior to performing the upgrade.

You can use in-place upgrade to migrate to Windows 10 from older versions of Windows, as well as to update from previous versions of Windows 10. After Windows Setup completes the upgrade, the task sequence can continue to run and upgrade applications like Office, replace drivers, and apply personalization settings. Likewise, you can use the upgrade task sequence to perform pre-installation tasks or checks prior to carrying out the upgrade.

Regardless of the deployment type you choose, automation provides predictability and repeatability.

## Learn more

- [Manage in-place upgrades](/windows/deployment/upgrade/upgrade-to-windows-10-with-system-center-configuraton-manager?azure-portal=true)
- [Windows Autopilot for existing devices](/windows/deployment/windows-autopilot/existing-devices?azure-portal=true)
- [Configure a Desktop Analytics environment](/configmgr/desktop-analytics/set-up?azure-portal=true)
- [Assess which computers can be upgraded to Windows 10](/configmgr/desktop-analytics/about-deployment-plans?azure-portal=true)
