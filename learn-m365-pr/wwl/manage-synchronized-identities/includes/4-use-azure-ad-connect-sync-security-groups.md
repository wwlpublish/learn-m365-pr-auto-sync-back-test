During setup, Azure AD Connect automatically creates Azure AD Connect Sync Security Groups. A Microsoft 365 Enterprise Administrator can use these groups to:

 -  delegate control in Azure AD Connect to other users.
 -  assign a user temporary permission to run a manual synchronization.
 -  troubleshoot directory synchronization issues using Azure AD Connect.

The following table identifies the Azure AD Connect Sync Security Groups that are automatically created by Azure AD Connect.

:::row:::
  :::column:::
    

**Group name**


  :::column-end:::
  :::column:::
    

**Description**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**ADSyncAdmins**


  :::column-end:::
  :::column:::
    

**Administrators Group:** Members of this group have Full Access to do anything in the Azure AD Connect Sync Service Manager.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**ADSyncOperators**


  :::column-end:::
  :::column:::
    

**Operators Group:** Members of this group have access to the operations of the Azure AD Connect Sync Service Manager, including:

 -  Execution of Management Agents
 -  View of Synchronization Statistics for each run
 -  Ability to save the Run History (Operations Tab) to a file

Members of this group must be a member of the ADSyncBrowse Group.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**ADSyncBrowse**


  :::column-end:::
  :::column:::
    

**Browse Group:** Members of this group have permission to gather information about a user’s lineage when resetting passwords.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**ADSyncPasswordSet**


  :::column-end:::
  :::column:::
    

**Password Reset Group:** Members of this group have permission to do all operations by using the password management interface.


Members of this group must be a member of the ADSyncBrowse Group.


  :::column-end:::
:::row-end:::


The groups are either created as local groups on domain-joined servers, or as Active Directory domain groups when Azure AD Connect is installed on a domain controller. To create domain groups on member servers, select the **Specify Custom Sync Groups** option during setup and specify the groups by Domain\\Group Name.
