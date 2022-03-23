Although Microsoft 365 is a managed service that requires little to set up for pure cloud companies, companies with an existing local environment still need to complete various checks to ensure a smooth transition. These checks should include analyzing network readiness and your on-premises Active Directory environment.

### Network concerns

Using Microsoft 365 may increase the utilization of your organization’s internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Microsoft 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.

### Cleaning up your on-premises Active Directory environment

It's recommended that companies with a legacy environment complete a system review and clean-up depending on the longevity of their Active Directory environment. This process will help ensure a successful synchronization with Microsoft 365 when either migrating completely to the cloud or setting up a hybrid environment.

Companies can clean their Active Directory environment by using the IdFix Directory Synchronization Error Remediation tool. IdFix discovers and remediates identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Azure Active Directory. IdFix is intended for the Active Directory administrators responsible for directory synchronization with Azure Active Directory. This tool provides a way to automate the cleaning process by either notifying the administrator of the errors or by fixing them automatically.

The following table describes the errors that are detected by IdFix, provides the most commonly suggested fixes from the tool, and in some cases provides examples of how to fix them.

:::row:::
  :::column:::
    **ERROR**
  :::column-end:::
  :::column:::
    **Error Type Description**
  :::column-end:::
  :::column:::
    **Suggested Fix**
  :::column-end:::
  :::column:::
    **Example**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    character
  :::column-end:::
  :::column:::
    Illegal characters. The value contains a character that's invalid.
  :::column-end:::
  :::column:::
    The suggested fix for the error shown in the **UPDATE** column shows the value with the invalid character removed.
  :::column-end:::
  :::column:::
    A trailing space at the end of a valid mail address is an illegal character. For example:
"user@contoso.com "
A leading space at the beginning of a valid mail address is an illegal character. For example:
" user@contoso.com"
The “ú “character is a non-supported character.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    duplicate
  :::column-end:::
  :::column:::
    Duplicate entry. The value has a duplicate within the scope of the query. All duplicate values will be displayed as errors.
  :::column-end:::
  :::column:::
    Edit or remove values to eliminate duplication. The tool won't provide a suggested fix for duplicates. Instead, you must choose which value is correct and delete the duplicate entry or entries.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    format
  :::column-end:::
  :::column:::
    Formatting error. The value violates the format requirements for the attribute usage.
  :::column-end:::
  :::column:::
    The suggested Update will show the value with any invalid characters removed. If there are no invalid characters, the Update and Value will appear the same. Determine what you really want in the update. The tool doesn't provide a suggested fix for all formatting errors.
  :::column-end:::
  :::column:::
    For example, SMTP addresses must follow RFC 2822 and mailNickName can't start or end with a period. For more information about format requirements for directory attributes, see "Directory object and attribute preparation" in [Prepare to provision users through directory synchronization to Microsoft 365](https://support.office.com/article/prepare-to-provision-users-through-directory-synchronization-to-office-365-01920974-9e6f-4331-a370-13aea4e82b3e?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    topleveldomain
  :::column-end:::
  :::column:::
    Top-level domain. This error applies to values subject to [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464?azure-portal=true) formatting when the top-level domain isn't internet routable. For example, this error is generated when an SMTP address ending in ".local" isn't internet routable.
  :::column-end:::
  :::column:::
    Change the value to an internet routable domain such as .COM or .NET.
  :::column-end:::
  :::column:::
    Change myaddress@fourthcoffee.local to fourthcoffee.com or another internet routable domain.
For instructions, see [How to prepare a non-routable domain for directory synchronization](https://support.office.com/article/how-to-prepare-a-nonroutable-domain-such-as-local-domain-for-directory-synchronization-e7968303-c234-46c4-b8b0-b5c93c6d57a7?azure-portal=true).
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    domain part
  :::column-end:::
  :::column:::
    Domain part error. This error applies to values subject to RFC 2822 formatting. This error is generated when the domain portion of the value is invalid and doesn't follow RFC 2822.
  :::column-end:::
  :::column:::
    Change the value to one that follows RFC 2822. For example, make sure that it doesn’t contain any spaces or illegal characters.
  :::column-end:::
  :::column:::
    Change myaddress@fourth coffee.com to myaddress@fourthcoffee.com.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    domainpart\_localpart
  :::column-end:::
  :::column:::
    Local-part error. This error applies to values subject to RFC 2822 formatting. This error is generated when the local-part of the value is invalid and doesn't follow RFC 2822.
  :::column-end:::
  :::column:::
    Change the value to one that follows RFC 2822. For example, make sure that it doesn’t contain any spaces or illegal characters.
  :::column-end:::
  :::column:::
    Change my”work”address@fourthcoffee.com to myworkaddress@fourthcoffee.com.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    length
  :::column-end:::
  :::column:::
    Length error. The value violates the length limit for the attribute. This error most commonly occurs when the directory schema has been altered.
  :::column-end:::
  :::column:::
    The update suggested by IdFix will truncate the value to the acceptable length, which may produce undesired results. Review the suggested fix and change it if necessary before you select **Apply**.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    blank
  :::column-end:::
  :::column:::
    Blank or null error. The value violates the null restriction for attributes to be synchronized. Only a few attributes must contain a value.
  :::column-end:::
  :::column:::
    If possible, the suggested update will use other attribute values to generate a likely replacement.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    mail match
  :::column-end:::
  :::column:::
    This error only applies to Microsoft 365 Dedicated. The value doesn't match the mail attribute.
  :::column-end:::
  :::column:::
    The suggested update will be the mail attribute value prefixed by “SMTP:”.
  :::column-end:::
  :::column:::
    
  :::column-end:::
:::row-end:::


## 

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”