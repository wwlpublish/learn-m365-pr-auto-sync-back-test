The Task Manager tool is one of the tools that end users and administrators use most for viewing system performance and resource utilization on a device. Task Manager primarily is a performance-monitoring tool, and not a reliability-monitoring tool.

:::image type="content" source="../media/task-manager-a4baea54.jpg" alt-text="Screenshot of the Task Manager screen.":::


You can run Task Manager in several ways, including by:

 -  Right-clicking the taskbar, and then selecting **Task Manager**.
 -  Pressing Ctrl+Alt+Del, and then selecting **Task Manager**.
 -  Pressing the Ctrl+Shift+Esc key combination.
 -  Running **taskmgr.exe** at a command prompt.
 -  Selecting **Start**, typing **taskmgr**, and then pressing Enter.

When you run Task Manager for the first time, it shows only apps and processes that are running. If you press the More details button, Task Manager expands and shows detailed information about the system’s activity. Task Manager includes the following tabs:

 -  **Processes**. The Processes tab displays a list of running programs, subdivided into apps and internal Windows processes. For each running process, this tab displays a summary of processor and memory usage.
 -  **Performance**. The Performance tab displays a summary of CPU and memory usage, and network statistics.
 -  **App history**. The App history tab displays statistics and resource consumption by apps. This is useful for identifying a specific app that is consuming excessive resources.
 -  **Startup**. The Startup tab displays items that run at startup. You can choose to disable any listed programs.
 -  **Users**. The Users tab displays resource consumption on a per-user basis. You also can expand the user view to see more detailed information about the specific processes that a user is running.
 -  **Details**. The Details tab lists all the running processes on a server, providing statistics about CPU, memory, and other resource consumption. You can use this tab to manage running processes. For example, you can stop a process, stop a process and all related processes, or change the priority values of processes. When you change the priority of a process, you determine the degree to which the process can consume CPU resources. When you increase priority, you allow the process to request more CPU resources.
 -  **Services**. The Services tab provides a list of running Windows services with related information, including whether a service is running and the process identifier (PID) value of a running service. You can start and stop services by using the list on the Services tab.

When a reliability problem first becomes apparent, you should use Task Manager to see if you can troubleshoot the issue. For example, you might examine the startup items to determine whether a particular program is causing problems after it starts and scan the processes for unresponsive apps.

> [!NOTE]
> Task Manager shows the current resource utilization on the local computer. You cannot use the Task Manager to monitor activity on a remote computer or to store activity and resource utilization to a log file.
