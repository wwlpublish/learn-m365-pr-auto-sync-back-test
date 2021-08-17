![checkmark icon](../media/checkmark-icon.png)

## Troubleshooting updates

Due to the similarity and shared processes between the initial installation and update processes with Office Click-to-Run packages, troubleshooting Office update failures are similar to troubleshooting installation failures.

- Make sure scheduled tasks are still present in Task Scheduler.
- Check that the device can access your defined update path:
  - officecdn.microsoft.com
  - Configuration Manager
  - other custom-defined location
- Check the **%ProgramFiles%\Microsoft Office\Updates\Download** and **..\Apply** folders for update packages.
- Check the registry for the last trigger source to make sure it's set properly. It's usually **SCHEDULEDTASK** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Scenario\UPDATE`
- Check `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration` for **VersionToReport** to make sure the version is correct.
- Try deleting the **Updates** folder in **%ProgramFiles%\Microsoft Office** to see if triggering another update will start to hydrate update files.

Remember that updates from CDN sources may be throttled – especially when it's close to an update release day. Files may trickle in more slowly than expected to **%ProgramFiles%** locations.

## Troubleshooting activation

In some cases, activation services will not set Office licensing and Office will lose its license activation state. In these cases, check the following:

- Check that network connections resolve to licensing services.
- Ensure that the user is provisioned in Azure Active Directory and correctly entered their credentials.
- Ensure that the user is licensed for the corresponding Office subscription versions. If you're using KMS, make sure that the device can reach KMS services and that a matching KMS key has been installed on the Key Management server.
- Check if there is a product key configured on the device – this applies to all activation types. Run **OSPP.vbs** to check licensing status using the following syntax:

    ```cscript "C:\Program files\Microsoft Office\office16\ospp.vbs" /dstatus```

In some cases, you'll need to use **OLicenseCleanup.vbs** to remove user-based activation and attempt to sign in again.

## Installation repair

Certain Office issues may be a result of recently applied Windows updates or other apps installed on the device. Some common cases include:

- Default file associations are lost or assigned to another app. For example, the default PDF viewer changes from Word to Microsoft Edge or Adobe Acrobat.
- Pinned taskbar icons for Office apps disappearing after an update.

To fix these kinds of issues, and before uninstalling and reinstalling Office to a known working version, you can try to fix the problem manually. This is where **Quick Repair** and **Online Repair** can help. You'll access these options in **Windows Settings > Apps and Features > your Office install > Modify**.

- **Quick repair** runs in standard user context (without local admin privilege) and doesn't need Internet connectivity. It runs from locally stored source to perform simple tasks like taking back default file associations.
- **Online repair** needs local admin privilege and Internet connectivity, but essentially reinstalls the affected version of Office according to previously configured installation parameters and properties.

These are just a few options to troubleshoot misconfigured Office installations and a few suggestions to fix issues. For further support, you can engage with Microsoft Support services.
