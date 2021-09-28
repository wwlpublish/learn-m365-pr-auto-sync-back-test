To use Teams Phone, users need a phone number. In this unit, we look at how we can acquire phone numbers from Microsoft or move existing numbers from other PSTN operators to Microsoft, a process known as porting.

## Acquire licenses for phone numbers from Microsoft

To acquire phone numbers and phone service from Microsoft, you need to have one or more users with the Phone System license and one or more users with the Calling plan license.

If you do not already have them, to purchase a Phone System add-on license and Calling Plan license, perform the following steps:

- Navigate to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com/).

- Select **Billing** and **Purchase services**.

- Below **View by category**, select **Add-ons**.

- Select **See all ‎Add-ons‎ products** to extend the list.

- Navigate to **Microsoft 365 Domestic Calling Plan** and select **Details**.

- Select **Start free trial** obtain trial licenses.

- On the Check-out screen, select **Try now** to add the trial licenses to your tenant.

- On the **order receipt** screen, apply with **Continue**.

- Back in the Microsoft 365 admin center, perform the steps for all licenses still missing in your tenant, such as the Phone System add-on.

Teams Phone System is a license enables the ability to make and receive phone calls, turning Teams into a "Private Branch Exchange (PBX)" or phone system. However, to make calls you also need a phone number and Public Switched Telephone Network (PSTN) connectivity. This can be provided by Microsoft Calling plans (an additional license) or via third-party operators with Direct Routing or Operator Connect.

In this unit, we are focused on Microsoft Calling Plans. You can buy Domestic plans that only allow calling within the country of the user and have the option of pay per minute on communication credits for international calls or Domestic and International plans that provide minutes for both domestic and international calls. The number of minutes bundled depends on the country, and the list of countries that have calling plans is constantly expanding. For the latest list of available countries check the Microsoft docs-link in the references section.

Having one or more phone system licenses and calling plan licenses on your tenant will unlock the ability to acquire PSTN phone numbers from Microsoft.

## Acquire phone numbers from Microsoft

Giving phone numbers to users is a two-step process. You must first order some numbers from Microsoft onto your tenant before you can then assign them to individual users or services.

There are two main types of numbers you can acquire: user numbers to be assigned to end users also called subscriber numbers, and Service numbers for services like Auto Attendant, Hunt Groups, Bots, or Conferencing.

**This table defines the number types**

| Number Type| Definition|
| :--- | :--- |
| User (subscriber)| Numbers for users in your organization|
| Call queue (Toll)| Service numbers for call queues|
| Call queue (Toll Free)| Toll free service numbers for call queues|
| Auto Attendant (Toll)| Service numbers for auto attendants|
| Auto Attendant (Toll Free)| Toll free service numbers for auto attendants|
| Dedicated conference bridge (Toll)| Service numbers for PSTN audio conferencing|
| Dedicated conference bridge (Toll free)| Toll free service numbers for PSTN audio conferencing|

Dependent on the country, user and service numbers are available in both geographic and non-geographic area codes. Some countries, such as Denmark, only have non-geographic numbers available. Toll-free service numbers are also available in over 60 countries/regions. These numbers don't typically incur a toll cost to the caller, but the cost is paid for by the tenant organization with communication credits.

The number of Calling Plan user phone numbers you can acquire is equal to the total number Calling Plan licenses multiplied by 1.1 + 10 additional phone numbers. The toll and toll free service numbers also have specific ratios you can acquire. More details of how this works is in a reference link. The limits don't include phone numbers you have ported or transferred to Microsoft.

To acquire phone numbers for your tenant, perform the following steps:

- Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

- Select **Voice** and **Phone numbers**.

- Select **Add** to order more numbers.

- Enter an appropriate **name for your order** and **friendly description**.

- Select a **Country or region.** Some regions will only have service numbers; review the reference links for a list all the countries and regions.

- Select a Number Type, such as **User (subscriber)**.

- Under **Quantity**, enter the number of numbers that you want, within the limit of numbers available to your tenant.

- Select the **City** you want from those available.

- **Location** associates this number set to an emergency address. For European countries, an emergency address must be aligned at time or ordering the numbers. If you don't have the emergency address already defined, you can select **Add a location.**

- Under Area code, select a numeric area code from those available.

- Select **Next**, a set of numbers will be reserved for you for 10 minutes. If you are happy with the numbers press place order to add them to your tenant. If you take more than 10 minutes, the phone numbers will be returned to the pool of numbers.

- If you are happy with the numbers offered, Select **Place Order**

- You will see, thank you, your order has been placed. Select **Finish**

The new numbers will appear in the list of phone numbers as soon as they become available. This can take anywhere between minutes and hours, typically not more than 24 hours.

After performing the described steps, you ordered PSTN Phone numbers from Microsoft and assigned them to your tenant, ready to be assigned to users or services.

## Create Microsoft Port Request for User and Service numbers

