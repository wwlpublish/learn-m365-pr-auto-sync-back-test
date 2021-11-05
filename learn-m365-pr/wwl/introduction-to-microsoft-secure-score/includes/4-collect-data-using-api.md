Besides the web-based Secure Score tool, there's also a Secure Score API that's fully integrated into the Microsoft Graph. This Secure Score API enables you to customize where you want to view a dashboard of your organization’s Secure Score and all pertinent information.

Potential benefits of collecting Secure Score data through Microsoft Graph include the following scenarios:

 *  Monitor and report on your Secure Score in downstream reporting tools.
 *  Track your security configuration baseline.
 *  Integrate the data into compliance or cybersecurity insurance applications.
 *  Integrate Secure Score data into your Security Incident and Event Management (SIEM) or cloud access security broker (CASB) solutions to drive a hybrid or multi-cloud framework for security analytics.

Once the Secure Score API has been set up, PowerShell scripts are used to retrieve the necessary data from Secure Score. The `Get-SecureScoreAPI` PowerShell cmdlet, along with scripts that can be written using this cmdlet, enable you to:

 *  feed data into a Power BI dashboard.
 *  conduct advanced analytics.
 *  quickly generate a historical view of the last 30 days of secure score data.

> [!NOTE]
> The Secure Score API and its related PowerShell cmdlets are outside the scope of this training. For more information, see [Using the Office 365 Secure Score API](https://docs.microsoft.com/archive/blogs/office365security/using-the-office-365-secure-score-api?azure-portal=true).
