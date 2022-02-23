*Group Policy* is a system that you can use to apply configuration settings to Windows clients and servers. You create Group Policy Objects (GPOs) that contain Group Policy settings. The settings can be applied to the local client individually. With domain-joined clients, Windows-based computers download and apply the settings in GPOs.

## Group Policy Objects

A *GPO* is an object that contains one or more policy settings that apply configuration settings for users, computers, or both. GPOs can be managed using Group Policy Management Console (GPMC). Within the GPMC, you can open and edit a GPO by using the Group Policy Management Editor window. GPOs logically link to AD DS containers to apply settings to the objects in those containers.

> [!NOTE]
> GPOs can be applied to AD DS sites, domains, and organizational units (OUs). This is referred to as linking. GPOs can't link to the default Computers or Users containers in AD DS.

> [!NOTE]
> GPOs can be used regardless of whether the machine is joined to a domain. This is covered in more detail in the next unit.

### Group Policy settings

A Group Policy setting is the most specific component of Group Policy. It defines a specific configuration change to apply to an object (a computer, a user, or both) within AD DS. Group Policy has thousands of configurable settings. These settings can affect nearly every area of the computing environment. Not all settings can be applied to all older versions of Windows Server and Windows operating systems. Each new version introduces new settings and capabilities that only apply to that specific version. If a computer has a Group Policy setting applied that it cannot process, it simply ignores it.

For example, in Windows 7 you do not use Group Policy to configure a Start menu layout, so Windows 7 computers ignore the Start menu layout. However, Windows 10 devices will process the setting.

Most Group Policy settings have three states:

 -  Not Configured. The GPO does not modify the existing configuration of the setting for the user or computer.
 -  Enabled. The GPO applies the policy setting.
 -  Disabled. The GPO reverses the policy setting.

> [!NOTE]
> By default, most Group Policy settings are set to Not Configured.

> [!NOTE]
> Some settings are multivalued or have text string values. These typically provide specific configuration details to applications or operating system components. For example, a setting might provide the URL of the home page for internet Explorer or for blocked applications.

The effect of the configuration change depends on the Group Policy setting. For example, if you enable the Prohibit Access to Control Panel Group Policy setting, users will be unable to open Control Panel. If you disable the Group Policy setting, you ensure that users can open Control Panel. Notice the double negative in this Group Policy setting: you disable a policy setting that prevents an action, thereby allowing the action.

#### Group Policy settings structure

There are two distinct types of Group Policy settings:

 -  **User settings.** These settings modify the HKEY\_CURRENT\_USER hive of the registry.
 -  **Computer settings.** These settings modify the HKEY\_LOCAL\_MACHINE hive of the registry.

User settings and computer settings each have three areas of configuration, as described in the following table.

:::row:::
  :::column:::
    **Section**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Software settings
  :::column-end:::
  :::column:::
    Contains software settings that can deploy to either the user or the computer. Software that deploys or publishes to a user is specific to that user. Software that deploys to a computer is available to all users of that computer.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Windows operating system settings
  :::column-end:::
  :::column:::
    Contains script settings and security settings for both user and computer, and Internet Explorer maintenance for the user configuration.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Administrative templates
  :::column-end:::
  :::column:::
    Contains hundreds of settings that modify the registry to control various aspects of the user and computer environment. Microsoft or other vendors might create new administrative templates. You can add these new templates to the GPMC. For example, Microsoft has Microsoft Office 2013 templates that are available for download that you can add to the GPMC.
  :::column-end:::
:::row-end:::


### Group Policy Management Editor

The Group Policy Management Editor window displays the individual Group Policy settings that are available in a GPO. These display in an organized hierarchy that begins with the division between computer settings and user settings, and then expands to show the **Computer Configuration** node and the **User Configuration** node. You configure all Group Policy settings and preferences in the Group Policy Management Editor window.

> [!NOTE]
> In Windows, some Group Policy settings such as disabling the lock screen, disabling Windows tips in the UI, and turning off the Microsoft Consumer Experience are available only in the Enterprise edition of the Windows operating system.

### Group Policy preferences

In addition to the Group Policy sections shown in the preceding table, there is a **Preferences** node under both the **Computer Configuration** and **User Configuration** nodes in the **Group Policy Management Editor** window. Preferences provide even more capabilities with which to configure the environment. The key difference between a GPO setting and Group Policy Preference is that the GPO setting is enforced, and cannot be modified outside of the GPO. For example, you cannot change an item whose setting was configured in a GPO by changing it in the Settings app or Control Panel. A Group Policy Preference, on the other hand, is not enforced. Users can change it if they have the necessary permissions and rights on the computer.
