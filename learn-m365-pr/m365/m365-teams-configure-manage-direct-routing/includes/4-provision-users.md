The next step is to set up and configure users for Microsoft Teams Direct Routing.

Suppose, in your clothing retailer, that you've configured your voice routing. Now you need to assign routes to your users. There are a few things to consider, including how you'll handle calls originating from your existing private branch exchange (PBX) system into Microsoft Teams, and the other way around. You'll also need to look at any specific rules and permissions around user access and the types of calls they're permitted to make.

Here, you'll learn how to create telephony routes for users in Direct Routing.

## Number translation

Number translation is an optional step you might consider when communicating with Session Border Controllers (SBCs). It's used to bring together a legacy PBX and the Microsoft Teams Phone, by converting the inbound or outbound dialed phone number to the correct format for either system. Number translation rules can be applied either at the gateway or at the SBC level. The rules apply to both inbound and outbound traffic, which covers calls coming from the public switched telephone network (PSTN) endpoint into the Microsoft Teams client (inbound), and from the Microsoft Teams client to the PSTN endpoint (outbound).

In the following examples, there are two users, Alice and Bob. Alice is a Microsoft Teams user whose number is +1 206 555 0100. Bob is a PSTN user whose number is +1 425 555 0100.

:::image type="content" border="false" source="../media/4-number-translation-inbound.png" alt-text="Diagram showing a typical session border controller requiring number translation":::

The management of all number translation processing is done through the tenant remote PowerShell (TRPS) command line, using the **-CsTeamsTranslationRule** cmdlets, prefixed with either **New**, **Set**, **Get**, or **Remove**. For example, **New-CsTeamsTranslationRule**.

### The E.164 format

E.164 is an international standard numbering plan that ensures each device on a data network or PSTN has a globally unique identified number. In Microsoft Teams, we use the E.164 format to represent a user's phone number, and also for caller ID purposes. It means that any non-Microsoft Teams phone numbers (typically from an existing PBX) need to be converted into E.164. The diagram below shows how Bob's extension (from an existing PBX) x2814 is translated to the E.164.  In this case, Bob's number is 9495552814.  To conform to the E.164 standard, it needs to be prefixed with a +1 (plus one).  So you'd create a translation rule to manage it automatically.

:::image type="content" border="false" source="../media/4-number-translation-inbound-translation-table.png" alt-text="A diagram showing how number translation modifies the RequestURI to and from elements":::

### Policy rules

Each rule needs to be assigned to a policy that resides on the SBC. Each policy can have multiple rules assigned, but has an upper limit of 400. Each rule will affect the *to* and *from* headers in the RequestURI. The rules are processed in the order that they appear when you list them using PowerShell.  You can also adjust the execution order of the rules in any policy.

> [!NOTE]
> You need to decide where you want the policy rules to run, either from the SBC, or in Microsoft Teams. You don't want to do both.

To assign, configure, and list number translation rules on SBCs, you use the **New-CSOnlinePSTNGateway** and **Set-CSOnlinePSTNGateway** cmdlets together with the following parameters:

- **InboundTeamsNumberTranslationRules**
- **InboundPSTNNumberTranslationRules**
- **OutboundTeamsNumberTranslationRules**
- **OutboundPSTNNumberTranslationRules**

For more information about these cmdlets, see the links in the **Learn more** section below.

### Create number translation rules for users

For this scenario, you could run the **New-CsOnlinePSTNGateway** cmdlet to create the following configuration:

```powershell
New-CSOnlinePSTNGateway -Identity sbc1.contoso.com -SipSignalingPort 5061 –InboundTeamsNumberTranslationRules 'AddPlus1' -InboundPSTNNumberTranslationRules 'AddPlus1' -OnboundPSTNNumberTranslationRules 'AddSeattleAreaCode'  -OutboundTeamsNumberTranslationRules 'StripPlus1'
```

The translation rules assigned to the SBC are summarized in the following table:

| Name                   | Pattern      | Translation |
| :--------------------- | :----------- | :---------- |
| AddPlus1               | ^(\d{10})$   | +1$1        |
| AddE164SeattleAreaCode | ^(\d{4})$    | +1206555$1  |
| AddSeattleAreaCode     | ^(\d{4})$    | 425555$1    |
| StripPlus1             | ^+1(\d{10})$ | $1          |
| | |

