There are several policies you may need to configure for specific features of Teams Phone. This unit covers configuration of these policies

## Configure Calling policies

Calling policies control which calling and call forwarding features are available to users.

Calling policies can enable or disable the following:

| Function| Description| Recommendation|
| :--- | :--- | :--- |
| Make private calls| The ability to make P2P VoIP and PSTN calls in Teams| Set to on to make calls|
| Cloud recording for calling| allow convenience recording of 1:1 calls| Set to on unless you have a compliance reason not to enable this.|
| Call forwarding and simultaneous ringing to people in your organization| Enables call forwarding or simultaneous ringing of inbound calls to other users in your tenant.| Set to on|
| Call forwarding and simultaneous ringing to external phone numbers| Enables call forwarding or simultaneous ringing of inbound calls to any phone number.| Set to on. Be aware this may incur phone charges.|
| Voicemail is available for routing inbound calls| Enables inbound calls to be routed to voice mail.| Select user controlled so the user can define their setting.|
| Inbound calls can be routed to call groups| Inbound calls can be routed to call groups| Set to on, this is a useful option for users who need to forward their number to a team|
| Delegation for inbound and outbound calls| Enables inbound calls to be routed to delegates; allows delegates to make outbound calls on behalf of the users for whom they have delegated permissions.| Set to on. Useful for users|
| Prevent toll bypass and send calls through the PSTN| Setting this to on will send calls through PSTN and incur charges rather than going through the network and bypassing the tolls.This setting only works with Direct Routing that is configured to handle location-based routing restrictions.| Set to off unless you have a particular regulatory reason to turn this on.Do not set this parameter to True for Calling Plan users as it will prevent successful call routing|
| Music on hold for PSTN callers| Allows you to turn on or turn off the music on hold when a PSTN caller is placed on hold.

This setting does not apply to call park and SLA boss delegate features.| Se this to On. Silence while on hold is confusing to users.|
| Busy on busy when in a call - when you are on a call a second incoming call will not alert you, it will be routed as an unanswered call for that user, typically to voicemail| Configures how incoming calls are handled when a user is already in a call or conference or has a call placed on hold.

When enabled, new or incoming calls will be rejected with a busy signal.

When set to Unanswered, the user's unanswered settings will take effect, such as routing to voicemail or forwarding to another user.| Set this to off. Most users want a notification of a second incoming call when on a call.|
| Web PSTN calling - specifically block PSTN calling from the web client| Allows PSTN calling from the Team web client.| Set to on. There is normally no reason to disable PSTN calling from the browser.|
| Real-time captions in Teams calls| Determines whether real-time captions are available for the user in Teams calls| Set this to on.|
| Automatically answer incoming meeting invites| Allows you to enable or disable auto answer for incoming meeting invites| Set to off. Most users don’t want meeting invites to automatically answer.|

You can use and modify the Global (Org-wide default) policy and or create custom policies for sets of users. You can create policies by following these steps:

1. Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Select **Voice** and **Calling policies**.

1. Select a Policy to edit or select **add** to add a new policy

1. Define an appropriate **name** and **friendly description**

1. Define the settings for the policy

1. Select **Save**

After performing the described steps, you have created a new calling Policy.

You can also use the Teams PowerShell module to perform the same configuration by using the following cmdlet:

```powershell
Set-CSTeamsCallingPolicy -Identity HROPolicy -LiveCaptionsEnabledTypeForCalling disabled

```

After performing the PowerShell, Live Captions have been disabled on the existing HROPolicy.

## Understanding Dial Plans

A dial plan allows you to transform the number dialed by the user into another number, for example from a local dialing format to the international E.164 format, or to allow users to dial short extension numbers for users.

These transformations are called normalization rules, and they use .NET Framework regular expressions to specify numeric match patterns that the server uses to translate the number the user dials into another number, usually E.164 format.

In Teams, there are two types of dial plans: service-country and tenant. Tenant-scoped dial plans can be further broken into two - tenant-scope or user-scope

| Dial plan scope| About|
| :--- | :--- |
| Service-country| -A service-scoped dial plan is defined for every country/region where Phone System is available-Each user is automatically assigned the service-country dial plan that matches the usage location assigned to the user. You can't change the service-country dial plan|
| Tenant-global| Applies to all users in your tenant/organization|
| Tenant-user| Can be applied to select users|

Each user is automatically assigned the service-country dial plan that matches the usage location assigned to the user. So, for most users you may not need any custom dial plan.

If you want to apply additional dial plan rules, a user’s effective dial plan will be a combination of their service-country dial plan and any tenant global or tenant user dial plans that are assigned to them.

The following are the possible effective dial plans:

- If no tenant scoped dial plan is defined and no tenant user scoped dial plan is assigned to the provisioned user, the user will receive an effective dial plan mapped to the **service-country** associated with their usage location.

- If a **tenant global dial plan** is defined, the user will receive an effective dial plan consisting of a merged tenant global dial plan and the service-country dial plan associated with their usage location. The tenant global dial plan is not assigned to any user

- If a **tenant user dial plan** is defined and assigned to a user, the provisioned user will receive an effective dial plan consisting of the merged tenant user dial plan and the service-country dial plan associated with their usage location. A tenant global dial plan, if defined, will not apply to a user with a tenant user dial plan assigned.

Teams traverses the list of normalization rules from the top down and uses the first rule that matches the dialed number. Tenant global and tenant user rules will be higher than service-country rules.

## Create a Dial Plan

To create a tenant global or tenant user dial plan, complete the following steps:
1. Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Select **Voice** and **Dial Plan**.

1. Select Add, and then enter a name and description for the dial plan.

