In the previous unit, we identified the voice configuration objects that interact with each other to allow users to place calls. In this unit, let's consider how to configure these voice routing objects.  The objects include **PSTN usage records**, a **Voice Routing Policy**, the **Voice Route**, **Dial Plan**, and **Gateway**.

:::image type="content" border="false"  source="../media/1-direct-routing-planning-steps.png" alt-text="Diagram shows seven steps for Direct Routing planning. These are, Self-deployed vs. hosting, Licensing and endpoints, Session border controllers (SBC), Fully qualified domain names and certificates, IP ranges and ports (firewall), Voice routing, Optimize Media.":::

## Voice routing objects

There are three objects that work together to specify the class of service and class of restriction for calls. They determine the type of calls that groups of users can make, and how they're handled. This unit looks at each one in a little more detail. They are:

- Voice routing policy
- PSTN usage record
- Voice route

A **PSTN usage record** specifies a class of call, such as internal, local, or international. The PSTN record is assigned to both a **Voice Routing Policy** and a **Voice Route**. If you have more than one PSTN usage record, the order is important. PSTN usage records are evaluated in order. If the first record matches a user's number, then no other PSTN usage record is evaluated. In summary:

- The PSTN usage record is associated with a voice routing policy.
- The voice routing policy is assigned to users.
- The PSTN usage record is assigned to a voice route that specifies the gateway and the SBC to be used.

:::image type="content" border="false" source="../media/3-pstn-usage-associations.png" alt-text="Diagram shows PSTN usage record associations.":::

> [!NOTE]
> Ensure the hierarchy of PSTN usage records is correct. If a number matches the first record, the rest are ignored. If the number doesn't match, it then looks at the next record, and so on. PSTN usage records in the wrong order could result in calls being assigned to a gateway you didn't intend.

A **Voice Routing Policy** is assigned to a group of users and a PSTN usage record. If a valid PSTN usage record can't be found for the user or a voice routing policy can't be found, the call fails.

The **Voice Route** specifies the **number patterns** that it will handle, the priority for them, and the gateway and SBCs assigned to it. The voice route is associated with a voice routing policy and therefore a group of users. Like PSTN usage records, the order of voice routes matters with the first one matching, and the others not evaluated. So when a user dials a number, it will match to a PSTN usage record, a voice routing policy and a specific voice route, then a gateway and SBC. If it doesn't match at any point, the call fails.

This diagram summarizes how the different components work together.

:::image type="content" border="false" source="../media/3-routing-example.png" alt-text="Routing components" lightbox="../media/3-routing-example.png":::

## Dial plans

A **dial plan** translates a shortened version of a number into one that adheres to the international dialing standard E.164. This standard ensures all numbers are globally unique. As an example, users might regularly dial a three-digit extension number that must be a globally unique number before it can be placed. You can create a dial plan for any pattern number that you use within your organization.

Dial plans are implemented as a set of normalization rules, using regular expressions. The normalization rules translate the user's familiar number into an internationally unique number.

The benefit of a dial plan is that you can migrate to Teams without changing users' habits. Alternatively, you might consider that it's more beneficial to train users in the new way of working, rather than encouraging them to keep legacy habits.

:::image type="content" border="false" source="../media/3-legacy-teams.png" alt-text="Legacy habits" lightbox="../media/3-legacy-teams.png":::

You're limited to a maximum of 1,000 dial plans per tenant and 50 normalization rules per dial plan. There are three types of dial plan:

### Service dial plan

The Service dial plan can't be changed and is the same for everyone in a specific country. The country is the same as that assigned when the user record is created in the Microsoft 365 Admin Portal. The Service dial plan includes a number of common normalization rules. For many organizations, the Service dial plan fits their needs without creating any additional dial plans.

### Tenant global dial plan

The tenant global dial plan can be customized. As the name suggests, it affects all users in your organization.

### Tenant user dial plan

The tenant user dial plan can also be customized. You can operate the tenant user dial plan for a group of users.

There is a **Dial Plan Hierarchy**:

- If you haven't modified any dial plan, then the service dial plan for the relevant country will be used.
- If you have modified the tenant global dial plan, this will be merged with the Service dial plan for the relevant country. The combination of the two will be used.
- If you have created  one or more tenant user dial plans, these will be merged with the Service country dial plan. The combination of the two will be used.

This diagram helps you to plan whether or not you need to create dial plans for your organization, and if so, what type.

:::image type="content" border="false" source="../media/3-dial-plans-planning.png" alt-text="This diagram helps you to plan whether or not you need to create dial plans for your organization, and if so, what type." lightbox="../media/3-dial-plans-planning.png":::

## Gateway

The gateway is the representation of the SBC within the telephony service. It's sometimes referred to as a trunk. The gateway can also be configured to handle translations of numbers, dynamic emergency calling, and location-based routing.

## Multiple SBCs

Your organization might require more than one SBC to handle a high volume of calls. You'll use different strategies depending on your objectives:

### Load distribution and high availability

To manage high loads, you group multiple SBCs in a single voice route. Depending on the SBC vendor, multiple SBCs can also be combined into a cluster. To Teams, a cluster looks like a single SBC.

### High availability with back-up routes

For high availability, you configure voice routes so they are assigned a priority level. A specific voice route can be configured so it's only used when a higher priority route isn't available.

### Disaster recovery

Voice routing policies can be configured to allow certain users to use specific routes. For example, if SBCs in the US aren't available, users would use SBCs in Europe.
