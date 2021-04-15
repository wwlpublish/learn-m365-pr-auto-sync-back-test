During setup, Azure AD Connect automatically creates Azure AD Connect Sync Security Groups. A Microsoft 365 Enterprise Administrator can use these groups to:

 *  delegate control in Azure AD Connect to other users
 *  assign a user temporary permission to run a manual synchronization
 *  troubleshoot directory synchronization issues using Azure AD Connect

The following table identifies the Azure AD Connect Sync Security Groups that are automatically created by Azure AD Connect.

:::row:::
  :::column:::
    <p><b>Group name</b></p>
  :::column-end:::
  :::column:::
    <p><b>Description</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>ADSyncAdmins</b></p>
  :::column-end:::
  :::column:::
    <p><b>Administrators Group:</b> Members of this group have Full Access to do anything in the Azure AD Connect Sync Service Manager.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>ADSyncOperators</b></p>
  :::column-end:::
  :::column:::
    <p><b>Operators Group:</b> Members of this group have access to the operations of the Azure AD Connect Sync Service Manager, including:</p>  Execution of Management Agents  View of Synchronization Statistics for each run  Ability to save the Run History (Operations Tab) to a file  <p>Members of this group must be a member of the ADSyncBrowse Group.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>ADSyncBrowse</b></p>
  :::column-end:::
  :::column:::
    <p><b>Browse Group:</b> Members of this group have permission to gather information about a user’s lineage when resetting passwords.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p><b>ADSyncPasswordSet</b></p>
  :::column-end:::
  :::column:::
    <p><b>Password Reset Group:</b> Members of this group have permission to do all operations by using the password management interface.<br></p>  <p>Members of this group must be a member of the ADSyncBrowse Group.</p>
  :::column-end:::
:::row-end:::


The groups are either created as local groups on domain-joined servers, or as Active Directory domain groups when Azure AD Connect is installed on a domain controller. To create domain groups on member servers, you must select the **Specify Custom Sync Groups** option during setup and specify the groups by Domain\\Group Name.
