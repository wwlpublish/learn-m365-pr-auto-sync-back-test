### Task Manager

You can use the Performance tab in Task Manager to help to identify performance problems. The Performance tab displays a summary of CPU and memory usage, and network statistics.

Generally, you might consider using Task Manager when a performance-related problem first becomes apparent. For example, you might examine the running processes to determine if a particular program is using excessive CPU resources. Remember that Task Manager shows a snapshot of current resource consumption. You may need to examine historical data to get a better understanding of a server computer’s performance and response under load.

### Resource Monitor

When the Resource Monitor first opens, the initial view is of the Overview tab. On the right side are four graphs: CPU, Disk, Network, and Memory. You can examine these graphs, looking for excessive peaks in CPU, Disk, Network, or Memory activity. In the main pane, you can examine details about each component by expanding each component’s information list. It lists each process that is running on the computer, and includes information about resource consumption for each process. For example, the number of threads and the percentage of CPU capacity in use displays for each running process.

Having determined that a particular component is causing a bottleneck, you can use the appropriate component tab to view more information. Remember that a snapshot of current activity, which Resource Monitor provides, tells only a partial story. For instance, you might see a peak in activity, which is not representative of average performance.

### Performance Monitor

Performance Monitor features multiple graph views that give you a visual review of performance log data. You can create custom views in Performance Monitor that you can export as data collector sets for use with performance and logging features.

You can use data collector sets and the Performance Monitor tools to organize multiple data collection points into a single component that you can use to review or log performance. The Performance Monitor also includes default data collector set templates to help system administrators begin the process of collecting performance data.

In the Performance Monitor, under the Data Collector Sets node, you can use the User Defined node to create your own data collector sets. You can specify which objects and counters you want to include in the set for monitoring. To help you select appropriate objects and counters, you can use the following templates provided for monitoring:

 -  **System Diagnostics**. This template selects objects and counters that report the status of hardware resources, system response time, and processes on the local computer, along with system information and configuration data. The report provides guidance on ways to optimize the computer’s responsiveness.
 -  **System Performance**. This template generates reports that detail the status of local hardware resources, system response times, and processes.
 -  **WDAC Diagnostics**. This template enables you to trace debug information for Windows Data Access Components.

You also can configure a data collector set to run at a scheduled time, for a specific length of time, or until it reaches a predefined size. For example, you can run the data collector set for 10 minutes every hour during working hours to create a performance baseline. You also can set the data collector to restart when set limits are reached, so that a separate file will be created for each interval.

You can use data collector sets and Performance Monitor tools to organize multiple data collection points into a single component that you can use to review or log performance. Performance Monitor also includes default data collector set templates to help system administrators begin the process of collecting performance data specific to a server role or monitoring scenario.

In Performance Monitor, beneath the Data Collector Sets node, you can use the User Defined node to create your own data collector sets. You can specify which specific objects and counters you want to include in the set for monitoring. To help you select appropriate objects and counters, you can access templates to use for monitoring, including:

 -  **System Diagnostics**. Selects objects and counters that report the status of hardware resources, system response time, and processes on the local computer, along with system information and configuration data. The report provides guidance on ways to optimize the computer’s responsiveness.
 -  **System Performance**. Generates reports that detail the status of local hardware resources, system response times, and processes.
 -  **WDAC Diagnostics**. Enables you to trace debug information for Windows Data Access Components.

> [!NOTE]
> It is not necessary for Performance Monitor to be running for data to be collected into a data collector set.

You can add many different performance counters to the Performance Monitor. Some performance counters are not often used. The following table shows the commonly used performance counters.

