Click-to-Run uses an optimized software-update model that provides unobtrusive background updates. This model results in simpler and smaller updates. Every month, on Patch Tuesday (also known as Update Tuesday, the second Tuesday of the month), Microsoft releases an updated Office build that includes a full set of source files.

Unlike traditional msi-based installations, these releases don't include separate security fixes, private hotfixes, cumulative updates, and service packs. You use the updated full set of source files for new installations. During the update process for existing installations, the client runs a delta comparison between the current and updated builds, and it only downloads the deltas or differences.

Additionally, this model doesn't affect users, even if they're using an Office application when an update is running. When they close and reopen the Office application, they'll automatically be using the newer build.

### Update options

Updating options include:

 -  **Automatic from cloud.** This option is the default mode (typically used for home or small office installations) where updates download from the cloud. A daily task checks for updates, and when a new build is available, the client automatically receives the deltas.
 -  **Automatic from network.** In managed deployments, administrators can specify (by using Group Policy or the configuration.xml file during setup) to check for updated builds from an internal source. Typically, small or medium organizations use this option.
 -  **Rerun setup.exe by using Electronic Software Delivery (ESD).** In large organizations, using an ESD such as Configuration Manager enables even more fine-grained control of update scheduling. You can use scripts or task sequences in the ESD to re-execute setup.exe /configure. In doing so, the current version will be compared with the source (defined in the SourcePath attribute in the config.xml) and only install the deltas. By using an ESD, administrators can specify how many users receive a new build in a given time period.

The second and third options enable administrators to control when users receive updated builds. For these two options, a best practice is to download the updated build to a test share initially, and to apply updates to test or pilot computers only. After the testing period, you move the updated build to a production update share, and it begins to update production computers automatically.

> [!NOTE]
> Although administrators can choose not to receive updates, it's important to note that clients can be on an outdated build for only 12 months. After 12 months, clients will need to download a newer build that Microsoft support will cover.

The following graphic shows that Microsoft 365 Apps for enterprise clients can be updated through GPO, or from a file share, or directly from Microsoft 365.

:::image type="content" source="../media/m365-clients-being-updated-cf951386.jpg" alt-text="graphic shows how Microsoft 365 Apps for enterprise clients can be updated through GPO, or from a file share, or directly from Microsoft 365":::


### Using the Office Deployment Tool's configuration.xml file to manage updates

Administrators can configure update behavior by using the Office Deployment Tool's configuration.xml file options. For example, updates can be turned on and directed to the shared folder using the following configuration script:

```powershell
&lt;Updates Enabled="TRUE" UpdatePath="\\Server\Share\Office\" /&gt;
```

where:

 -  **Enabled.** If set to TRUE (default), Click-to-Run will automatically detect, download, and install updates.
 -  **UpdatePath.** Specifies a network, local, or HTTP path for a Click-to-Run installation source to use for updates. If not set, or set to default, the Click-to-Run source on the Internet is used.
 -  **TargetVersion.** Sets a specific product build number (for example, 16.0.6366.2036) that the next update cycle will update. If not set or set to default, Click-to-Run will update to the latest version advertised at the Click-to-Run source.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”