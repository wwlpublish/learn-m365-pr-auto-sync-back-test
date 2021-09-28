![Screenshot of conference mode and routing method settings](../media/cq-routing-method.png)


**Conference mode** significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call. Conference mode control how calls are connected to agents. When the administrator turns this off, a call is connected to a call agent using a traditional transfer. If you select Conference Mode On, a call is connected to a call agent much faster than if it uses a traditional transfer by spinning up a conference and bringing in relevant agents and hosted number.  For conference mode to work, agents in the call queue must use one of the following clients:

- The client should be running the latest version of the Microsoft Teams desktop client, Android app, or iOS app.

- The client version must be using Microsoft Teams phone version 1449/1.0.94.2020051601 or later.

Agents' Teams accounts need to be set to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list. We recommend enabling conference mode for your call queues if your agents are all using compatible clients.

> [!NOTE]
> Conference mode is not supported if phone calls are routed to the queue from a Direct Routing gateway that is enabled for Location Based Routing.

> [!TIP]
> Setting Conference mode to **On** is the recommended setting. 

