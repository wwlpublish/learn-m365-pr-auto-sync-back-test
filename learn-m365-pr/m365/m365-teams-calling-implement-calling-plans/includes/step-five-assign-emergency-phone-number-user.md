When you're setting up Calling Plans, you need to assign an emergency location to each phone number or user. In European countries, the emergency location is associated with the phone number when you get it from Microsoft 365 or Office 365 or when you transfer a phone number over to Microsoft 365 or Office 365. In the United States, the emergency location is associated with the phone number when it's assigned to the user. The emergency address can be changed if the user that it's assigned to moves to a new location. For more about emergency addresses and locations, see **What are emergency locations, places, and call routing** located in the **Additional resources** section in the Summary.

> [!TIP]
> If you add more people to your business right before doing this step, it may take **several hours** for them to appear on the **Voice users** page. There's a latency.

You can assign or change an emergency location for a user in the Microsoft Teams admin center or by using PowerShell.

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, select **Voice** > **Phone numbers**.
1. On the **Phone numbers** page, select the **Numbers** tab, select a user number in the list, and then select **Edit**.
1. On the **Edit** pane, under **Emergency location**, do one of the following:
    - To assign an emergency location, search for, and select an emergency location.
    - To change the emergency location that's already assigned to the user, select X to remove the existing location, and then search for and select the location you want to assign.
1. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on Email user with telephone number information. By default, this is on.
1. Select **Apply**.

    :::image type="content" source="../media/5-edit-emergency-location-inline.png" lightbox="../media/5-edit-emergency-location-expanded.png" alt-text="Porting Wizard – Adding account information.":::

### Using PowerShell

Use the following cmdlet to set the PSTN-specific parameters (like telephone numbers and emergency response locations.)

```powershell
Set-CsOnlineVoiceUser
```

For more information, see **Set-CsOnlineVoiceUser** in the **Additional resources** section in the Summary.
