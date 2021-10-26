You’ve learned what the deployment service is. However, you want to take advantage of a tool you already use daily, PowerShell, to access and use the deployment service. In this unit, you’ll learn about the Microsoft Graph PowerShell SDK and how to set it up for use.

## What is the Microsoft Graph PowerShell SDK?

[Microsoft Graph SDKs](/graph/sdks/sdks-overview) simplify the work required to interface with the Microsoft Graph, the cloud endpoint for various Microsoft services, including the Windows Update for Business deployment service. There are different Microsoft Graph SDKs for various platforms. The *Microsoft Graph PowerShell SDK* makes it possible for you to interact with the Microsoft Graph service using PowerShell. This SDK is a library that provides you with PowerShell commands and capabilities designed to help you use Microsoft Graph. The library includes commands that you'll use to deploy updates from the Windows Update for Business deployment service to your devices.

## Prepare your tenant and devices

To use the Microsoft Graph PowerShell SDK, make sure you have access to:

- A tenant that meets the [subscription requirements](/graph/windowsupdates-concept-overview).
- One or more target devices that meet the [device requirements](/graph/windowsupdates-concept-overview).
- A Microsoft Azure or Microsoft Intune account that meets the [user role requirements](/azure/active-directory/roles/manage-roles-portal).
- A supported version of PowerShell. If you don’t already have PowerShell, see [install PowerShell](/powershell/scripting/install/installing-powershell?view=powershell-7.1&preserve-view=true) for your operating system.

## Get the SDK

Once you’ve confirmed that you have access to all the required components, you’re ready to get the Microsoft Graph PowerShell SDK. To do this, you’ll install the SDK. You can install the SDK in PowerShell Core or Windows PowerShell using the following command:

```PowerShell
Install-Module Microsoft.Graph
```

>[!TIP]
>You can keep your SDK and its dependencies up-to-date using the **Update-Module Microsoft.Graph** command.

Every command in the PowerShell SDK uses the prefix **Mg**, which is short for Microsoft Graph. The deployment service is currently available using the beta endpoint in Microsoft Graph. This means you’ll need to set your user profile to the appropriate API contract by running the following:

```PowerShell
Select-MgProfile -Name "beta"
```

Finally, you use the **Connect-MgGraph** command to sign in by running:

```PowerShell
Connect-MgGraph -Scopes "WindowsUpdates.ReadWrite.All"
```

You’ll be prompted to sign in. You’ll sign in using a Microsoft Azure or Microsoft Intune account that has one of the required permission roles, such as Global Administrator, [Windows Update Deployment Administrator](/azure/active-directory/roles/permissions-reference), or Intune Administrator.

When you’ve signed in successfully, you’re ready to start using the Microsoft Graph PowerShell SDK.

> [!NOTE]
>If you need to author an automated script instead of using the PowerShell console, you can use the [**PSCredential Class**](/dotnet/api/system.management.automation.pscredential?view=powershellsdk-7.0.0&preserve-view=true) to automate usernames, passwords, and credentials.
