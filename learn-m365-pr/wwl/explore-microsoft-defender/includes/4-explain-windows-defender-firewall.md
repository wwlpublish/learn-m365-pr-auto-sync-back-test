Windows centralizes basic firewall information in Control Panel, in the Network and Sharing Center and System and Security items. In System and Security, you can configure basic Windows Defender Firewall settings and access the Action Center to view notifications for firewall alerts. In the Network and Sharing Center, you can configure all types of network connections, such as changing the network location profile.

:::image type="content" source="../media/windows-10-firewall-add-app-54ec8e61.png" alt-text="Screenshot in Windows Defender Firewall showing the existing apps that are allowed.":::


### Firewall exceptions

When you add a program to the list of allowed programs, or open a firewall port, you are allowing that program to send information to or from your computer. Allowing a program to communicate through a firewall is like making an opening in the firewall. Each time that you create another opening, the computer becomes less secure.

Generally, it is safer to add a program to the list of allowed programs than to open a port for an app. If you open a port without scoping the port to a specific app, the opening in the firewall stays open until you close the port, regardless of whether a program is using it. If you add a program to the list of allowed programs, you are allowing the app itself to create an opening in the firewall, but only when necessary. The openings are available for communication only when required by an allowed program or computer.

To add, change, or remove allowed programs and ports, you should perform the following steps. Select **Allow an app or feature through Windows Defender Firewall** in the left pane of the Windows Defender Firewall page, and then select **Change settings**. For example, to view performance counters from a remote computer, you must enable the Performance Logs and Alerts firewall exception on the remote computer.

To help decrease security risks when you open communications:

 -  Only allow a program or open a port when necessary.
 -  Remove programs from the list of allowed programs, or close ports when you do not require them.
 -  Never allow a program that you do not recognize to communicate through the firewall.

### Multiple active firewall profiles

Windows includes multiple active firewall policies. These firewall policies enable computers to obtain and apply a domain firewall profile, regardless of the networks that are active on the computers. Information technology (IT) professionals can maintain a single set of rules for remote clients and those that physically connect to an organization’s network. To configure or modify profile settings for a network location, select **Change advanced sharing settings** in the left pane of the **Network and Sharing Center**.

### Windows Defender Firewall notifications

You also can display firewall notifications in the taskbar by performing the following steps. Select **Change notification settings** in the left pane of the **Windows Defender Firewall** page, and then for each network location, select or clear the **Notify me when Windows Defender Firewall blocks a new app** check box.
