A call queue can organize a large number of incoming calls and make sure that they are answered in turn. Callers don't like to spend a lot a time waiting in a queue, so plan your queues carefully to minimize long waits.

You want to plan the use of call queues in your digital camera manufacturer. You're going to use queues to ensure that calls are not dropped, even during busy times, but you want to avoid callers getting bored by long waits and dropping their call.
Here, you'll learn what questions to answer when you plan call queues.

## Assess business need

The first stage in planning a call queue is to understand the business needs. This can be done by using the following the steps.

### How many call agents will you assign to the queue?

Imagine that your company has 25 call agents in their existing call center. There are typically 12-20 agents active at one time.

### How is the existing system setup, and what changes do you want to make?

Suppose there's an auto attendant system for the company office and there's an option in that system that routes to retail ordering, but it only connects one or two calls a day. You have a 1-800 number for placing orders for delivery and advertise it heavily. The legacy call queue service provides a single auto attendant node in front of the call queue to provide a different caller experience during business hours and outside business hours.

You must decide whether to implement this arrangement in Teams or to replace it with a more efficient configuration.

### Will the call center be active 24 hours a day, or only during business hours?

For example, the queue might need to be in use from 11am to 11:30pm, seven days a week.

### Do you want distinct initial greetings for business hours, after-hours, weekends, or holidays?

For example, if the call rate outside of their business hours is low, you can consider using special greetings.

### How are the agents compensated?

Suppose the agents that receive call are paid on an hourly basis plus a performance bonus, and their performance is tracked in the ordering system. There was a perception that one agent was getting favored by the queue's distribution of calls. Ensure your agents know that calls are distributed fairly.

### What is the usual size of the call queue in the existing call center?

Suppose that, depending on the hour, the call queue can vary from 5 to 30. Wait times are known to be up to 3 minutes most of the time, and 5 minutes at peak times. Consider carefully whether callers are likely to put up with these times.

### Do you want to play hold music?

Hold music can help to reassure queuing callers but must be carefully chosen to avoid irritation and fit with your brand.

## Design and mockup

A cloud call queue has a limited number of options. The main decisions to make for the queue are:

- Whether to assign a number directly to the queue or to have callers connect to an auto attendant first
- Whether to have an initial greeting as part of the call queue. Alternatively, an auto attendant can provide a greeting
- What hold music to use
- How to distribute the calls among the available agents

The following diagram shows an example call queue design without an attendant.

:::image type="content" border="false" source="../media/5-plan-call-queues.png" alt-text="Design Call Queues":::

The following diagram shows an example call queue design with an attendant.

:::image type="content" border="false" source="../media/5-plan-call-queues-with-att.png" alt-text="Design Call Queues with auto attendant":::

## Write the scripts

As for auto attendants, make sure your scripts are planned carefully and consider having them professionally recorded. The goal is to connect the caller to a live person as efficiently as possible.

## Implement a call queue

Let's examine the steps to implement a call queue.

1. In the Microsoft Teams admin center, select **Voice > Call queues**, then select **+ Add queue**:

    :::image type="content" source="../media/5-new-call-queue.png" alt-text="New Call Queue":::

    In the image above, we've numbered the key fields 1 and 2 to make them easier to reference.  Below are the suggested settings.

    |Option | Setting |
    |-------|---------|
    |**1 - Name**   |Enter a descriptive display name for the call queue. This name is required and can contain up to 64 characters, including spaces. This name is displayed in the notification for the incoming call.|
    |**2 - Add Accounts**|All call queues are required to have a resource account. Resource accounts aren't required to have a service toll or toll-free phone number.|

1. Next, set the greeting:

    :::image type="content" source="../media/5-set-greeting.png" alt-text="Set Greeting":::

    In the image above, we've numbered the key fields 1 and 2 to make them easier to reference.  Below are the suggested settings.

    |Option | Setting |
    |-------|---------|
    |**1 - Greeting**| The optional greeting played for people who call the call queue number. You can upload an audio file (.wav, .mp3, or .wma formats).|
    |**2 - Music on hold**| You can use the default Music on Hold provided with the call queue. You can also upload an audio file in .wav, mp3, or .wma formats to use as your custom Music on hold.|

1. Now you can select the **Call answering** options:

    :::image type="content" source="../media/5-call-answering.png" alt-text="Call answering":::

    In the image above, we've numbered the key fields 1 through 4 to make them easier to reference.  Below are the suggested settings.

    |Option | Setting |
    |-------|---------|
    |**1 - Call agents and groups**| To add individual agents directly, without adding them to a group, click **Add users**. Put individual agents in the order in which you want them to receive the call. You can add up to 20 individual agents (to add more than 20, put them in a group). |
    |**2 - Conference mode**| Conference mode significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call. If you have more than one call queue, you can enable conference mode on some or all of your call queues; enabling or disabling conference mode on one call queue doesn't impact any other call queues. |
    |**3 - Routing method**| You can choose either **Attendant, Serial, Longest idle, or Round Robin** as the distribution method. All new and existing call queues have attendant routing selected by default. When attendant routing is used, the first call in the queue rings all call agents at the same time. The first call agent to pick up the call gets the call. |
    |**4 - Presence-based routing**| Presence-based routing uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method. Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and won't receive calls until their availability status changes back to Available. |

1. Choose agent opt-out options:

    :::image type="content" source="../media/5-agent-opt-out.png" alt-text="Agent Opt Out":::

    In the image above, we've numbered the key fields 1 and 2 to make them easier to reference.  Below are the suggested settings.

    |Option | Setting |
    |--------------------|---------|
    |**1 - Agent can opt out of getting calls**| You can choose to allow call queue agents to opt-out of taking calls from a particular queue by enabling this option.  Enabling this option allows all agents in this queue to start or stop receiving calls from this call queue at will. You can revoke the agent opt-out privilege at any time by clearing the check box, causing agents to become automatically opted in for this queue again (the default setting for all agents). |
    |**2 - Agent alert setting**| This defines the duration of an agent being notified of a call before the Serial or Round Robin routing methods move to the next agent. The default setting is 30 seconds, but it can be set for up to 3 minutes. |

1. Finally, you can set the overflow handling options.

    :::image type="content" source="../media/5-overflow-handling.png" alt-text="Overflow Handling":::

    In the image above, we've numbered the key fields 1 through 4 to make them easier to reference.  Below are the suggested settings.

    |Option | Setting |
    |-------|---------|
    |**1 - Maximum calls in the queue**| Use this to set the maximum calls that can wait in the queue at the same time. The default is 50, but it can range from 0 to 200. When this limit is reached, the call is handled in the way you set on the When the maximum number of calls is reached setting below. |
    |**2 - When the maximum number of calls is reached**| When the call queue reaches its maximum size (set using the Maximum calls in the queue setting), you can choose what happens to new incoming calls. |
    |**3 - Call Timeout: maximum wait time**|  You can also decide how much time a call can be on hold in the queue before it times out and needs to be redirected or disconnected. Where it's redirected is based on how you set the When a call times out setting. You can set a time from 0 to 45 minutes. |
    |**4 - When call times out**| When the call reaches the limit you set on the How long a call can wait in the queue setting, you can choose what happens to the call. |

## Edit and Test your call queues

After you've saved your call queue, it will be listed on the call queues page of the Admin center. This display will allow you to see at a glance some of the options that you have set up.
The best way to test the implementation is to call the number configured for the call queue.

## Learn more

- [Planning and implementing call queues](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-cq)
- [Creating a cloud call queue](/MicrosoftTeams/what-are-phone-system-auto-attendants)
