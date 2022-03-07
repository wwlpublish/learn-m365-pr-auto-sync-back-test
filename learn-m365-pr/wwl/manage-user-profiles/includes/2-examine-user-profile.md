In Windows, a user profile contains a user state. A user profile is a set of files and folders. It is personal to each user who has signed in to the computer, and it’s stored in the Users folder. Windows requires each user who signs in to have a user profile. The Windows operating system creates a user profile when a user signs in for the first time. The initial user profile is based on the default user profile and is used for all subsequent sign-ins. User profiles contain details about the user environment, such as Start menu settings, desktop settings, user documents, and the user hive of the registry. By default, a user profile is stored on the same drive as the Windows operating system, in the C:\\Users folder. The user profile is used only when a user signs in to the same computer, but you can change the user profile type if you want to use it from multiple computers.

User profiles provide the following advantages:

 -  When the user logs on to a computer, the system uses the same settings that were in use when the user last logged off.
 -  When sharing a computer with other users, each user receives their customized desktop after logging on.
 -  Settings in the user profile are unique to each user. The settings cannot be accessed by other users. Changes made to one user's profile do not affect other users or other users' profiles.

#### Elements in a user profile

User state consists of four main data categories, including:

:::row:::
  :::column:::
    **Category**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User settings
  :::column-end:::
  :::column:::
    This component describes all settings that a user has personalized after the operating system was installed.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User registry
  :::column-end:::
  :::column:::
    This is the part of a computer’s registry that is specific to each user. Registry hive HKEY\_CURRENT\_USER (HKCU) stores settings that are specific to the currently signed-in user. The HKCU registry key is a link to the HKEY\_USERS subkey that corresponds to the user. The same information is accessible in both locations. On computers that run Windows, each user's settings are stored in their own files, named NTUSER.DAT. These files are in the Users folder on the boot volume. Settings in the HKCU hive follow users with a roaming profile from device to device.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Application Data
  :::column-end:::
  :::column:::
    The AppData folder, short for Application Data, is part of user state. This folder contains mostly application settings that are specific to a user. For example, if a user installs Microsoft Word 2016 and personalizes settings to fit their needs, such as adjusting toolbars, proofing, or language settings, Word 2016 stores these settings in the AppData folder. All well-designed applications should store their data in the AppData folder. However, it’s not possible to enforce this, and it’s entirely up to the developer to decide where an application stores its data. AppData folder provides a high degree of separation for user-related and computer-related application settings.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User data
  :::column-end:::
  :::column:::
    This component contains all user-specific data, such as files, which is stored in multiple user profile sub-folders, such as Documents, Favorites, Pictures, and Music. Users can change this location and store their data in any other folder to which they have Write permissions. However, by default, user data is stored in the individual user profile.
  :::column-end:::
:::row-end:::


When a user signs into a device for the first time, a new user profile is created. The configuration for that is based on the configuration of the Default Profile. A default profile is a pre-configured baseline profile, which contain all of the initial settings to be included, whenever a new profile is created.
