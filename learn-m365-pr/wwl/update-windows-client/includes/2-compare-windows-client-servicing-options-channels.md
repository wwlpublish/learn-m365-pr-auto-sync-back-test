With Windows as a service, Microsoft simplifies the operating system deployment process. Microsoft now releases improvments and even new versions of Windows through the same technology used to deliver regular updates. Updates are now delivered as follows:

 -  **Quality updates**. Provide reliability and security updates and fixes, usually at least once a month. Each month, a cumulative update is released which supersedes all previous updates. This helps to ensure that organizations’ devices more closely align to those used for testing in Microsoft.<br>
 -  **Feature updates**. Adds new functionality annually. Microsoft aims to package new features into annual updates that can be readily deployed using existing management tools. Because the updates are delivered using the same method as quality updates, deployment is considerably easier. Consequently, the workload and cost impact on organizations is reduced. OS upgrades are also now delivered through this method, such as upgrading from Windows 10 to Windows 11.

In addition to feature and quality updates, Windows update continues to provide the following update types:

 -  **Driver updates**. These are non-Microsoft drivers that are applicable to your devices.
 -  **Microsoft product updates**. These are updates for other Microsoft products, such as Office.

### Servicing channels

To streamlining of the update process, Windows offers three servicing channels, each of which offers you a different level of flexibility with how and when updates are delivered to devices. Using the different servicing channels allows you to deploy Windows "as a service", which conceives of deployment as a continual process of updates, which roll out across the organization in waves.

You can assign devices to the following servicing channels:

 -  **Windows Insider Program**. Insider preview releases are made available during the development of the features that will be shipped in the next feature update, enabling organizations to validate new features and compatibility with existing apps and infrastructure, providing feedback to Microsoft on any issues encountered. Within the Windows Insider Program, there are three options:
    
     -  Dev Channel
     -  Beta Channel
     -  Release Preview
 -  **General Availability Channel.** This is the channel most devices will typically be assigned to. Computers configured in the General Availability Channel receive updates as soon as Microsoft publishes them (if no deferral is configured).
 -  **Long-Term Servicing Channel**. For computers and other devices that perform a single task or a number of specialized tasks, the long-term servicing channel prevents configured devices from receiving feature updates; delivery of quality updates is not affected. Note that the Long-term Servicing Channel is available only in the Windows 10/11 Enterprise LTSC edition.

> [!NOTE]
> The Semi-Annual Channel (Targeted) servicing channel was removed in version 1903. As Microsoft has shifted to annual feature updates in Windows, the General Availability channel replaced the Semi-Annual channel.

### Deployment rings

In Windows 10 and later, you can use deployment rings to further control how and when updates are applied to your devices. Rings are where you can define the type of update, the channel, and any deferrals. These rings can then be assigned to groups to control the device update experience and schedule.

Below is an example of deployment rings you might create:

:::row:::
  :::column:::
    **Name of ring**
  :::column-end:::
  :::column:::
    **Channel**
  :::column-end:::
  :::column:::
    **Feature update deferral**
  :::column-end:::
  :::column:::
    **Quality update deferral**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Preview
  :::column-end:::
  :::column:::
    Windows Insider Program
  :::column-end:::
  :::column:::
    None
  :::column-end:::
  :::column:::
    None
  :::column-end:::
  :::column:::
    You can test updates on a small group of devices before they become more widely available on the General Availability Channel.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Broad
  :::column-end:::
  :::column:::
    Semi-Annual Channel
  :::column-end:::
  :::column:::
    120 days
  :::column-end:::
  :::column:::
    7-14 days
  :::column-end:::
  :::column:::
    Use this ring to deploy to most of your users’ devices. Use the deferment period to thoroughly test the updates before further deployment. Note: You can pause updates if you encounter significant problems or issues.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Critical
  :::column-end:::
  :::column:::
    Semi-Annual Channel
  :::column-end:::
  :::column:::
    180 days
  :::column-end:::
  :::column:::
    30 days
  :::column-end:::
  :::column:::
    Reserved for devices that are critical and which are only updated when the updates have been thoroughly tested throughout the rest of your organization.
  :::column-end:::
:::row-end:::


> [!NOTE]
> You can defer feature updates up to 365 days and quality updates up to 30 days.
