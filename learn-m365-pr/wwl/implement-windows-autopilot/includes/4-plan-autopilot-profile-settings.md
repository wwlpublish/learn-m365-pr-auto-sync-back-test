Windows Autopilot profiles control how Windows is installed on user devices. Profiles contain settings that are automatically set, and optional settings that must be manually set.

### Automatically set options

The following table identifies the Autopilot settings that are automatically set.

:::row:::
  :::column:::
    **Setting**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Skip Cortana, OneDrive, and OEM registration

  :::column-end:::
  :::column:::
    Skips the installation of consumer apps like Cortana and personal OneDrive. The device user can install these apps at a later time, as long as the user is a local admin on the device. The original manufacturer (OEM) registration is skipped because the device will be managed by Microsoft 365 Business Premium.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Sign in experience with your company brand

  :::column-end:::
  :::column:::
    If your company has an "[Add your company branding to Microsoft 365 Sign In page](/microsoft-365/admin/setup/customize-sign-in-page)," the device user will get that experience when signing in.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    MDM auto-enrollment with configured AAD accounts

  :::column-end:::
  :::column:::
    The user identity will be managed by Azure Active Directory. Users will sign in to Windows and Microsoft 365 with their Microsoft 365 Business Premium credentials.

  :::column-end:::
:::row-end:::


### Manually set options

The following table identifies the optional settings that must be manually set.

:::row:::
  :::column:::
    **Setting**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Skip privacy settings (Off by default)

  :::column-end:::
  :::column:::
    If this option is set to On, the device user won't see the license agreement for the device and Windows when they first sign in.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Don't allow the user to become the local admin

  :::column-end:::
  :::column:::
    If this option is set to On, the device user can't install any personal apps, such as Cortana.

  :::column-end:::
:::row-end:::
