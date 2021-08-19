Microsoft Teams Phone System provides auto attendants and call queues. These features enable external and internal callers to move through a menu system to place calls and transfer calls to users or departments in an organization. Companies can use these tools to design and build phone systems that satisfy their exact business needs.

## What is the auto attendant service?

An auto attendant provides a caller with a series of voice prompts or audio files rather than interacting with a human operator. 

When people call a number associated with an auto attendant, their choices can redirect the call to a user or locate someone in the organization and then connect to that user. They can express their choices and interact with the menu system by using either a phone keypad or speech recognition. The choices they make can also redirect the call to another auto attendant or to a call queue. An auto attendant service can:

- Deliver corporate or informational greetings.
- Provide custom corporate menus, which can be customized.
- Search a directory for a name.
- Enable callers to reach or leave a message for a person in the organization.
- Support multiple languages for prompts, text-to-speech, and speech recognition.
- Specify holidays and business hours.
- Transfer calls to an operator, other users, call queues, and auto attendants.
- Support shared voicemail for callers to leave a message for an organization.

## What are call queues?

Call queues organize calls into queues while alerting a group of users with a choice of different alerting methods.
Cloud call queues can provide:

- A greeting message.
- Music while people are waiting on hold.
- Redirection of calls to agents in mail-enabled distribution lists and security groups.
- Configuration parameters such as queue maximum size, timeout, and call handling options.
- Shared voicemail for callers to leave a message for an organization.

The following image shows what an attendant would see when a caller was in a call queue:

‎:::image type="content" source="../media/answer-auto-attendant-and-call-queue-calls-image1.png" alt-text="Phone system layout":::

## Business decisions

Before an organization sets up auto attendants and call queues, it must decide how it wants to use these features in its business. These decisions will determine how it configures the auto attendant and call queue services. The following list provides a series of typical questions that an organization should consider when planning their auto attendant and call queue features:

- What languages do you need? Where are these languages needed - which department or group?
- Do you want to allow voice inputs from callers or only dialing inputs?
- Do you need separate call routing for off hours or holidays? What are the hours and holidays?
- Do you want to allow agents in a call queue to opt out of taking calls?
- Do you want agents in your call queues or your operator to have a specific caller ID if they dial out?
- Do you want to enable [call parking and retrieval](/microsoftteams/call-park-and-retrieve) in your organization to help with call handoffs between people or departments?
- For the voice prompts, do you want to record your own or use the system-generated voice? 

## Technical decisions

When using auto attendants and call queues to connect callers to people in your organization, there are some technical decisions to make before you start the configuration.

* **How should agents be added to call queues?** Agents can be added to call queues in the following ways:

    - Individual users
    - Distribution lists
    - Security groups, including mail-enabled security groups
    - Microsoft 365 Groups or Teams

    You can use a combination of these options for each queue if needed. Groups that have an email address can be used for voicemail. Using Teams offers many advantages, including:
    
    - shared file storage and chat between agents
    - a common mailbox where voicemails can be received
    - an extensible platform that can include integration with your line-of-business applications or Power Apps

* **Do you need to port existing phone numbers?** If you have an existing auto attendant and call queue infrastructure and you're migrating to Teams, you'll need a plan to transfer your existing phone numbers to the new auto attendants and call queues. 

* **Do you want to use Conference mode?** Conference mode is call queue option that significantly reduces the amount of time it takes to connect Teams VOIP calls and PSTN calls to an agent. 

* **Do you want to set Teams-only coexistence mode for agents?** If you set agents' Teams accounts to Teams-only mode, agents who don't meet the requirements aren't included in the call routing list.

* **Should you implement Zero Licensing cost?** When using nested auto attendants, as long as they don't have a phone number assigned, you won't need a license.


## Call routing with auto attendants and call queues

Auto attendants route calls in one of the following ways:

- **Redirect immediately**. Calls can be redirected to one of the call routing destinations immediately upon answering or after an initial greeting.
- **Redirect based on dial options**. Callers can be directed to choose between options that are assigned to the numbers on their telephone keypad, 0-9. Each dial key can be assigned a call routing destination.
- **Dial people by name or extension**. Callers can be directed to dial the extension number of the person they're trying to reach in the organization's directory, or by spelling the person's name.
- **Disconnect**. An auto attendant can hang up the call.

When calls are redirected by an auto attendant or call queue, you can choose from the following call routing destinations:

- **A person in the organization**. This person must be able to receive voice calls. They can be an online user or a user hosted on-premises using Skype for Business Server.
- **Voice app**. Another auto attendant or a call queue. Choose the resource account associated with the destination.
- **External phone number**. Any phone number. 
- **Voicemail**. The voice mailbox associated with a Microsoft 365 group that you specify. You can choose if you want voicemail transcriptions and the "Please leave a message after the tone" system prompt.
- **Operator (auto-attendant only)**. The operator defined for the auto attendant. Defining an operator is optional. An operator can be any of the other destinations in this list.

Auto attendants offer separate call routing options for calls received outside of business hours and on holidays. 
- After-hours call routing allows all the options listed above. 
- Holiday call routing allows only redirecting or disconnecting a call, but no dial key options.

Call queues place the caller on hold until an agent assigned to the queue is available to take their call. There are two situations where a caller may be directed out of the queue:

- **Call overflow**. If the number of calls in the queue exceeds the limit that you set, then new callers are redirected out of the queue.
- **Call timeout**. If a caller has been in the queue longer than the configured timeout setting, they're redirected out of the queue.

Calls redirected out of a queue can be sent to any of the call routing destinations listed above, except for an operator. Call queues don't have operators, but you can redirect callers to the same destination as an operator that you've configured for an auto attendant.


## Design call routing flow

As part of the planning process, it's recommended that you design the call routing for your organization in a diagram. The diagram helps determine the most efficient routing for people calling into your organization. You can also use the diagram to determine the auto attendants and call queues that must be created, along with related requirements such as service numbers, licenses, and resource accounts. 

The following diagram shows an example of call routing using auto attendants and call queues.

‎:::image type="content" source="../media/aa-lawyeroffice-callqueues.png" alt-text="Example auto attendant design":::


## Knowledge check<br>

Choose the best response for the following question. Then select “Check your answers.”