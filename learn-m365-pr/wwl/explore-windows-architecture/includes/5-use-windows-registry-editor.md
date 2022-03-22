Typically, you will not need to edit the registry directly. However, a software problem could arise, and the software vendor could provide a solution that involves changing the registry. After you determine that you must make a direct change to the registry, you must choose the most appropriate tool. The number of computers on which you must make the change will influence your choice. For example, if you must make the required change on a single computer only, then using the Registry Editor is your best choice. However, if you must make the change across hundreds of computers, you may decide to use Windows PowerShell or Group Policy. The following sections describe ways in which you can make registry edits.

> [!TIP]
> As a best practice, back up the registry before making any edits to it. You can export the specific key that you are editing, or you can use a tool, such as System Restore, to capture a restore point. Incorrectly editing the registry could severely damage your system.

### The Registry Editor tool

The Registry Editor tool is probably the easiest and most direct way to make changes to the registry, and you can use it to:

 -  Search the registry for a given value entry, value name, subkey, or key.
 -  Create, delete, and edit keys, subkeys, and values.
 -  Import entries into the registry from an external file.
 -  Export entries from the registry into an external file.
 -  Back up the registry (by exporting the entire registry).
 -  Connect to a remote computer and manage its registry.

> [!NOTE]
> To manage a remote registry, from the Registry Editor, select **File**, and then select **Connect Network Registry**. In the **Select Computer** dialog box, type the name of the remote computer, and then select **OK**. You must have administrative credentials on the remote computer, and the remote computer’s firewall must be configured to allow remote management. You only can manage *HKEY\\\_LOCAL\\\_MACHINE* and *HKEY\\\_USERS* hives on the remote computer.

To access the Registry Editor, open an elevated command prompt, type regedit.exe, and then press Enter.

#### REG files

You also can use a structured text file with a .reg extension (a registry entries file) to merge values into the registry. The file will look like the following example:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\services\atapi]

"Start"=dword:00000001

```

> [!NOTE]
> This particular .reg file edits the Start value stored in the *HKEY\\\_LOCAL\\\_MACHINE\\\\SYSTEM\\\\ControlSet001\\\\services\\\\atapi* path, and assigns it the *DWORD* value of 1.

After you have created the .reg file, you can import the when you:

 -  Double-click the file and confirm that you want to continue.
 -  Run a script that loads the file. The following command imports the settings stored in setting1.reg without prompting the user to confirm:
    
    ```
    regedit /s C:\Registry\setting1.reg \> nul
    
    ```

 -  Open the Registry Editor, and use the import option to access the appropriate .reg file.

### Windows PowerShell

Windows PowerShell displays a registry provider that represents the registry like a file system, displaying keys and subkeys as subfolders of the registry hive, the same way as folders and subfolders of the drive C are displayed. For example, to see the contents of the *HKEY\_LOCAL\_MACHINE* hive, open an elevated Windows PowerShell command prompt, and then type the following command, and press Enter:

```
prompting the user to confirm: Get-ChildItem -Path hklm:\

```

As cd is the alias for the Get-ChildItem Windows PowerShell cmdlet, you also can type:

```
cd hklm:

```

To modify registry values, you must:

 -  Use the Set-Location cmdlet to change to the appropriate registry drive.
 -  Use the Set-ItemProperty cmdlet to assign a new value to the registry property.

For example:

```
Set-Location HKCU:\Software\Example

Set-ItemProperty . examplevaluename "assigned value"

```

In the preceding code sample, assigned value is assigned to a value called examplevaluename in the registry path, *HKEY\_CURRENT\_USER\\Software\\Example*.

### Group Policy Preferences

You can create, update, replace, and delete registry keys and values when you use Group Policy Preference in the domain GPO. This approach is very effective if you need to manage registry updates on many computers in an Active Directory environment.
