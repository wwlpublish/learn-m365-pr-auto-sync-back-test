Microsoft Exchange Server is dependent on Active Directory. Exchange stores relevant settings, such as proxy addresses and SendAs permission, in Active Directory rather than Exchange. This interconnection requires several considerations in enterprise environments because the job roles of a messaging administrator and an Active Directory administrator differ substantially. A messaging administrator must plan and configure permissions carefully so as not to put their environment or their entire Active Directory at risk.

To support the varying needs to separate the management of Exchange and Active Directory, Exchange 2013 and later lets you choose whether you want a shared permissions model or a split permissions model. Exchange offers two types of split permissions models, RBAC and Active Directory, but it defaults to a shared permissions model.

This module examines these models and identifies the major differences between them.

### Prerequisites

This module is designed for persons who are aspiring to the Microsoft 365 Messaging Administrator role. The prerequisites for this module include:

 -  Ability to navigate the Microsoft 365 admin center, the Exchange admin center, and the Microsoft 365 Defender portal.
 -  Ability to create Domain Name System (DNS) records at an intermediate level.
 -  Familiarity with Active Directory concepts such as centralized domain management, sites, and directory-based identity-related services.
 -  Ability to write PowerShell commands at an intermediate level.

### Learning objectives

After this completing module, you'll be able to:

 -  Identify the differences between shared permissions and split permissions.
 -  Describe multi-forest permissions.
 -  Identify the differences between the permission models.
