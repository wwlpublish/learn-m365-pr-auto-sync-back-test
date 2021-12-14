Running the Hybrid Configuration Wizard (HCW) configures a hybrid deployment for your Exchange environment.

In the past, after you ran the HCW, you had to manually configure all Exchange organizational settings, such as Active Sync Mailbox Policies in Exchange Online. If you didn't configure these settings, the user experience was different once their mailbox was moved to Exchange Online.

For this reason, Microsoft added a feature to the HCW called Organization Configuration Transfer (OCT). OCT enables an organization to complete a one-time transfer of its organizational settings from its Exchange Server on-premises environment to Exchange Online.

:::image type="content" source="../media/oct-56dbea1f.png" alt-text="screenshot from the HCW showing the Hybrid Features page with the OCT option selected":::


OCT enables organizations to transfer the following Exchange Server settings:

 -  Active Sync Mailbox Policy
 -  Mobile Device Mailbox Policy
 -  OWA Mailbox Policy
 -  Retention Policy
 -  Retention Policy Tag
 -  Active Sync Device Access Rule
 -  Active Sync Organization Settings
 -  Address List
 -  DLP Policy
 -  Malware Filter Policy
 -  Organization Config
 -  Policy Tip Config

OCT runs as part of HCW. It reads an organization's on-premises Exchange Server configuration and its settings in Exchange Online. An organization can then decide whether it wants to transfer each setting.

:::image type="content" source="../media/oct-settings-1550b416.png" alt-text="screenshot from the HCW showing the OCT Object Review page":::


If an object with the same name already exists in both on-premises Exchange Server and Exchange Online, you can choose to either overwrite the values of the objects in Exchange Online or keep them as is. And, just in case you overwrite the Exchange Online settings and didn’t mean to, there’s a rollback script to undo those changes.

For example, if you had an OWA mailbox policy on-premises that didn’t exist in Exchange Online, HCW compare the policy between both organizations. The comparison is accomplished using the name attribute of the policy. As such, if there's no OWA mailbox policy matching the name attribute, HCW will:

 -  Read all the configured properties on-premises.
 -  Save it in the memory.
 -  Create a new one (using the New-\* cmdlet) with the same properties, just like you had on-premises.

OCT supports Exchange Server 2010 and later and requires the latest cumulative update or update rollup that's available for the version of Exchange that's installed in the on-premises organization.

When using OCT, you must consider the following items:

 -  OCT is a one-time transfer of your organizational settings.
 -  OCT can't match all settings, so always make sure you review them.
 -  You can revert the OCT settings using the rollback script available in the logging folder of the HCW.
