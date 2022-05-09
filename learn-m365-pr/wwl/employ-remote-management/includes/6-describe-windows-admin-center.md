Windows Admin Center is a new, locally deployed, browser-based management tool set that lets you manage Windows clients and servers remotely over https. It's the evolution of what Server Manager and MMC tools have typically been used for. It can be used to manage Windows Server 2012 R2 or later and Windows 10 or later clients. It's installed on a Windows client, and has no cloud service dependencies. Alternatively, you can install it on Window Server 2016 or later as a gateway to enable the entire organization to manage devices via Microsoft Edge or Google Chrome. Both installations are included in a single .msi package.

:::image type="content" source="../media/server-overview-5ef49a71-4254b762.png" alt-text="Screenshot of the WAC UI showing the available tools and an example of the overview dashboard.":::


Windows Admin Center is intended to compliment tools like System Center Virtual Machine Manager (SCVMM), Azure security and management, and RSAT tools. While it's primary function is managing servers, Windows Admin Center provides Desktop Administrators a subset of the Server Manager features for managing Windows client PCs. That subset includes:

 -  Displaying resources and resource utilization
 -  Certificate Management
 -  Managing Devices
 -  Event Viewer
 -  File Explorer
 -  Firewall Management
 -  Configuring Local Users and Groups
 -  Viewing/Ending Processes and Creating Process Dumps
 -  Registry Editing
 -  Managing Scheduled tasks
 -  Managing Windows Services
 -  Managing Storage
 -  Virtual Machines
 -  Virtual Switches

When Windows Admin Center is installed on a Server as a gateway, WAC defines two roles for access to the gateway service: gateway users and gateway administrators. Gateway users can access and use the service, but only gateway administrators can define who can access the gateway. These permissions only grant access to the WAC tool itself. The user must have the appropriate permissions necessary on the target client or server to manage it.

With WAC, a user with full local administrator privileges will have full permissions to manage the target client. However, WAC supports role-based access control, to allow users certain permissions that enable them to perform their job, without granting full administrative permissions. This is typically more useful for servers than clients.

The following provides a list of the available roles:

:::row:::
  :::column:::
    **Role name**
  :::column-end:::
  :::column:::
    **Intended use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Administrators
  :::column-end:::
  :::column:::
    Allows users to use most of the features in Windows Admin Center without granting them access to Remote Desktop or PowerShell. This role is good for "jump server" scenarios where you want to limit the management entry points on a machine.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Readers
  :::column-end:::
  :::column:::
    Allows users to view information and settings on the server, but not make changes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Hyper-V Administrators
  :::column-end:::
  :::column:::
    Allows users to make changes to Hyper-V virtual machines and switches, but limits other features to read-only access.
  :::column-end:::
:::row-end:::
