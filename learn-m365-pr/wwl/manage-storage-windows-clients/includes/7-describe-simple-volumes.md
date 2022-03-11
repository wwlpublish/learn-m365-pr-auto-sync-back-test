The most commonly used disk arrangement is a simple volume. This volume is a contiguous, unallocated area of a physical hard disk that you format to create a file system. You then assign a drive letter to it or mount it in an existing volume by using a volume mount point.

:::image type="content" source="../media/simple-volumes-c42737bd.jpg" alt-text="Diagram showing the storage concept of a simple volume.":::


### Simple volume characteristics

A simple volume is a volume that encompasses available free space from a single, basic, or dynamic hard-disk drive. A simple volume can consist of a single region on a disk or multiple regions of the same disk that link together. Simple volumes have the following characteristics:

 -  Not fault-tolerant. Disk failure leads to volume failure.
 -  Volume I/O performance is the same as disk I/O performance.

### Simple volume scenarios

The following table contains example scenarios for disks and volumes.

:::row:::
  :::column:::
    **Scenario**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Business desktop computer with one disk
  :::column-end:::
  :::column:::
    Most business users require a basic disk and one basic volume for storage, but do not require a computer with volumes that span multiple disks or that provide fault tolerance. This is the best choice for those who require simplicity and ease of use.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Business desktop computer with one disk and more than one volume
  :::column-end:::
  :::column:::
    If small business users want to upgrade their operating systems and reduce the impact on their business data, they must store the operating system in a separate location from business data. This scenario requires a basic disk with two or more simple volumes. Users can install an operating system on the first volume, creating a boot volume or system volume, and use the second volume to store data. When a new version of an operating system releases, users can reformat the boot or system volume, and then install the new operating system. The business data, located on the second volume, remains untouched.
  :::column-end:::
:::row-end:::


A simple volume might provide better performance than striped data layout schemes. For example, when serving multiple, lengthy, sequential streams, performance is best when a single disk services each stream. Workloads composed of small, random requests do not always result in performance benefits when you move them from a simple to a striped data layout.

The emergence of SSDs, which offer extremely fast data transfer rates, offers the Windows user another decision related to storing data. SSDs currently are more expensive and have smaller capacities compared to traditional magnetic hard disk drives. This combination of performance, size, and cost is an acceptable compromise when used in small form factor devices. However, a desktop PC might benefit from a combination of an SSD for Windows system files and a large capacity hard disk drive for business data.
