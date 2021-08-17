Before you can set up users in your organization to make and receive phone calls, you must get phone numbers for them. There are three ways to get new user numbers:

- **Use the Teams admin center**. For some countries/regions, you can get numbers for your users by using the Teams admin center, see Getting phone numbers for your users below.
- **Port your existing numbers**. You can port or transfer existing numbers from your current service provider or phone carrier to Microsoft 365 or Office 365. For more information, see **Manage phone numbers for your organization** in the **Additional resources** section in the Summary.)
- **Use a request form for new numbers**. Sometimes (depending on your country/region) you won't be able to get your new phone numbers using the Teams admin center, or you will need specific phone numbers or area codes. If so, you will need to download a form and send it back to us. For more information, see **Manage phone numbers for your organization** in the **Additional resources** section in the Summary.

### Getting phone numbers for your users

Use the Microsoft Teams admin center to obtain new phone numbers for your users. You must be a Teams service admin to make these changes.

1. Go to the Microsoft Teams Admin Center.
1. In the left navigation, go to **Voice** > **Phone numbers**, and then select **Add**.
1. Under **Order name**, enter a description for the order.
1. Under **Location and quantity**, do the following:
    1. Under **Country or region**, select a country or region.
    1. Under **Number type**, select **User (subscriber)**.
    1. Under **Location**, select a location. If you need to create a new location, select **Add a location**.
    1. Under **Area code**, select an area code.
    1. Under **Quantity**, enter the number of numbers that you want for your organization, and then select **Next** to select your numbers.
1. Select the numbers you want. You have 10 minutes to select your phone numbers and place your order. If you take more than 10 minutes, the phone numbers will be returned to the pool of numbers.
1. When you're ready to place your order, select **Place order**.

> [!IMPORTANT]
> The number of phone numbers for users (subscribers) is equal to the total number of **Domestic Calling Plan** and/or **Domestic and International Calling Plan** licenses you have assigned multiplied by 1.1, plus 10 additional phone numbers. For example, if you have 50 users in total with a Domestic Calling Plan and/or Domestic and International Calling Plan, you can acquire **65** phone numbers (**50 x 1.1 + 10**). For information see **How many phone numbers can you get?** in the **Additional resources** section in the Summary. If you need to get more phone numbers than this, see **Ways to contact support for business products - Admin Help** in the **Additional resources** section in the Summary.

### Port your existing numbers

The procedure to port or transfer numbers from your service provider or phone carrier depends on how many numbers you are dealing with. If you are working with 999 numbers or fewer, use the porting wizard in the Microsoft Teams Admin Center using the procedure described in **Transfer phone numbers to Teams** below.
If you need to port more than 999 numbers, you must manually submit  a port order.

### Transfer phone numbers to Teams

> [!NOTE]
> This is a preview or early release feature
Use the porting wizard in the Microsoft Teams admin center to transfer your phone numbers from your current service provider to Teams. After you port your phone numbers to Teams, Microsoft will become your service provider and will bill you for those phone numbers.
If you have service numbers for dial-in conferencing bridges, auto attendants or other service numbers, toll-free phone numbers, or have more than 999 user (subscriber) phone numbers that you need to transfer to Teams, see the **Manage phone numbers for your organization** web page in the **Additional resources** section below to download the correct forms and send them to us.

#### Create a port order and transfer your phone numbers to Teams

If you currently have a phone service provider or carrier and already have phone numbers for your users or services, you need to create a "port order" to transfer those phone numbers to Microsoft Teams. When the numbers are ported over, you can assign those phone numbers to your users and services such as audio conferencing (for conference bridges), auto attendants, and call queues.
After you port your phone numbers over to Teams, Microsoft becomes your service provider and you can disconnect your service with your old service provider or carrier.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone numbers**. Select **Numbers**, and then select **Port** to start the porting wizard.
1. Review the information on the Get started page, and then when you're ready, select Next.
1. On the **Select country/region and number type** page, specify the following, and then select **Next**:

    - Country or region: Country or region where you're getting numbers.
    - Type of phone numbers: Type of number, such as geographic or toll-free numbers.
    - Numbers assigned to: What the numbers are assigned to. For example, users, or conferencing or voice features.

    :::image type="content" source="../media/select-country-region-number-type.png " alt-text="Porting Wizard – Select country/region and number type.":::

