When users experience problems, you need to diagnose and fix the causes fast. In Microsoft Teams, those problems are often caused by wrongly configured firewalls or proxy servers that block communications. Other issues can be investigated in the log files that Teams creates.

## Client connectivity

If you're experiencing connectivity issues with the Teams client, the most likely causes are firewall or proxy settings. Verify that the necessary URLs, IP addresses, and ports are opened in your firewall or proxy server. For information on the URLs and IPs required for Microsoft Teams, see the support articles Office 365 URLs and IP address ranges and Prepare your organization's network for Microsoft Teams, in the Learn more section below.
The following services require specific URLs and ports to be opened in the firewall:

- Authentication
- Microsoft Teams client connectivity
- Collaboration
- Media
- Shared services
- Third-party integration
- Skype for Business interoperability
- Skype for Business client interoperability

## Using logs

Log files are created automatically and provide information to help you troubleshoot specific issues.

There are three types of log files: debug, media, and desktop. The debug log is used most often. Media and desktop logs are used by Microsoft for specific support cases. If you create a Microsoft support request, the support engineer will require the debug log.

Debug log records are produced by the Windows and Mac desktop clients, and browser-based clients. The logs are text files and can be read using any text-based editor. Logs are read from the bottom up and new log records are created when logging into the client. Debug logs show the following data flows:

- Login
- Connection requests to middle tier services
- Call/conversation

The debug logs are produced using the following OS-specific methods:

- Windows: keyboard shortcut: <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>
- Mac OSX: keyboard shortcut: <kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>
- Linux: keyboard shortcut: <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>

These logs are automatically downloaded to the following folders:

- Windows: %userprofile%\Downloads
- Mac OSX: Downloads
- Linux: ~/Downloads
- Browser: You'll be prompted to save the debug log to a default save location

Media logs contain diagnostic data about audio, video, and screen sharing. These logs are required for support cases only when requested and can only be inspected by Microsoft.

Desktop logs, also known as bootstrapper logs, contain log data about events that occur between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text-based and can be read using any text-based editor in a top down format.

## Common problems

Common problems are documented in the Teams Troubleshooting section of the Microsoft Teams documentation. If there's a problem, refer to this documentation for details of symptoms, causes, and how it can be resolved.
