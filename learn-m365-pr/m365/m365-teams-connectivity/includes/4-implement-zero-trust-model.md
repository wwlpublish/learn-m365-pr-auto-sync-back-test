In the modern business environment, there are many personal and company-owned computers and devices that move in and out of your perimeter network. Also, Microsoft 365 and Microsoft Teams performance require direct connections to the cloud. Traditional security systems built on firewalls and proxy servers have difficulty fully protecting such an environment and might result in loopholes that malicious users can exploit. They also often prevent direct connections and degrade performance.

In your bicycle manufacturing company, the security team in the IT department has traditionally used edge devices such as proxy servers and firewalls to enforce security within the company network. After several meetings with you, they have become concerned that the network design changes you want to make to support Microsoft 365 and Microsoft Teams will undermine their security infrastructure. You want to provide a new set of security principles that will protect the new cloud-based systems, and both on-premises and mobile users who may bring their own devices to work.  

Let's examine a more modern set of security principles that can address these issues and how they apply to Microsoft 365 and Teams.

## Zero Trust principles

Traditionally, IT security teams have implemented security at the edge of their network by using technologies such as firewalls and proxy servers. These systems check incoming and outgoing traffic and can filter them based on the IP properties, content, source, destination, and so on. This model is no longer satisfactory because users bring their own devices, such as phones, tablets, and computers, to work and want to use them to access your systems from within your premises and from home, customer sites, internet cafés, and other locations.

Another problem with the traditional security approach is that it doesn't fit with the Microsoft 365 principles that you have learned about in the previous modules. Edge security systems are likely to cause network hairpins and prevent local egress for example. This model is likely to lower your Microsoft 365 and Teams performance.

To address these concerns, Microsoft has developed a new security paradigm for modern business environments called the Zero Trust model.

### A Zero Trust network

In a *cloud-first* and *mobile-first* world, networks can't rely on perimeter-based security. With the bring your own device (BYOD) model, security has become more complex, and more important. Networks that rely on traditional defenses risk a single breach that puts their whole network at risk.

The Zero Trust network removes the idea of a perimeter that can be secured, and instead relies on device and user trust claims to access organizational data and resources.

A Zero Trust network model typically has:

- An identity provider to keep track of users and user-related information
- A device directory to maintain a list of devices that have access to corporate resources, including information such as type of device, integrity, and so on
- A policy evaluation service to determine if a user or device conforms to the relevant policy
- An access proxy that grants or denies access to an organizational resource

 :::image type="content" source="../media/4-zero-trust.png" alt-text="Zero Trust principles in network design":::

A solution based on the Zero Trust network model, configured with the effective policies for user and device trust, can help prevent stolen network credentials from being used to access a network.

Using gated access to resources with dynamic trust decisions allows you to grant access to certain assets from any device. At the same time, you can restrict access to high-value assets on other devices.

If attackers compromise a single device, Zero Trust prevents them from "hopping" across the network using stolen credentials. Only the initial device is compromised.

### Zero Trust Microsoft 365 and Azure

Microsoft Azure Active Directory Conditional Access combines data from several sources to evaluate the risk to security, including:

- User role
- Group membership
- Device health and compliance
- Mobile applications
- Location
- Sign-in risk

These considerations are used to decide whether to **allow access**, **deny access**, or **control access** with additional authentication challenges such as multifactor authentication, Terms of Use, or access restrictions.

Conditional access works robustly with any application configured for access with Azure Active Directory.

## Adopting a Zero Trust security model

The Zero Trust model is a significant change from the traditional approach and requires time and planning to implement correctly. You probably won't be able to complete this implementation in a single day. Instead, you must gradually adopt Zero Trust implementation steps and apply them to key applications over time.

Start by implementing Zero Trust principles for key Microsoft 365 workloads, such as Exchange Online, SharePoint Online, and Microsoft Teams. These are well trusted, widely used, and will realize the highest return on your investment in Zero Trust. Less important applications and workloads can continue to connect through edge security systems and suffer from suboptimal performance, until you can reconfigure them.

## Learn more

- [Building Zero Trust networks with Microsoft 365](https://www.microsoft.com/security/blog/2018/06/14/building-zero-trust-networks-with-microsoft-365)
