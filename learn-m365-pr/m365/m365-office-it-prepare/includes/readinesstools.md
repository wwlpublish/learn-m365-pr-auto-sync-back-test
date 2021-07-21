>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE3YvJ1]

Current versions of Microsoft Office are designed to be natively compatible with existing files and Office COM add-ins. In this unit, we'll show you the tools to discover Office COM add-ins and VBA Macros in files and assess their compatibility. More than 99% of your existing add-ins and macros will continue to work if you're coming from Office 2010 or newer and installing a matching architecture of Office.

## Assess compatibility with readiness tools

You can use the Readiness Toolkit for Office on its own or with Configuration Manager to gain insights on Office COM add-in and VBA macro compatibility. Configuration Manager also has new capabilities to inventory Office COM add-ins  with hardware inventory. Configuration Manager can also assess Office COM add-ins against known compatibility information.  Using this process, Configuration Manager downloads a copy of known compatibility information from Microsoft and performs local queries against your inventoried Office COM add-ins. With this approach, you don't have to send Office client or add-in information to the Microsoft cloud to assess compatibility.

You can access this information in the Office Dashboard in Configuration Manager and drill into lists of the add-ins it found. Use this information to prioritize testing the most commonly used and installed Office COM add-ins – especially where there isn't known compatibility information, such as with in-house developed COM add-ins.

Configuration Manager's expanded inventory capability doesn't discover files with VBA macros, but it can discover which computers have recently run macros. In most environments, this is a small number of specialized devices and roles. You can use this inventory to create device collections scoped to those devices. Then you can use the Readiness Toolkit for Office to discover and assess the compatibility of macros on those devices.

Another tool to help with compatibility is the Desktop App Assure program available through the FastTrack Center. With Desktop App Assure, if a  valid compatibility issue blocks your upgrade, you can work with a Microsoft engineer at no additional cost to resolve or remediate the issue.

In smaller environments, you can also use the Readiness Toolkit for Office on its own to check a handful of PCs or to validate its findings on a small number of devices before deploying it to a large collection of devices.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [FastTrack Center](/fasttrack/win-10-daa-assistance-offered)
