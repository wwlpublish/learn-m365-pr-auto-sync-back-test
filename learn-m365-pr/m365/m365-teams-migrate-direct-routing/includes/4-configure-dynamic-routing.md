Direct Routing in Microsoft Teams supports conditional routing, which is when the Session Border Controller (SBC) looks up a user in a directory before connecting an incoming call. It allows you to make routing decisions based on dynamic rules. For example, if a user is on-premises, send the call to Skype for Business Server. If the user is online, send the call to Teams. The advantage is that you don't need to use an individual telephone number. Dynamic routing provides a much more flexible way to connect calls, based on the result of a particular query.

Suppose you have been tasked with configuring dynamic routing in your organization. You need to configure an LDAP connection on the SBC and build the rules to query the respective attributes that you want from Active Directory.

Here, you'll see what dynamic routing looks like, how to configure an LDAP connection, and see an example of how to configure a specific SBC.

## SBC dynamic routing

SBC dynamic, or conditional, routing involves a directory lookup. The system does conditional routing based on an LDAP query against the local Active Directory. The following diagram shows how directory lookup works:

:::image type="content" border="false" source="../media/4-directory-lookup-flow.png" alt-text="Directory Lookup Flow":::

In this example, we start with the telco-provided connection that could be a SIP trunk or a PRI line. The SBC is configured with a SIP trunk to the Skype for Business Server and to Teams with Direct Routing.

The SBC makes routing decisions because of an LDAP connection to a Domain Controller, in which there's a set of attributes that can be queried. The attributes in question are:

- msRTCSIP-Line
- msRTCSIP-DeploymentLocator
- msRTCSIP-OptionsFlags
- extensionAttribute1

The last two attributes are optional. For example, you can use the msRTCSIP-OptionalFlags to ensure the account is enabled for Enterprise Voice (value 385).

If Exchange is deployed, you could use extensionAttribute1 to flag when a user has been migrated or to differentiate between Skype for Business Online and Teams.

The msRTCSIP-Line attribute can be considered as the anchor. It's used to match a user with an incoming call. For example, a call is coming in for Bob (949-555-2832) that reaches the SBC. The SBC makes an LDAP query to see if there's a user with this phone number. Because Bob has been enabled for Enterprise Voice, a match will be found. If the phone number wasn't assigned to a user, the call can be rejected. The system looks at the mcRTCSIP-line attribute because that's where the user's phone number is stored when they're enabled for Enterprise Voice in Skype for Business Server.

Next, the system looks at the msRTCSIP-DeploymentLocator attribute. If msRTCSIP-DeploymentLocator contains **SRV:**, it indicates the account is on-premises and the call will be routed to Skype for Business Server. Or, if msRTCSIP-DeploymentLocator contains **sipfed.online.lync.com**, the call is sent to Teams.

## Configure dynamic routing on an SBC

Configurations are specific to each vendor. In this discussion, we'll reference SBCs from AudioCodes.

The first step is to configure the LDAP connection, which is often disabled by default. You set up the connection by configuring an LDAP server group that contains an LDAP server.

Next you build the rules to query the respective attributes that you want from Active Directory; it's where you start building logic. If the user is on-premises, send the call to Skype; if the user is online, send it to Teams. These rules are the ones you're going to query. With AudioCodes, these are referred to as Call Setup Rules. The following sample shows what it looks like:

:::image type="content" border="false" source="../media/4-audiocodes-left.png" alt-text="Configuring Call Setup Rule":::

Here's how to configure the Call Setup Rule:

1. Start with the **Rule Set ID**, which is an arbitrary number. In this example, it's **1**.
2. Set the **Request Type** to **LDAP**.
3. Set the **Request Target** to your Domain Controller Group.
4. Set the **Request Key** to your anchor attribute that, as you'll recall, is the msRTCSIP-Line attribute.
5. **Attributes To Get** is the attribute you want to have after you've found the user. In this example, it's the deployment locator **msRTCSIP-DeploymentLocator**. As we discussed earlier, the deployment locator will be either **SRV:** or **sipfed.online.lync.com**.
6. Finally, set **Condition** to be equal to **sipfed.online.lync.com**.

Now look at the routing in this diagram:

:::image type="content" border="false" source="../media/4-audiocodes-right.png" alt-text="IP-to-IP Routing":::

On the routing, the first field you'll fill in is **Source IP Group**. This field is for the call received from the PSTN Trunk. The next field is **Destination IP Group** that you want to set for Teams. Next is **Call Setup Rules Set ID** that, as you recall from earlier, is **1**. You're telling the SBC that, before the call gets routed, to look up Call Setup Rule number 1. If it doesn't match, the SBC will go on to the next one that does match, which would be the Skype for Business rule.

Remember that, when you configured the Call Setup Rule, you defined two attributes to read: msRTCSIP-Line and msRTCSIP-DeploymentLocator. On some SBCs, you can optionally cache these attributes. It means that you don't impact the performance of having to query the local domain controllers all the time.
