To pinpoint why a computer is experiencing a problem, you should identify whether a hardware component or device is the source of the problem. Knowing which devices are most susceptible to failure can help accelerate your diagnosis. Being aware of the conditions under which vulnerable devices are most likely to fail can help you avoid those conditions, as well. You then can use reliability measures to calculate the probability of failure.

One such measure is mean time between failures (MTBF), which is the average time interval, usually expressed in thousands or tens of thousands of hours, before a component fails and requires service.

#### Hard disk drives

There are five main reasons why hard disk drives fail:

 -  **Logical failure**. Examples of logical failures include invalid entries in a file allocation table (FAT) or master file table (MFT) on the NTFS file system volume. Logical failures are the least severe type of failure. However, logical errors can cause corruption and file-system loss on a severely fragmented drive. In these situations, you may need specialized tools to fix the problem.
 -  **Mechanical failure**. Platters (one or more rotating, magnetically coated disks) store data on a hard disk. Data is accessed through read/write heads mounted on rotating mechanical arms. One of the most common mechanical failures occurs when the read/write heads of the hard disk come in contact (momentarily or continuously) with the hard disk platters. Additionally, physical shock, computer movement, static electricity, power surges, or mechanical read/write head failure can all cause head crashes. Hard disk drives also could fail because of motor problems.
 -  **Electronic failure**. An electronic failure is a problem with the hard disk’s controller board. If the controller fails, the disk could be undetectable by the system BIOS. Additionally, electronic failure can occur because of electrical surges that damage the controller board or because of defective board components. However, you often can recover data because the disk platters and other mechanical components remain undamaged.
 -  **Firmware failure**. Hard disk firmware is code that controls the hardware. Often, it is stored on a flash memory chip on the hard disk controller board. If the firmware becomes corrupt or unreadable, the computer could be unable to communicate with the disk.
 -  **Bad sector**. Bad sectors can be logical or physical sectors. A lost cluster is an example of a logical bad sector that typically you can repair with software tools. Shock or vibrations often cause physical bad sectors. Most hard disk drives have firmware that marks bad sectors. If the damage is minor, no data is lost. You can use drive-monitoring tools to determine when the number of physical bad sectors is critical enough to replace the drive.

> [!NOTE]
> Some disks implement Self-Monitoring, Analysis, and Reporting Technology (SMART). This technology enables the operating system to monitor the hard disk proactively, checking for reliability issues before they can result in data loss.

#### Solid-state drives

Many devices, including tablets and some laptops, have SSDs. This technology differs from traditional hard drives and offers benefits to users in terms of physical device size, speed, and, to some extent, power consumption. Although there are no moving parts, SSDs can fail, often resulting in data loss. Every time the operating system writes to an SSD drive, it uses memory cells to store the data. These cells can wear out after extensive write operations, resulting in errors or even drive failure. Some drives offer error checking memory cells, which can help to mitigate data errors, and some users report more problems with larger drives. However, it is important not to consider SSDs as a fail-safe storage solution.

#### Power supplies

The power supply converts regular current into low, direct current (DC) voltage that a device can use. A failing power supply can cause erratic behavior, including devices restarting randomly, memory errors, or power being supplied to some devices and not others. Symptoms of power supply problems can include:

 -  No indicator lights, disk action, or screen display.
 -  On/Off indicator lights are visible, but there is no disk action or screen display.
 -  The system produces a continuous beep.

#### Optical drives

Optical drives such as CD and DVD drives tend to have shorter lifetimes compared to other hardware devices, and the MTBF is lower than that for a hard disk drive. Most hardware manufacturers provide a one-year guarantee on optical drives and a three-year guarantee on hard drives.

The media quality in optical drives is a significant factor in the length of the optical drive’s life:

 -  Higher-quality media can increase a device’s life.
 -  Unclean media could reduce the device’s life.

Software settings also can affect optical drives. Using a high maximum write speed can result in a greater number of irreparable and subsequently unusable disks, compared to using slower write speeds. Optical drives can fail due to vibration because they require precise optical alignment in the device to work properly. You can cause vibration by moving the computer while it is in use, or by operating the computer in a location that is not stable. Excessive dust also can damage optical drives, which can be an environmental factor.

#### Cool fans

The most common cause of cooling fan failures is dust building up inside the computer and around the fan area. This accumulation can lead to failures in the fan bearings, motor, or power supply. Cooling fan failure can cause system to fail because of overheating.

#### CPUs and GPUs

Central processing units (CPUs) and graphics processing units (GPUs) are the devices least likely to fail. However, you can overheat and damage the CPU if you attempt to overclock the CPU. Overheating also can occur because of a failure with the cooling fan. Additionally, power spikes and static electricity discharge can cause CPU failures.

#### System memory

Memory problems can occur because of heat, power surges, or static electricity. You can use the Windows Memory Diagnostics Tool to help identify and resolve memory issues.

#### Additional components at risk

Additionally, other components can fail. These include:

 -  **Batteries**. Laptop computers and tablets have batteries. Although battery technology has improved dramatically over the past several years, they still have a limited life. When your device battery begins to degrade, consider replacing it. Common signs of impending battery failure include:
    
     -  Inability to maintain a charge for extended periods.
     -  Inability to supply a charge to a device for extended periods.
     -  Excessive time required to charge a battery.
    
    > [!NOTE]
    > Although almost all laptops have batteries that users can replace, this is not the case with all tablets. Some tablets require the manufacturer or service agent to replace the battery.

 -  **Docking stations**. Many users rely on docking stations to use their Windows devices. This is especially true for smaller devices such as tablets, as users connect their tablets to docking stations to utilize peripherals such as keyboards and monitors. Failure of these intermediate devices can result in productivity loss for the user.
 -  **Display monitors**. Display monitors are something that will require manufacturer replacement. Before acting on a possible display failure, eliminate all other causes, including device drivers and the graphics card or system board.
