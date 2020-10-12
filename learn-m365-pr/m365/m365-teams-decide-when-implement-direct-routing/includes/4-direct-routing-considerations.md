When considering whether Direct Routing is right for your organization, make sure you plan for service numbers and dynamic emergency calling.

In your clothing retailer, you've been asked at the recent board meeting, how your proposed Direct Routing implementation will handle the main sales phone number for your company, which handles a large volume calls and uses a menu system and a queue. You want to make sure this arrangement is possible in Direct Routing and you also want to find out how emergency numbers will be handled.

Here, you'll learn about service numbers and emergency dialing in Direct Routing.

## Plan for service numbers

Microsoft has two types of telephone numbers:

- **Subscriber numbers**. These are numbers that can be assigned to users in your organization.
- **Service numbers**. Service numbers handle a higher volume of calls, compared to numbers assigned to individual users. They are designed to handle a high concurrent call capacity and are typically toll or toll-free. Service numbers are also assigned to services such as audio conferencing, auto attendants, or call queues.

Direct Routing supports service numbers with call queues and auto attendants. A call queue provides a greeting message and music while people are on hold. Auto attendant provides a menu system for external and internal callers to allow them to be put through to the correct person or department.

Dial-in conferencing, however, isn't supported in Direct Routing. You can only use dial-in conferencing if you have a government platform plan, such as **GCC High** or **Department of Defense (DoD)**, which do support dial-in conferencing.

## Plan for dynamic emergency calling

You'll also need to consider emergency calling, and how you want to configure it. Dynamic emergency calling, also named E-911 in the USA, is supported by both Direct Routing and Calling Plans. You'll require an additional Emergency Routing Service Provider and have a Session Border Controller (SBC) that supports emergency routing.

## Learn more

- [Getting service phone numbers](https://docs.microsoft.com/MicrosoftTeams/getting-service-phone-numbers)
- [Manage emergency calling](https://docs.microsoft.com/MicrosoftTeams/what-are-emergency-locations-addresses-and-call-routing)
- [List of Session Border Controllers certified for Direct Routing](https://docs.microsoft.com/MicrosoftTeams/direct-routing-border-controllers)
