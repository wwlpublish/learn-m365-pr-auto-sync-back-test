AppLocker is a popular tool that administrators use to restrict the software users can install and run on Windows. Restricting software is an important technique in compliance because, if users can install and run any software, they can often find work-arounds for any restrictions that you put in place. These work-arounds may compromise compliance with regulations.

Suppose you're using AppLocker to control the software that Windows users can install on desktop and laptop computers. You want to ensure that they're permitted to use the Microsoft Teams application because it's essential for many users' work and is compliant.
Here, you'll see how to ensure that Teams is allowed by AppLocker.

## How does AppLocker restrict software?

AppLocker uses rules and the properties of files to restrict applications. With AppLocker, you can create rules that allow or deny apps from running based on file types. In addition, you can specify which users or groups can run applications.

AppLocker-based allow listing policies are required to enable Teams with AppLocker. You can create these policies either through Group Policy management in Azure Active Directory (Azure AD) or by using Windows PowerShell cmdlets for AppLocker. AppLocker policies are saved in XML format and can be edited with any text or XML editor.

## Allowing Teams in AppLocker rules

AppLocker rules are a collection of rules. AppLocker rules apply to the targeted app, and they're the components that make up the AppLocker policy.
All Teams app files are digitally signed, so you can use the AppLocker publisher condition rules to allow them. The publisher condition identifies an app file based on its digital signature and embedded version attributes.

Because the Teams installation directory is user-writable, the use of path rules to allow Teams isn't recommended because other, unauthorized software could be placed in the Teams folder. Hash rules are also not recommended because they would have to be changed each time the Teams client app is updated.

### Example of publisher condition rules

For the Teams client app (all files, all versions) add the following to the Executable Rules & DLL Rules:

```typescript
Publisher: O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US
Product name: MICROSOFT TEAMS
Product name: MICROSOFT TEAMS UPDATE
```

## Learn more

- [AppLocker technical reference](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-technical-reference)
- [Understanding the publisher rule condition in AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/understanding-the-publisher-rule-condition-in-applocker)
