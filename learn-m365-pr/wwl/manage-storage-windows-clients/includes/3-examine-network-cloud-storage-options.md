There are two types of external storage systems: NAS (Network-Attached Storage) and SAN (Storage Area Networking). You use NAS for both client-based and server-based computing, whereas you most often use SAN for server-based computing and then make it accessible to users. Although Windows includes the iSCSI initiator that allows you to connect to SANs, you usually use SANs in server-based computing.

:::image type="content" source="../media/network-storage-5ccce6a8.jpg" alt-text="Diagram showing NAS and SAN configurations.":::


#### NAS

NAS is storage that is connected to a dedicated storage device. You can access it over the network. Unlike DAS, NAS is not directly attached to a computer or server, and users access it over the network. NAS has two distinct solutions: a low-end appliance (NAS only), and an enterprise-class NAS that integrates with SAN.

Each NAS device has a dedicated operating system that controls access to the data on the device, which reduces the overhead associated with sharing the storage device with other server services. An example of NAS software is Windows Storage Server, a special edition of Windows Server.

NAS devices typically provide file-level access to the storage, which means that you can access the data on the storage only as files. You must use protocols such as Common Internet File System (CIFS), Server Message Block (SMB), or network file system (NFS) to access the files.

To enable NAS storage, you need a storage device. Frequently, these devices do not have any server interfaces such as keyboards, mice, and monitors. To configure the device, you need to provide a network configuration, and then access the device across the network. You can then create network shares on the device by using the name of the NAS and the share created. The network’s users can then access these shares.

#### SAN

SAN is a high‐speed network that connects computer systems or host servers to high-performance storage subsystems. A SAN usually includes various components such as host bus adapters (HBAs), special switches to help route traffic, and storage disk arrays with logical unit numbers (LUNs) for storage.

A SAN enables multiple servers to access a pool of storage in which any server can potentially access any storage unit. Because a SAN is a network, you can use a SAN to connect many different devices and hosts and provide access to any connected device from anywhere.

SANs provide block-level access. This means that, rather than accessing the content on the disks as files by using a file access protocol, SANs write blocks of data directly to the disks by using protocols such as Fibre Channel over Ethernet or Internet Small Computer System Interface (iSCSI).

Today, most SAN solutions offer SAN and NAS together. The backend head units, disks, and technologies are identical, and only the access method differs. Enterprises often provision block storage from the SAN to the servers by using Fibre Channel over Ethernet or iSCSI. NAS services use the CIFS and NFS protocols. If you want to use a SAN, Windows supports the iSCSI protocol with the iSCSI initiator.

#### Cloud Based Storage

Cloud storage simplifies access to your files as long as you have Internet access. When you sign in with your Microsoft account, you can access all the files on your Microsoft OneDrive. Microsoft also offers enterprise cloud storage with Microsoft Azure Storage. Cloud storage provides several benefits:

 -  Easy access anywhere to data such as photos, music, and documents.
 -  Automatic backup of important files.
 -  Synchronizing favorites and other settings across devices.

#### OneDrive

OneDrive offers the benefits of making files accessible by any device, while offering a seamless end user experience in the desktop client. OneDrive is covered in more detail in the next topic.

#### Azure Storage

Microsoft Azure Storage is a cloud storage solution that developers and IT professionals use to build applications. Azure Storage saves data in the cloud. You can access Azure Storage by using any type of device and by using any type of application, from the smallest app to applications with terabytes of data.

Azure Storage can handle four types of storage:

 -  Blob storage stores any type of text or binary data. This includes documents and media files.
 -  Table storage stores structured datasets. Table storage is a NoSQL key-attribute data store.
 -  Queue storage provides messaging for workflows. Communication between different components of cloud services is also one of the uses of queue storage.
 -  File storage uses the standard SMB protocol. Azure virtual machines and cloud services can share file data with file storage. On-premises applications can also access file data in a share via file storage.
