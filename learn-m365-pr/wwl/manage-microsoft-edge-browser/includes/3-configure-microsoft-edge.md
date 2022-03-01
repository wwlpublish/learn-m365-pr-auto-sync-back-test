Administrators will typically want to configure some of the settings in Microsoft Edge on devices used by the organization. You can use group policy objects (GPOs) to configure policy settings for Microsoft Edge and managed Microsoft Edge updates on all supported versions of Windows.

### Install the Microsoft Edge administrative templates

To configure Microsoft Edge with group policy objects, you must first install the *administrative templates (ADMX files)* that add rules and settings for Microsoft Edge to the group policy Central Store in your Active Directory domain or the Policy Definition template folder on individual computers. If using an MDM such as Microsoft Intune, you can ingest the ADMX files, and create configuration policies.

There are two administrative templates for Microsoft Edge. Both can be applied with common group policy management tools such as Local Group Policy Editor for application on an individual computer or the Group Policy Management Console for Microsoft Windows domain networks. These templates are:<br>

*msedge.admx* contains the objects used to configure Microsoft Edge settings. Examples of these settings include:

 -  Default home page URL
 -  Setting connections to default to HTTPS.
 -  Allowed Extensions

*msedgeupdate.admx* contains the objects used to manage Microsoft Edge updates. Examples of these settings include:

 -  How often automatic update checks are performed.
 -  Changing the update channel
 -  Address or URL of a proxy server

### Setting mandatory and recommended policies

Microsoft Edge supports both *mandatory* and *recommended* policies. Mandatory policies override user preferences and prevent the user from changing it, while recommended policies provide a default setting that may be overridden by the user. For example, you may set a mandatory policy that requires users are prompted for a device password when a saved password is used in an autofill form. You may use a recommended policy to set a default Home page, that the user is free to change.

You can set mandatory or recommended policies to configure Microsoft Edge with the Group Policy Editor for both Active Directory and individual computers. You can scope policy settings to either the Computer Configuration or User Configuration by selecting the appropriate node as described below.

 -  To configure a mandatory policy, open the Group Policy Editor and go to (Computer Configuration or User Configuration) &gt; Policies &gt; Administrative Templates &gt; Microsoft Edge.
 -  To configure a recommended policy, open the Group Policy Editor and go to (Computer Configuration or User Configuration) &gt; Policies &gt; Administrative Templates &gt; Microsoft Edge – Default Settings (users can override).

### Verifying applied policies<br>

On a target client device, open Microsoft Edge and navigate to *edge://policy* to see all policies that are applied. If you applied policy settings on the local computer, policies should appear immediately. If you used Active Directory group policy settings, settings are propagated to domain computers at a regular interval defined by your domain administrator. To force policies to be applied immediately, open a command prompt or PowerShell session and run the `gpupdate /force` command. You may need to close and reopen Microsoft Edge if it was open while you were configuring policy settings.
