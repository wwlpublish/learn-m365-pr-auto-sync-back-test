Microsoft Teams Calling enables users to make and receive calls from any location, using their work number. You can connect from Teams to landline and mobile devices through the Public Switched Telephone Network (PSTN). Microsoft Teams works with Microsoft Teams Phone to enable call control and PBX capabilities through the Office 365 cloud. Phone System supports two primary options to implement PSTN connectivity with Microsoft Teams:

- Use a Microsoft Calling Plan, or
- Use Direct Routing.

## Microsoft Calling Plan

Using Calling Plan, Microsoft acts as your PSTN carrier. Phone System operates with a PSTN calling plan and acts as part of Office 365 to enable external calls. You don't need to purchase or deploy any additional equipment, or require a contract with a third-party carrier. All you require is an uninterrupted connection to Office 365.

:::image type="content" source="../media/uninterrupted-connection-phone-system-expanded.png" lightbox="../media/uninterrupted-connection-phone-system-inline.png" alt-text="Uninterrupted connection to Office 365.":::

You can purchase a domestic calling plan or an international calling plan. A domestic calling plan allows users to connect to phone numbers located in the country/region where they are assigned in Office 365. An international calling plan extends the reach to international numbers.

This option supports Teams and Skype for Business users. However, not all Office 365 regions support Calling Plan.

## Direct Routing

Direct Routing connects Phone System through an on-premises PBX, using your on-premises telephony network and existing carrier to connect to the PSTN to place external calls. This option requires a supported Session Border Controller (SBC) for interoperability with a third-party PBX and other telephone equipment, depending on the telephony configuration you have running on-premises.

:::image type="content" source="../media/2-direct-routing-expanded.png" lightbox="../media/2-direct-routing-inline.png" alt-text="Direct routing":::

You can use almost any telephony carrier with Phone System, but requires that you (or a partner) can configure interoperability between your on-premises telephony equipment with Phone System.

Unlike using Calling Plan, this option is available worldwide. It still requires an uninterrupted connection to Office 365.

This solution is suitable for Teams users. If you also need to support Skype for Business users, connect Skype for Business Server to the PSTN through your on-premises PBX or telecommunications gateway. If you don't have an existing Skype for Business Server available, you can deploy Cloud Connector Edition. Phone System connects to your SBC through Skype for Business Server or Cloud Connector Edition.

:::image type="content" source="../media/2-direct-routing-expanded.png" lightbox="../media/2-direct-routing-inline.png" alt-text="Connect to Phone System through Skype for Business":::

> [!NOTE]
> If you only have Skype for Business Users, you can use Skype for Business Server to route internal calls over your on-premises WAN, while enabling external calls through your PBX or telco gateway.
> This option does not require an uninterrupted connection to Office 365.
