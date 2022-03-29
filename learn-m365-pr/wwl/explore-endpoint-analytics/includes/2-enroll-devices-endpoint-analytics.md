Endpoint Analytics provides insights for measuring the quality of the experience you're delivering to your users. Endpoint analytics can help identify policies or hardware issues that may be slowing down devices and help you proactively make improvements before end-users generate a help desk ticket. Endpoint analytics aims to improve user productivity and reduce IT support costs by providing insights into the user experience through proactive support and to detect regressions to the user experience by assessing user affect of configuration changes.

It's not uncommon for end users to experience long boot times or other disruptions. These disruptions can be due to a combination of:

 -  Legacy hardware
 -  Software configurations that aren't optimized for the end-user experience
 -  Issues caused by configuration changes and updates

These issues and other end-user experience problems persist because IT doesn't have much visibility into the end-user experience. Generally, the only visibility into these issues comes from a slow costly support channel that doesn't usually provide clear information about what needs to be optimized. It's not only IT support bearing the cost of these problems. The time information workers spend dealing with issues is also costly. Performance, reliability, and support issues that reduce user productivity can have a large affect on an organization's bottom line as well.

### Score

Endpoint analytics scores range from 0 to 100. Lower scores indicate there's room for improvement. Scores help you understand the relative affect of each metric in your environment. There's a built-in baseline for All organizations (median), which allows you to compare your scores to a typical enterprise. For instance, when reviewing your startup score, you find that overall your score of 61 is higher than the baseline of 50 for all organizations. You can create new baselines based on your current metrics so you can track progress or view regressions over time.

:::image type="content" source="../media/8816759-baseline-0113a08c.png" alt-text="Screenshot clip of Endpoint analytics score.":::


Scores are aggregated across all devices. Endpoint analytics also shows some scores per device, so that you can also identify devices that could be affecting user experience. Reviewing scores per device may help you find and resolve end-user affecting issues before a call is made to the help desk.

:::image type="content" source="../media/8816759-per-device-scores-chart-014d10e0.png" alt-text="Screenshot of Endpoint analytics Overview showing Device scores page.":::


### Filter

Use the Add filter option on tables to display items that match your criteria. You can add more filters to drill further into your data. Using filters enables you to discover trends in your environment or spot potential issues. For instance, in the Device performance tab of the Startup performance report, you might use a filter to identify devices with a high Time to responsive desktop. After reviewing your filtered data, you add another filter to include devices with a high Group Policy sign-in time. With the additional filter, you can gauge the affect that Group Policy has on the user experience for devices that take a long time to get to a responsive desktop.

### Requirements

You can enroll devices via Configuration Manager or Microsoft Intune. Devices enrolled in Endpoint analytics need a valid Microsoft Endpoint Manager license.

#### To enroll devices via Intune requires:

 -  Intune enrolled or co-managed devices running the following:
    
     -  Windows 10 version 1903 or later
     -  July 2021 cumulative update or later
     -  Pro, Pro Education, Enterprise, or Education. Home and long-term servicing channel (LTSC) aren't supported.
 -  Windows devices must be Azure AD joined or hybrid Azure AD joined. Workplace joined or Azure AD registered devices aren't supported.
 -  Network connectivity from devices to the Microsoft public cloud.
 -  The Intune Service Administrator role is required to start gathering data.

#### To enroll devices via Configuration Manager requires:

 -  A minimum of Configuration Manager version 2002 with KB4560496 or later
 -  The Configuration Manager clients upgraded to version 2002 (including KB4560496) or later
 -  Microsoft Endpoint Manager tenant attach enabled.
 -  Enable Endpoint analytics for devices uploaded to Microsoft Endpoint Manager.

Organizations can take advantage of proactive remediation when enrolling devices through Intune or Configuration Manager. Proactive remediation scripting has the following requirements:

 -  Devices must be Azure AD joined or hybrid Azure AD joined and meet one of the following conditions:
    
     -  Is managed by Intune and runs an Enterprise, Professional, or Education edition of Windows 10 or later.
     -  A co-managed device running Windows 10, version 1903 or later.
 -  Devices must be licensed for either Windows Enterprise E3 or E5, Education A3 or A5, or Virtual Desktop Access (VDA) per user.

Proactive remediations are script packages that can detect and fix common support issues on a user's device before they even realize there's a problem. You can create your own script package, or deploy one of the built-in script packages. Each script package consists of a detection script, a remediation script, and metadata.

Through Intune, you can deploy these script packages and see reports on their effectiveness. The Microsoft Intune Management Extension service gets the scripts from Intune and runs them. To add proactive remediation scripts, select the Proactive remediations repot option in Endpoint Analytics. In this location you can add scripts, as well as monitor detection and remediation successes and failures.

### Endpoint Analytics compared to Desktop Analytics

Endpoint Analytics is a different solution than Desktop Analytics. They are similar in concept, and some metrics do overlap. However, the main differences between these two products include:

 -  Desktop Analytics focuses on assessing compatibility. Endpoint Analytics focuses more on the health of the device and user experience.
 -  Desktop Analytics requires Endpoint Configuration Manager, where Endpoint Analytics does not.
 -  Desktop Analytics only integrates with Configuration Manager. Endpoint Analytics supports clients that are enrolled in either Configuration Manager or Intune.
