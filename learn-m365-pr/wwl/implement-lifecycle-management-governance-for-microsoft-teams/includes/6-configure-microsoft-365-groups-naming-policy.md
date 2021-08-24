You can use a group naming policy to enforce a consistent naming strategy for groups created by users. A naming policy helps users identify the function of the group, membership, geographic region, or the person who created the group. 

The naming policy is applied to groups that are created across all groups workloads. For example, Outlook, Microsoft Teams, SharePoint, Planner, or Yammer. The naming policy gets applied to both the group name and group alias. 

## Microsoft 365 groups naming policies
The group naming policy consists of the following features:

- **Prefix-suffix naming policy**. You can use prefixes or suffixes to define the naming convention of groups. 

- **Custom blocked words**. You can also specify various words that will be blocked in groups created by users, such as GM, Billings, Payments, HR.

### Prefix-suffix naming policy

Prefixes and suffixes can either be fixed strings or user attributes.

- **Fixed Strings**: When using fixed strings, it is recommended that you use short strings that will help differentiate groups in the Global Address List(GAL). Some of the frequently used prefixes and suffixes are keywords as: 'Grp_Name', '#Name', '_Name'

- **Attributes**: you can use attributes that can help in identification of which user has created the group like [Department] and where it was created from like [Country].

For example, a naming policy = "GRP [GroupName] [Department]" will result in the following if the group is named "My Group" and the user's department is "Engineering": 

"GRP My Group Engineering"

Supported Azure Active Directory (Azure AD) attributes are [Department], [Company], [Office], [StateOrProvince], [CountryOrRegion], [Title]. Unsupported user attributes are considered as fixed strings. For example,  "[postalCode]". Also, extension attributes and custom attributes aren't supported. It's recommended that you use attributes that have values filled in for all users in your organization and don't use attributes that have longer values.

**There are things you need to be aware of**: 

- The total prefixes and suffixes string length is restricted to maximum 53 characters.

- Prefixes and suffixes can contain special characters that are supported in group name and group alias. Any characters in the prefix or suffix that are not supported in the group alias are still applied in the group name, but removed from the group alias. Because of this restriction, the prefixes and suffixes applied to the group name might be different from the ones applied to the group alias.

- If you are using Yammer Office 365 connected groups, avoid using the following characters in your naming policy: @, #, [, ], <, and >. If these characters are in the naming policy, regular Yammer users will not be able to create groups.

### Custom blocked words

You can use custom blocked words to prevent the users from using them when creating a group. You may also list blocked words that need to be separated by a comma between the different words. The blocked words check is done on the user entered group name. For example, if a user enters 'final' and 'Prefix_' as the naming policy, 'Prefix_final' will fail.

Substring search is not done so that users can use some of the common words like 'Pilot' even if 'lot' is a blocked word.
 

## Configure Microsoft 365 groups naming policy 

You can configure Microsoft 365 groups naming policy using Azure AD admin center or Azure AD PowerShell. 

### Use Azure AD admin center


1. Sign in to Azure portal, select Azure AD, and under **Manage** section, choose **Groups**.

2. Under **Settings** section, select **Naming policy**.

3. Select the **Blocked words** tab, and upload the .csv file with your blocked words.
 
4. Select the **Group naming policy** tab.

5. In **Current policy** section, select whether you would like to require a prefix or suffix (or both), and select the appropriate check boxes.

6. Choose between **Attribute** and **String**.

7. When you are done setting up the required settings, click the **Save** button.  
‎
    ‎:::image type="content" source="../media/naming-policy-configuration.png" alt-text="Naming Policy Configuration":::  

### Use Azure AD PowerShell

To view the current naming policy settings, run the following PowerShell command as an administrator:
 
```powershell
$Setting = Get-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ).id
$Setting.Values
```

In the output, check the following values: 

- **CustomBlockedWordsList**, 

- **EnableMSStandardBlockedWords**

- **PrefixSuffixNamingRequirement**.

 
To configure Microsoft 365 groups naming policy 

1. Get the existing directory settings from your Azure AD:

    ```powershell
    $Setting = Get-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ).id
    ```

2. Set the group name prefixes and suffixes, for example the prefix "GRP_":

    ```powershell
    $Setting["PrefixSuffixNamingRequirement"] ="GRP_[GroupName]"
    ```

3. To configure custom blocked words that you want to restrict, for example Payroll and CEO run the following cmdlet:

    ```powershell
    $Setting["CustomBlockedWordsList"]="Payroll,CEO"
    ```
4. Update the setting in Azure AD directory settings:

    ```powershell
    Set-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ).id -DirectorySetting $Setting
    ```
    
## Remove the naming policy

### Use Azure AD admin center
To remove the naming policy by using Azure AD, perform the following steps:

1. On the **Naming policy** page, select **Delete policy**.

2. After you confirm the deletion, the naming policy is removed, including all prefix-suffix naming policy and any custom blocked words.

### Use Azure AD PowerShell

To remove the naming policy using Azure AD PowerShell, perform the following steps:

1. Empty the group name prefixes and suffixes in Azure AD PowerShell.

    ```powershell
    $Setting["PrefixSuffixNamingRequirement"] =""
    ```
2. Empty the custom blocked words.

    ```powershell
    $Setting["CustomBlockedWordsList"]=""
    ```
3. Save the settings.

    ```powershell
    Set-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ).id -DirectorySetting $Setting
    ```

## User experiences with naming policy

After you create a group naming policy in Azure AD, when users create a group in an Office 365 app, they will have the following experiences depending on the group naming policies settings:

- Users will see a preview of the name according to your naming policy (with prefixes and suffixes) as soon as the user types in the group name.
- If the users enter blocked words, they will see an error message so they can remove the blocked words.

### Microsoft Teams experience

When creating a team from the Teams client, the prefix and suffix are automatically added to the team's name. An error message will appear when users enter terms containing blocked words.

‎:::image type="content" source="../media/teams-blocked-words.png" alt-text="Blocked words warning from Teams":::

When creating a team from PowerShell, you will need to include the prefix and suffix in the cmdlet parameters. 

For example, the following cmdlet creates a team while prefix is "Contoso" and the suffix is "Group."
 
```powershell
New-Team -DisplayName "ContosoSalesGroup" -MailNickName "ContosoSalesGroup"
```

### Outlook web client experience

When users enter custom blocked words in Outlook, an error message will appear in the UI together with the blocked words. Users can then remove it, as shown on the example below:

‎:::image type="content" source="../media/outlook-web-blocked-words.png" alt-text="Blocked words warning from OWA":::


### Outlook Desktop experience

Groups created in Outlook desktop are compliant with naming policy, so the created naming policy will automatically apply when selecting create/edit and users will be presented with errors if there are custom blocked words in the group name or alias.



## License requirements

Using Azure AD naming policy for Microsoft 365 Groups requires that you possess but not necessarily assign an Azure Active Directory Premium P1 license or Azure AD Basic EDU license for each unique user (including guests) that is a member of one or more Microsoft 365 groups.

 
For more information, see [Groups naming policies](/office365/admin/create-groups/groups-naming-policy).
