A Zero Trust network strategy requires a shift in approach to network security. Small steps that are easily implemented can have a big impact. When you consider a Zero Trust strategy for your network, focus on three key areas:

- Network segmentation
- Threat protection
- Network encryption

## Network segmentation

Network segmentation is the process of dividing up your network into smaller, discrete zones, and limiting who has access to each segment. This can mitigate the effects of a breach, limit the amount of damage a cybercriminal can inflict, and reduce the ease with which they might move laterally across your network.

Let’s look at how this might apply to your home. It’s composed of a number of rooms—the lounge, kitchen, dining room, bathrooms, bedrooms, and so on. In a traditional security model, after someone has got through the front door, they can visit each of the rooms as they want.

The diagram below shows a simplified rendering of a flat network. When an attacker gets onto your network, they can go anywhere.

:::image type="content" source="../media/flat-network.png" alt-text="Diagram showing a simplified flat network structure with a single firewall protecting three servers.":::

However, using segmentation, you can make sure that each room has a door that’s always locked and requires a unique key to unlock. If someone were to get into the house, the places they can visit are severely limited and require more effort, and time to access.

The diagram below shows a simplified rendering of a segmented network. The cybercriminal will have to attack each segment in turn to access your data.

:::image type="content" source="../media/segmented-network.png" alt-text="Diagram showing the simplified flat network now transformed to a segmented network, with three segments and a server within each.":::

Network segmentation creates boundaries around critical operations or assets, in much the same way as you'd put your finance team in their own office. It improves the integrity of your network assets by ensuring that, even if your network is breached, the attacker can't reach the segmented areas.

When there's an attack, this strategy helps to prevent the cybercriminal from moving across the network – called lateral movement—because each segment is integrated with a Zero Trust strategy, and access won’t be granted without authentication and authorization.

## Real-time threat protection

As cyberattacks get more sophisticated, there’s a need to use threat intelligence to help correlate warnings and threat indicators, and thereby prioritize responses to an attack. To achieve this, you need to deploy sophisticated software tools that monitor, in real time, all activities that occur on and across your network. These tools rely on the very latest data from multiple sources in your network to identify whether the traffic is good or bad.

A robust threat protection solution must, therefore, scan all traffic looking for malicious payloads, and unusual device and user behavior.

Using extended detection and response (XDR) tools is pivotal in providing the necessary end-to-end visibility and automated response to protect assets, remediate threats, and support investigations. A typical XDR solution uses threat intelligence to classify each activity as either known or unknown malware, or a valid operation. XDRs also monitor user activity—for example, user login events—to understand the geographical location of the user, the applications they typically access, and the device they’re using to accurately pinpoint threats.

Typically, threats fall into two broad categories: known and unknown attacks.

- **Known attacks** are those that have been previously discovered by other sources. Each attack has a unique signature, which enables it to be identified. By keeping your threat detection tools up-to-date, you'll spot these attacks and mitigate them before they can do any damage.
- **Unknown attacks** are threats and attacks that don’t match any known signatures. These are called zero-day attacks. The ability of your threat protection system to identify these attacks depends on it knowing what normal traffic and behaviors are, and what aren't.

Using these tools empowers security teams, giving them the necessary information required to detect, deter, and defeat the most critical attacks and risks, both internally and externally.

## Restrict access using encryption

Data is at the heart of everything we do, whether it’s pictures of your loved ones, the contents of your online shopping basket, or customer financial records. Networks provide the means by which we can access this data, but they're also open to abuse by cybercriminals.

One of the best ways to keep data safe is to ensure that it's encrypted. Encryption is the process of rendering a message unintelligible to anyone who doesn’t have the right key to decode it.

Encrypting your data applies not only to data that is stored on a device, whether on-premises, in the cloud, or on an external drive—known as data at rest—but also to data that is sent across your network, known as data in transit.

One of the key objectives when applying a Zero Trust strategy to the network is to ensure that any app that accesses data encrypts it. You should also consider encrypting all data that moves from your on-premises networks to the cloud or the internet. There are many tools on the market that can seamlessly encrypt all communications between user devices and the apps they're using, and the source of data. If you're developing your own applications, encryption of all data in transit is essential.
