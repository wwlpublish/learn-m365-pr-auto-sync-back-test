Today’s organizations face a number of challenges in controlling which applications run on client computers. These challenges include controlling:<br>

 -  The Universal Windows and desktop apps that users can access.
 -  Which users are allowed to install new applications.
 -  Which versions of the applications are allowed to run, and for which users.

Users who run unauthorized software can experience a higher incidence of malware infections and generate more help-desk calls. However, it can be difficult for you to ensure that the users’ computers run only approved and licensed software.

### AppLocker benefits

You can use AppLocker to specify which software can run on user PC’s and devices. AppLocker enables users to run the applications, installation programs, and scripts that they require to be productive, while still providing the security and compliance benefits of application standardization.

AppLocker can be useful for organizations that want to:

 -  Limit the number and types of applications that can run. This can be done by preventing unlicensed software or malware from running, and by restricting the ActiveX controls that are installed.
 -  Reduce the total cost of ownership by ensuring that workstations are homogeneous across an enterprise, and that users run only the software and applications that the enterprise approves.
 -  Reduce the security risks and possibility of information leaks from running unauthorized software.

### AppLocker rules

You can prevent many problems in your work environment by controlling which applications a user can run. AppLocker enables you to do this by creating rules that specify exactly which applications a user can run. AppLocker continues to function even when applications are updated.

Because you configure AppLocker with Group Policy, you need to understand Group Policy creation and deployment. This makes AppLocker ideal for organizations that currently use Group Policy to manage their Windows computers or have per-user application installations.

To author AppLocker rules, you use a new AppLocker Microsoft Management Console (MMC) snap-in in the Group Policy Management Editor window. AppLocker provides several rule-specific wizards. You can use one wizard to create a single rule and another wizard to generate rules automatically, based on your rule preferences and the folder that you select. The four wizards that AppLocker provides administrators with to author rules are:

 -  Executable Rules Wizard
 -  Windows Installer Rules Wizard
 -  Script Rules Wizard
 -  Packaged App Rules Wizard

At the end of each wizard, you can review the list of analyzed files. You then can modify the list to remove any file before AppLocker creates rules for the remaining files.

The Event Viewer stores events for AppLocker on the local computer. You can review these events if you want to check whether your AppLocker rules apply as designed. You can use the events in the following table to troubleshoot AppLocker from the client.

:::row:::
  :::column:::
    **Event ID**
  :::column-end:::
  :::column:::
    **Event reason**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    8000
  :::column-end:::
  :::column:::
    Indicates that the AppLocker policy did not apply correctly to the computer.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    8004
  :::column-end:::
  :::column:::
    Indicates that an .exe or .dll file did not run.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    8007
  :::column-end:::
  :::column:::
    Indicates that a script or .msi file did not run.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    8022
  :::column-end:::
  :::column:::
    Packaged app is disabled.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    8025
  :::column-end:::
  :::column:::
    Packaged app installation is disabled.
  :::column-end:::
:::row-end:::


> [!NOTE]
> Only the Windows Enterprise and Windows Education editions support AppLocker.
