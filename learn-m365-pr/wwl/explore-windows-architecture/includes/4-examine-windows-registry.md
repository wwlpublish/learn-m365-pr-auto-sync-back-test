The registry is a database in which Windows stores user and computer configuration settings. Whenever you make a configuration change to Windows, the registry records the change.

Usually, you don't need to make direct changes to the registry. In fact, making direct changes to the registry risks introducing errors that might cause applications or devices to behave incorrectly and even can result in your computer being unable to start at all. However, as an IT professional, you engage in troubleshooting regularly, so you might be required to work directly with the registry by performing imports and exports of settings and making edits of registry settings. This lesson explores the registry’s structure and explains the tools that you can use to edit a registry

The Windows registry is organized in a hierarchical manner. At the top level, there are five registry hives, which is a discrete collection of related settings that are structured as a series of keys, subkeys, and values.<br>

:::image type="content" source="../media/registry-editor-e5745f45.jpg" alt-text="Screenshot of the registry editor.":::


### Hives

The following table describes the top-level hives, or subtrees.

:::row:::
  :::column:::
    **Hive**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **HKEY\_CLASSES\_ROOT**
  :::column-end:::
  :::column:::
    This hive contains file association information and defines which application opens when a user double-clicks a particular file type on the file system. For example, it defines that the application for .xlsx files is Microsoft Excel. This hive is populated from the computer-related and user-related settings that are stored in HKEY\_LOCAL\_MACHINE\\Software\\Classes and HKEY\_CURRENT\_USER\\Software\\Classes. You typically won't make edits to this hive.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **HKEY\_CURRENT\_USER**
  :::column-end:::
  :::column:::
    This hive contains configuration information for the currently signed-in user. Items such as the user’s Windows color scheme and font settings are stored in relevant values below this hive. When referencing this hive while editing the registry, this hive sometimes is referred to as HKCU. This hive is a shortcut to a key stored in HKEY\_USERS.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **HKEY\_LOCAL\_MACHINE**
  :::column-end:::
  :::column:::
    This is probably the most important hive and the one to which you likely will make the most edits. Sometimes abbreviated to HKLM, this hive stores all of the computer-related configuration settings.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **HKEY\_USERS**
  :::column-end:::
  :::column:::
    This hive contains a collection of all of the configuration information for all users that have signed in locally to the computer, including the currently signed-in user. In fact, one of the keys beneath this hive is the key of the currently signed in user, which is shown as HKEY\_CURRENT\_USER hive. It's important to know that you're likely to make direct edits to the user settings for the currently signed-in user only.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **HKEY\_CURRENT\_CONFIG**
  :::column-end:::
  :::column:::
    This hive contains information about the current hardware profile that the local computer used during system startup. You typically don't make edits to this hive.
  :::column-end:::
:::row-end:::


> [!NOTE]
> Most likely, you'll make direct changes only to the values stored within the hives HKEY\\\_LOCAL\\\_MACHINE and HKEY\\\_CURRENT\\\_USER.

> [!NOTE]
> The registry is a hierarchical database of values structured in hives, keys, and subkeys, but the actual registry database is stored on the local file system in the C:\\Windows\\System32\\Config file. There's no requirement for you to access these files directly.

### Keys and subkeys

To maintain structure within the database, similar settings are stored in folders and subfolders known as keys and subkeys. This makes it easier to reference a particular registry value. You can specify a pathname by declaring the appropriate hive, key, subkeys, and value, as the following example shows:

 -  HKCU\\Control Panel\\Desktop\\Wallpaper is the value (Wallpaper) that stores the name and location of a user’s desktop wallpaper.
 -  HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\Run is the key that contains values that relate to programs that start automatically when the computer starts and a user signs in. Typically, these programs reside in the system tray.

### Values

Values define the behavior of the operating system, and they're stored in keys and subkeys. There are many types of values, depending upon the type of data that each stores. For example, you may wish to store text values, numerical data, variables, and similar data. The following table lists the more common types of registry values.

:::row:::
  :::column:::
    **Value type**
  :::column-end:::
  :::column:::
    **Data type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **REG\_BINARY**
  :::column-end:::
  :::column:::
    Binary
  :::column-end:::
  :::column:::
    Raw binary data. These values usually display in hexadecimal format. Hardware information is often stored in REG\_BINARY values.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **REG\_DWORD**
  :::column-end:::
  :::column:::
    DWORD
  :::column-end:::
  :::column:::
    4-byte numbers (a 32-bit integer). Many device-driver and service-related values are stored in REG\_DWORD values. For example, the START and TYPE values for device drivers always are defined in REG\_DWORD type values.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **REG\_SZ**
  :::column-end:::
  :::column:::
    String
  :::column-end:::
  :::column:::
    A fixed-length text string. The values listed in the HKLM\\Software\\Microsoft\\Windows\\CurrentVersion\\Run key are all REG\_SZ values. These values store the path and filename to the appropriate autostart program.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **REG\_EXPAND\_SZ**
  :::column-end:::
  :::column:::
    Expandable string
  :::column-end:::
  :::column:::
    A variable length text string. The Windows operating system uses REG\_EXPAND\_SZ values to contain variables. For example, the ImagePath value that defines the name of a service’s executable in the file system is stored in an expandable string: %systemroot%\\System32\\service.exe.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **REG\_MULTI\_SZ**
  :::column-end:::
  :::column:::
    Multiple strings
  :::column-end:::
  :::column:::
    Multiple string values. This value typically is used when multiple values are stored. For example, the DependOnService value for a service is a REG\_MULTI\_SZ data type, and contains one or more services on which this service is dependent.
  :::column-end:::
:::row-end:::


When you decide to make a direct change to the registry, you must be accurate about the value name, its type, and its full registry path, including all subkeys, keys, and the appropriate hive. If you don't use this information accurately, your changes might not have the desired effect and could cause the computer to fail to work properly or even start up.
