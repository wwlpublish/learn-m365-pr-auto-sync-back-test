While the Start menu in Windows 11 is different from Windows 10 with regard to its presentation and capabilities, the process for creating a Start menu layout is similar. You configure the Start layout on a standard build, and export the layout. In Windows 11, the layout is exported to a JSON file instead of an XML file.

You can only customize the full layout. Partial layouts aren't applicable in Windows 11.

While you can define a default layout, users can change the layout, including pinning and unpinning apps.

## Creating a custom Start menu JSON layout file

1.  Configure the Start Menu as desired.
2.  Open the Windows PowerShell app.
3.  Run the following cmdlet. Name the file LayoutModification.json. Export the Start menu to a JSON file using the Export-StartLayout command in Windows PowerShell. For the -Path switch, place a path and name the filename "LayoutModification.json".
4.  For example:
    
    `Export-StartLayout -Path "C:\Layouts\LayoutModification.json"`
5.  Once you've saved the file, you can optionally make manual edits to the JSON file.

The JSON file will look something like this:

```JSON
{
  "pinnedList": [
    { "desktopAppId": "MSEdge" },
    { "desktopAppId": "Microsoft.Office.WINWORD.EXE.15" },
    { "packagedAppId": "Microsoft.WindowsStore_8wekyb3d8bbwe!App" },
    { "packagedAppId": "Microsoft.WindowsNotepad_8wekyb3d8bbwe!App" }
  ]
}
```

Applying pinned custom layouts must be applied using an MDM policy. There's no Group Policy for creating a pinned list.

## Creating a custom set of pinned apps on the taskbar

Customizing the taskbar in Windows 11 is the same process as Windows 10, using an XML file. However, as configuring a Windows 11 Start Menu uses a JSON file, the XML file used for configuring pinned apps on the taskbar, wouldn't contain any Start Menu configurations.
