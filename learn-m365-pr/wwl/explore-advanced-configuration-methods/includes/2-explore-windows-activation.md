All Windows editions require activation. Activation confirms the status of a Windows product and ensures that the product key has not been compromised. The activation process links the software�s product key to a particular installation of that software on a device. Windows client does not have a grace period. You must activate Windows immediately upon installation. Failure to activate a Windows operating system prevents users from completing customization. If you want to evaluate Windows, Microsoft provides a separate evaluation edition that is available as an .iso image file.

Windows has three main methods for activation:<br>

 -  **Retail**. Any Windows product purchased at a retail store comes with one unique product key that you type in during product installation. You use the product key to complete activation after installing the Windows operating system.
 -  **OEM**. OEM system builders typically sell computer systems that include a customized build of Windows. You can perform OEM activation by associating the Windows operating system to the computer system BIOS, which means that you cannot transfer this license to another computer.
 -  **Microsoft Volume Licensing (volume activation)**. Microsoft Volume Licensing is a series of software licensing programs that are tailored to the size and purchasing methods of your organization. Volume customers set up volume licensing agreements with Microsoft. These agreements include Windows upgrade benefits and other benefits related to value-added software and services. Microsoft Volume Licensing customers use Volume Activation Services to assist in activation tasks, which consist of Active Directory�based activation, KMS, and multiple activation key (MAK) models.

You can view the Windows activation status either on the System properties page, or by running the following command at a command prompt:

`cscript C:\windows\system32\slmgr.vbs �dli`

When you activate your Windows Home and Pro editions, Windows generates a unique ID based on the hardware present in your computer. This ensures that you cannot use your Windows license on another computer. If you change a significant amount of hardware, you could have to reactivate Windows.

If you plan to implement KMS, MAK, or Active Directory�based activation, you must consider certain aspects, limitations, and requirements. The following factors are applicable for each of these three volume activation methods.<br>

## MAK activation considerations

A MAK also allows permanent activation of computers that are isolated from the KMS or are part of an isolated network that does not have enough computers to use the KMS. Activating using MAK is similar to activation with a retail key, except that a MAK is valid for activating multiple computers. Each MAK can be used a specific number of times. The VAMT can assist in tracking the number of activations that have been performed with each key and how many remain.

When selecting MAK activation, keep in mind the following considerations:

 -  MAK activation is for computers that rarely or never connect to the corporate network, and for environments where the number of computers that need activation does not meet the KMS activation threshold.
 -  You can use MAK to activate computers in one of two ways:
     -  MAK Independent. This activation method requires that each computer connect independently and activate with Microsoft over the Internet or by telephone. This method is best suited for computers within an organization that do not have a connection to the corporate network.
     -  MAK Proxy. This activation method enables a centralized activation request on behalf of multiple computers with one connection to Microsoft. This method is suitable for environments where security concerns restrict direct access to the Internet or to the corporate network.

## KMS activation considerations

Installing a KMS host key on a computer running Windows allows you to activate other computers running Windows clients against this KMS host. Clients locate the KMS server by using resource records in DNS, so some configuration of DNS may be required. This scenario can be beneficial if your organization uses volume activation for clients and MAK-based activation for a smaller number of servers. To enable KMS functionality, a KMS key is installed on a KMS host; then, the host is activated over the Internet or by phone using Microsoft activation service

When working to implement KMS activation, keep in mind the following considerations:

 -  Client computers that are not activated attempt to connect with the KMS host every two hours.
 -  To stay activated, client computers must renew their activation by connecting to the KMS host at least once every 180 days.
 -  After activation, client computers attempt to renew their activation every seven days. After each successful connection, the expiration extends to the full 180 days.
 -  KMS activation requires at least 25 computers to run Windows Client for activation to be successful.
 -  Client computers connect to the KMS host for activation by using anonymous remote procedure calls (RPCs) over TCP/IP and by using default port 1688. You can configure this port information. The connection is anonymous, enabling workgroup computers to communicate with the KMS host. You might need to configure the firewall and the router network to pass communications for the Transmission Control Protocol (TCP) port that you have configured.

## Active Directory�based activation considerations

Active Directory-Based Activation (ADBA) enables enterprises to activate computers through a connection to their domain. Many companies have computers at offsite locations that use products that are registered to the company. Previously these computers needed to either use a retail key or a Multiple Activation Key (MAK), or physically connect to the network in order to activate their products by using Key Management Services (KMS). ADBA provides a way to activate these products if the computers can join the company�s domain. When the user joins their computer to the domain, the ADBA object automatically activates Windows installed on their computer, as long as the computer has a Generic Volume License Key (GVLK) installed. No single physical computer is required to act as the activation object, because it is distributed throughout the domain.

When working with Active Directory�based activation, keep in mind the following considerations:

 -  You do not need an additional host server with Active Directory�based activation. Your existing domain controllers can support activation clients with the following limitations:
     -  You cannot configure Active Directory�based activation on read-only domain controllers.
     -  You cannot use Active Directory�based activation with non-Microsoft directory services.
     -  To store activation objects, the Active Directory schema must be at a Windows Server 2012 R2 or newer version.
 -  Active Directory�based activation is forest wide, and you only need to implement it once, even if the forest contains multiple domains.
 -  There are no threshold limits that must be met before computers can be activated by using Active Directory�based activation.
