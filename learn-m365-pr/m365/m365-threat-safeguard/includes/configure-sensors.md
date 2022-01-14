At a high level, the following steps are required to enable Microsoft Defender for Identity:

1. Create an instance on Microsoft Defender for Identity management portal.
2. Specify an on-premises AD service account in the Microsoft Defender for Identity portal.
3. Download and install the sensor package.
4. Install the Microsoft Defender for Identity sensor on all domain controllers.
5. Integrate your VPN solution (optional).
6. Exclude the sensitive accounts you've listed during the design process.
7. Configure the required permissions for the sensor to make SAM-R calls.
8. Configure integration with Microsoft Defender for Cloud Apps.
9. Configure integration with Microsoft 365 Defender (optional).

The following diagram shows the Microsoft Defender for Identity architecture. In this unit, we will discuss how to configure the Microsoft Defender for Identity Sensor.  

:::image type="content" source="../media/defender-identity-architecture-topology.png" alt-text="Microsoft Defender for Identity architecture" border="false":::

Installed directly on your domain controllers, the Microsoft Defender for Identity sensor accesses the event logs it requires directly from the domain controller. After the logs and network traffic are parsed by the sensor, Microsoft Defender for Identity sends only the parsed information to the Microsoft Defender for Identity cloud service (only a percentage of the logs are sent).

The Microsoft Defender for Identity sensor has the following core functionality:

- Capture and inspect domain controller network traffic (local traffic of the domain controller)
- Receive Windows events directly from the domain controllers
- Receive RADIUS accounting information from your VPN provider
- Retrieve data about users and computers from the Active Directory domain
- Perform resolution of network entities (users, groups, and computers)
- Transfer relevant data to the Microsoft Defender for Identity cloud service

The Microsoft Defender for Identity sensor has the following requirements:

- KB4487044 is installed on Server 2019. Microsoft Defender for Identity sensors already installed on 2019 servers without this update will be automatically stopped.
- The Microsoft Defender for Identity sensor supported domain controller OS list:
  - Windows Server 2008 R2 SP1 (not including Server Core)
  - Windows Server 2012
  - Windows Server 2012 R2
  - Windows Server 2016 (including Windows Server Core but not Windows Nano Server)
  - Windows Server 2019 (including Windows Core but not Windows Nano Server)
- The domain controller can be a read-only domain controller (RODC).
- 10 GB of disk space is recommended. This includes space needed for the Microsoft Defender for Identity binaries, Microsoft Defender for Identity logs, and performance logs.
- The Microsoft Defender for Identity sensor requires a minimum of two cores and 6 GB of RAM installed on the domain controller.
- Power option of the Microsoft Defender for Identity sensor to high performance.
- Microsoft Defender for Identity sensors can be deployed on domain controllers of various loads and sizes, depending on the amount of network traffic to and from the domain controllers, and the amount of resources installed.
- When running as a virtual machine, dynamic memory or any other memory ballooning feature is not supported.

### To install the Microsoft Defender for Identity sensor

1. Download and extract the sensor file. Run **Microsoft Defender for Identity sensor setup.exe** and follow the setup wizard.
2. On the Welcome page, select your language and click **Next**.

   ![Install steps: Choose Language](../media/install-choose-language.png)

3. The installation wizard automatically checks if the server is a domain controller or a dedicated server. If it's a domain controller, the Microsoft Defender for Identity sensor is installed. If it's a dedicated server, the Microsoft Defender for Identity standalone sensor is installed. For example, for a Microsoft Defender for Identity sensor, the following screen is displayed to let you know that a Microsoft Defender for Identity sensor is installed on your dedicated server:

   ![Install steps: Determine server type](../media/install-server-type.png)

4. Under **Configure the sensor**, enter the installation path and the access key, based on your environment:

   - **Installation path**: The location where the Microsoft Defender for Identity sensor is installed. By default, the path is **%programfiles%\Microsoft Defender for Identity sensor**. Leave the default value.
   - **Access key**: Retrieved from the Microsoft Defender for Identity portal.

    ![Install steps: Configure the sensor](../media/install-configure-sensor.png)

5. Click **Install**.

After the Microsoft Defender for Identity sensor is installed, do the following to configure Microsoft Defender for Identity sensor settings:

1. Click **Launch** to open your browser and sign into the Microsoft Defender for Identity portal.
2. In the Microsoft Defender for Identity portal, go to **Configuration**. Under the System section, select **Sensors**.

   [![Install steps: Select sensors in Microsoft Defender for Office 365 portal](../media/install-select-sensors.png)](../media/install-select-sensors-magnify.png#lightbox)

3. Click on the sensor you want to configure and enter the following information:

   - **Description**: Enter a description for the Microsoft Defender for Identity sensor (optional).
   - **Domain Controllers** (FQDN) (required for the Microsoft Defender for Identity standalone sensor, this can't be changed for the Microsoft Defender for Identity sensor): Enter the complete FQDN of your domain controller and click the **plus sign** to add it to the list. For example, dc01.contoso.com.

     The following information applies to the servers you enter in the Domain Controllers list:

     - All domain controllers whose traffic is being monitored via port mirroring by the Microsoft Defender for Identity standalone sensor must be listed in the Domain Controllers list. If a domain controller isn't listed in the Domain Controllers list, detection of suspicious activities might not function as expected.
     - At least one domain controller in the list should be a global catalog. This enables Microsoft Defender for Identity to resolve computer and user objects in other domains in the forest.

   - **Capture Network adapters** (required):
     - For Microsoft Defender for Identity sensors, all network adapters that are used for communication with other computers in your organization.
     - For Microsoft Defender for Identity standalone sensor on a dedicated server, select the network adapters that are configured as the destination mirror port. These network adapters receive the mirrored domain controller traffic.

   ![Install steps: Enter information to configure sensor](../media/install-configure-sensor-info.png)

4. Click **Save**.
