Windows supports file compression on an individual-file basis on NTFS-formatted volumes only. The file compression algorithm is a lossless compression algorithm, which means that compressing and decompressing a file results in no data loss. This is different from other types of compression algorithms, where compression and decompression always cause some data loss.

### Configuring compression

You set compression from the properties of a file or folder on the General tab. You select Advanced and set or clear the compression attribute. You can also configure compression from the command line by using the compact command.

#### Features of NTFS folder compression

NTFS compression, which is available on volumes that use NTFS, has the following features and limitations:

 -  Compression is an attribute of a file or folder.
 -  Volumes, folders, and files on an NTFS volume are either compressed or uncompressed.
 -  New files created in a compressed folder are compressed by default.
 -  The compression state of a folder does not necessarily reflect the compression state of the files within that folder. For example, you can compress a folder without compressing its contents, and you can compress some or all of the files in a compressed folder.
 -  NTFS compression works with NTFS-compressed files without decompressing them because they are decompressed and recompressed without user intervention:
 -  When you open a compressed file, the Windows operating system automatically decompresses it for you.
 -  When the file closes, the Windows operating system compresses it again.
 -  NTFS-compressed file and folder names display in a different color, by default, to make them easier to identify.
 -  NTFS-compressed files and folders only remain compressed while an NTFS volume is storing them.
 -  You cannot encrypt an NTFS-compressed file.
 -  The compressed bytes of a file are not accessible to applications, which see only the uncompressed data:
 -  Applications that open a compressed file can perform tasks on it as if the file was not compressed.
 -  If you copy compressed files to a file allocation table (FAT) or Resilient File System (ReFS) volume, the copy of the file will not be compressed because those file systems do not support NTFS compression.

### Copying and moving compressed files and folders

When you move or copy compressed files and folders, the method and destination can change the compression state. The following list explains what happens when you move and copy files:

 -  When you copy a file or folder within an NTFS partition, the file or folder inherits the compression state of the target folder. For example, if you copy a compressed file or folder to an uncompressed folder, the file or folder is uncompressed automatically.
 -  When you move a file or folder within an NTFS partition, the file or folder retains its original compression state. For example, if you move a compressed file or folder to an uncompressed folder, the file remains compressed.
 -  When you move a file or folder between NTFS partitions, the file or folder inherits the target folder’s compression state. Because Windows treats a move between partitions as a copy followed by a delete operation, the files inherit the target folder’s compression state.
 -  When you copy a file to a folder that already contains a file of the same name, the copied file takes on the compression attribute of the target file, regardless of the compression state of the folder.
 -  Compressed files that you copy to a FAT partition are uncompressed because FAT volumes do not support compression. However, when you copy or move files from a FAT partition to an NTFS partition, they inherit the compression attribute of the folder into which you copy them.
 -  When you copy a file, NTFS calculates disk space based on the uncompressed file’s size. This is important because files are uncompressed during the copy process, and the system must ensure there is enough space. If you copy a compressed file to an NTFS partition that does not have enough space for the uncompressed file, an error message notifies you that there is not enough disk space.

### **Compressed (zipped) folder**

 -  In Windows, you can combine several files and folders into a single compressed folder by using the Compressed (zipped) Folder feature. Use this feature to share a group of files and folders with others, without sending individual files and folders.
 -  Files and folders that you compress by using the Compressed (zipped) Folder feature can compress on both FAT-formatted and NTFS-formatted volumes. A zipper icon identifies files and folders that you compress by using this feature.
 -  You can open files directly from these compressed folders, and you can run some of these programs directly from compressed folders without uncompressing them. Files in compressed folders are compatible with other file compression programs and files. You also can move compressed files and folders to any drive or folder on your computer, the Internet, or your network.
 -  Compressing folders by using Compressed (zipped) Folder does not affect a computer’s overall performance. Central processing unit (CPU) utilization increases only when you use Compressed (zipped) Folder to compress a file. Compressed files take up less storage space, and you can transfer them to other computers more quickly than uncompressed files. You can work with compressed files and folders the same way you work with uncompressed files and folders.

**Comparing zipped folder compression and NTFS folder compression**

 -  You should be aware of the differences between zipped folder compression and NTFS folder compression. A zipped folder is a single file inside which Windows allows you to browse. Some applications can access data directly from a zipped folder, while other applications require that you first unzip the folder contents before the application can access the data.
 -  In contrast, NTFS compression compresses individual files within a folder. Therefore, NTFS compression does not affect data access as zipped folders do, because it occurs at the individual file system level and not the folder level. Additionally, zipped folders are useful for combining multiple files into a single email attachment, whereas NTFS compression is not.
 -  File and folder compression that uses the Send To Compressed (zipped) Folder command is different from NTFS file and folder compression:
 -  For selected files or folders, the Send To Compressed (zipped) Folder command compresses the selected content into a portable zip file. The original file or folder does not change, and a new, compressed zip file is created.

NTFS compression does not create a second, compressed zip-type file. Instead, it actually reduces the size of the selected file, folder, or volume by compressing its content.
