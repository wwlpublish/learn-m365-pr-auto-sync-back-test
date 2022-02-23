You can use Windows PowerShell to run individual cmdlets that perform actions, or to run scripts that use cmdlets. Using Windows PowerShell is much simpler than other scripting languages such as VBScript.

Windows PowerShell uses Windows PowerShell drives to provide access to data stores. These drives present data in a format similar to a file system. Some common Windows PowerShell drives are:

 -  The C drive is the local file system's C drive.
 -  The cert drive is the local certificate store.
 -  The Env drive contains environmental variables that are stored in memory.
 -  The HKCU drive is the HKEY\_CURRENT\_USER portion of the registry.
 -  The HKLM drive is the HKEY\_LOCAL\_MACHINE portion of the registry.
 -  The Variable drive contains the variables that are stored in memory.

## Cmdlets

Cmdlets use a naming convention of a verb or action, followed by a noun or a subject. For example, to retrieve a list of services, you would use the **Get-Service** cmdlet. This standardization makes it easier to learn how to accomplish administrative tasks. Some common cmdlet verbs are:

 -  Get. Retrieves data.
 -  Set. Establishes or modifies data.
 -  New. Creates a new object.

Each cmdlet has options called parameters. Some parameters are required and some are optional. The parameters vary for each cmdlet. The following example shows how to start the Application Identity service by using the - Name parameter:

```
Start-Service -Name "Application Identity"


```

> [!NOTE]
> The cmdlets that are available for use on a computer system vary depending on its Windows PowerShell version and the snap-ins with cmdlets that are installed.

## Compatibility with command-line tools

You can run batch files and executable files at a Windows PowerShell command prompt. For example, you can run **ipconfig.exe** at a Windows PowerShell command prompt, and it behaves exactly as if you ran it from a command prompt. This allows you to start using Windows PowerShell as your default command-line environment for administration. Note that there are also equivalent cmdlets that return similar values as older executables. For example, the cmdlet alternative to **ipconfig.exe /all** is **Get-NetIPAddress**, which returns a somewhat similar data set.

In some cases, commands or options for commands contain reserved words or characters for Windows PowerShell. In such a case, you can enclose the command in single quotation marks to prevent Windows PowerShell from evaluating the reserved word or combination of words. You also can use the grave accent (\`) character to prevent the evaluation of a single character.

In rare cases, an executable file does not run correctly at a Windows PowerShell command prompt. You should test batch files to ensure that they work properly at a Windows PowerShell command prompt.

## Using Windows PowerShell for bulk operations

Windows PowerShell helps you manage multiple computers or perform bulk operations in the Windows environment. You can leverage Windows PowerShell features, such as variables, scripts, and system interoperability, to encapsulate tedious and time-consuming management tasks into scripts or cmdlets that only take seconds to run.

## Getting help with using Windows PowerShell

You can use a number of cmdlets to get help with using Windows PowerShell. One of the key cmdlets for help is the **Get-Help** cmdlet. **Get-Help** followed by the name of the cmdlet will give you a brief but detailed guide on that particular cmdlet, including the parameters that you can use.

For example, the **Get-Help Set-Item** returns the following result:

```
    NAME
     Set-Item  
    SYNOPSIS
     Changes the value of an item to the value specified in the command.   
    SYNTAX
     Set-Item [-Path] <String[]> [[-Value] <Object>] [-Credential <PSCredential>] [-Exclude <String[]>] [-Filter 
    <String>] [-Force] [-Include <String[]>] [-PassThru] [-Confirm] [-WhatIf] [-UseTransaction [<SwitchParameter>]] 
     [<CommonParameters>]
     Set-Item [[-Value] <Object>] [-Credential <PSCredential>] [-Exclude <String[]>] [-Filter <String>] [-Force] 
    [-Include <String[]>] [-PassThru] -LiteralPath <String[]> [-Confirm] [-WhatIf] 
    [-UseTransaction 
     [<SwitchParameter>]] [<CommonParameters>]
    DESCRIPTION
    The Set-Item cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.  
    RELATED LINKS
     Online Version: http://aka.ms/J6rrhw
     Clear-Item 
     Copy-Item 
     Get-Item 
     Invoke-Item 
     Move-Item 
     New-Item 
     Remove-Item 
     Rename-Item 
     about_Providers 
    REMARKS
     To see the examples, type: "get-help Set-Item -examples".
     For more information, type: "get-help Set-Item -detailed".
     For technical information, type: "get-help Set-Item -full".
     For online help, type: "get-help Set-Item -online"


```

Another useful cmdlet is **Get-Command**. This cmdlet shows a list of all cmdlets, aliases, functions, workflows, filters, scripts, and applications installed on your version of Windows PowerShell.

There are numerous websites that can help you learn Windows PowerShell. Microsoft TechNet has the Microsoft Script Center, where you can search for Windows PowerShell scripts based on what you want the script to do. Examples include deleting files older than X number of days, controlling Windows Update on your computer, and a wide variety of other functions.
