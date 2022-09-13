You can use several methods to install Windows clients. However, regardless of the method, the image-based nature of the installation process and the desired result—a properly functioning Windows device—remain consistent. Determining which method to use and how to best implement that method is an essential part of the planning process for a Windows installation.

In this topic, you'll learn to analyze the reasons for specific installation methods and implement those methods. You'll also learn about the new provisioning method introduced in Windows 10 that you can use to customize an existing Windows installation with a provisioning package.

### High-touch Deployment

The high-touch retail media deployment strategy is suitable for small organizations that don't have information technology (IT) staff or IT staff members with no deployment experience. Such organizations typically have fewer than 100 client computers. This strategy is the simplest way to deploy Windows. Insert the Windows media and run the setup program. It's a manual installation that requires you to answer each prompt in the setup program.

Organizations with 100-200 client computers should consider high-touch with a standard image. This strategy involves the creation of a standard image by using the tools in the Windows ADK, which you can customize. It requires an IT professional with imaging knowledge and is ideal for small or distributed networks with minimal configuration requirements.

### Lite-touch Deployment

The Lite-touch Installation (LTI) deployment strategy is suitable for medium-sized organizations with 200–500 client computers. This strategy uses management tools such as Microsoft Deployment Toolkit (MDT) or Microsoft Intune. It's a more straightforward deployment strategy because Administrators use a centrally managed console to automate the delivery of the OS, configurations, and applications. MDT also requires minimal infrastructure, and Intune is a cloud-based solution.

:::image type="content" source="../media/microsoft-deployment-toolkit-windows10-ecac9a65-569f4d30.png" alt-text="Example of Microsoft Deployment Toolkit UI":::


### Zero-touch Deployment

The Zero-touch Installation (ZTI) deployment strategy is suitable for large organizations with over 500 client computers. This deployment strategy uses MDT and/or Intune together with Microsoft Endpoint Configuration Manager to deliver a more streamlined, fully automated deployment that doesn't require user interaction.

:::image type="content" source="../media/task-sequence-2073446e-165d9b56.png" alt-text="Example of the Task Sequence Editor":::


### Bring Your Own Device

The Bring Your Own Device (BYOD) deployment refers to deploying configurations and applications to devices the organization doesn't own, typically a user-owned device. Using a smartphone to access work e-mail is the most common example. With the concept of a mobile workforce becoming more prominent, employees using their home computers to work or students using their personal laptops at school has increased the need for IT to support BYOD on various devices.

You can use Mobile Device Managers (MDM) such as Microsoft Intune to manage personally owned devices such as phones, tablets, and computers. Intune allows users to enroll their devices, access applications, and meet compliance requirements without giving up administrative control of their own devices. Like Configuration Manager, Intune can also manage organization-owned devices and be used to create a unified endpoint management solution.
