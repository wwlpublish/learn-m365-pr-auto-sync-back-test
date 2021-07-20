Microsoft Cloud App Security uses IP address ranges to help to identify locations and the services they host. Cloud App Security is preconfigured with IP address ranges for commonly accessed cloud providers.

## How are IP address ranges used?

It's good practice to configure additional IP address ranges to suit your organizational needs. When you add IP address ranges in Cloud App Security, you:

- Improve detection accuracy
- Reduce false positives
- Simplify the investigative experience

For example, IT administrators at Contoso should define the IP address ranges of the Contoso datacenters. This will help reduce false positives in Cloud App Security.

When you add IP address ranges, you must define the properties described in the following table. 

| Property                 | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Name                     | Provide a  meaningful name for the IP address range.         |
| IP address  range        | Enter the  IPv4 address range (or ranges) using network prefix notation (also known as  CIDR notation). For example, 172.16.16.0/20. |
| Category                 | Select from a  range of predefined categories or choose Other. The category defines the type  of the location, such as Corporate or Cloud provider. |
| Tags                     | Enter a word  into the text box to assign a tag. You use these tags to help build policies  in Cloud App Security. |
| Override  registered ISP | Select this  option to enter an ISP name.                    |
| Override  location       | Select this  option to select from a list of locations.      |

> [!TIP]
> You use the Location and Registered ISP override values to override defaults. For example, suppose the Contoso administrator defines an IP address range that is considered publicly to be in the UK. However, the administrator knows that the IP range is actually in the United States, so the administrator overrides the location for that IP address range.

### Tags and categories

A tag is a text label that you can associate with objects in Cloud App Security, including IP address ranges. You can then use the tags to implement Cloud App Security policies.

For example, in the following graphic, the Contoso administrator has created tag called London HQ, which is associated with an IP address range.

The screenshot displays a filter that looks for the condition:

```
IP address Tag does not equal London HQ and Activity type equals Log on
```

:::image type="content" source="../media/policy.png" alt-text="A screenshot displays the policy details for a policy matching the preceding text.":::

You select a category when you define an IP address range. You use categories so that you can easily recognize activities from interesting IP addresses.

> [!IMPORTANT]
> Categories typically require you to determine which IP addresses are included in each category. The exception to this configuration is the **Risky** category, which includes two IP tags - **Anonymous proxy** and **Tor**.

You can select between the categories described in the following table.

| Category        | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| Administrative  | The IP  address ranges associated with your administrators.  |
| Cloud  provider | The IP  address ranges associated with your cloud provider   |
| Corporate       | The IP  address ranges of your public IP addresses for your internal network, any  branch offices, and your Wi-Fi roaming addresses. |
| Risky           | The IP  address ranges that you consider to be risky. These might include suspicious  addresses you've encountered before, or the IP ranges of your competitors'  networks. |
| VPN             | The IP ranges allocated for use by remote employees that connect via VPN. |
| Other           | For custom use based on tagging.                            |

> [!TIP]
> When you tag an IP address as corporate, that's reflected in the portal, and the IP addresses are excluded from triggering specific detections.

## Setup IP address ranges

To create an IP address range in Cloud App Security, use the following procedure:

1. Navigate to the [Cloud App Security portal](https://portal.cloudappsecurity.com).
2. Sign in as a Global Admin in your Microsoft 365 tenant.
3. In the portal, select **Settings**. This is the cog next to your profile picture.
4. Select **IP address ranges**. A list of defined (and previously created) IP address ranges is returned.
5. To create a new IP address range, select **Add IP address range**. This is the **+** symbol on the header.
6. In the **New IP address range** dialog box, enter the following information:

    - Name
    - IP address ranges
    - Category
    - Tags
    - Override registered ISP
    - Override location

7. Select **Create**.

> [!WARNING]
> You cannot add IP address ranges with overlapping IP addresses.

For example, in the following screenshot, the administrator has defined the following properties:

- Name: Contoso London HQ
- IP address ranges: 172.16.16.0/20 and 172.16.32.0/20
- Category: Corporate
- Tags: London HQ
- Both Override registered ISP and Override location are not selected

:::image type="content" source="../media/ip-address-range.png" alt-text="A screenshot displays the New IP address range dialog box. The administrator has created a range based on the text in the preceding section":::

The following video describes the benefits of configuring IP address ranges, and demonstrates how to set up IP address ranges:

 >[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4MGkV]
