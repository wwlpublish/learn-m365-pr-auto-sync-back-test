ReFS was first introduced in Windows Server 2012 and is also available on Windows client. It's built on NTFS, and it's designed to provide the highest level of resiliency, integrity, and scalability, regardless of software or hardware failures. ReFS includes only some of NTFS features, such as security and auditing, but doesn't support others, such as quota, compression, and EFS encryption. ReFS is especially useful for data volumes in multiterabyte (TB) file servers and for cluster-shared volumes in failover clusters.

:::image type="content" source="../media/refs-disk-properties-4ef850fe.jpg" alt-text="Screenshot of the disk properties windows for ReFS.":::


ReFS includes the following benefits:

 -  ReFS is designed to provide the highest level of protection for data from common errors that can cause corruption, such as unexpected loss of power or disk failure. If you use ReFS with redundant storage, which is mandatory in Windows 10 and later, ReFS can detect data corruption and automatically correct it by using the second copy of the data.
 -  ReFS periodically scans volumes. If it detects corruption, ReFS tries to correct the corruption automatically. If it can’t repair the corruption automatically, ReFS localizes the salvaging process to the corruption area. This doesn't require any downtime for the volume.
 -  ReFS supports extremely large volumes, even larger than NTFS, without impacting performance. ReFS volumes can have multiple petabytes of data and a theoretical size limit for ReFS volume is 2^78 bytes.
 -  ReFS allows you to control file permissions and configure auditing as you would with NTFS. But several other NTFS features, such as compression, disk quotas, EFS, and volume shrinking, aren't available with ReFS volumes.

Windows client provided limited support for ReFS. You can use it only with two-way or three-way storage spaces. You can’t format ReFS for non-mirrored storage spaces, such as simple or parity storage spaces.
