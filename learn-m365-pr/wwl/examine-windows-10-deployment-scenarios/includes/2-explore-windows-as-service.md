Windows as a Service (WaaS) provides a new way to think about building, deploying, and servicing the Windows operating system. The Windows as a Service model is focused on continually providing new capabilities and updates while maintaining a high level of hardware and software compatibility.

Deploying new versions of Windows is simpler than ever before. Microsoft releases a new Windows 10 version twice a year that includes new features. Compare this schedule to the traditional upgrade cycle where new features were only made available every few years.

Ultimately, the WaaS model replaced the need for traditional Windows deployment projects, which could be disruptive and costly. The WaaS model spreads out the required effort into a continuous updating process. This design reduces the overall effort required to maintain Windows 10 devices in your environment.

The WaaS servicing model includes the following capabilities:

 -  **Feature updates.** These updates are released twice per year, around March and September. They're installed as an in-place upgrade to newer Windows 10 versions. As the name suggests, they add new features to Windows 10. The Feature update version is named after the year and month (yymm) when it's released. For example, version 1803 was released in March (month 03) in the year 2018 (thus, version number 1803). You can view your Windows 10 version by running the **Winver.exe** command. Microsoft supports each feature update for 18 months after the release.
 -  **Quality updates.** These updates deliver both security and non-security fixes. They're typically released on the second Tuesday of each month (known in the Microsoft world as "Patch Tuesday"), though they can be released at any time. Quality updates are cumulative. Installing the latest quality update is sufficient to get all the available fixes for a specific Windows 10 version. Quality updates include:
    
     -  Security updates
     -  Critical updates
     -  Servicing stack updates
     -  Driver updates

 -  **Insider Preview.** These builds are made available during the development of the features that will be shipped in the next feature update. This design enables organizations to validate new features and compatibility with existing apps and infrastructure, and provide feedback to Microsoft. Microsoft also collects feedback on new features by using telemetry.
 -  **Servicing channels.** These channels allow organizations to choose when to deploy new Windows 10 features.<br>
    
     -  The **Semi-Annual Channel (Targeted)** and **Semi-Annual Channel** receive feature updates twice per year. If you want, you can use the Windows 10 Settings options, Group Policy, Windows Server Update Services, or Configuration Manager to delay the deployment. In this channel, each feature update is supported for 18 months after release date.<br>
     -  The **Long-Term Servicing Channel** is designed only for specialized devices. It receives new feature releases every two to three years. In this channel, each feature release is supported for 5+5 years (5 years of mainstream and 5 years of extended support).
 -  **Deployment rings.** Rings are groups of devices used to initially pilot, and then to broadly deploy, each feature update in a company. You can configure deployment rings by using Windows Update for Business, Intune, or Configuration Manager.

Organizations can familiarize and test new Windows 10 features by participating in the Windows Insider program. After a feature update is released to the Semi-Annual Channel (Targeted) channel, an organization can use the feature update for pilot deployments to ensure compatibility with existing apps and infrastructure.

After a period of time, typically about four months after the release, Microsoft publishes the feature update to the Semi-Annual Channel. This schedule makes it suitable for broad deployment throughout the company. You can decide to skip deployment of some feature updates. Each feature update is supported and serviced with quality updates for 18 months from the date of the release. For example, Windows 10 version 1709, which was released in September 2017, was supported for 18 months, until March 2019.

:::image type="content" source="../media/windows-update-timeline-a4fcda7d.jpg" alt-text="graphic showing timelines of the four most recent Windows 10 updates, ending with Windows 10 1903":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”