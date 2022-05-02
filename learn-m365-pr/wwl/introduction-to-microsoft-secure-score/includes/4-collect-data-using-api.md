Besides the web-based Secure Score tool, there's also a Secure Score API that's fully integrated into the Microsoft Graph. This Secure Score API enables organizations to customize where they want to view a dashboard of their Secure Score and all pertinent information.

Collecting Secure Score data through Microsoft Graph provides organizations with numerous benefits, especially in the following scenarios:

 -  Monitor and report on their Secure Score in downstream reporting tools.
 -  Track their security configuration baseline.
 -  Integrate the data into compliance or cybersecurity insurance applications.
 -  Integrate Secure Score data into their Security Incident and Event Management (SIEM) or Cloud Access Security Broker (CASB) solutions. Doing so drives a hybrid or multi-cloud framework for security analytics.

Once the Secure Score API has been set up, PowerShell scripts are used to retrieve the necessary data from Secure Score. The `Get-SecureScoreAPI` PowerShell cmdlet, along with scripts that can be written using this cmdlet, enable organizations to:

 -  Feed data into a Power BI dashboard.
 -  Conduct advanced analytics.
 -  Generate a historical view of the last 30 days of secure score data.

> [!NOTE]
> The Secure Score API and its related PowerShell cmdlets are outside the scope of this training. For more information, see [Using the Office 365 Secure Score API](/archive/blogs/office365security/using-the-office-365-secure-score-api?azure-portal=true).
