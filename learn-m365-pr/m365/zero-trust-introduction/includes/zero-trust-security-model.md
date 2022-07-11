Zero Trust is an end-to-end security strategy that monitors and controls the six main pillars of security: identity, endpoints, applications, network, infrastructure, and data.

:::image type="content" source="../media/overview-of-zero-trust.png" alt-text="Diagram showing an overview of Zero Trust and its security pillars – identity, endpoints, applications, network, infrastructure, and data." border="false":::

The Zero Trust approach addresses the security concerns that emerge due to the evolving digital landscape. Today, nearly every organization has a mobile, remote or hybrid workforce, cloud applications, data stored in different environments, and devices enrolled from various locations. In the absence of a robust security model, all these factors can inadvertently lead to a major security breach.

In practice, the “trust no one and verify everything” rule suggests that every request, device, or user must **not** be trusted and should be treated as a potential threat until verified by strong authentication methods, before allowing access to the network. This also means that users and devices are _only_ allowed access to the specific applications or data that they need.

## Zero Trust principles

> [!div class="centered"]
> :::image type="content" source="../media/key-principles-of-zero-trust.png" alt-text="Diagram showing the key principles of Zero Trust - verify explicitly, apply least privilege access, and assume breach." border="false":::

The Zero Trust security framework operates on key principles that are applied across the security infrastructure to provide multiple layers of defense. The underlying principles of a Zero Trust framework are:

- **Verify explicitly**: The Zero Trust security model requires strict identity verification for _every_ user and device attempting to access resources. With Zero Trust, the identity verification of users and devices is a continuous process, often at multiple levels. This ensures the constant monitoring and validating of _who_ can access _what_.
- **Use least privilege access**: The principle of least privilege access ensures that user access is minimized with Just-In-Time (JIT) and Just-Enough-Access (JEA). This means only granting access to systems and applications to authorized users for specific tasks for a minimum time.
- **Assume breach**: This principle assumes that every request from a user or device to access your systems and data has come from a cybercriminal. It embodies a deny-all approach and uses real-time monitoring to assess every request against known behaviors to limit and control access. _Assume breach_ is the mindset of creating the necessary segregation of access to contain the damage to a small area, and in doing so, minimizing the blast radius of attackers.