1. On the Add account information page, complete the following, and then select Next.

    > [!IMPORTANT]
    > The information displayed on this page is determined by the country or region and number type. Each country and region have different regulations on the information that's required to port numbers. What you see on this page may be different from what's described here.

    - **Order details**:
      - **Order name**: Name of your order
      - **Notification emails**: Email addresses to receive order notifications. If you enter multiple email addresses, separate each with a semicolon.
      - **Transferred date**: Transfer date issued by your current service provider.
    - **Phone number details**
      - **Port type**: Whether you're doing a full-port to transfer all your numbers or a partial-port to transfer some of your numbers.
    - **Person requesting details**
      - Your organization name and contact details of the person requesting the transfer.
    - **Current provider's details**
      - **Billing telephone number (BTN- )**: Your BTN in E.164 format, which requires a + sign to prepend the number. For example, for a North America number, use +1XXXYYYZZZZ format.
      - Other details including the name of your current service provider, your account number, and your service address.
      - Select **Next**.

    :::image type="content" source="../media/4-add-account-information-inline.png" lightbox="../media/4-add-account-information-expanded.png" alt-text="Porting Wizard – Adding account information.":::

1. On the **Add numbers** page, select **Select a file**, browse to and select the CSV file that contains the phone numbers that you want to transfer, and then select **Next**.

    > [!NOTE]
    > The CSV file must have only one column with a header named PhoneNumber. Each phone number must be on a separate row and can be digits only or in E.164 format.

1. On the **Complete your order** page, select **Upload a signed Letter of Authorization** to upload a scanned copy of the signed Letter of Authorization (LOA).

    If you haven't already downloaded and signed the LOA, do the following:
      1. Select Download the template to download the LOA for your country or region.
      2. Print the LOA.
      3. Have the LOA signed by the person who is authorized to make changes to the account.
      4. Scan the signed LOA, and then select Upload a signed Letter of Authorization to upload it.

    > [!NOTE]
    > After you upload your LOA, submit your order. Just uploading the LOA isn't sufficient. You have to also submit the order for it be processed.

1. Review your order details, and then select **Submit**.

#### What numbers can be transferred

In general, you can transfer any phone number that's from a supported provider, including:

- Land line phone numbers.
- Mobile device phone numbers such as those used for cell phone and tablets.
  
  >[!NOTE]
  >Transferring mobile numbers is only available in the United States and Puerto Rico.

- Toll phone numbers.
- Toll-free phone numbers.

  >[!NOTE]
  >Universal International Freephone Number (UIFN) can't be transferred to us.

- Service phone numbers such as those used for conference bridges, auto attendants, etc.
- Fax phone numbers, but they can't be used for faxing. They have to be assigned to a user.
- VoIP phone numbers from a phone provider such as Vonage or RingCentral.
- Skype for Business hybrid phone numbers. If you want to transfer these numbers, email us at ptn@microsoft.com.

**You can't transfer:**

>[!NOTE]
>At this time, you can't transfer any phone number or numbers that aren't from a supported country or region, including phone numbers from a VoIP phone provider. For a list of supported countries/regions, see **Country and region availability for Audio Conferencing and Calling Plans** in the **Additional resources** section in the Summary.

- Phone numbers used for data connections like for DSL lines or broadband Internet connections.
- Phone numbers dedicated to faxing.

If you have existing dedicated phone numbers that are being used for faxing, you can transfer these numbers over to Teams but your fax services won't continue to work as expected. Faxing services aren't available to Teams customers, even if you have licenses for Phone System, Domestic Calling Plan, or International Calling Plan.

If you port the phone number to Teams, you can assign this phone number to a user in your organization instead of using it for faxing.
 >[!NOTE]
 >At this time in the United Kingdom, we currently don't support transferring UK non-geographic numbers including shared cost numbers for area codes 0843, 0844, 0845, 0870, 0871, 0872.

#### What information do I need to provide

You need to have all the account information for your current carrier. The information that you enter in the port order is mostly found on the most recent bill or invoice from your current service provider. You also need to know whose name is on the account and what numbers you want to port.

#### What are full-port and partial-port transfers

