Windows includes a number of tools that you can use to diagnose network problems, including:

 -  Event Viewer
 -  Windows Network Diagnostics
 -  IPConfig
 -  Ping
 -  Tracert
 -  NSLookup
 -  Pathping
 -  Windows PowerShell

## Event Viewer

**Event logs** are files that record significant events on a computer, such as when a process encounters an error. IP conflicts are reflected in the system log and might prevent services from starting. When these events occur, Windows records the event in an appropriate event log. You can use Event Viewer to read the log. When you troubleshoot errors on Windows, you can view the events in the event logs to determine the cause of the problem.

You can use Event Viewer to access the Application, Security, Setup, and System logs under the Windows Logs node. When you select a log and then select an event, a preview pane under the event list contains details of the specified event. To help diagnose network problems, look for errors or warnings related to network services in the System log.

## Windows Network Diagnostics

In the event of a Windows networking problem, the Diagnose Connection Problems option helps diagnose and repair the problem. Windows Network Diagnostics then presents a possible description of the problem and a potential remedy. The solution might require manual intervention from the user.

## IPConfig

The **IPConfig** command displays the current TCP/IP network configuration. Additionally, you can use **IPConfig** to refresh DHCP and DNS settings. For example, you might need to flush the DNS cache. The following table provides a brief description of some of the **IPConfig** command switches.

:::row:::
  :::column:::
    **Command**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **ipconfig /all**
  :::column-end:::
  :::column:::
    View detailed configuration information.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **ipconfig /release**
  :::column-end:::
  :::column:::
    Release the leased configuration back to the DHCP server.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **ipconfig /renew**
  :::column-end:::
  :::column:::
    Renew the leased configuration.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **ipconfig /displaydns**
  :::column-end:::
  :::column:::
    View the DNS resolver cache entries.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **ipconfig /flushdns**
  :::column-end:::
  :::column:::
    Purge the DNS resolver cache.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **ipconfig /registerdns**
  :::column-end:::
  :::column:::
    Register/update the client’s host name with the DNS server.
  :::column-end:::
:::row-end:::


## Ping

You use the **Ping** command to verify IP-level connectivity to another TCP/IP computer. This command sends and receives Internet Control Message Protocol (ICMP) echo request messages, and displays the receipt of corresponding echo reply messages. The **Ping** command is the primary TCP/IP command used to troubleshoot connectivity.

> [!NOTE]
> Firewalls might block the ICMP requests. As a result, you might receive false negatives when using \*\*Ping\*\* as a troubleshooting tool.

## Tracert

The **Tracert** tool determines the path taken to a destination computer by sending ICMP echo requests. The path displayed is the list of router interfaces between a source and a destination. This tool also determines which router has failed, and what the latency, or speed, is. These results might not be accurate if the router is busy, because the router will assign the packets a low priority.

## Pathping

The **Pathping** command traces a route through the network in a manner similar to the Tracert tool. However, **Pathping** provides more detailed statistics on the individual steps, or hops, through the network. The command can provide greater detail because it sends 100 packets for each router, which enables it to establish trends.

## NSLookup

The **NSLookup** tool displays information that you can use to diagnose the DNS infrastructure. You can use the tool to confirm connection to the DNS server, in addition to the existence of the required records.

## Windows PowerShell

You can use Windows PowerShell to configure network connection settings. In addition to this, you can use Windows PowerShell cmdlets for troubleshooting network settings.