## Provision Direct Routing users

Before people use Direct Routing, you'll need to provision them. There are two options available: **Direct Routing only**, or **Direct Routing with a Microsoft Calling Plan**.

### Direct Routing only

You connect your organization's telecom voice trunks directly to Microsoft Teams so staff can make and receive calls. Your organization can still use their local telecommunications provider to connect their voice trunks via a certified SBC to Microsoft Teams and the Phone System.

### Microsoft Calling Plan and Direct Routing

A Calling Plan is an add-on telephone service that, when combined with Phone System in Microsoft Teams, can become the voice solution for your entire organization. A Calling Plan provides staff with a primary phone number and lets them make and receive calls.  

### Considerations when provisioning users

Whether you're provisioning for Direct Routing only or using Microsoft Calling Plan and Direct Routing, there are five steps to consider:

- What licenses are required? Typically, you'll need a minimum of:
  - Microsoft Teams Phone
  - Microsoft Teams
  - Audio Conferencing (for scheduled meeting dial in/out)
  - Microsoft Calling Plan (only applicable if you choose that provisioning type)
- Number provisioned - where will the number come from?  
  - Direct Routing - the number will come from Azure Active Directory
  - Microsoft Calling Plan and Direct Routing - the number will come from Microsoft as part of the service
- Enabled the user - what mechanism will you use to enable provisioning? Will it be through a PowerShell cmdlet, or the Microsoft Teams Admin Center?
- Assign routing - What voice routing will be used?  This is where you'll assign one or more routing policies.
- Routing behavior - How will the routing be evaluated and what are the outcomes?

The table below provides an at-a-glance example of the type of settings you might use:

|  | Direct Routing only  | Microsoft Calling Plan and Direct Routing |
|---------|---------|---------|
|Licenses required     | Microsoft Teams Phone, Microsoft Teams, Audio Conferencing (for scheduled meeting dial in/out)        | Microsoft Teams Phone, Microsoft Teams, Audio Conferencing (for scheduled meeting dial in/out)        |
|Number provisioned     | In Azure Active Directory (User Online or AADSync)        |  Acquired from **Microsoft** or **ported to Phone System**       |
|Enable the user     | `Set-CsUser -Identity "User name" -OnPremLineURI tel:+123456789 -EnterpriseVoiceEnabled $true -HostedVoiceMail $true`        |  User is assigned a number through Teams Admin Center or **Set-CsOnlineVoiceUser** (inbound calling is anchored on Calling Plan)       |
|Routing behavior     | Only administrator routes evaluated, if no routes exist matching the callee number, the call drops        | <ul><li>Step 1. Routes configured by administrator evaluated.</li><li>Step 2. If no routed matching the callee number exist on Step 1, route the call via Microsoft Calling plan.</li></ul>         |
|Assign routing     | `Grant-CsOnlineVoiceRoutingPolicy -Identity "User name" -PolicyName "US Only"` | `Grant-CsOnlineVoiceRoutingPolicy -Identity "User name" -PolicyName "US Only"` |

## Dial plans

A dial plan consists of one or more normalization rules that define how phone numbers expressed in various formats are translated to an alternate format. The same dial string might be interpreted and translated differently in different dial plans. Depending on which dial plan is assigned to a given user, the same dialed number might be translated and routed differently. There can be a maximum of 1,000 tenant dial plans.
A dial plan's scope determines the hierarchical level at which it can be applied. Clients get the appropriate dial plan through provisioning settings that are automatically provided when users sign in to Microsoft Teams. As an admin, you can manage and assign dial plan scope levels by using the Microsoft Teams admin center or PowerShell.

The following are the possible effective dial plans:

- **Service country**. If no tenant scoped dial plan is defined and no tenant user scoped dial plan is assigned to the provisioned user, the user receives an effective dial plan mapped to the service country associated with their usage location.
- **Tenant global - service country**. If a tenant user dial plan is defined but not assigned to a user, the provisioned user receives an effective dial plan consisting of a merged tenant dial plan and the service country dial plan associated with their usage location.
- **Tenant user - service country**. If a tenant user dial plan is defined and assigned to a user, the provisioned user will receive an effective dial plan consisting of the merged tenant user dial plan and the service country dial plan associated with their usage location.

