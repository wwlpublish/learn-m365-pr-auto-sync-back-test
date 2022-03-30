If your Windows computer fails to start correctly, you can use a number of tools to help resolve the problem. The following unit discusses these tools.

#### Windows RE

Windows RE is a recovery platform based on the Windows Preinstallation Environment (Windows PE). Windows RE provides two main functions:

 -  Diagnose and repair startup problems automatically.
 -  Provide a centralized platform for additional advanced recovery tools.

#### How to access Windows RE

If Windows starts normally, you can access Windows RE by:

 -  Selecting **Start**, **Power**, then holding **SHIFT** while selecting **Restart**.
 -  In the Settings App under **Update &amp; Security**, select **Recovery** and select **Restart now** under Advanced Startup.
 -  From a command prompt, run **shutdown /r /o**

If you cannot successfully boot Windows, you can access Windows RE by:

 -  Insert the Windows media, and then start the computer. When prompted, run the Windows media Setup program. After you configure language and keyboard settings, select the **Repair your computer** option, which scans the computer for Windows installations, and then presents you with a Choose an option menu, Select **Troubleshoot**.
 -  Some systems will support pressing a function key during boot (such as F11). The previous method of using F8/SHIFT-F8 is no longer reliable.

#### Automatic failover

Windows provides an on-disk version of Windows RE. A computer that runs Windows can fail over automatically to the on-disk Windows RE if it detects a startup failure.

During startup, Windows OS Loader sets a status flag that indicates when the startup process begins. Winload.exe clears this flag before it displays the Windows sign-in screen. If startup fails, the loader does not clear the flag. Consequently, the next time the computer starts, Windows OS Loader detects the flag, assumes that a startup failure has occurred, and then launches Windows RE instead of Windows.

The advantage of automatic failover to Windows RE Startup Repair is that you might not need to check the problematic computer when a startup problem occurs.

> [!NOTE]
> Note that the computer must start successfully for Windows OS Loader to remove the status flag. If there is an interruption to the computer’s power during the startup sequence, Windows OS Loader does not remove the flag, and instead initiates Startup Repair automatically.

Remember that this automatic failover requires the presence of both Windows Boot Manager and Windows OS Loader. If either of these elements is missing or corrupt, automatic failover cannot function, and you must initiate a manual diagnosis and repair of the computer’s startup environment.
