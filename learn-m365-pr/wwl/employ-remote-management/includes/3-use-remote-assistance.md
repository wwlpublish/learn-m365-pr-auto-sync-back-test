With remote management tools and technologies, a network administrator can access a computer on the network, take control of it, and perform tasks on it, without having to be physically in front of the computer. This saves both time and money by reducing the number of trips required to service problematic computers. Users can also remotely access their own computers for working at them while not physically sitting in front of them. Remote Assistance is a bundled service with Windows. It enables a technician to take control of a computer to troubleshoot and perform maintenance tasks without having to physically travel to the problematic machine. This enables the technician to resolve problems without leaving their home or office. The end user must be there to authorize this, and the user can end the session at any time. This technology is generally used only to troubleshoot remote computers and is not used for telecommuting or accessing files or folders.

### Enable or disable remote features

By default, Remote Assistance connections are enabled for a Windows computer. You can make changes to the default from the System Properties dialog box, shown below. You can open this dialog box in many ways.

1.  Sign in as Administrator.
2.  Right-click **Start.**
3.  Select **System.**
4.  Select **Advanced system settings** or **Remote settings** in the left pane.
5.  Select the **Remote** tab.
6.  Select the **Allow Remote Assistance connections to this computer** check box.

:::image type="content" source="../media/remote-assistance-permission-9215ebc2.jpg" alt-text="Screenshot of System Properties window showing how to allow remote assistance.":::


### **Verify the Windows firewall is configured correctly**

Check to see that the Windows firewall is not blocking Remote Assistance.

1.  Select **Start** and then select **Settings.**
2.  Select **Network &amp; Internet.**
3.  Select **Windows Firewall.**
4.  Select **Allow an app or feature through Windows Firewall.**
5.  Scroll through the list of **Allowed apps and features** looking for **Remote Assistance.**
6.  Verify that **Remote Assistance** is selected, if not select **Change settings.**
7.  Select the **select box** for Remote Assistance, and select **OK.**

### Configure and use Remote Assistance

To use Remote Assistance, the user must be at the problematic computer. A Remote Assistance session must be initiated by that user, and the user must approve the connection before it can be made.

1.  Right-click **Start** and then select **Control Panel.**
2.  Enter invite in the search box.
3.  Select **Invite someone to connect to your PC** and help you, or offer to help someone else. The Windows Remote Assistance wizard starts.

Once configured, Windows Remote Assistance can also be access using an Administrative PowerShell console. After you select Invite someone you trust to help you, you have three options:

 -  Save this invitation as a file
 -  Use email to send an invitation the user sends the invitation using an email client on the machine but cannot send it using any form of web-based email
 -  Use Easy Connect (the easiest option if it is enabled by the help and support team)

When the user selects Easy Connect, an Easy Connect password appears. The user only needs to relay that password to the help and support team. The support technician can then send a connection request, which the user then accepts. Once the connection is made, the “Expert” can ask to control the computer to resolve the problem, train the user, or perform other tasks. For security reasons, consider turning off this feature until it is needed.

### Quick Assist

Microsoft Quick Assist is a Windows app that enables two people to share a computer over a remote connection so that one person can help solve problems on the other person’s computer just like Remote Assistance. In fact, depending on which version of Windows is on a PC may determine whether Quick Assist or Remote Assistance is installed. The significant difference between Quick Assist and Remote Desktop is that the former enables the helper to take over the remote computer without forcing the other user to sign out; this enables the helper to demonstrate the solution to a problem

Select **Start** &gt; **Windows Tools** &gt; **Quick Assist**, or select the search box on the taskbar and type **Quick Assist,** and then select Quick Assist in the list of results.

Quick assist uses a one-time passcode for establishing a connection. The person who is providing the help will select **Assist another person** in the Quick Assist app. A one-time passcode will be generated. The user requesting the assistance will request this passcode and enter it in the **Code from assistant** field. This will establish the Quick Assist session.
