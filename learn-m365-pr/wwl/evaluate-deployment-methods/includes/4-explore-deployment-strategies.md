You can use a number of different methods to install Windows clients. However, regardless of the method, the image-based nature of the installation process and the desired result—a properly functioning Windows device—remain consistent. Determining which method to use and how to best implement that method are important parts of the planning process for a Windows installation.

In this topic, you will learn to analyze the reasons for using certain installation methods and implement those methods. You will also learn about the new provisioning method introduced in Windows 10 that you can use to customize an existing Windows installation with a provisioning package.

### High-touch Deployment

The high-touch with retail media deployment strategy is suitable for small organizations that do not have information technology (IT) staff, or have IT staff members without deployment experience. Such organizations typically have fewer than 100 client computers. This strategy is the simplest way to deploy Windows. Insert the Windows media and run the setup program. It is a manual installation that requires you to answer each prompt in the setup program.

Organizations with 100-200 client computers should consider high-touch with a standard image. This strategy involves the creation of a standard image, by using the available tools in the Windows ADK, which you can customize. It requires an IT professional with imaging knowledge and is ideal for small or distributed networks with minimal configuration requirements.

### Lite-touch Deployment

The Lite-touch Installation (LTI) deployment strategy is suitable for medium-sized organizations with 200–500 client computers. This strategy uses management tools such as Microsoft Deployment Toolkit (MDT) or Microsoft Intune. It is an easier deployment strategy, because Administrators use a centrally managed console to automate the delivery of the OS, configurations, and applications. MDT also requires minimal infrastructure and Intune is a cloud-based solution.

:::image type="content" source="../media/mdt_windows10-ecac9a65-ec7ae4ac.png" alt-text="Example of Microsoft Deployment Toolkit UI":::


### Zero-touch Deployment

The Zero-touch Installation (ZTI) deployment strategy is suitable for large organizations that typically have more than 500 client computers. This deployment strategy uses MDT and/or Intune together with Microsoft Endpoint Configuration Manager to deliver a more streamlined, fully automated deployment that does not require user interaction.

:::image type="content" source="../media/task_sequence-2073446e-ab778466.png" alt-text="Example of the Task Sequence Editor":::


### Bring Your Own Device

The Bring Your Own Device (BYOD) deployment refers to deploying configurations and applications to devices that are not owned by the organization, typically a user-owned device. Using a smartphone to access work e-mail is the most common example. With the concept of a mobile workforce becoming more common, employees using their home computer to work on, or students using their personal laptops at school has increased the need for IT to support BYOD on a variety of devices.

Mobile Device Managers (MDM) such as Microsoft Intune can be used to manage personally owned devices such as phones, tablets, and computers. Intune offers the ability for users to enroll their devices, access applications and meet compliance requirements, without giving up administrative control of their own device. Like Configuration Manager, Intune can also manage organization owned devices and the two can be leveraged together to create a unified endpoint management solution.
