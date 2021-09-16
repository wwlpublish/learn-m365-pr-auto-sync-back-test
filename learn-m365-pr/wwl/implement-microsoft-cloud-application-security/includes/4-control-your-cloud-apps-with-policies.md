Policies allow you to define the way you want your users to behave in the cloud. They enable you to detect risky behavior, violations, or suspicious data points and activities in your cloud environment. If necessary, policies enable you to integrate remediation workflows to achieve complete risk mitigation.

Multiple types of policies correlate to the different types of information you can gather about your cloud environment and the types of remediation actions you may want to take. For example, assume there's a data violation threat that you want to quarantine. You need a different type of policy in place than if you want to block a risky cloud app from being used by your organization.

Complete the following steps to control risk with policies:

1.  In the **Cloud App Security** dashboard, hover your mouse over the **Control** icon on the left-hand bar and then select **Policies.**
2.  On the **Policies** page, select the policy you want to maintain and fine-tune the policy to achieve expected results.
3.  Add automated actions to respond and remediate risks automatically.

**Additional reading.** For more information, see [How to control cloud apps with policies](/cloud-app-security/control-cloud-apps-with-policies?azure-portal=true).

The rest of this unit examines the types of policy apps that are available, and how you can identify risks within a policy.

### Policy types for cloud apps

The following table displays the policy types that are available for cloud apps.

:::row:::
  :::column:::
    

**Policy type**


  :::column-end:::
  :::column:::
    

**Use**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Access policy


  :::column-end:::
  :::column:::
    

Access policies provide you with real-time monitoring and control over user logins to your cloud apps.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Activity policy


  :::column-end:::
  :::column:::
    

Activity policies allow you to enforce a wide range of automated processes that use the app provider’s APIs. You can monitor specific activities carried out by various users or follow unexpectedly high rates of a certain type of activity.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Anomaly detection policy


  :::column-end:::
  :::column:::
    

Anomaly detection policies enable you to look for unusual activities on your cloud based on the risk factors you set here to alert you when something happens that is different from either the baseline of your organization or from the user's regular activity.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

App permission policy


  :::column-end:::
  :::column:::
    

App permission policies enable you to investigate, for Microsoft 365, G Suite and Salesforce, which permissions each app requested, and which users authorized them. You can also mark these permissions as approved or banned.


For example, you can automatically be alerted when there are apps that require a high permission level and were authorized by more than 50 users.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

App discovery policy


  :::column-end:::
  :::column:::
    

App discovery policies enable you to set alerts that notify you when new apps are detected within your organization.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Cloud Discovery anomaly detection policy


  :::column-end:::
  :::column:::
    

Cloud Discovery anomaly detection policies look at the logs you use for discovering cloud apps and search for unusual occurrences, such as when the number of transactions on a particular app are higher than usual.


For example, a user who never used Dropbox before suddenly uploads 600 GB to Dropbox.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

File policy


  :::column-end:::
  :::column:::
    

File policies enable you to scan your cloud apps for specified files or file types (shared, shared with external domains), data (proprietary information, personal information, credit card information, and so on) and apply governance actions to the files (governance actions are cloud-app specific).


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Malware detection policy


(Conditional Access App Control policies)


  :::column-end:::
  :::column:::
    

Access policies enable real-time monitoring and control over access to cloud apps based on user, location, device, and app. You can create access policies for any device, including devices that aren't domain joined, and not managed by Windows Intune by rolling out client certificates to managed devices or by using existing certificates, such as third-party MDM certificates.


For example, you can deploy client certificates to managed devices, and then block access from devices without a certificate.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

Session policy

(Conditional Access App Control policies)


  :::column-end:::
  :::column:::
    

Session policies enable real-time session-level monitoring, affording you granular visibility into cloud apps and the ability to take different actions depending on the policy you set for a user session. Instead of allowing or blocking access completely, with session control you can allow access while monitoring the session and limit specific session activities using the reverse proxy capabilities of Conditional Access App Control.


For example, you can decide that from unmanaged devices, or for sessions coming from specific locations, you want to allow the user to access the app, but also limit the download of sensitive files or require that certain documents be protected upon download.


  :::column-end:::
:::row-end:::


### Identifying risk

Cloud App Security also helps you mitigate different risks in the cloud. You can configure any policy and alert to be associated with one of the risks in the following table.

:::row:::
  :::column:::
    

**Risk**


  :::column-end:::
  :::column:::
    

**How to mitigate**


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Access control.** Who accesses what from where?


  :::column-end:::
  :::column:::
    

Continuously monitor behavior and detect anomalous activities, including high-risk insider and external attacks, and apply a policy to alert, block, or require identity verification for any app or specific action within an app. Enables on-premises and mobile access control policies based on user, device, and geography with coarse blocking and granular view, edit, and block. Detect suspicious login events, including multifactor authentication failures, disabled account login failures, and impersonation events.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Compliance**. Have your compliance requirements been breached?


  :::column-end:::
  :::column:::
    

Catalog and identify sensitive or regulated data, including sharing permissions for each file, stored in file-sync services to ensure compliance with regulations such as PCI, SOX, and HIPAA.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Configuration control.** Are unauthorized changes being made to your configuration?


  :::column-end:::
  :::column:::
    

Monitor configuration changes, including remote configuration manipulation.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Cloud Discovery.** Are new apps being used in your organization? Do you have a problem of Shadow IT apps being used that you don't know about?


  :::column-end:::
  :::column:::
    

Rate overall risk for each cloud app based on regulatory and industry certifications and best practices, enables you to monitor the number of users, activities, traffic volume, and typical usage hours for each cloud application.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Data Loss Prevention (DLP).** Are proprietary files being shared publicly? Do you need to quarantine files?


  :::column-end:::
  :::column:::
    

On-premises DLP integration provides integration and closed-loop remediation with existing on-premises DLP solutions.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Privileged accounts.** Do you need to monitor admin accounts?


  :::column-end:::
  :::column:::
    

Real-time activity monitoring and reporting of privileged users and admins.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Sharing control.** How is data being shared in your cloud environment?


  :::column-end:::
  :::column:::
    

Inspect the content of files and content in the cloud and enforce internal and external sharing policies. Monitor collaboration and enforce sharing policies, such as blocking files from being shared outside your organization.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    

**Threat detection.** Are there suspicious activities threatening your cloud environment?


  :::column-end:::
  :::column:::
    

Receive real-time notifications for any policy violation or activity threshold via text message or email. When applying machine learning algorithms, Cloud App Security enables you to detect behavior that could indicate that a user is misusing data.


  :::column-end:::
:::row-end:::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”