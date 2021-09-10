Call queues provide a method of routing callers to people in an organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue (who are known as agents).

To set up a call queue, in the Teams admin center, expand **Voice**, select **Call queues**, and then select **Add**. Provide a **name** of your call queue and configure the following settings with your call queue design.

‎:::image type="content" source="../media/call-queue.png" alt-text="Configure call queues":::

The following sections describe each of the available settings for a call queue.

### Resource accounts

All call queues are required to have a resource account. Agents will see the resource account name when they receive an incoming call.

Select **Add**, and search for the resource account that you want to use with this call queue, then select **Add** twice.

### Assign calling ID

If you plan to use a Teams channel for your call agents, you can assign an outbound caller ID number for the agents by specifying one or more resource accounts with a phone number.

Select **Add**, and search for the resource accounts that you want to allow agents to use for calling ID purposes when making outbound calls, then select **Add** twice.

If you're not using a Teams channel to control agent membership, consider directly setting the caller ID for members of the call queue to the service number of the call queue or appropriate auto attendant

### Language

Choose a supported language. This language will be used for system-generated voice prompts and voicemail transcription (if you enable them).

### Greeting

Teams can provide a greeting to callers when they arrive in the queue. To set up a greeting, upload an MP3, WAV, or WMA file containing the greeting that you want to play.

### Music on hold

Teams can also provide default music to callers while they're on hold in a queue. If you want to play a specific audio file, choose **Upload file** and upload an MP3, WAV, or WMA file.

### Call answering

The following call answering settings can be configured:

- **Answer incoming calls** - You can choose either a channel, or groups and individual users to answer incoming calls for this call queue.

	- **Teams channel** - You can add up to 200 agents through a Teams channel.
	- **Users and groups** - You can add up to 20 agents individually and up to 200 agents through groups. You can use distribution lists, security groups, Microsoft 365 groups, or Microsoft Teams teams.

- **Conference mode** - Conference mode significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call.

	Agents' Teams accounts must be set to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list.

- **Routing method** - Routing method determines the order in which agents receive calls from the queue. Choose from these options:

	- **Attendant routing** - Rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

	- **Serial routing** - Rings all call agents one by one in the order specified in the **Call agents** list. If an agent dismisses or doesn't pick up a call, the call will ring the next agent and will try all agents until it's picked up or times out.

	- **Round robin** - Balances the routing of incoming calls so that each call agent gets the same number of calls from the queue. This design may be desirable in an inbound sales environment to assure equal opportunity among all the call agents.

	- **Longest idle** - Routes each call to the agent who has been idle the longest time. An agent is considered idle if their presence state is Available or if their presence state has been Away for less than 10 minutes. Agents whose presence state has been Away for more than 10 minutes aren't considered idle and won't be eligible to receive calls until they change their presence to Available.

- **Presence-based routing** - Presence-based routing uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method. Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and won't receive calls until their availability status changes back to **Available**.

- **Call agents can opt out of taking calls** - If an agent opts out of getting calls, they won't be included in the call routing list, even if their availability status indicates they're available.

- **Call agent alert time (seconds)** - Agent alert time specifies how long an agent's phone will ring before the queue redirects the call to the next agent.

	‎:::image type="content" source="../media/call-answering-options.png" alt-text="Screenshot of call answering options, with numbered callouts":::

### Call overflow handling

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time. The default is 50, but it can range from 0 to 200. When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

You can choose to disconnect the call or redirect it to any of the call routing destinations. For example, you can have the caller leave a voicemail for the agents in the queue.

‎:::image type="content" source="../media/call-queue-overflow-handling.png" alt-text="Screenshot of call overflow settings":::
 
### Call timeout handling

Call Timeout is the maximum time a call can be on hold in the queue before it's redirected or disconnected. You can specify a value from 0 seconds to 45 minutes. You can choose to disconnect the call or redirect it to one of the call routing destinations. For example, you can have the caller leave a voicemail for the agents in the queue.

‎:::image type="content" source="../media/call-queue-timeout-handling.png" alt-text="Screenshot of call timeout settings":::
 
## Call queue PowerShell cmdlets

You can also create and set up call queues with Windows PowerShell. The following cmdlets can be used to manage a call queue:

- ```New-CsCallQueue```
- ```Set-CsCallQueue```
- ```Get-CsCallQueue```
- ```Remove-CsCallQueue```

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”