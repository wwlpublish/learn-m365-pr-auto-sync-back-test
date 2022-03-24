The default version of Microsoft Edge received updates on a fairly regular basis, approximately every four weeks. Like the Windows Insider program, Edge provides different channels for giving more control to Administrators on how often devices receive these updates and providing a way for administrators and users to preview upcoming builds.

Edge provides the following channel options: Stable, Extended Stable, Beta, Dev, and Canary. Each channel is a separate browser application that is downloaded. This means that you can have multiple channels installed if desired, such as using the Stable channel browser for using line-of-business web applications, and the Dev channel browser for previewing upcoming features.

:::row:::
  :::column:::
    **Channel**
  :::column-end:::
  :::column:::
    **Primary purpose**
  :::column-end:::
  :::column:::
    **How often updated with new features**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Stable
  :::column-end:::
  :::column:::
    Intended for broad deployment. Stable version of the prior Beta channel release. Most users should be using this channel.
  :::column-end:::
  :::column:::
    New features shipped about every four weeks.
Security and quality updates ship as needed.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Extended Stable
  :::column-end:::
  :::column:::
    An enterprise release option for Stable aligned to a longer release cycle. Intended for scenarios that require longer timeline to test and validate updates.
Updated on every other release, aligned with even-numbered releases, such as version 94, 96, 98, etc.
  :::column-end:::
  :::column:::
    New features shipped about every eight weeks.
Security and quality updates ship as needed.

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Beta
  :::column-end:::
  :::column:::
    Supported release that is ideal for a sample set of users validating the next build in the environment prior to its release in the Stable channel.
  :::column-end:::
  :::column:::
    New features shipped about every four weeks.
Security and quality updates ship as needed.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Dev
  :::column-end:::
  :::column:::
    Opportunity to see what is coming in the next beta release. Intended for planning and developing with the latest capabilities. Higher quality build than Canary channel, but is not supported.
  :::column-end:::
  :::column:::
    Updated weekly.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Canary
  :::column-end:::
  :::column:::
    Bleeding edge content. Builds have a high chance of issues, and are not supported.
  :::column-end:::
  :::column:::
    Updated daily.
  :::column-end:::
:::row-end:::


### Installing Channels

Channels can be downloaded from the Microsoft Edge Insider channels site at [https://www.microsoftedgeinsider.com/en-us/download/](https://www.microsoftedgeinsider.com/en-us/download/). You can select the channel and platform to download, and run these channels side by side. You can identify the version of Edge that is running by navigating to the Settings Help page at *edge://settings/help*. MSI packages are also available to be deployed like any other application.

> [!NOTE]
> The Extended Stable channel is not a separate browser application. When this channel is selected, the existing Edge installation is changed to update on the even-numbered versions.

You can also opt in to channels using policies as well, such as Group Policy or Endpoint Configuration Manager. This can be accomplished by setting the Target Channel override setting to a different channel. Applying this policy is useful for targeting devices that are better suited for longer update cycles, or selective groups for previewing or collecting feedback on an upcoming release.

The following steps are an example of configuring a client configured for automatic updates to switch to the Extended Stable channel using Group Policy:

1.  Open the local Group Policy Editor and go to *Computer Configuration > Administrative Templates > Microsoft Edge Update > Applications > Microsoft Edge*.
2.  Select **Target Channel override** and then select **Enabled**.
3.  Under **Options**, select **Extended Stable** from the Policy dropdown list.

> [!NOTE]
> When configuring the override policy, this becomes seemless to the end user, and users do not need to select a separate browser to open. If switching to the Extended Stable channel, the existing version will not downgrade if the Stable version is higher than the current Extended Stable version.
