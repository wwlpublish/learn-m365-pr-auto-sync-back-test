To properly protect your network from internet attacks, you should reduce the attack surface of the network. The attack surface is the number of computers and services directly exposed to the internet.

The Edge Transport server role is optional and typically deployed on a computer located in an Exchange organization's perimeter network. It's designed to minimize the attack surface of the organization. The Edge Transport server role handles all internet-facing mail flow.

:::image type="content" source="../media/exchange-edge-transport.png" alt-text="Exchange Edge transport server role diagram." border="false":::

## Adding an Edge Transport server to a hybrid deployment

Deploying an Edge Transport server in your on-premises organization when you configure a hybrid deployment is optional. When you configure a hybrid deployment, the Hybrid Configuration wizard offers two choices. You can either select one or more internal on-premises Exchange servers, or select one or more on-premises Edge Transport servers to handle hybrid mail transport with the Exchange Online organization.

When you add an Edge Transport server to your hybrid deployment, it communicates with EOP on behalf of the internal Exchange servers. The Edge Transport server acts as a relay between the internal Exchange servers and EOP for outbound messaging, from the on-premises organization to the Exchange Online organization. The Edge Transport server also acts as a relay between the internal Exchange servers for inbound messaging from the Exchange Online organization to the on-premises organization.

## Learn more

- [Edge Transport servers with hybrid deployments](/Exchange/edge-transport-servers?azure-portal=true)
