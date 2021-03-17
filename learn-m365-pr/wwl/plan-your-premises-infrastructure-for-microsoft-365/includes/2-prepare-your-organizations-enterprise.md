Although Microsoft 365 is a managed service that requires little to set up for pure cloud companies, companies with an existing local environment still need to complete various checks to ensure a smooth transition. These checks should include analyzing network readiness and your on-premises Active Directory environment.

### Network Concerns

Using Microsoft 365 may increase the utilization of your organization’s internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Microsoft 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.

### Cleaning up your on-premises Active Directory environment

It's recommended that companies with a legacy environment complete a system review and clean-up depending on the longevity of their Active Directory environment. This process will help ensure a successful synchronization with Microsoft 365 when either migrating completely to the cloud or setting up a hybrid environment.

Companies can clean their Active Directory environment by using the [IdFix Directory Synchronization Error Remediation tool](https://microsoft.github.io/idfix/installation?azure-portal=true). IdFix performs discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Azure Active Directory. IdFix is intended for the Active Directory administrators responsible for directory synchronization with Azure Active Directory. This tool provides a way to automate the cleaning process by either notifying the administrator of the errors or by fixing them automatically.

The following table describes the errors that are detected by IdFix, provides the most commonly suggested fixes from the tool, and in some cases provides examples of how to fix them.

:::row:::
  :::column:::
    <p><b>ERROR</b></p>
  :::column-end:::
  :::column:::
    <p><b>Error Type Description</b></p>
  :::column-end:::
  :::column:::
    <p><b>Suggested Fix</b></p>
  :::column-end:::
  :::column:::
    <p><b>Example</b></p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>character</p>
  :::column-end:::
  :::column:::
    <p>Illegal characters. The value contains a character that's invalid.</p>
  :::column-end:::
  :::column:::
    <p>The suggested fix for the error shown in the <b>UPDATE</b> column shows the value with the invalid character removed.</p>
  :::column-end:::
  :::column:::
    <p>A trailing space at the end of a valid mail address is an illegal character. For example:<br></p>  <p>"user@contoso.com "<br></p>  <p>A leading space at the beginning of a valid mail address is an illegal character. For example:<br></p>  <p>" user@contoso.com"<br></p>  <p>The “ú “character is a non-supported character.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>duplicate</p>
  :::column-end:::
  :::column:::
    <p>Duplicate entry. The value has a duplicate within the scope of the query. All duplicate values will be displayed as errors.</p>
  :::column-end:::
  :::column:::
    <p>Edit or remove values to eliminate duplication. The tool won't provide a suggested fix for duplicates. Instead, you must choose which value is correct and delete the duplicate entry or entries.</p>
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>format</p>
  :::column-end:::
  :::column:::
    <p>Formatting error. The value violates the format requirements for the attribute usage.</p>
  :::column-end:::
  :::column:::
    <p>The suggested Update will show the value with any invalid characters removed. If there are no invalid characters, the Update and Value will appear the same. Determine what you really want in the update. The tool doesn't provide a suggested fix for all formatting errors.</p>
  :::column-end:::
  :::column:::
    <p>For example, SMTP addresses must follow RFC 2822 and mailNickName can't start or end with a period. For more information about format requirements for directory attributes, see "Directory object and attribute preparation" in <a href="https://support.office.com/en-us/article/prepare-to-provision-users-through-directory-synchronization-to-office-365-01920974-9e6f-4331-a370-13aea4e82b3e?azure-portal=true">Prepare to provision users through directory synchronization to Microsoft 365</a>.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>topleveldomain</p>
  :::column-end:::
  :::column:::
    <p>Top-level domain. This error applies to values subject to <a href="https://go.microsoft.com/fwlink/p/?LinkId=401464?azure-portal=true">RFC 2822</a> formatting when the top-level domain isn't internet routable. For example, this error is generated when an SMTP address ending in ".local" isn't internet routable.</p>
  :::column-end:::
  :::column:::
    <p>Change the value to an internet routable domain such as .COM or .NET.</p>
  :::column-end:::
  :::column:::
    <p>Change myaddress@fourthcoffee.local to fourthcoffee.com or another internet routable domain.<br></p>  <p>For instructions, see <a href="https://support.office.com/en-us/article/how-to-prepare-a-nonroutable-domain-such-as-local-domain-for-directory-synchronization-e7968303-c234-46c4-b8b0-b5c93c6d57a7?azure-portal=true">How to prepare a non-routable domain (such as .local domain) for directory synchronization</a>.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>domain part</p>
  :::column-end:::
  :::column:::
    <p>Domain part error. This error applies to values subject to RFC 2822 formatting. This error is generated when the domain portion of the value is invalid and doesn't follow RFC 2822.</p>
  :::column-end:::
  :::column:::
    <p>Change the value to one that follows RFC 2822. For example, make sure that it doesn’t contain any spaces or illegal characters.</p>
  :::column-end:::
  :::column:::
    <p>Change myaddress@fourth coffee.com to myaddress@fourthcoffee.com.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>domainpart_localpart</p>
  :::column-end:::
  :::column:::
    <p>Local-part error. This error applies to values subject to RFC 2822 formatting. This error is generated when the local-part of the value is invalid and doesn't follow RFC 2822.</p>
  :::column-end:::
  :::column:::
    <p>Change the value to one that follows RFC 2822. For example, make sure that it doesn’t contain any spaces or illegal characters.</p>
  :::column-end:::
  :::column:::
    <p>Change my”work”address@fourthcoffee.com to myworkaddress@fourthcoffee.com.</p>
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>length</p>
  :::column-end:::
  :::column:::
    <p>Length error. The value violates the length limit for the attribute. This error most commonly occurs when the directory schema has been altered.</p>
  :::column-end:::
  :::column:::
    The update suggested by IdFix will truncate the value to the acceptable length, which may produce undesired results. Review the suggested fix and change it if necessary before you select **Apply**.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>blank</p>
  :::column-end:::
  :::column:::
    <p>Blank or null error. The value violates the null restriction for attributes to be synchronized. Only a few attributes must contain a value.</p>
  :::column-end:::
  :::column:::
    <p>If possible, the suggested update will use other attribute values to generate a likely replacement.</p>
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    <p>mail match</p>
  :::column-end:::
  :::column:::
    <p>This error only applies to Microsoft 365 Dedicated. The value doesn't match the mail attribute.</p>
  :::column-end:::
  :::column:::
    <p>The suggested update will be the mail attribute value prefixed by “SMTP:”.</p>
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”