:::row:::
  :::column:::
    **Counter**
  :::column-end:::
  :::column:::
    **Usage**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    LogicalDisk\\% Free Space
  :::column-end:::
  :::column:::
    This counter measures the percentage of free space on the selected logical disk drive. Take note if this falls below 15 percent, because you risk running out of free space for the operating system to store critical files. One solution is to add more disk space.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PhysicalDisk\\% Idle Time
  :::column-end:::
  :::column:::
    This counter measures the percentage of time the disk was idle during the sample interval. If this counter falls below 20 percent, the disk system is saturated. You should consider replacing the current disk system with a faster one.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PhysicalDisk\\Avg. Disk Sec/Read
  :::column-end:::
  :::column:::
    This counter measures the average time, in seconds, to read data from the disk. If the number is larger than 25 milliseconds (ms), that means the disk system is experiencing latency when it is reading from the disk.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PhysicalDisk\\Avg. Disk Sec/Write
  :::column-end:::
  :::column:::
    This counter measures the average time, in seconds, it takes to write data to the disk. If the number is larger than 25 ms, the disk system experiences latency when it is writing to the disk.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    PhysicalDisk\\Avg. Disk Queue Length
  :::column-end:::
  :::column:::
    This counter indicates how many I/O operations are waiting for the hard drive to become available. If the value is larger than two times the number of spindles, it means that the disk itself might be the bottleneck. If this counter indicates a possible bottleneck, consider measuring the Avg. Disk Read Queue Length and Avg. Disk Write Queue Length to try to determine if read or write operations are the cause.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Memory\\Cache Bytes
  :::column-end:::
  :::column:::
    This counter indicates the amount of memory that the file-system cache uses. There might be a disk bottleneck if this value is greater than 300 megabytes (MB).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Memory\\% Committed Bytes in Use
  :::column-end:::
  :::column:::
    This counter measures the ratio of Committed Bytes to the Commit Limit, or in other words, the amount of virtual memory in use. If the number is greater than 80 percent, it indicates insufficient memory.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Memory\\Available Mbytes
  :::column-end:::
  :::column:::
    This counter measures the amount of physical memory, in megabytes, available to run processes. If this value is less than 5 percent of the total physical random access memory (RAM), that means there is insufficient memory, which can increase paging activity.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Memory\\Free System Page Table Entries
  :::column-end:::
  :::column:::
    This counter indicates the number of page table entries not currently in use by the system. If the number is less than 5,000, there might be a memory leak.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Memory\\Pool Non-Paged Bytes
  :::column-end:::
  :::column:::
    This counter measures the size, in bytes, of the nonpaged pool. This is an area of system memory for objects that cannot be written to a disk, but instead must remain in physical memory for as long as they are allocated. If the value is greater than 175 MB (or 100 MB with a /3 gigabyte (GB) switch), then there is a possible memory leak.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Memory\\Pool Paged Bytes
  :::column-end:::
  :::column:::
    This counter measures the size, in bytes, of the paged pool. This is an area of system memory for objects that can be written to disk when they are not being used. There might be a memory leak if this value is greater than 250 MB (or 170 MB with the /3 GB switch).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Memory\\Pages per Second
  :::column-end:::
  :::column:::
    This counter measures the rate at which pages are read from or written to the disk to resolve hard-page faults. If the value is greater than 1,000 as a result of excessive paging, there might be a memory leak.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Processor\\% Processor Time
  :::column-end:::
  :::column:::
    This counter measures the percentage of elapsed time that the processor spends executing a non-idle thread. If the percentage is greater than 85 percent, the processor is overwhelmed, and the server might require a faster processor.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Processor\\% User Time
  :::column-end:::
  :::column:::
    This counter measures the percentage of elapsed time that the processor spends in user mode. If this value is high, the server is busy with the application.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Processor\\% Interrupt Time
  :::column-end:::
  :::column:::
    This counter measures the time that the processor spends receiving and servicing hardware interruptions during specific sample intervals. If the value is greater than 15 percent, this counter indicates a possible hardware issue.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    System\\Processor Queue Length
  :::column-end:::
  :::column:::
    This counter indicates the number of threads in the processor queue. The server does not have enough processor power if the value is more than two times the number of CPUs for an extended period of time.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Network Interface\\Bytes Total/Sec
  :::column-end:::
  :::column:::
    This counter measures the rate at which bytes are sent and received over each network adapter, including framing characters. The network is saturated if more than 70 percent of the interface is consumed.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Network Interface\\Output Queue Length
  :::column-end:::
  :::column:::
    This counter measures the length of the output packet queue, in packets. There is network saturation if the value is more than 2.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Process\\Handle Count
  :::column-end:::
  :::column:::
    This counter measures the total number of handles that a process currently has open. This counter indicates a possible handle leak if the number is greater than 10,000.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Process\\Thread Count
  :::column-end:::
  :::column:::
    This counter measures the number of threads currently active in a process. There might be a thread leak if this number is more than 500 between the minimum and maximum number of threads.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Process\\Private Bytes
  :::column-end:::
  :::column:::
    This counter indicates the amount of memory that this process has allocated that it cannot share with other processes. If the value is greater than 250 between the minimum and maximum number of threads, there might be a memory leak.
  :::column-end:::
:::row-end:::