Here's how to manage existing tenant dial plans in PowerShell:

### Start a remote PowerShell session

Use PowerShell to connect to Microsoft 365 by running:

```PowerShell
$credential = Get-Credential
$session = New-CsOnlineSession -Credential $credential
Import-PSSession $session
```

> [!NOTE]
> Make sure that you're running Windows PowerShell version 3.0 or later.

Now that you have a remote PowerShell session running, you can use the following cmdlets to investigate and review any assigned dial plans:

### Edit the settings of an existing dial plan

Use the **Set-CsTenantDialPlan** command to edit the settings of any existing dial plan. For example:

```PowerShell
Set-CsTenantDialPlan -Identity RedmondDialPlan  -NormalizationRules <pslistmodifier> -ExternalAccessPrefix 9 -SimpleName "Dial-Plan-for-Redmond"
```

### Add users to a dial plan

You can use the **Grant-CsTenantDialPlan** to add users to a dial plan. For example:

```PowerShell
Grant-CsTenantDialPlan -Identity jenny.brown@contoso.com -PolicyName RedmondDialPlan
```

### View the settings on a dial plan

You check the settings for your dial plan by using the **Get-CsTenantDialPlan** command. For example:

```PowerShell
Get-CsTenantDialPlan -Identity RedmondDialPlan
```

### View the settings of the effective dial plan

To check the settings of an effective dial plan, you run the **Get-CsEffectiveTenantDialPlan** command:

```PowerShell
Get-CsEffectiveTenantDialPlan -Identity amos.marble@contoso.com
```

### Use Microsoft Teams admin center to create a dial plan

You can also use the Microsoft Teams admin center to create a dial plan.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Dial plan**.
1. Select **Add**, and then enter a name and description for the dial plan.

    :::image type="content" source="../media/4-add-dial-plan-admin-center.png" alt-text="Screenshot showing the Add page for creating a dial plan":::

1. Under **Dial plan details**, specify an external dialing prefix if users need to dial one or more additional leading digits (for example, 9) to get an external line:

   1. In the **External dialing prefix** box, enter an external dialing prefix. The prefix can be up to four characters (#,*, and 0-9).
   1. Turn on **Optimized device dialing**. If you specify an external dialing prefix, you must also turn on this setting to apply the prefix so calls can be made outside your organization.
1. Under **Normalization rules**, configure and associate one or more normalization rules for the dial plan. Each dial plan must have at least one normalization rule associated with it. Do one or more of the following actions:

   - To create a new normalization rule and associate it with the dial plan, select **Add**, and then define the rule.
   - To edit a normalization rule that's already associated with the dial plan, select the rule to the left of the rule name. Select **Edit**, make the changes you want, and then select **Save**.
   - To remove a normalization rule from the dial plan, click to the left of the rule name, and then select **Remove**.

1. Arrange the normalization rules in the order that you want. Select **Move up** or **Move down** to change the position of rules in the list.

    > [!NOTE]
    > Microsoft Teams traverses the list of normalization rules from the top down, using the first rule that matches the dialed number. If you set up a dial plan so that a dialed number can match more than one normalization rule, make sure the more restrictive rules are sorted above the less restrictive ones.

1. Select **Save**.
1. If you want to test the dial plan, under **Test dial plan**, enter a phone number, and then select **Test**.

### Assign a dial plan to users

You assign a dial plan in the same way you assign policies. You can assign a policy directly to users, either individually or at scale through a batch assignment, if supported for the policy type, or to a group that the users are members of, if supported for the policy type.

## Learn more

- [New-CSOnlinePSTNGateway](/powershell/module/skype/new-csonlinepstngateway)
- [Set-CSOnlinePSTNGateway](/powershell/module/skype/set-csonlinepstngateway)
- [Set-CsTenantDialPlan](/powershell/module/skype/set-cstenantdialplan)
- [Grant-CsTenantDialPlan](/powershell/module/skype/grant-cstenantdialplan)
- [Get-CsTenantDialPlan](/powershell/module/skype/get-cstenantdialplan)
- [Get-CsEffectiveTenantDialPlan](/powershell/module/skype/get-cseffectivetenantdialplan)
- [Normalization rules](/microsoftteams/what-are-dial-plans#normalization-rules)
