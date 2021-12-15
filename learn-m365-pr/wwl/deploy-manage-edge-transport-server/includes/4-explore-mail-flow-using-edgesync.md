It's recommended that organizations use the Edge Subscription process to establish mail flow between their Exchange organization and an Edge Transport server. Edge Subscriptions are used to populate the Active Directory Lightweight Directory Services (AD LDS) instance on the Edge Transport server with Active Directory data. Although creating an Edge Subscription is optional, subscribing an Edge Transport server to the Exchange organization provides a simpler management experience and enhances anti-spam features.

An Edge Transport server doesn't have direct access to Active Directory. As such, they can't directly access the Exchange Server organization configuration or recipient information that's stored in Active Directory. Instead, the configuration and recipient information the Edge Transport server uses to process messages is stored locally in AD LDS. Creating an Edge Subscription establishes secure, automatic replication of information from Active Directory to AD LDS.

**Additional reading.** For more information, see [Edge Subscriptions](/exchange/architecture/edge-transport-servers/edge-subscriptions?azure-portal=true).

### The EdgeSync service

The Edge Subscription process authenticates the credentials used to establish a secure LDAP connection between the internal Exchange Mailbox servers and a subscribed Edge Transport server. The Microsoft Exchange EdgeSync service (EdgeSync) that runs on Mailbox servers completes periodic one-way synchronization to transfer up-to-date data to AD LDS.

EdgeSync enables the shared information to replicate from Active Directory to AD LDS. This design reduces the administration tasks Messaging administrators must complete in the perimeter network. It does so by letting them configure the Mailbox server and then synchronize that information to the Edge Transport server. After the initial replication, EdgeSync synchronizes changed data in Active Directory to AD LDS keeps this data up to date.

:::image type="content" source="../media/edge-sync-c2c502ac.png" alt-text="Diagram showing how EdgeSync enables the shared information to replicate from Active Directory to AD LDS":::


Edge Transport servers can be deployed without using EdgeSync. However, using EdgeSync can reduce the effort needed to administer the Edge Transport servers. Active Directory contains much of the configuration information required by the Edge Transport server. For example, if you configure accepted domains in your Exchange admin center or Exchange Management Shell, these accepted domains can replicate automatically to the Edge Transport servers. To enable any filtering or transport rules that are based on recipients, you must implement EdgeSync to replicate the recipient information to AD LDS.

> [!TIP]
> When you deploy Edge Transport servers, it's recommended that you also deploy EdgeSync.

### How to configure EdgeSync

You must manually configure EdgeSync between Edge Transport servers and Mailbox servers. Additionally, you can only deploy Edge Transport servers to one Active Directory site at a time.

Configuring EdgeSync on each Edge Transport server requires the following steps:

1.  Create an Edge subscription file on an Edge Transport server.
2.  Import an Edge subscription file on a Mailbox server.
3.  Start and verify the EdgeSync process.

To verify that EdgeSync is configured correctly, you should run the following PowerShell command:

```powershell
Test-EdgeSynchronization -FullCompareMode
```

### Information replicated by EdgeSync

After you enable EdgeSync, the EdgeSync process establishes connections between an Exchange server and the Edge Transport server. It then synchronizes configuration and recipient information between Active Directory and AD LDS. Once the initial synchronization completes, only the changes are synchronized to the Edge Transport server.

> [!IMPORTANT]
> The internal Exchange servers, and not the Edge Transport servers, always start EdgeSync replication. EdgeSync replication traffic always encrypts using secure LDAP.

During synchronization, EdgeSync replicates the following data from Active Directory to AD LDS:

 -  Accepted domains
 -  Remote domains
 -  Recipients (hashed)
 -  Safe Senders Lists (hashed)
 -  Blocked Senders Lists
 -  Send connector configuration
 -  List of send and receive domains used in domain secure communications with partners
 -  List of SMTP servers listed as internal in your organization's transport configuration
 -  List of Mailbox servers in the subscribed Active Directory site (for dynamic connector generation)

> [!NOTE]
> The recipient and the safe senders are hashed by using a one-way hash. This hash prevents an attacker from retrieving recipient information from the Edge Transport server.

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.