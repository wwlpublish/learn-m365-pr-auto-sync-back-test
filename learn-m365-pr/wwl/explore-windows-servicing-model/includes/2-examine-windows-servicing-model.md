Historically, new versions of Windows have been released every few years. The deployment of those new versions within an organization would then become a project, either by leveraging a "wipe and load" process to deploy the new operating system version to existing computers, or by migrating to the new operating system version as part of the hardware replacement cycle. Either way, a significant amount of time and effort was required to complete these tasks. Starting with Windows 10, a new model is being adopted. This new model, referred to as "Windows as a service," requires organizations to rethink how they deploy and upgrade Windows. It is no longer a project that happens every few years, it is a continual process.

### Windows as a service

Instead of new features being added only in new releases that happen every few years, the goal of Windows as a service is to continually provide new capabilities. New features are provided or updated two to three times per year, while maintaining a high level of hardware and application compatibility. The key to enabling significantly shorter product cycles while maintaining high-quality levels is an innovative community-centric approach to testing that Microsoft has implemented for Windows 10 and later. The community, known as Windows Insiders, is comprised of millions of users around the world.

When Windows Insiders opt in to the community, they test many builds over the course of a product cycle, and provide feedback to Microsoft through an iterative methodology called flighting. Builds distributed as flights provide the Windows engineering team with significant data regarding how good builds are performing in actual use. Flighting with Windows Insiders also enables Microsoft to test builds in much more diverse hardware, application, and networking environments than in the past, and to identify issues far more quickly. As a result, Microsoft believes that community-focused flighting will enable both a faster pace of innovation delivery, and better public release quality than ever.

Although Microsoft releases flight builds to Windows Insiders, Microsoft will publish two types of Windows releases broadly to the public on an ongoing basis:

 -  **Feature updates that install the latest new features, experiences, and capabilities on devices that are already running Windows 10 and later**. Because feature upgrades contain an entire copy of Windows, they are also what customers can use to install Windows 10 or later on existing devices running Windows 8.1, and on new devices where no operating system is installed.
 -  **Quality updates that focus on the installation of security fixes and other important updates**. Microsoft expects to publish an average of two to three new feature upgrades per year, and to publish servicing updates as needed for any feature upgrades that are still in support. Microsoft will continue publishing servicing updates on Update Tuesday (sometimes referred to as Patch Tuesday). Additionally, Microsoft may publish additional servicing updates for Windows outside the Update Tuesday process when required to address customer needs.

It is important to note that, to improve release quality and simplify deployments, all new releases that Microsoft publishes for Windows 10 and later will be cumulative. This means new feature upgrades and servicing updates will contain the payloads of all previous releases (in an optimized form to reduce storage and networking requirements), and installing the release on a device will bring it completely up-to-date. Also, unlike earlier versions of Windows, you cannot install a subset of the contents of a Windows servicing update. For example, if a servicing update contains fixes for three security vulnerabilities and one reliability issue, deploying the update will result in the installation of all four fixes.

This new model uses simpler deployment methods, reducing the overall amount of effort required for Windows servicing. By combining these simpler methods (such as in-place upgrade) with new techniques to deploy upgrades in phases to existing devices, the effort that used to be performed as part of a traditional deployment project is spread across a broad period.

The following terms are used when discussing the Windows servicing model:

:::row:::
  :::column:::
    **Term**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Feature updates**
  :::column-end:::
  :::column:::
    A new Windows release that contains additional features and capabilities, released one to two times per year.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Quality updates**
  :::column-end:::
  :::column:::
    Rather than receiving several updates each month and trying to figure out which the organization needs, which ultimately causes platform fragmentation, administrators will see one cumulative monthly update that supersedes the previous month’s update, containing both security and non-security fixes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Channel**
  :::column-end:::
  :::column:::
    The Windows servicing channel offers three choices: Windows Insider, General Availability Channel, or Long-Term Servicing Channel. Channels allow customers to designate how frequently their General Availability Channel devices are updated.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Ring**
  :::column-end:::
  :::column:::
    This method is used to separate machines into a deployment timeline. These are groups determined by administrators. Examples of ring names could be Preview, Limited, Broad, and so on.
  :::column-end:::
:::row-end:::