1. Optionally, specify an external dialing prefix if users need to dial one or more additional leading digits (for example, 9) to get an external line. If you want to do this:

    - In the External dialing prefix box, enter an external dialing prefix. The prefix can be up to four characters (#,*, and 0-9).
    - Turn on Optimized device dialing. If you specify an external dialing prefix, you must also turn on this setting to apply the prefix so calls can be made outside your organization.

1. Under Normalization rules, configure and associate one or more normalization rules for the dial plan. Each dial plan must have at least one normalization rule associated with it. 

    - To create a new normalization rule and associate it with the dial plan, select **Add**, and then define the rule using .NET Framework regular expressions. There are some good samples on Microsoft Docs.

1. Arrange the normalization rules in the order that you want. Select **Move up** or **Move down** to change the position of rules in the list.

1. Select **Save**

1. If you want to test the dial plan, under **Test dial plan**, enter a phone number, and then select **Test**.

A good overview of dial plans is available on Microsoft docs in resources.

## Configure Call Park policies

Call Park and retrieve lets users put calls on hold and enables the same user or someone else to retrieve and continue the call.

This is often used in retail environments, where someone may say over a public address system “There is a call for the electronics department on 22" and someone in the electronics department can then retrieve that call by dialing 22.

> [!NOTE]
> Only Teams Phone licensed users can park and retrieve calls.

Call park is disabled by default. It can be enabled in the global policy, or a custom policy can be created. The global policy will allow any user to pick up a parked call. Custom policies can be used to assign the policy to a subset of users, when you apply the same policy to a set of users, they can park and retrieve calls among themselves.

To enable call park:

1. Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Select **Voice** and **Call park policies**.

1. Select Add, and then enter a **name** and friendly **description**

1. Switch **Allow call park** to **On**.

1. Select **Save**

> [!TIP]
> The call pickup range is from 10 to 99 and cannot be customized. In daily use, this limit is not normally reached; so, it is generally not something to worry about unless you have a very large number of users using call park simultaneously. 

After performing the described steps, you have defined a call park policy you can now assign to a group of users.

## Configure Caller ID policies

Caller ID policies are used to change or block the Caller ID or phone number presented when making or receiving PSTN calls.

By default, the user's phone number is displayed when an outbound call is made to a PSTN phone number such as a landline or mobile phone. In most cases, most companies will be happy with this default.

Some organizations may wish to not present any number, so callers don’t know it is their company calling, or to present another number, such as a main number. So if someone calls back, they are routed to a main reception or Auto Attendant.

| **Caller ID configuration options**| **Use Case**|
| :--- | :--- |
| Replace the caller ID with Anonymous| Blocks the outbound ID completely; useful when customers do not want to be rung back.|
| Replace the caller ID with Service number| Allows you to assign any service number. The number must be on your tenant and actively assigned to a service. Useful to have call backs route to a call queue or auto attendant.|
| Block incoming caller ID| Allows you to block the Caller ID of incoming PSTN calls. This is not normally required.|
| Replace the caller ID with User's number| Sets caller ID back to the default of presenting the user’s actual number.|
| Override the caller ID policy| Let’s end users control if their caller ID is displayed or not for outbound calls. They can set this in their Teams client settings if this option is enabled. This is useful to allow users to make their own decision.If this is on, End users can set their caller ID to Anonymous by going to Settings > Calls in the Teams client, and then under Caller ID, select Hide my phone number and profile information for all calls.|

You can use the Global (Org-wide default) policy and customize it or create a custom policy for a subset of users.

To create a caller ID policy:

1. Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

1. Select **Voice** and **Caller ID policies.**

1. Select **Add**

1. Enter a name and description for the policy.

1. Choose the settings you want

    - Block incoming caller ID

    - Override the caller ID policy

    - Replace the caller ID with:

        - User's number: Displays the user's number.

        - Service number: Lets you set a service phone number to display as the caller ID.

        - Anonymous: Displays the caller ID as Anonymous.

    - Replace the caller ID with this service number: Choose a service number to replace the caller ID of users.

1. Select **Save**

## Configure Inbound call blocking

In some scenarios, you may want to block specific inbound calls at the tenant level. For example, if a specific phone number is constantly spam calling.

Admin controls for blocking numbers are provided using PowerShell only. Patterns are matched using Regular Expressions (Regex).

The Microsoft Teams PowerShell module contains multiple cmdlets to manage call blocking:

| Cmdlet| Function|
| :--- | :--- |
| Get-CsInboundBlockedNumberPattern | Returns a list of all blocked number patterns added to the tenant list including Name, Description, Enabled (True/False), and Pattern for each.|
| New-CsInboundBlockedNumberPattern | Adds a blocked number pattern to the tenant list.|
| Remove-CsInboundBlockedNumberPattern| Removes a blocked number pattern from the tenant list.|
| Set-CsInboundBlockedNumberPattern| Modifies one or more parameters of a blocked number pattern in the tenant list.|
| Test-CsInboundBlockedNumberPattern| Use the cmdlet to verify whether a number is blocked in the tenant.|

To configure a call block rule, perform the following steps:

In following example, we will block all calls coming from the number 1 (412) 555-1111:

1. Connect to Microsoft Teams with PowerShell as an administrator

1. Run the following

```powershell
Test-CsInboundBlockedNumberPattern -PhoneNumber "14125551111"

```

1. Verify the pattern is working

```powershell
New-CsInboundBlockedNumberPattern -Name "BlockNusance1" -Enabled $True -Description "Block Fabrikam" -Pattern "^\+?14125551111$"

```

1. The Test will confirm the number is being blocked.

After performing the described steps, you have configured and verified blocking calls from 1 (412) 555-1111.

> [!TIP]
> Blocked callers may experience slightly different behaviors depending on how their carrier handles the notification that the call isn't allowed to be successfully completed. Examples may include a carrier message stating the call can't be completed as dialed or simply dropping the call.

