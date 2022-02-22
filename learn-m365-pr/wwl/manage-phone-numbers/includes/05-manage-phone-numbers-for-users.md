When an organization sets up Calling Plans, it must assign phone numbers to its users. Depending on the regulations of the organization's country/region, the organization may also need to assign an emergency location to each phone number or user. 

## Assign phone numbers

Complete the following steps to assign phone numbers to users:

1. Sign into the **Microsoft Teams admin center**.
2. On the left-hand navigation pane, select **Voice** and then select **Phone numbers**.
3. On the **Phone numbers** window, select an unassigned number in the list and then select **Edit**.
‎‎:::image type="content" source="../media/manage-phone-numbers.png" alt-text="Manage phone numbers":::  
4. To assign or change the associated emergency location, search for and then select the location under the **Emergency location** tab.  
‎‎:::image type="content" source="../media/assign-phone-number.png" alt-text="Assign phone number":::  

5. In the **Assigned to** section, search for the user by display name or username, and then select **Assign**.
    > [!NOTE]
    > You can only find a user if the user has the appropriate license applied.
6. Select **Apply**.

You can assign or change a phone number or an emergency location for a user in the Microsoft Teams admin center or by using PowerShell. Use the ```Set-CsOnlineVoiceUser``` cmdlet to set the PSTN-specific parameters, such as telephone numbers and emergency response locations.

## Change a phone number for a user

Complete the following steps to change a user’s phone number using the Teams admin center:

1. In the left-hand navigation pane, select **Users** > **Manage users** and select a user.
2. In the **Account** tab, below **General information**, you can see the user’s assigned phone number.
3. In the left-hand navigation pane, select **Voice**, and then select **Phone numbers**.
4. On the **Phone numbers** page, select the number that you want to change, and then select **Edit** from the top pane.
5. In the right-side **Edit** pane, below **Assigned to**, select **X** to remove the user.
6. Select **Apply**.
7. On the **Phone numbers** page, select an unassigned number in the list, and then select **Edit**.
8. Under **Assigned to**, search for the user by display name or username, and then select **Assign**.
9. Select **Apply**.

## Remove a phone number for a user

Complete the following steps to remove a user’s phone number using the Microsoft Teams admin center:

1. In the **Manage users** section, locate and select the user, select **Account**, and then under **General information**, make a note of the phone number that's assigned to the user.
2. In the left-hand navigation pane, select **Voice** and then select **Phone numbers**.
3. On the **Phone numbers** page, select the number that you want to remove for a user, and then select **Edit**.
4. In the **Edit** section, under **Assigned to**, select **X** to remove the user.
5. Select **Apply**.

## Show phone numbers for users

In the Microsoft Teams client, users can see their phone number by selecting **Calls** in the left-hand navigation pane. The phone number is displayed above the dial pad, as seen in the following screenshot.

‎:::image type="content" source="../media/teams-client-phone-number.png" alt-text="Teams Client Phone Number":::
