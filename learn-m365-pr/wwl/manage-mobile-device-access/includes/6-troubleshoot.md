ActiveSync is commonly used to provide email access to mobile devices. Access is provided through the built-in email app or through a third-party email app. ActiveSync is the protocol used to support this access. There are several tools available to troubleshoot ActiveSync, including:

 -  **PowerShell**. You can use PowerShell to quickly run through some basic ActiveSync tasks to determine if there are issues. If things are healthy, the results for each test will be Success. You can optionally decide to not filter the output. You can also get another column of information that lists errors. For example, the messaging administrator at Adatum Corporation could run the following command to start the ActiveSync test on their client access server named **exchange1.adatum.com**:
    
    ```powershell
    Test-ActiveSyncConnectivity -ClientAccessServer exchange1.adatum.com | FT CasServer,LocalSite,Scenario,Result -AutoSize
    ```
 -  **Smartphone**. Don't overlook the value of testing from a client device such as a smartphone. You can quickly set up a new email profile and attempt to connect with ActiveSync. By testing with a smartphone, you can determine whether the issue you're troubleshooting is limited to only one device or device type (such as all Apple iPhones). The downside to smartphone testing is that you'll get limited troubleshooting information. In many scenarios, you'll only receive a message that there was a failure to connect, without any supporting information.
 -  **Microsoft Remote Connectivity Analyzer**. The Remote Connectivity Analyzer mimics a smartphone to run through ActiveSync testing. This tool provides detailed troubleshooting information. Instead of just finding out that the connection failed, you receive support information that enables you to find out where in the connection it failed, and often why it failed.

> [!TIP]
> Most troubleshooting tools require that you specify credentials to run their specific test. As such, it’s recommended that you create a temporary test account for testing. You can then delete the account when the testing is complete.

Messaging administrators should determine whether ActiveSync is functional and then analyze the user configuration. Analyzing the user configuration is especially important if just one (or a few) users are reporting the issue. At the user level, ActiveSync can be enabled or disabled.

Messaging administrators can also test individual user access by using the Remote Connectivity Analyzer test. This test can help you ensure that a user has functional ActiveSync access without reliance on their device. If you opt to run this test, you should first reset the user’s password to a temporary password, run the test, and then reset the password again (at which point, the user can reset the password back to what they had or want).

> [!CAUTION]
> In several countries/regions, it's considered a violation of users' data protection rights if you reset their password and access their messaging data, even if it’s just for troubleshooting purposes. You should always be familiar with the data protection regulations and laws of the country/region in which your company is located.

#### Debug logging

If a specific mobile device is having problems with Exchange ActiveSync connectivity, you can enable Exchange ActiveSync debug logging. The debug log is a text file that contains detailed information about the command and responses between the mobile device and the Exchange server. Users can enable their own debug logging in Outlook on the web and retrieve the log as an email attachment.

You can also enable debug logging, but it must be done in the Exchange Management Shell by running the following commands (in this example, sending email notification to Contoso’s administrator):

```powershell
Set-CASMailbox -Identity <user> -Exchange ActiveSyncDebugLogging $true

```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.