You may have existing phone numbers with another carrier/operator that you want to move to Microsoft calling plans; this move is called a "Port." Once numbers are ported, the new service provider, Microsoft in this case, manages them and you can disconnect the service from the old service provider (subject to any contractual requirements you have with them).

You can port or transfer phone numbers in all the supported countries or regions. Most types of numbers can be ported in, but not all. See the link in references for more information on what can't be ported.

How you submit a port order request depends on the country or region where the phone numbers come from. Currently, the porting wizard in the Microsoft Teams admin center supports porting phone numbers for the United Kingdom, United States, and Canada.

To get phone numbers for other countries and regions, you can manually submit a port order.

After you've completed the port order request, it takes between 7-14 days to be processed. However, depending on your service provider it may take up to 30 days. If there are issues with any of the information, it can take longer. Don’t disconnect or cancel any of the phone numbers with your current provider before or while porting, as this can stop the process.

Each port must be for numbers with a single provider. You also must submit separate port orders for each type of number, for example user, toll service number(s), toll free service number(s).

### Information needed for a Port

As part of your port request, you need to fill out and upload a Letter of Authorization ‎(‎LOA)‎. The person authorized on the account must sign it, scan it (or take a good photo with one of those "scanning apps"), and sent it to Microsoft.

To complete a port, you need the following information:

- The account information for your current carrier such as account number, carrier name, address, Billing Telephone Number (BTN) for the range

- You also need to know the exact name and address on the account. The "service address"

- The numbers/number range you want to port in E.164 format

It is best to validate this information with your current provider before beginning the port process, as incorrect information, even slightly incorrect like a different spelling of the account holder or company name, can cause a port to be rejected or delayed.

### Creating a port request with the porting wizard

For the United Kingdom, United States, and Canada you can use the porting wizard in the Teams Admin Center.

- Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

- Select **Voice** and **Phone numbers**.

- Select **Port**

- Review the information provided about the porting process, Select **Next**.

- Select a **Country or region.** Some regions will only support porting in service numbers. Review the reference links for a link to Microsoft docs.

- Select the **country** and **type** of phone numbers you wish to port in. The type options are based on the country or region you select

- Fill in the **order name**, Email for **Notification emails,** and **desired transfer date** (the "losing" provider will define the actual date, called an FOC (Firm Order Commitment) date).

- Fill in the Authorizing person on account details, i.e. the details of the person on the existing providers account; **organization name, name, job title, phone number, email address, organization address**.

- Fill in the **current provider details**, **the Billing Telephone Number (BTN), Account number, carrier name, and address.**

- Fill in the **service address** this is the address the existing operator would associate with the customer and number range

- Upload the number range in a CSV Comma-Separated Value) file that has only one column named PhoneNumber (note, one word, no spaces). Each phone number is listed per row in E.164 format, e.g., +1425550199

- On the Complete your order page, upload a signed Letter of Authorization to upload a scanned copy of the signed Letter of Authorization (LOA).

- Select **submit** to complete the order.

After performing the described steps, you have completed a port request using the porting wizard.

To see the status of your port order, in the left navigation of the Microsoft Teams admin center > Voice > Port orders, and then select Order history.

### Creating a manual port request

For all countries other than the United Kingdom, United States, and Canada you must submit your port order manually to Microsoft.

To manually submit a new port order, you must do the following steps in order:

- Download the Letter of Authorization ‎(‎LOA) for the country or region. Available from Microsoft docs. Link in the resources section.

- Complete the form.

- Send it to the Microsoft PSTN service desk.

> [!NOTE]
> Note, there's a tick box to specify if you're porting user vs. service numbers. Each port must only be for one number type.

To contact the PSTN service desk, perform the following steps:

- Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

- In the left-hand pane, select **Phone numbers**.

- At the top of the page, select **Get phone number support**.

- This will open a link to the **Phone Number Service Center**.

- Select Create a new case

- Select the **Case category,** “Submit new request”

- Select the **Country** that relates to the numbers being ported

- Provide an appropriate **Title** and **Description**

- **Submit** the case.

- Microsoft will communicate with you and update in the portal under **view my existing cases**

After performing the described steps, you have performed a manual number port from another operator to Microsoft.

## Create request to convert Service number to User number or User number to service number

Sometimes you may need to covert user numbers to service numbers or service numbers to user numbers. You can do this by contacting the Microsoft PSTN Service Desk.

- Navigate to the Microsoft Teams admin center at [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

- In the left-hand pane, select **Phone numbers**.

- At the top of the page, select **Get phone number support**.

- This will open a link to the **Phone Number Service Center**.

- Select Create a new case

- Select the **Case category,** “Submit new request”

- Select the **Country** that relates to the numbers being converted.

- Provide a **Title** and **Description** and request an "Inventory Type Change.” List the number(s) you wish to convert.

- **Submit** the case.

- Microsoft will make the change and you will receive an update in the portal under **view my existing cases.**

After performing the described steps, you have converted Service number to User number or User number to service number.

