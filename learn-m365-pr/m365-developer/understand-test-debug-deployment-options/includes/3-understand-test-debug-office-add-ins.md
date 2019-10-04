At various points during your add-in's life cycle, you need to verify functionality and fix bugs. You have several options for how you go about testing and debugging your add-in.

## Sideload your add-in

You can locally install (sideload) your add-in for testing and debugging on Windows, Mac, and in a web browser. You can also sideload your Excel or Word add-in on an iPad. Use Node.js, ASP.NET, or another preferred means to web host your add-in on your development machine.

## Debug your add-in

You can debug your add-in using the following methods:

- A web browser with the browser's built-in developer tools
- Visual Studio, provided you prepared your add-in using this IDE
- Visual Studio Code for custom functions projects only
- Runtime logging on Windows and Mac

If you need to debug your add-in on a specific platform, there are additional tools that may help you. A few options for Windows and Mac are mentioned next in this section.

### Windows

On Windows 10, the tool you use depends on if the add-in is running in Microsoft Edge or Internet Explorer. For Microsoft Edge, install and use Microsoft Edge DevTools. For Internet Explorer, run F12 developer tools according to your Office version:

- 32-bit Office version: C:\Windows\System32\F12\IEChooser.exe
- 64-bit Office version: C:\Windows\SysWOW64\F12\IEChooser.exe

An available option to debug task pane add-ins in Office 2016 or later is to attach a debugger. Where the **Attach Debugger** is available through the Personality menu, as shown in the following image, the supported tool is Visual Studio 2015 Update 3 or later. This tool only enables JavaScript debugging.

![Personality menu displaying **Attach Debugger** item in Excel on Windows](../media/attach-debugger.png)

*Personality menu displaying **Attach Debugger** item*

If the Personality menu isn't present or you're already using Visual Studio (VS), you can use **Attach to Process** in VS to debug the add-in in Microsoft Edge or Internet Explorer as applicable.

### Mac

For your sideloaded task pane and content add-ins, you can use the Safari Web Inspector on Mac OS High Sierra and Office version 16.9.1 (build 18012504) or later. The supported Office applications are:

- Excel
- Outlook
- PowerPoint
- Word

## Validate your manifest

You can validate your add-in's manifest using any of these options:

- Yeoman generator for Office Add-ins
- office-addin-manifest `validate` command
- libxml

## Test required Office clients and platforms

Test your add-in in Office versions and on platforms where you or your intended users will be using it.

### Private use or limited to your organization

If your add-in will be limited to you or your organization, test it in Office versions and on platforms where they'll use it. For example, if you're developing a Word add-in for your organization where your coworkers usually work in Microsoft Edge and Word 2019 on Windows, test your add-in in that browser and version of Word.

### Public use

If your add-in will be available to the public through AppSource, you should look over the AppSource validation policies so review and validation of your add-in is as smooth as possible. A few key validation requirements are:

- Browsers: Internet Explorer 11 and later, Microsoft Edge, Chrome, Firefox, and Safari (Mac)
- Office: All applications you specified in the `Hosts` section of the add-in's manifest configuration file
- Operating systems: Windows, Mac, and iPad&mdash;if your Outlook add-in supports mobile, include iOS and Android

AppSource validation policy 4.12 discusses the expected client and platform support requirements in more detail.