When you're porting phone numbers to Teams, you have the option to transfer all your numbers or some of them.

- **Full-port** This is when you transfer all of your numbers from your current service provider to Teams. When you're asked for the phone numbers you want to transfer, you must include the billing telephone number (BTN) along with all of the other phone numbers on your account.
For example, let's say your BTN is +1 425-555-1234 and you want to port all of your 25 phone numbers (+1 425-555-1235 through 1259). When you follow the instructions below to transfer your numbers, you would enter: **+14255551234 - +14255551259**.

- Partial-port This is when you're only transferring some of your phone numbers from your current service provider to Teams. When you want to port some of the phone numbers tied to the same BTN, you *must not include* the BTN along with all of the other phone numbers on your account.
For example, let's say your BTN is +1 425-555-1234 and you want to port only 5 of your 25 phone numbers (+1 425-555-1235 through 1259). When you follow the instructions below to transfer your numbers, you would enter: **+1 425 555 1235 - +1 425 555 1239**.

#### Can I submit a single number porting request for all of my numbers at one time

A unique request is needed for each carrier and type of number being ported.

For example, you need to submit a unique number porting request for each of the following types of numbers:

- Local toll numbers, also known as subscriber numbers or geographic numbers
- Toll Free numbers with area codes such as: 800, 844, 855, 866, 877 and 888
- Mobile numbers
- Service numbers that can be used for Audio Conferencing in Microsoft 365 or Office 365.

Here's more information about how to submit number porting requests for each of these types of numbers:

- **Phone numbers** provided by different carriers require a unique porting request for numbers with each carrier.
- **Toll-free numbers** with area codes such as: 800, 844, 855, 866, 877 and 888 can't be included in a number porting request with other types of numbers. To port these toll-free numbers, you must manually submit a port order. You can't port these numbers in the Microsoft Teams admin center. For more information, see **Manage phone numbers for your organization** in the **Additional resources** section in the Summary.
- It's important to use the correct Letter of Authorization (LOA) for the country and type of phone numbers that you want to port. You can download the LOA that you need here.
- **Mobile numbers** require a PIN code to authorize the transfer. Therefore, they need separate number porting request.
- **Service number** porting requests need to be submitted by themselves. They can't be submitted with other types of numbers.

#### How long does it take to port numbers

After you've completed the port order request, it takes between 7-14 days to be processed. However, depending on your service provider it may take up to 30 days. After the phone numbers are ported over, you'll get an email from us to let you that you're good to go.

To check the status of your port order, in the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone numbers**, and then select **Order history**. Each port order status is listed in the **Status** column.

#### Can user (subscriber) phone numbers be converted to service numbers

Yes they can. All you need to do is submit a service request that includes your organization's tenant GUID and the phone numbers you want converted. To do this, see **Manage phone numbers for your organization** in the Additional resources section in the Summary.

#### Can I port out my numbers from Teams to a different phone service provider or carrier

To port out your numbers from Teams to a different carrier, you must submit a request with the new carrier. You'll also need to set a porting PIN in the Microsoft Teams admin center.

To define your porting PIN, in the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone numbers**, on the upper-right corner of the page, select **Manage porting PIN**, and then enter a 10-digit PIN.

When your new carrier contacts us with the porting request, we'll ask them to provide the PIN you defined.

#### Common mistakes to watch out for

Number porting is easy to do. Your order can get messed up, however, if there's a problem with the phone service provider, the order is incomplete and missing information, or there are typos.

Here are the most common mistakes we see customers make when they port numbers. Save yourself a call to customer support and double-check for these errors.

- Make sure the account information you give matches exactly what your phone carrier has on record. Mismatched information is the most common cause of errors and delay your port order. Verify the following is true:

  - Name or person authorized to make changes to the account is correct.
  - Address is correct.
  - Account number is correct.
  - BTN is correct.

- Make sure there are no advanced call control features, for example, Call Hunt or Distinctive Ring, enabled on these phone numbers.
- Make sure you haven't placed any new service orders or disconnects with your current service provider.
- Make sure all numbers are from the same carrier and the same account.
- Make sure your service is active. Freezing the account prevents the change of carriers on the account. The person authorized to make changes to the account must submit an order to the current carrier to remove the freeze. This process can take one to three weeks depending on the carrier.
