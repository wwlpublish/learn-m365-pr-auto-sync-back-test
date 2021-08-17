Phone System provides many key capabilities to help your organization's users to be productive and collaborate in a protected way such as through call sharing, protected voicemail, number blocking, and more. As the administrator for your company, you want to explore how you can set up these key capabilities of Phone System.

In this unit, you'll learn about how to set up Phone Systems' key capabilities.

## Key capabilities

Phone System's key capabilities include:

- **Caller ID**
- **Protected voicemail**
- **Blocking inbound calls**
- **Call park and retrieve**
- **Auto attendant**
- **Call queues**

Let's go through what these capabilities are and see how you can set them up.

### Set up caller ID

When a Microsoft Teams user makes a call to a public switched telephone network (PSTN) telephone, the Teams user's phone number is visible. Similarly, a PSTN caller's phone number is visible when they call a Microsoft Teams user. Caller ID policies enable you to show alternative phone numbers for Microsoft Teams users in your organization when they make a call, or prevent phone numbers of incoming calls from being visible. For instance, you can ensure that your organization's main phone number is displayed instead of individual users' numbers. You can configure caller ID using either PowerShell or the Teams admin center. For instance, you can create and configure caller ID policies using the admin center to configure caller ID across your organization:

:::image type="content" source="../media/setup-caller-id-policy.png" alt-text="Screenshot of setting up the caller ID policy":::

You can block incoming caller ID, replace your users' caller ID with "Anonymous", or replace it with a service number.

The steps you carry out to configure caller ID are covered in detail in the **Control caller ID information** unit in the **Secure Microsoft Teams voice functionality** module (link in the **Learn more** section).

### Set up voicemail

Any voicemail might include personal, or confidential business-critical information. So you must ensure that voicemail is protected across your organization. When protected voicemail is implemented, your users can listen to their encrypted messages by calling into their voicemail boxes, or open their messages from Outlook (web or desktop client), or mobile Outlook on iOS or Android. Voicemail is also transcribed automatically, which can be disabled, and you can also enable profanity masking to meet organizational policies and protect users.

For a detailed rundown on configuring protected voicemail, use the **Protect voicemail** unit in the **Secure Microsoft Teams voice functionality** module (link in the **Learn more** section).

### Set up call park and retrieve

With call parking and retrieve, your users can place calls on hold. When they park a call, a unique code will be generated that can be used to retrieve the call later down the line.  For example, a front desk worker at one of your organization's branches parks a call that they think a specialist who works in the back offices can help with. The receptionist can notify the relevant specialist and share the unique code that the specialist can use to access the call on their Teams client.

> [!NOTE]
> To park and retrieve calls, the relevant users must be Enterprise Voice licensed users, and must be added to the call park policy.

### Create a call park policy

You can enable call parking and retrieval by first enabling a call park policy:

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/).
1. In the left navigation pane, select **Voice > Call park policies**.

    :::image type="content" source="../media/create-call-park-policies.png" alt-text="Screenshot of creating call park policies":::

1. Select **Add** on the **Manage policies** tab.
1. Provide a name for your policy, and then set **Allow call park** to **On**.

    :::image type="content" source="../media/switch-on-call-parking.png" alt-text="Screenshot of enabling call parking":::

1. Select **Save**.

### Assign the policy to a group

In order for your policy to take effect, you assign it to users either on a per-user level, or on a group-level. For example, to assign your policy to a group you can do the following steps:

1. Select the **Group policy assignment** tab in the Call park policies pane.

    :::image type="content" source="../media/assigning-group-policy.png" alt-text="Screenshot of the Group policy assignment option":::

1. Select **Add**. The Assign policy to group pane appears.
1. In the **Select a group** field, look for your target group and select it.

    :::image type="content" source="../media/assign-policy-to-group.png" alt-text="Screenshot showing how to assign policy to a group":::

1. In the **Select rank** field, set a rank you want to set for this group assignment compared with other assignments.
1. In the **Select a policy** field, select your newly created policy.
1. Select **Apply** to apply your policy to the group.

### Set up call sharing

Call sharing enables your Microsoft Teams users to share incoming calls with their colleagues so that colleagues can answer calls when they're unavailable. Calls sharing in Microsoft Teams can be done in different ways:

- Through call forwarding -  where calls are forwarded to another person or voicemail
- Through simultaneous ringing - where two people are notified at the same time to answer calls.
- Through group call pickup - which enables:

  - Call forwarding to a group
  - Simultaneous ringing to a group

With group call pickup, your users can also decide how they should be notified of incoming calls. For example, through visual and audio notifications, visual only notifications, or the banner in the Microsoft Teams app.  This is less intrusive than regular call forwarding and simultaneous ring.

To take advantage of call sharing with group call pickup, a user creates a call group and then adds their target users to share calls with to that group. These are user-driven features, so you'll need to share the instructions on how they can do this using the **Call forwarding, call groups, and simultaneous ring in Teams** guide for users (link in the **Learn more** section).

> [!NOTE]
> Users Enterprise Voice licensing to configure and use call sharing. Additionally, a call group has a limit of a maximum of 25 users.

As the admin, you're responsible for enabling call groups. You can do this through either PowerShell or the Teams admin center. For example, to do this through PowerShell you can run the **Set-CsTeamsCallingPolicy** cmdlet and set its **AllowCallGroups** parameter to **$true**:

```powershell
Set-CsTeamsCallingPolicy -Identity Global - AllowCallGroups $true
```

### Block inbound calls

Your organization's office branches naturally receive daily phone calls from customers. But they also receive nuisance calls and spam calls. So, you want to make sure that these types of calls are blocked going forward.
With Phone System call blocking features, you can match the caller ID of every incoming PSTN call against a global tenant list that is based on number patterns using regular expression (Regex). The call will be blocked if a match is found. Through PowerShell commands you can:

- Block a number
- Allow a number
- Add number exceptions
- Modify/remove number exceptions
- Test whether numbers are blocked

The steps you carry out to configure blocking inbound calls are covered in detail in the **Control inbound calls unit in the Secure Microsoft Teams voice functionality** module (link in the **Learn more** section).

### Auto attendants and call queues

With auto attendants, you can automate incoming calls to be routed to the right teams by enabling callers to select options from a menu during calls. And with call queues, you can ensure calls are queued appropriately during the busiest times, and ensure callers don't drop out of calls because of long wait times.

The steps to configure auto attendants and call queues are in the **Manage calls in Microsoft Teams by using auto attendants and call queues** module (link in the **Learn more** section).

## Learn more

- [Call forwarding, call groups, and simultaneous ring in Teams](https://support.microsoft.com/office/call-forwarding-call-groups-and-simultaneous-ring-in-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e?ui=en-us&rs=en-gb&ad=gb)
- [Control caller ID information](/learn/modules/m365-teams-secure-teams-voice-functionality/5-configure-caller-id-policies)
- [Protect voicemail](/learn/modules/m365-teams-secure-teams-voice-functionality/3-protect-voicemail)
- [Control inbound calls]( /learn/modules/m365-teams-secure-teams-voice-functionality/4-block-inbound-calls)
- [Manage calls in Microsoft Teams by using auto attendants and call queues](/learn/modules/m365-teams-manage-calls-using-auto-attendants/)
