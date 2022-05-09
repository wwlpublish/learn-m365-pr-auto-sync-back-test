On occasion, an update can introduce reliability or performance problems after you install it on a computer. In these situations, you must remove the update that has caused the problem.

### Test updates

To avoid issues with feature upgrades and servicing updates, you should perform extensive testing before installing the updates on your Windows devices. The fastest way to test new upgrades is to sign up as a Windows Insider. As a Windows Insider, you have access to new upgrades before devices configured for General Availability Channel get the upgrades. If you are using a management system such as WSUS to approve upgrades, you can defer upgrades for an additional time to test the upgrades.

#### Uninstall updates

The simplest way to remove a problematic update is to uninstall it. To remove an update:

1.  Open the Settings app, select **Update &amp; security**, select **Windows Update**, select **Update history**, and then select **Uninstall updates**.
2.  Right-click the suspect update, and then select **Uninstall**.

#### Uninstall drivers

If you suspect a driver to be problematic, you can uninstall the driver. To uninstall an unwanted driver:

1.  Open **Device Manager**.
2.  Locate the device driver with the problem driver installed, right select it, and then select **Uninstall**.
3.  In the **Uninstall** dialog box, select the **Delete the driver software for this device** check box, if available.

### Use System Restore

If you are unsure which update has caused a problem, you can use System Restore to restore the computer’s configuration to an earlier point in time. However, this can potentially remove many updates.
