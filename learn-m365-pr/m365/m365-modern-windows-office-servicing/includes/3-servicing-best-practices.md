To align with the new method of delivering feature and quality updates in Windows 10, Microsoft uses **servicing channels** to let you designate how frequently your individual devices are updated. For example, you can have test devices that the IT department updates with new features as soon as possible as well as specialized devices that require a longer feature update cycle to ensure continuity.

## Use phased deployments for feature and security updates

For any release, we recommend at least three deployment phases for IT: validation, piloting, and broad production deployment.


## Expand your validation of security updates

Before security updates are rolled out for broad deployment, builds are released through the **Insider Programs** for Office and Windows. The Insider Program provides access to early update releases that you can validate on your own system before deploying them to your whole organization. Microsoft also uses the Insider Programs to gather diagnostic data and feedback prior to releasing updates broadly. This helps minimize update incompatibilities. The Insider Programs are open to everyone.

## Simplify feature updates with Windows Update for Business

Windows Update for Business is a free service that helps you keep Windows 10 devices up to date by directly connecting the devices to the Windows Update service. You can configure Windows Update for Business by using Group Policy or through MDM solutions, like Microsoft Intune. Windows Update for Business lets you create deployment rings to validate new builds. It's integrated into existing management tools like Windows Server Update Services (WSUS), Configuration Manager (current branch), and Microsoft Intune. Windows Update for Business also supports peer-to-peer delivery to help optimize bandwidth efficiency and reduce network congestion.

## Employ Express Updates for bandwidth management

You can significantly reduce download size by using a technology like **Express Updates** in Windows. In this approach, the update engines compare the PC's current status and find only the delta needed to update it. Windows Update for Business and Windows Server Update Services have supported express updates for a long time, and Configuration Manager has been updated so that it can also use express updates.

![Express Updates screen](../media/step-7-1.png)

### Explore how to optimize Windows 10 updates

View a [video version](https://www.microsoft.com/videoplayer/embed/RE44iA0) of the interactive guide (captions available in more languages).

<a href="https://mslearn.cloudguides.com/guides/Optimize%20delivery%20of%20Windows%2010%20updates">![Optimize delivery of Windows 10 updates](../media/lab-optimize-updates.png)</a>  

Be sure to click the full-screen option in the video player. When you're done, use the **Back** arrow in your browser to come back to this page.
