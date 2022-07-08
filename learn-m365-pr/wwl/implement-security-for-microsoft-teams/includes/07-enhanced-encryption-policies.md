For situations that require heightened confidentiality, Teams offers end-to-end encryption (E2EE) for one-on-one calls. End-to-end encryption, or E2EE, happens when content is encrypted before it's sent and decrypted only by the intended recipient. With end-to-end encryption, only the two endpoint systems are involved in encrypting and decrypting the call data. No other party, including Microsoft, has access to the decrypted conversation.

By default, Teams encrypts all communication using industry-standard technologies such as Transport Layer Security (TLS) and Secure Real-Time Transport Protocol (SRTP).

## End-to-end encryption for one-to-one Microsoft Teams calls

With end-to-end encryption,

  - Only the two endpoint systems are involved in encrypting and decrypting the call data

  - No other party, including Microsoft, has access to the decrypted conversation

  - Data exchanged during calls is always secure while in transit and at rest

> [!NOTE]
> End-to-end encryption isn't available, if your organization uses compliance recording.

### What is encrypted:

During an end-to-end encrypted call, Teams secures:

* Audio
* Video
* Screen sharing

### Unavailable features:

The following advanced features aren't available during an E2EE call:

* Live captions and transcription
* Call transfer
* Call merge
* Call park
* Consult then transfer
* Call companion and transfer to another device
* Adding a participant
* Recording

## Configure enhanced encryption policies 

The Teams admin enables end-to-end encryption for the organization by creating one or more enhanced encryption policies that define who can use end-to-end encryption.

The global, organization-wide, default policy specifies that end-to-end encryption is disabled. Users in your organization will automatically get the global policy unless you create and assign a custom policy. To enable end-to-end encryption, create a new encryption policy or modify the global default policy 

### Use the Teams admin center

To configure end-to-end encryption using the Teams admin center:

1.  Sign in to the Teams admin center.

2.  Go to **Enhanced encryption policies**.

3.  Either choose the default policy or choose Add to add a new policy and then name the new policy.

4.  To enable end-to-end encryption for your users, for End-to-end call encryption, choose **Off, but users can turn it on**, and then choose Save.

    :::image type="content" source="../media/encryption-policies.png" alt-text="Screenshot of the Enhanced encryption policies in Teams admin center":::

Once you’ve finished setting up the policy, assign the policy to users, groups, or your entire tenant the same way you manage other Teams policies.  
  
### Use Microsoft PowerShell

You can manage end-to-end encryption policies using Microsoft PowerShell cmdlets:

  - [Get-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Get-CsTeamsEnhancedEncryptionPolicy?azure-portal=true) returns information about the Teams enhanced encryption policies in your organization.

  - [Grant-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Grant-CsTeamsEnhancedEncryptionPolicy?azure-portal=true) assigns and unassigns existing enhanced encryption policies to a user. Use $NULL to unassign all policies from a user.

  - [New-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/New-CsTeamsEnhancedEncryptionPolicy?azure-portal=true) creates a new Teams enhanced encryption policy.

  - [Remove-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Remove-CsTeamsEnhancedEncryptionPolicy?azure-portal=true) deletes an enhanced encryption policy from your organization. You can't delete the global, default policy.

  - [Set-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Set-CsTeamsEnhancedEncryptionPolicy?azure-portal=true) updates values in an existing Teams enhanced encryption policy.

To enable end-to-end encryption for the entire tenant by setting the default global policy, run the **```Set-CsTeamsEnhancedEncryptionPolicy```** cmdlet:

```PowerShell
Set-CsTeamsEnhancedEncryptionPolicy -Identity Global -CallingEndtoEndEncryptionEnabledType DisabledUserOverride
```

## Place end-to-end encrypted calls in Teams client

After the admin enables end-to-end encryption, users will need to switch on end-to-end encrypted calls in Teams settings on their device. Each user needs to complete this task, but they only need to do it on one device. Teams synchronizes this setting across supported end points for each user.

Before the call, both users must turn on E2EE from the Teams client:

1.  In Teams, select **More options** next to your profile picture and then select **Settings**.

2.  Select **Privacy** on the left and then select the toggle next to **End-to-end encrypted calls** to turn it on.  
      
    :::image type="icon" source="../media/encryption-client.png" alt-text="Screenshot of the end to end encryptioed calls setting in Teams client":::
