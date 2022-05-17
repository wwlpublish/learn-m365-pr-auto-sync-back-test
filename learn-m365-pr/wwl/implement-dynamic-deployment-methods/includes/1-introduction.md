Even with the ability to reset the existing Windows image with Autopilot, sometimes even that isn’t necessary, especially with new devices purchased from an OEM. A new device typically starts with a fresh install of Windows, and what’s typically needed is the correct edition deployed (such as Windows Enterprise or Education), correct configuration and apps. When this is the case, dynamic provisioning can further simplify deployments.

Dynamic provisioning uses a number of transforms to achieve this objective.

:::row:::
  :::column:::
    **Name**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Windows 10 Subscription Activation
  :::column-end:::
  :::column:::
    With Windows Subscription Activation, users of Windows Pro can upgrade to Windows Enterprise without needing to enter a product key, nor perform a restart.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Provisioning package configuration
  :::column-end:::
  :::column:::
    By using Windows Configuration Designer, you can create configuration packages that you can deploy to users’ devices that can be used to configure apps and settings on those devices.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Azure AD join with automatic MDM enrollment
  :::column-end:::
  :::column:::
    Using Azure AD join with automatic MDM enrollment, users enter their work or school account details and their device is automatically joined to Azure AD and enrolled in MDM. The user’s device is then configured per the organization’s MD policies.
  :::column-end:::
:::row-end:::


### Objectives

After completing this module, you will be able to:

 -  Describe how Subscription Activation works.
 -  Describe the benefits of Provisioning Packages.
 -  Explain how Windows Configuration Designer creates Provisioning Packages.
 -  Describe the benefits of using MDM enrollment with Azure AD join.
