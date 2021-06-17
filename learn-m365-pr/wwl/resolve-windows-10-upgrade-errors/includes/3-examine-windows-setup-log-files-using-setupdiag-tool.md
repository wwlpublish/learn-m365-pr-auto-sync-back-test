Windows 10 setup creates several log files when you install or upgrade the operating system. In most cases, an upgrade is completed without any issues, and you usually don’t have a need to open log files. But if a problem occurs, log files can provide an important insight on what caused the error and how to mitigate it.

Manually searching through the log files and looking for error codes and troubleshooting steps can be a tedious and time-consuming task. To simplify this process, Microsoft created the SetupDiag diagnostic tool. SetupDiag, which isn't part of Windows 10, can be downloaded from the Microsoft Download Center. Its purpose is to obtain details about why a Windows 10 upgrade failed.

SetupDiag works by examining Windows Setup log files. It reviews the log files and tries to determine the root cause of an upgrade failure. SetupDiag can be run in either online or offline mode:

 -  **Online mode.** Run SetupDiag on the device on which the update failed.
 -  **Offline mode.** Export logs from the failed device and run SetupDiag in offline mode.

For offline processing, SetupDiag should be run with a parameter that points to the folder in which the setup log files are located. SetupDiag automatically searches for log files in the folder and in all of its subdirectories.

When running in offline mode, SetupDiag can also debug setup-related minidumps. A minidump is created by Windows setup when:

 -  crash dumps are enabled on the device.
 -  the setup process comes across a condition that compromises a safe system operation.

:::image type="content" source="../media/setupdiag-command-prompt-cc011504.jpg" alt-text="screenshot of command prompt window showing results of running SetupDiag":::


### Using SetupDiag

Before running SetupDiag, ensure the following prerequisites are in place:<br>

 -  The destination OS must be Windows 10.
 -  .NET Framework 4.6 must be installed. 

To quickly use SetupDiag on your current computer:

1.  Verify that your system meets the requirements described above.
2.  [Download SetupDiag](/windows/deployment/upgrade/setupdiag).
3.  If your web browser asks what to do with the file, choose **Save**. By default, the file will be saved to your **Downloads** folder. You can also save it to a different location if desired by using **Save As**.
4.  When SetupDiag has finished downloading, open the folder where you downloaded the file.
5.  Double-click the **SetupDiag** file to run it. Select **Yes** if you are asked to approve running the program.
    
     -  Double-clicking the file to run it will automatically close the command window when SetupDiag has completed its analysis. However, if you wish to keep this window open and review the messages that you see, run the program by typing **SetupDiag** at the command prompt instead of double-clicking it. You'll need to change directories to the location of SetupDiag to run it this way.
6.  A command window will open while SetupDiag diagnoses your computer. Wait for this process to finish.
7.  When SetupDiag finishes, two files will be created in the same folder where you double-clicked SetupDiag. One is a configuration file, the other is a log file.
8.  Use **Notepad** to open the log file: **SetupDiagResults.log**.
9.  Review the information that is displayed. If a rule was matched, this information can tell you why the computer failed to upgrade, and potentially how to fix the problem.

### Searching setup log files

When searching through setup log files in both online and offline mode, SetupDiag uses a set of rules to match known issues. SetupDiag currently uses over 60 rules, which are contained in the rules.xml file that's extracted when you run the tool.

If a match is found between one of the rules and an error in a log file, SetupDiag:

 -  displays the rule name and a description of the known upgrade-blocking issue.
 -  creates a SetupDiagResults.log file, which includes upgrade issues that it detected.
 -  creates a Logs.zip archive of all log files that were processed.

> [!TIP]
> When SetupDiag indicates there were multiple failures, the last failure in the log file is typically the fatal error, not the first one.

**Additional reading.** For more information, see [SetupDiag](/windows/deployment/upgrade/setupdiag).

### Setup bug check analysis, crash dumps, and minidumps

When Microsoft Windows meets a condition that compromises safe system operation, the system halts. This condition is called a bug check. It's also commonly referred to as a system crash, a kernel error, a Stop error, or Blue screen of death (BSOD). Typically a hardware device, hardware driver, or related software causes this error.

If [crash dumps are enabled](/windows-hardware/drivers/debugger/enabling-a-kernel-mode-dump-file) on the system, a crash dump file is created. If the bug check occurs during an upgrade, Windows Setup will extract a minidump (setupmem.dmp) file. SetupDiag can also debug these setup-related minidumps.

To debug a setup-related bug check, you must:

 -  Specify the /LogsPath parameter. You can't debug memory dumps in online mode.
 -  Gather the setup memory dump file (setupmem.dmp) from the failing system.
    
     -  Setupmem.dmp will be created in either %SystemDrive%$Windows.~bt\\Sources\\Rollback, or in %WinDir%\\Panther\\NewOS\\Rollback depending on when the bug check occurs.
 -  Install the [Windows Debugging Tools](/windows-hardware/drivers/debugger/debugger-download-tools) on the computer that runs SetupDiag.

In the following example, the setupmem.dmp file is copied to the D:\\Dump directory and the Windows Debugging Tools are installed before running SetupDiag:

`SetupDiag.exe /Output:C:\SetupDiag\Dumpdebug.log /LogsPath:D:\Dump`

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”