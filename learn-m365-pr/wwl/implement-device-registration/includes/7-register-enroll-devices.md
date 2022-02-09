After all prerequisites are met, you can enable Device Registration on a device. Any user with domain credentials can enroll a device, and each device can be enrolled multiple times, once per user who uses that device. To enroll the device, perform the following procedure:

1.  Open the **Start** menu, select the **Settings** option, and then select **Accounts**.
2.  On the **Accounts** page, select **Access work or school**.
3.  On the **Access work or school** page, select **Connect**.
4.  Enter the user ID with which you want to register the device. The user ID looks the same as a user’s email address and is composed of the user’s sign-in name, the at sign (@), and a domain suffix. Domain administrators refer to user ID as the user principal name (UPN). When performing a device registration, the computer tries to resolve the Enterprise registration name, and verifies that the SSL certificate is trusted and still valid.
5.  Enter user domain credentials. The device can be a workgroup member, but the user must have a domain account to enable Device Registration on the device.
6.  Once the device is enabled for Device Registration, Device Registration Service creates a domain object for the joined device in the Registered Devices AD DS container, and the user is provided with a certificate for client authentication.

You must configure a device for which you want to enable Device Registration with network settings to resolve company server names. You also must configure the device to trust the company CA. If your company uses a publicly trusted certificate on the server with the Enterprise registration address, you need not configure the device. If your company uses certificates issued by a private CA, you must export a certificate from your root CA, and then import it in the trusted root store on your device.
