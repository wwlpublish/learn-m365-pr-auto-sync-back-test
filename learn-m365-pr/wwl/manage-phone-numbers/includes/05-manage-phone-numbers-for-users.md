When an organization sets up Calling Plans, it must assign phone numbers to its users. Depending on the regulations of the organization's country/region, the organization may also need to assign an emergency location to each phone number or user. 

## Assign phone numbers

Complete the following steps to assign phone numbers to users:

1. Sign into the **Microsoft Teams admin center**.
2. On the left-hand navigation pane, select **Voice** and then select **Phone numbers**.
3. On the **Phone numbers** window, select an unassigned number in the list and then select **Edit**.

    ‎‎:::image type="content" source="../media/manage-phone-numbers.png" alt-text="Screenshot of Manage phone numbers.":::  

4. In the **Edit** pane, under **Assigned to**, search for the user by display name or user name, and then select **Assign**.

5. To assign or change the associated emergency location, search for and then select the location under the **Emergency location** tab. 

    ‎‎:::image type="content" source="../media/assign-phone-number.png" alt-text="Screenshot of Assign phone number.":::  

6. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this is on.

7. Select **Apply**.

You can assign or change a phone number or an emergency location for a user in the Microsoft Teams admin center or by using PowerShell. Use the ```Set-CsOnlineVoiceUser``` cmdlet to set the PSTN-specific parameters, such as telephone numbers and emergency response locations.

## Change a phone number for a user

Complete the following steps to change a user’s phone number using the Teams admin center:

1. In the left navigation, click **Users**, locate and double-click the user you want, click **Account**, and then under **General information**, make a note of the phone number that's assigned to the user.

2. In the left navigation, click **Voice** \> **Phone numbers**.

3. On the **Phone numbers** page, select the number that you identified in step 1, and then click **Edit**.

4. In the **Edit** pane, under **Assigned to**, click the **X** to remove the user.

5. Click **Save**.

6. On the **Phone numbers** page, select an unassigned number in the list, and then click **Edit**.

7. In the **Edit** pane, under **Assigned to**, search for the user by display name or user name, and then click **Assign**.

8. To assign or change the associated emergency location, under **Emergency location**, search for and then select the location.

9. Select **Save**.

## Remove a phone number for a user

Complete the following steps to remove a user’s phone number using the Microsoft Teams admin center:

1. In the left navigation, click **Users**, locate and double-click the user you want, click **Account**, and then under **General information**, make a note of the phone number that's assigned to the user.

2. In the left navigation, click **Voice** \> **Phone numbers**.

3. On the **Phone numbers** page, select the number that you identified in step 2, and then click **Edit**.

4. In the **Edit** pane, under **Assigned to**, click the **X** to remove the user.

5. Select **Save**.

## Show phone numbers for users

In the Microsoft Teams client, users can see their phone number by selecting **Calls** in the left-hand navigation pane. The phone number is displayed above the dial pad, as seen in the following screenshot.

‎:::image type="content" source="../media/teams-client-phone-number.png" alt-text="Screenshot of Teams Client Phone Number.":::
