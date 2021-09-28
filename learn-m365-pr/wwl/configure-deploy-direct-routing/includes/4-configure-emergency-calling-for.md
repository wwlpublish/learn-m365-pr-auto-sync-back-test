If you've deployed Phone System Direct Routing in your organization, you can use emergency voice routing policies in Microsoft Teams to set up emergency numbers and specify how emergency calls are routed. An emergency voice routing policy determines whether enhanced emergency services are enabled for users who are assigned the policy, the numbers used to call emergency services (for example, 911 in the United States), and how calls to emergency services are routed.

You can manage emergency voice routing policies by going to **Voice > Emergency** policies in the Microsoft Teams admin center or by using Windows PowerShell. The policies can be assigned to users and network sites.

For users, you can use the global (Org-wide default) policy or create and assign custom policies. Users will automatically get the global policy unless you create and assign a custom policy. Keep in mind that you can edit the settings in the global policy, but you can't rename or delete it. For network sites, you create and assign custom policies.

If you assigned an emergency voice routing policy to a network site and a user, and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.

## Create a custom emergency voice routing policy

You can create a custom emergency voice routing policy via the Microsoft Teams admin center or PowerShell module.

Perform the following steps to create a custom emergency voice routing policy:

1. Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/)

1. In the left navigation, go to **Voice** and **Emergency policies.**

1. Select the **Call routing policies** tab.

1. Select **Add**

1. Enter a name and description for the policy.

1. To enable dynamic emergency calling, turn on **Dynamic emergency calling**. When dynamic emergency calling is enabled, Teams retrieves policy and location information from the service and includes that information as part of the emergency call.

1. Define one or more emergency numbers. To do this, under **Emergency numbers**, select **Add**, and then do the following:

   1. **Emergency dial string**: Enter the emergency dial string. This dial string indicates that a call is an emergency call.
       > Note: For Direct Routing, Microsoft is transitioning away from Teams clients sending emergency calls with a "+" in front of the emergency dial string. Until the transition is completed, the voice route pattern to match an emergency dial string should ensure a match is made for strings that have and don't have a preceding "+", such as 911 and +911. For example, ^\+?911 or .*.
   1. Emergency dial mask: For each emergency number, you can specify zero or more emergency dial masks. A dial mask is a number that you want to translate into the value of the emergency dial string. This allows for alternate emergency numbers to be dialed and still have the call reach emergency services.For example, you add 112 as the emergency dial mask, which is the emergency service number for most of Europe, and 911 as the emergency dial string. A Teams user from Europe who is visiting may not know that 911 is the emergency number in the United States, and when they dial 112, the call is made to 911. To define multiple dial masks, separate each value by a semicolon. For example, 112;212.

   1. PSTN usage record: Select the Public Switched Telephone Network (PSTN) usage record. The PSTN usage record is used to determine which route is used to route emergency calls from users who are authorized to use them. The route associated with this usage should point to a Session Initiation Protocol (SIP) trunk dedicated to emergency calls or to an Emergency Location Identification Number (ELIN) gateway that routes emergency calls to the nearest Public Safety Answering Point (PSAP).

    > [!NOTE]
    > Note: Dial strings and dial masks must be unique within a policy. This means that for a policy you can define multiple emergency numbers. You can set multiple dial masks for a dial string, but each dial string and dial mask must only be used one time.

1. select **Save**

You have successfully created a location and routing information to allow emergency services to correctly find the location should you require it. This is only suitable for static locations and will need to be amended should people start to work from other locations, home, or hybrid working.

