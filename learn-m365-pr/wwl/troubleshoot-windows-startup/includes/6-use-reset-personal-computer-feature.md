There are several reasons why a user might want to reset their computer. For example, a user might choose to reset their Windows computer if it has significant configuration problems or errors, or does not run correctly. The user might plan to repurpose the computer and give it to a family member. You can use the Reset this PC feature to reset the computer. The Reset this PC tool reinstalls Windows, but based on your selections, it can preserve computer settings and files. Optionally, the Rest this PC tool can remove most everything and leave the computer only with the default Windows installation.

:::image type="content" source="../media/windows-11-reset-personal-computer-72ac8131.png" alt-text="Reset PC which provides options to Keep my files or Remove everything.":::


You can access the Reset this PC tool from the Settings app or from Windows RE. In either case, you can select the option in the Reset this PC tool to preserve your files or to remove everything from the computer. If you decide to remove everything, you can specify to remove only your files or to clean the drive fully. When you clean your drive fully, it takes considerably longer. However, it is more secure, since you cannot recover the deleted files easily. Regardless of your selection, the Reset this PC tool always preserves the size and names of disk partitions, and it always removes apps and drivers that are not part of the initial Windows installation.

You can run the Reset this PC tool from the Settings app only as a local user. You do not need to provide credentials if you run it from the Settings app and you select to preserve your files. The Reset this PC tool will notify you about the apps that it will remove and that you will need to reinstall manually. If you run Reset this PC from the Windows RE that is available on a local drive, you will need to select the local user and provide the user’s credentials. However, you will not be notified about the apps that it will remove. In either case, the Reset this PC tool will add a list of the removed apps to the local user’s desktop after it completes the operation.

Although Reset this PC operation reinstalls Windows, it preserves computer settings such as computer name, domain membership, and local users. The Reset this PC tool removes device drivers and apps that were not part of the default Windows installation, but preserves all user settings and files. You do not need a backup or Windows media to perform the Reset this PC function, which is different from the **System Image Recovery** option. Reset this PC restores using files located in the C:\\Windows\\WinSxS folder.

If you run the Reset this PC tool and select to remove everything, and if your computer has more than one drive, you will be prompted to specify if you want to remove all files from all drives or remove all files only from the drive where Windows is installed. You also will have to specify whether the Reset this PC operation should remove your files only, or clean the drive fully. If you select to clean your drive fully, the Reset this PC operation will overwrite all of the disk space several times before installing Windows. You should select this option if you do not want to recover your files, such as before you sell your Windows computer or give it to a family member for personal use. If you select to remove everything, the Reset this PC operation removes all apps, configuration, and data that the default Windows installation does not include.

The following table shows which configuration and settings are preserved when you select different Reset this PC options.

:::row:::
  :::column:::
    **Information Retained**
  :::column-end:::
  :::column:::
    **Keep my files with Preinstalled Apps On**
  :::column-end:::
  :::column:::
    **Keep my files with Preinstalled Apps On**
  :::column-end:::
  :::column:::
    **Remove everything with Clean drive Off**
  :::column-end:::
  :::column:::
    **Remove everything with Clean drive On**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Disk partitions
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User settings and files
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Computer settings, (such as name and membership)
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Apps, drivers and printers
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Only apps preinstalled by manufacturer
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Rewrite all disk space multiple times
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    
  :::column-end:::
  :::column:::
    \-
  :::column-end:::
  :::column:::
    Yes
  :::column-end:::
:::row-end:::


### Considerations for using the Reset this PC tool with the Keep my files option

Consider the following when you are deciding whether to use the Reset this PC tool with the Keep my files option:

 -  The **Keep my files** option is not as destructive as the **Just remove my files** and **Fully clean** the drive options. However, although the Reset this PC tool retains your files and settings, it removes all apps that the default Windows installation did not include. After selecting Keep my files, there is an option to review apps being removed before beginning the reset.
 -  You need a local user with administrative permissions if you start the Reset this PC tool with the **Keep my files** option from the Windows RE that is available from the local drive. If you start the Reset the PC tool with the **Keep my files** option from Windows media, anyone with physical access to the computer can utilize the Reset this PC tool’s functionality.
 -  You must reinstall any apps and reapply any updates that were made since the computer was first installed with Windows.

### Use the Reset this PC tool with the Just remove my files or Fully clean the drive options

You should consider the following when deciding whether to use the Reset this PC tool with the Just remove my files or Fully clean the drive options:

 -  The Reset this PC tool removes all of your Microsoft Store apps and desktop apps. If preinstalled apps is enabled, only the apps that were pre-installed by the manufacturer will be available on the computer.
 -  You do not need any special permissions to use Reset this PC with the **Just remove my files** or **Fully clean the drive** options.
 -  Your files, settings, and computer configuration settings are set to their initial, post-installation state. For example, a computer will have the name DESKTOP- name, and it will be in a workgroup.
 -  You must reinstall any apps and reapply any updates that were made since the computer was first installed with Windows.
 -  If the device is correctly configured and a location has been pre-defined, an option can be made available for users to choose between installing Windows from the cloud or from the local device.
