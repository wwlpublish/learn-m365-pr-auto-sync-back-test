In the past, organizations had to activate Windows manually or set up an on-premises infrastructure for activation, such as the Key Management Service (KMS). This traditional process continues to work with Windows 10. However, Windows 10 version 1703 and newer includes a new capability, Subscription Activation.

This module introduces you to Subscription Activation, which enables an automatic, online upgrade from Windows 10/11 Professional to Windows 10/11 Enterprise. It also provides automatic activation when an Azure AD user with an assigned Windows 10/11 Enterprise E3 or E5 license signs in. This activation happens with no keys and no reboots.

The module reviews the benefits and advantages that Windows 10 Enterprise Subscription Activation has over traditional activation With Subscription Activation, organizations no longer have to worry about activation keys. They just let Azure AD assign Windows 10 licenses to users or groups.

This module also examines why Azure AD is used for upgrading the device to Windows 10 Enterprise and for activation. Organizations no longer need to track used Windows 10 licenses, because Azure AD automatically tracks them. With Subscription Activation, organizations don’t need any on-premises activation infrastructure. Windows 10/11 devices can be activated wherever they are, as long as they have Internet connectivity.

:::image type="content" source="../media/traditional-versus-subscription-activation-3f2f273f.jpg" alt-text="graphic showing comparison of traditional versus subscription activation":::


In this module, you'll learn how to design a Windows 10/11 Subscription Activation strategy. This strategy should cover three components. You'll begin by exploring Windows 10/11 Enterprise E3 availability through the Cloud Service Provider channel. Windows 10/11 Enterprise E3 in CSP provides a flexible, per-user subscription for small- and medium-sized companies.

You'll then learn how to configure Virtual Desktop Access (VDA) for automatic subscription activation on virtual machines. Users sometimes use Remote Desktop to connect to a remote Windows 10/11 computer. An example of this scenario is when users connect to Azure virtual machines. Users must have VDA rights to be allowed to connect to the remote Windows 10/11 computer. This module examines VDA in two scenarios - when organizations own their own virtual machines, and when their virtual machines are owned and hosted by another company.

Finally, you'll analyze the different ways to deploy Windows 10 Enterprise licenses. You'll learn how licenses can be obtained by an organization, and how those licenses can then be assigned to users.

After completing this module, you'll be able to:

 -  Describe how Windows 10/11 Enterprise E3 subscriptions can be purchased through the Cloud Service Provider channel.
 -  Configure Virtual Desktop Access for automatic subscription activation on virtual machines.
 -  Explain how Windows 10/11 Enterprise licenses can be deployed automatically and without device restart.
