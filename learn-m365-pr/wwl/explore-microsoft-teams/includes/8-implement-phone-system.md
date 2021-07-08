Before an organization implements calling within Microsoft Teams, it must compare its business requirements to Microsoft Teams’ calling features. These features include:

 -  Connecting to the Public Switched Telephone Network (PSTN)
 -  Service availability and user locations
 -  Microsoft 365 Phone System licensing
 -  Phone numbers and emergency locations
 -  Voicemail
 -  Optional: Calling identity
 -  Optional: Dial plans

### Connecting to the PSTN

The Public Switched Telephone Network (PSTN) is used for landline telephone systems. For users to place and receive calls to the PSTN by using Teams, Microsoft 365's Phone System must be installed and connected to the PSTN.

#### **Example**

To better understand how Microsoft 365's Phone System works together with a company's PSTN connection, imagine you’re buying a mobile phone. The phone has nice features (such as buttons and apps), but to make calls you’ll need a call plan with a phone provider, who gives you an actual phone number and provides connectivity to the PSTN.

Microsoft 365's Phone System is the equivalent of the mobile phone. In other words, it provides functionality such as voicemail, but it doesn't provide a phone number or let you place or receive phone calls to or from the PSTN. For connecting Phone System to the PSTN—the equivalent of a contract with a phone provider—Microsoft offers Calling Plans. Calling Plans is an add-in to the Phone System feature in Microsoft 365. With Calling Plans, Microsoft provides each user a phone number that can be used to place and receive calls.

Calling Plans are currently the only way to connect Microsoft 365 Phone System to the PSTN. In the future, any existing telephone environment that an organization has on-premises can be connected to Teams.

### Service availability and user locations

