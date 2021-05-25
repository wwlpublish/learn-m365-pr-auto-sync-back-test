The most common reason why data governance retention policies fail is because of incorrect configuration of the retention tags or retention policies assigned to users. As such, it's important that organizations systematically verify the configuration of the retention settings to confirm they're correctly set up.<br>

Organizations should complete the following steps to troubleshoot retention policies that don’t run:

1.  Assess data governance requirements for different sets of users. As a best practice, the expected results should be documented for each set of users.
2.  Determine which Outlook client versions are in use. Older versions of Outlook, such as Outlook 2007, don't allow users to set retention tags.
3.  Test retention policies by applying a retention policy to a single mailbox to determine whether the retention policy is working as desired.
4.  Create and test new retention tags.
5.  Create and test new retention policies.
6.  Confirm that retention tags have been added to retention policies.
7.  During testing, confirm whether mailboxes have been placed on hold. Retention policies shouldn't take effect on mailboxes that are enabled for Litigation or In-Place Hold.

### Mailboxes less than 10 MB in size

For mailboxes in Exchange Online that are larger than 10 megabytes (MB), the retention policy runs automatically once every seven days. However, the retention policy doesn't automatically run for mailboxes that are smaller than 10 MB.

For mailboxes that are smaller than 10 MB, you must manually run the following PowerShell command in the Exchange Management Shell every time that you want to move messages to the archive.

```powershell
<code>Start-ManagedFolderAssistant –Identity &lt;mailbox&gt;</code>
```

**Additional reading.** For information related to Outlook client license requirements, see [Outlook license requirements for Exchange features](https://support.microsoft.com/office/outlook-license-requirements-for-exchange-features-46b6b7c5-c3ca-43e5-8424-1e2807917c99?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”