When you have designed and started setting up and using your call queues, you can use more advanced features to help refine and automate the phone system process.

Suppose that, in your digital camera manufacturer, support calls from customers are routed to first line or second line support desks. You want to ensure that the calls go to the right desk and that they're assigned fairly to agents, based on how long each agent has been idle.
Here, you'll learn how to control these call routing options.

## Ordering individual agents

When you edit the call answering options for a call queue, you can choose who can answer the calls.

:::image type="content" source="../media/5-call-answering.png" alt-text="Call Answering Options":::

To add individual agents directly, without adding them to a group, select **Add users**. Place individual agents in the order in which you want them to receive the call. You can add up to 20 individual agents. To add more than 20, use a group.

Calls are routed first to individual agents, then to the agents in groups.

## Routing Method

In the image above, you can see that you have a choice of routing methods for the call queue.

You can choose either **Attendant, Serial, Longest idle**, or **Round Robin** as the distribution method. All new and existing call queues have attendant routing selected by default.

- **Attendant routing** causes the first call in the queue to ring all call agents at the same time. The first call agent to pick up the call gets the call.

- **Serial routing** incoming calls ring all call agents one by one, from the beginning of the call agent list. Agents can't be ordered within the call agent list. If an agent dismisses or doesn't pick up a call, the call will ring the next agent and will try all agents until it's picked up or times out.

- **Longest idle** routes the next available call to the call agent whose has been idle the longest time. The idle time is defined as the length of time a call agent's presence state is set to Available or Away (if less than 10 minutes), at the time of the call. If a call agent's presence is set to Away for more than 10 minutes, the idle timer resets. Presence states of users are queried every minute.

## Learn more

- [Ordering individual agents](https://docs.microsoft.com/microsoftteams/create-a-phone-system-call-queue#select-the-call-answering-options)
