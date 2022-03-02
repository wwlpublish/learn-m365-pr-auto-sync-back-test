In addition to the Network and Settings section in Settings, you can configure network settings by using a number of tools in Windows. The tool you decide to use depends on your situation and goals.

## Network Setup Wizard

Windows provides the Network Setup Wizard, a user-friendly interface that you can use to configure network settings. Windows recognizes any unconfigured network devices on the computer, and then automates the process of adding and configuring them. The Network Setup Wizard also recognizes any wireless networks in range of the computer, and then guides you through the process of configuring them.

You can save network settings to a USB flash drive for use when configuring additional computers, which makes that process quicker. You also can use the Network Setup Wizard to enable sharing across your network for documents, photos, music, and other files.

## Windows PowerShell

Although you can use the graphical tools previously described to perform all network configuration and management tasks, sometimes it can be quicker to use command line tools and scripts. Windows has always provided the command prompt for certain network management tools. However, Windows PowerShell provides a number of network-specific cmdlets that you can use to configure, manage, and troubleshoot Windows network connections.

The following table lists some of the network-related Windows PowerShell cmdlets and their purposes.

:::row:::
  :::column:::
    **Cmdlet**
  :::column-end:::
  :::column:::
    **Purpose**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get NetIPAddress
  :::column-end:::
  :::column:::
    Retrieves information about the IP address configuration.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get NetIPv4Protocol
  :::column-end:::
  :::column:::
    Retrieves information about the IPv4 protocol configuration (the cmdlet **Get-NetIP6Protocol** returns the same information for the IPv6 protocol).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get NetIPInterface
  :::column-end:::
  :::column:::
    Obtains a list of interfaces and their configurations. This does not include IPv4 configuration of the interface.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set NetIPAddress
  :::column-end:::
  :::column:::
    Sets information about the IP address configuration.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set NetIPv4Protocol
  :::column-end:::
  :::column:::
    Sets information about the IPv4 protocol configuration (the cmdlet **Set-NetIP6Protocol** returns the same information for the IPv6 protocol.)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set NetIPInterface
  :::column-end:::
  :::column:::
    Modifies IP interface properties.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get NetRoute
  :::column-end:::
  :::column:::
    Obtains the list of routes in the local routing table.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Test-Connection
  :::column-end:::
  :::column:::
    Runs similar connectivity tests to that used by the **Ping** command. For example, **test-connection lon-dc1**.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Resolve-Dnsname
  :::column-end:::
  :::column:::
    Provides a similar function to the **NSLookup** tool.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get NetConnectionProfile
  :::column-end:::
  :::column:::
    Obtains the type of network (public, private, or domain) to which a network adapter is connected.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Clear-DnsClientCache
  :::column-end:::
  :::column:::
    Clears the client’s resolver cache, similar to the **IPConfig /flushdns** command.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-DnsClient
  :::column-end:::
  :::column:::
    Retrieves configuration details specific to the different network interfaces on a specified computer.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-DnsClientCache
  :::column-end:::
  :::column:::
    Retrieves the contents of the local DNS client cache, similar to the **IPConfig /displaydns** command.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-DnsClientGlobalSetting
  :::column-end:::
  :::column:::
    Retrieves global DNS client settings, such as the suffix search list.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Get-DnsClientServerAddress
  :::column-end:::
  :::column:::
    Retrieves one or more DNS server IP addresses associated with the interfaces on the computer.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Register-DnsClient
  :::column-end:::
  :::column:::
    Registers all of the IP addresses on the computer onto the configured DNS server.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set-DnsClient
  :::column-end:::
  :::column:::
    Sets the interface-specific DNS client configurations on the computer.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set-DnsClientGlobalSetting
  :::column-end:::
  :::column:::
    Configures global DNS client settings, such as the suffix search list.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set-DnsClientServerAddress
  :::column-end:::
  :::column:::
    Configures one or more DNS server IP addresses associated with the interfaces on the computer.
  :::column-end:::
:::row-end:::


For example, to configure the IPv4 settings for a network connection by using Windows PowerShell, use the following cmdlet:

```
Set-NetIPAddress –InterfaceAlias Wi-Fi –IPAddress 172.16.16.1

```

## Netsh

You also can use the **Netsh** command ¬line tool to configure network settings. For example, to configure IPv4 by using **Netsh**, you can use the following example:

```
Netsh interface ipv4 set address name="Local Area Connection"
source=static addr=172.16.16.3 mask=255.255.255.0 gateway=172.16.16.1

```

:::image type="content" source="../media/netsh-show-configure-0b915336.jpg" alt-text="Slide showing a diagram of the envisioning process.":::


> [!NOTE]
> Functionality in the Windows PowerShell network-related cmdlets has largely replaced **Netsh**.
