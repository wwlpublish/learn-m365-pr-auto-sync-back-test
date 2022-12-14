Log files are created automatically by the system. They’re usually the initial source of information that Teams administrators turn to when troubleshooting specific issues. There are three types of log files: debug, media, and desktop. The debug log is used most often. Media and desktop logs are used by Microsoft for specific support cases. If you create a Microsoft support request, the support engineer will require the debug log.

> [!NOTE]
> **Debug logs** refers to the logs that are used for troubleshooting. However, the files that are generated for these logs will contain the term **diagnostic logs** in their names.

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

- Login
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

Media logging is turned on by default for computers if your CPU is:

* any Apple M1
* any Intel Xeon
* any Intel i9, except for the U, G7, M, and MQ series
* any 6th generation and later Intel i7, except for the U, G7, M, and MQ series

To log diagnostic data for Teams meetings, users must turn on the option in the Teams client. In the Teams admin center, navigate to **Settings** > **General**, select the **Enable logging for meeting diagnostics (requires restarting Teams**) check box, restart Teams, and reproduce the issue. When users sign out of Teams, Media logging resets to its default.

## Desktop logs

Desktop logs, also known as bootstrapper logs, contain log data about events that occur between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text-based and can be read using any text-based editor in a top down format.

## Other logs

* **Browser trace**. Microsoft Support might require you to collect a browser trace, for some categories of errors. This information can provide important details about the state of the Teams client when the error occurs.

    Before you start the browser trace, make sure that you’re signed in to Teams. It's important to do this before you start the trace so that the trace doesn't contain sensitive sign-in information.

* **WebRTC logs in browsers**. WebRTC logs can assist Microsoft Support by providing connection details for audio and video calls.