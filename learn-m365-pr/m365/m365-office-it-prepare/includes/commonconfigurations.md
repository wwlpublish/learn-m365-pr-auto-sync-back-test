In this unit, we'll explain relevant network considerations, language configurations, policies and preferences, and application architectures.

## Network optimizations for software updates

You can update general purpose devices using automatic updates over the Internet. You can configure Office software updates to use Delivery Optimization in Windows 10. This will minimize Internet and VPN traffic while ensuring your Office installation is kept up-to-date. Delivery Optimization uses peer-to-peer delivery to minimize internet bandwidth usage. You can load updates to a small number of devices on a shared network. Then other connected devices use their network peers to discover and load the updates from them. This prevents every device from individually downloading updates from the internet, saving significant bandwidth.

If your organization uses Configuration Manager infrastructure, you can configure peer cache to reduce internal network or VPN traffic to remote distribution points. With peer cache in Configuration Manager, you identify well-connected client PCs on a local network to cache deployment source. In this case Office uses Configuration Manager as the software update mechanism. Update traffic is directed to the nearest peer cache device on the network in order to save bandwidth.

## Language configurations

If your organization has devices and users with multiple languages, you can configure your Office deployments for full language support, partial language support, or proofing language support as needed. You configure this in the configuration XML file and can edit it using the Office Customization Tool, or as part of the updated Office application packaging process in Configuration Manager.
  
> [!TIP]
> A common mistake made in multi-lingual environments is to build a single package that contains most or all of the languages used in the organization. If you add too many languages, the Office package can quickly exceed several gigabytes.

One advantage of installing from the internet-based CDN instead of using Configuration Manager is that you can use the **match OS** property. With the **match OS** property, you can  download language-specific files dynamically as Office is installed.

## Policies and preferences

Microsoft 365 Apps and volume licensing editions of Office 2019 support Active Directory Group Policy management. New versions continue to use the Office 2016 ADMX templates. Additionally, you can configure install-time policy preferences with the same versions of Office by using the new Office Customization Tool or as part of the Installer process in Configuration Manager. These are policy preferences and not enforced policies - in many cases your users can change or modify the configurations post-installation.

Microsoft 365 Apps has a new policy enforcement option - the Office Cloud Policy Service. When a user signs into their account, if Microsoft 365 Apps is installed on their device, the service enforces the policies you've configured. These policies work regardless of how Microsoft 365 Apps was installed and whether or not the user's PC is domain-joined or managed using other systems.

To configure policies with the Office Cloud Policy Service, you add users to a group, then assign that group to configured policies. You can also get to the Office Cloud Policy Service experience from the Office Customization Tool link below under **Learn more.** To use this capability, you need to authenticate with an administrator account to set policies and assign them to groups.

> [!NOTE]
> The policies set in the Office Cloud Policy Service are currently limited to **User Configuration** policies and don't include **Computer Configuration** policies.

## Visio and Project considerations

If any of your users have Visio or Project installed, there are a few additional things to be aware of:

- Volume licensing versions of Visio or Project can coexist on the same computer with subscription activation versions of Microsoft 365 Apps.
- Visio 2019 and Project 2019, as well as Visio Online and Project Online applications, are packaged using Click-to-Run. Because of codependencies and shared components in Office, they must be at an equivalent version level. For example, if you have Visio 2019, and you want to also use Office, you need Office 2019 or Microsoft 365 Apps.
- Click-to-Run packaged versions of Visio or Project must use the same update channel as other Click-to-Run Office features on the PC.

## Office installation architecture

The installation architecture for all Office applications (including Visio and Project) must match that of any other Office application on the same device, whether that is 32-bit or 64-bit. If the Office installation process detects another architecture, the installation won't proceed. Office COM add-ins must also match the architecture of the installed version of Office. If you want to move to 64-bit versions of Office, you must replace native 32-bit COM add-ins with the equivalent 64-bit COM add-ins.

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Office Customization Tool](https://config.office.com)
