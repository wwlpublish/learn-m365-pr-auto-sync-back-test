Log files are created automatically by the system. They're usually the initial source of information that Teams administrators turn to when troubleshooting specific issues. There are three types of log files: debug, media, and desktop. The debug log is used most often. Media and desktop logs are used by Microsoft for specific support cases. If you create a Microsoft support request, the support engineer will require the debug log.

The following table outlines the various clients and their associated logs. Log files are stored in locations specific to the client and operating system.

| Client| Debug|  Media |Desktop|
| - |-| -| -| 
| Web| X| -| - |
| Windows| X| X| X |
| Mac OSX| X| X| X |
| Linux| X| X| X |
| iOS| -| -| - |
| Android| -| -| - |

## Debug logs

Debug log records are produced by the Windows and Mac desktop clients and browser-based clients. The logs are text files and can be read using any text-based editor. Logs are read from the bottom up and new log records are created when logging into the client. Debug logs display the following data flows:

- Sign-in
- Connection requests to middle tier services
- Call/conversation

The debug logs are produced and downloaded using the following OS-specific methods:

| Teams Client| Keyboard shortcut| Log file folder |
| - |-| -|
| Windows| Ctrl + Alt + Shift + 1| %userprofile%\Downloads |
| Mac OSX| Option + Command + Shift + 1| Downloads |
| Linux|  Ctrl + Alt + Shift + 1| ~/Downloads |
| Browser| Ctrl + Alt + Shift + 1| You'll be prompted to save the debug log to the default save location |

## Media logs

Media logs contain diagnostic data about audio, video, and screen sharing. These logs are required for support cases only when requested. They can only be inspected by Microsoft.

Media logging is turned off by default. To log diagnostic data for Teams meetings, users must turn on the option in the Teams client. In the Teams admin center, navigate to **Settings** > **General**, select the **Enable logging for meeting diagnostics (requires restarting Teams**) check box, restart Teams, and reproduce the issue.

## Desktop logs

Desktop logs, also known as bootstrapper logs, contain log data about events that occur between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text-based and can be read using any text-based editor in a top down format.