Phone System is available where Microsoft 365 is available (for the complete list of countries and regions, see [International availability](https://products.office.com/business/international-availability?azure-portal=true)). The availability of the Calling Plans service is a little more restricted. The commercial availability of Phone System and Calling Plans depends on two factors:

 -  Where an organization is based
 -  In which country or region the organization has a commercial relationship with Microsoft and its partners

Calling Plans can be assigned and used only for users located in countries and regions where calling plans are available. Calling Plans can only be purchased if a company's billing address is located in a country or region where Audio Conferencing can be purchased.

#### **Example 1**

Contoso's billing address is in Austria. The company wants to use Phone System with Calling Plans for their users in Germany. Although the Calling Plans are available in Germany, they aren’t available in Austria. However, Audio Conferencing can be purchased in Austria, so Contoso can buy the required licenses for their users in Germany.

#### **Example 2**

Fabrikam, Inc. is a company based out of Hong Kong SAR, with some users in the United States. Their billing address is in Hong Kong SAR. Although Microsoft can provide a phone number for Audio Conferencing in Hong Kong SAR, Audio Conferencing isn’t available for purchase in that region. Unfortunately, this situation means that Fabrikam can't acquire Calling Plans for their US-based users.

**Action**: Review [Country and region availability for Audio Conferencing and Calling Plans](/SkypeForBusiness/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans) for the following information:

 -  For the country or region where your billing address is located, check whether Audio Conferencing is available for purchase. You can buy Calling Plans if Audio Conferencing is available for purchase.
 -  For every country or region where you want users to use Calling Plans, check the “Is Phone System available for purchase?” option to learn whether Calling Plans are available in that country or region.

### Phone System licensing

A Phone System license is available as part of Office 365 E5 subscription plans, or as an add-on service to Office 365 E3 subscription plans.

Because Calling Plans is an add-in to the Phone System feature in Microsoft 365, users must be assigned a Phone System license to use Calling Plans. In general, there are two types of Calling Plan add-ins:

 -  Domestic Calling Plan
 -  International and Domestic Calling Plan

Each Calling Plan type provides an allocation for calling minutes that users can use per month, either to make domestic calls or international calls. The number of minutes varies by country or region. Once a user has exhausted their allocation of minutes, they can't make outbound calls (except for Emergency Services calling) until the next month’s billing cycle.

As you might expect, a Domestic Calling Plan costs less than the International and Domestic Calling Plan. Typically, not everyone in an organization needs to make international calls. Individual users can be assigned to different calling plans based on the user’s business requirements. This flexibility can help an organization control the costs of its Phone System with Calling Plans implemented.

Communications Credits can be set up so that users can make calls even after they’ve used up their minutes. They can do so without having to wait until the next month’s billing cycle. As soon as a user's allocation is exhausted, the user can pay based on their consumption. Communications Credits can also be used to let users who have been assigned to a Domestic Calling Plan make international calls, which are then charged by using a “pay-per-minute” model.

> [!TIP]
> Review the Calling Plans section in [Country and region availability for Audio Conferencing and Calling Plans](/SkypeForBusiness/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans) to understand the calling minutes allocation for each Calling Plan add-in type.

**Additional reading.** For more information on phone system licensing, see:

 -  [What are Calling Plans in Office 365?](/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-calling-plans-in-office-365)<br>
 -  [What are Communications Credits?](/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits)

### Phone numbers and emergency locations

For Phone System with Calling Plans implementation, every user in an organization must have a unique subscriber (user) phone number. Subscriber (user) phone numbers can be obtained directly from Microsoft, or existing phone numbers can be transferred (ported) to Microsoft.

> [!NOTE]
> The complexity of obtaining or transferring phone numbers varies greatly depending on country/region, carrier, number of circuits involved, and many other contributing factors.

Besides ensuring that every user has a unique phone number, an organization must assign an emergency address to each phone number. This address can be assigned either when the phone number is assigned, or when its first acquired, depending on the country/region. The emergency address is required to support emergency services calling. It must be validated to ensure the address is recognized and it’s in the correct format for emergency response services to use.

To give emergency responders more exact information about the location of an organization's users, the organization can define emergency locations and associate them with validated emergency addresses. An emergency location is typically a building number, floor, building wing, or office number where the user is located.

**Additional reading.** For more information on phone numbers and emergency locations, see:

 -  [Different kinds of phone numbers used for Calling Plans](/SkypeForBusiness/what-are-calling-plans-in-office-365/different-kinds-of-phone-numbers-used-for-calling-plans).
 -  [Manage phone numbers for your organization.](/SkypeForBusiness/what-are-calling-plans-in-office-365/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization)
 -  [Transfer phone numbers to Office 365](/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365).
 -  [What are emergency locations, addresses and call routing?](/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-emergency-locations-addresses-and-call-routing)
 -  [Emergency calling terms and conditions](/SkypeForBusiness/legal-and-regulatory/emergency-calling-terms-and-conditions).

### Voicemail

Phone System voicemail is powered by Azure Voicemail services. It only supports voicemail deposits to Exchange mailbox, and it doesn’t support third-party email systems.

By default, Phone System voicemail works with Exchange Online. It has a minimum [supported Exchange on-premises version and deployment model](https://support.microsoft.com/help/3195158/customer-issues-between-exum-and-azure-voicemail?azure-portal=true) to allow delivery of voicemail messages to user mailboxes in the on-premises Exchange deployment.

Phone System voicemail includes voicemail transcription, which is enabled by default for all users in an organization. A business may require that voicemail transcription be disabled for specific users or everyone throughout the organization.

> [!NOTE]
> A fallback mechanism has been implemented so that Phone System voicemail can resend messages by using SMTP. This design means users who have a mailbox on a third-party email system will receive their voicemail messages. This mechanism doesn’t include guaranteed service uptime or other voicemail features such as changing voicemail greetings.

**Additional reading.** For more information, see [Azure PBX voicemail support for Exchange Server](https://support.microsoft.com/help/3195158/customer-issues-between-exum-and-azure-voicemail?azure-portal=true) to understand how to enable on-premises Exchange to support Phone System voicemail.

### Optional: Calling identity

By default, all outbound calls use the assigned phone number for the calling identity (Caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call. In some cases, there are legitimate business reasons to display a different number to mask the identity of a caller.

#### **Example**

Contoso is using Phone System with Calling Plans for their users. However, their business requirement demands that if the receptionist calls a phone number, the caller ID shouldn’t represent the phone number of the receptionist but rather the main phone number of the office.

Other calling identity options include the ability to block (anonymize) Caller ID presentation altogether, and to give users the choice of using their caller ID or calling out anonymously. Caller ID can also be blocked for incoming calls.

**Additional information.** For more information, see [How can caller ID be used in your organization](/SkypeForBusiness/what-are-calling-plans-in-office-365/how-can-caller-id-be-used-in-your-organization).

### Optional: Dial Plans

A Dial Plan in the Microsoft 365 Phone System feature controls how users dial phone numbers on the dial pad. The PSTN expects phone numbers in a specific format that starts with a plus sign (+) followed by digits that represent an E.164 number. E.164, which is the standard for PSTN numbers, specifies country/region codes.

Obviously, users prefer not to use that long format when dialing phone numbers. When they’re calling a local number, they want to avoid having to enter an area code or a country/region code. Organizations can address this issue through calling plans, which can normalize a user-entered phone number to the required format.

#### **Example 1**

Alice wants to call the phone number +1 311-555-2368. Because Alice is in the United States, based out of Seattle (area code 206), she only needs to dial **311-555-2368**. Microsoft Teams will normalize this phone number to the full number +1 311-555-2368 before routing it to the PSTN.

By default, a generalized dialing behavior is implemented by the automatically assigned Dial Plan (also known as a *service dial plan*) based on each individual user’s license usage location. This generalized dialing behavior may not meet user requirements. For example, it may require the user to dial an area code to make local calls. In such a case, an organization will need a customized Dial Plan (also known as a *tenant dial plan*) so that users can dial phone numbers the way they’re accustomed to. In other words, they can omit the area code for local calls and use short-digit dialing to call other users in the same location or office.

#### **Example 2**

Bob also wants to call the phone number +1 311-555-2368. Because Bob is located in the 311 area code, he wants to place the call by dialing **555-2368**. Teams can be configured to accommodate Bob’s dialing behavior and normalize the phone number to the correct format before sending it to the PSTN.

By assigning different dial plans to different users, an organization can create a specific experience matching the different requirements of its users. For example, the organization may have users in one location who want a dialing experience that’s different from users in another location.
