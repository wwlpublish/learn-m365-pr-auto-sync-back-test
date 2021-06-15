If the Windows 10 upgrade process isn't successful, Windows Setup returns two codes:

 -  **Result code.** This code corresponds to a specific Win32 or NTSTATUS error.
 -  **Extend code.** This code contains information about both the phase and the operation in which the error occurred.

For example, a result code of 0xC1900101 with an extend code of 0x4000D will be logged as: 0xC1900101 - 0x4000D. If the upgrade process completes without an error, the result code and extend code will have a value of 0x0.

Both codes are written in the setup log and the event log.

### Result codes

Some of the more common result codes associated with Windows Setup compatibility warnings are shown in the following table.

:::row:::
  :::column:::
    

**Result code**


  :::column-end:::
  :::column:::
    

**Message**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC1900210


  :::column-end:::
  :::column:::
    

MOSETUP\_E\_COMPAT\_SCANONLY


  :::column-end:::
  :::column:::
    

Setup didn't find any compatibility issues.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC1900208


  :::column-end:::
  :::column:::
    

MOSETUP\_E\_COMPAT\_INSTALLREQ\_BLOCK


  :::column-end:::
  :::column:::
    

Setup found an actionable compatibility issue, such as an incompatible app.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC1900204


  :::column-end:::
  :::column:::
    

MOSETUP\_E\_COMPAT\_MIGCHOICE\_BLOCK


  :::column-end:::
  :::column:::
    

The migration choice selected isn't available (for example, Enterprise to Home).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC1900200


  :::column-end:::
  :::column:::
    

MOSETUP\_E\_COMPAT\_SYSREQ\_BLOCK


  :::column-end:::
  :::column:::
    

The computer isn't eligible for Windows 10.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

0xC190020E


  :::column-end:::
  :::column:::
    

MOSETUP\_E\_INSTALLDISKSPACE\_BLOCK


  :::column-end:::
  :::column:::
    

The computer doesn't have enough free space to install.


  :::column-end:::
:::row-end:::


> [!NOTE]
> A result code of **0xC1900101** is generic and indicates that a rollback occurred. In most cases, the error is caused by a driver compatibility issue. To troubleshoot a failed upgrade that returned a result code of 0xC1900101, analyze the extend code to determine the Windows Setup phase in which the error occurred.

### Extend code

An extend code can be matched to the phase and operation in which the error occurred. To match an extend code to the phase and operation, complete the following steps:

1.  Use the first digit of the extend code to identify the phase. For example, if the extend code is 0x4000D, the code was added in setup phase 4 (second boot phase). If the extend code is 0x2000C, the code was added in setup phase is 2 (SafeOS phase).
2.  Use the last two digits of the extend code to identify the operation where the error occurred. For example, if the extend code is 0x4000D, the operation code that triggered the error is 0D.
3.  Match the phase and operation to values in the appropriate table that's available in technical documentation or on the Microsoft portal. For example, an extend code of 0x4000D represents a problem that occurred during phase 4 (0x4) with data migration (0D).

**Additional reading.** For more information, see [Find tables to match the phase and operation to values in the extend code](/windows/deployment/upgrade/upgrade-error-codes).
