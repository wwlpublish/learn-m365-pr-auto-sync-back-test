Windows enables System Restore features automatically. System Restore takes snapshots of your computer system, and then saves them as restore points. These restore points represent a point in time for the computer’s configuration when it was running successfully. Using System Restore doesn't affect user data.

After you enable System Restore points, Windows creates them automatically when the following actions occur:

 -  You install a new application or driver.
 -  You uninstall certain programs.
 -  You install updates.

Windows also creates System Restore points:

 -  Manually, whenever you choose to create them.
 -  Automatically, once daily.
 -  Automatically, if you choose to use System Restore to restore to a previous point in time.

In this last instance, System Restore creates a new restore point before it restores the system to a previous state. This provides you with a recovery option, should the restore operation fail or result in issues. However, Windows RE does not create a restore point for the current state if you are in safe mode and you restore to a previous state.

### Perform driver rollbacks

You might use System Restore when you install a device driver that results in a computer that is unstable, or that fails to operate entirely. Earlier Windows operating systems had a mechanism for driver rollback, but it required the computer to start successfully from safe mode. With Windows computers, you can use System Restore to roll back drivers by accessing the System Restore points, even when the computer doesn't start successfully.

### Protect against accidental deletion of programs

System Restore also provides protection against accidental deletion of programs. When you add or remove programs, System Restore creates restore points, and keeps copies of application programs (file names with an .exe or .dll extension). If you accidentally delete an executable (.exe) file, you can use System Restore to recover the file by selecting a recent restore point prior to when you deleted the program.

> [!NOTE]
> If you use System Restore to restore your computer to a previous point in time, be aware that it might affect connectivity to the computer’s domain. Specifically, if the computer’s password has changed since the restore point was created, your computer will be unable to sign in to the domain. In this instance, you must reset the computer’s secure channel with the domain. You can do this by using the Windows PowerShell **Reset-MachineAccountPassword** cmdlet.

You also can use the Netdom command prompt tool and Active Directory Users and Computers.
