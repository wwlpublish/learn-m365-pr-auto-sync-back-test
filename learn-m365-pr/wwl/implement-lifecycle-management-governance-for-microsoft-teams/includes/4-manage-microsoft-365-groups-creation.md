There are many ways to create a Microsoft 365 group. Beyond the Microsoft 365 admin center, users can create Microsoft 365 groups in the following three primary communication applications in Microsoft 365:

- **Outlook**. Collaboration through email with a shared group inbox and calendar.  

- **Microsoft Teams**. A persistent chat-based workspace where you can have informal, real-time, conversations around various topics, organized by specific subgroups.  

- **SharePoint**. A central repository for information, links and content relating to your group.

- **Yammer**. Enterprise social experience for collaboration.

While users can create a Microsoft 365 group from Outlook or other apps, as an admin, you may need to create or delete groups, add or remove members, and customize how they work. The Microsoft 365 admin center is the place to do this.

## Create a new Microsoft 365 group

### Use Microsoft 365 admin center

1. In the Microsoft 365 admin center, on the left navigation pane, select **Groups** > **Active groups**.

2. On the **Groups** page, select **Add a group**.

3. On the **Choose a group type** page, select **Microsoft 365**, and select Next.

4. On the **Set up the basics** page, type a name for the group, and, optionally, a description. Select Next.

5. On the **Assign owners** page, select **+ Assign owners** and add the name of one or more people who will be designated to manage the group.

6. On the **Add members** page, you can select **+ Add members** to add the members of the group or skip to the next step. 

7. On the **Edit settings** page, type a unique email address for the group, choose a privacy option and whether you want to add Microsoft Teams, and then selectNext.

‎‎:::image type="content" source="../media/create-m365-group.png" alt-text="Create a Microsoft 365 Group":::

5. In the **Group email address** field, type an email address for the group, for example SalesDepartment@contoso.com and optionally enter a description in the **Description** field.

6. From the **Privacy** drop-down menu, choose **Private** or **Public**.

7. Under **Owner** section, select **Select owner**, then choose the user who will be the owner of the group, and then select **Add**.
 
Once the group is created, it will appear in Outlook with members assigned to it.

### Use PowerShell

To create Microsoft 365 Group with PowerShell, use the ```New-UnifiedGroup``` cmdlet when connected to Exchange Online. For example, to create a new Microsoft 365 group with name **"Sales Department"** and alias **Salesdepartment**, run the following cmdlet:

```powershell
New-UnifiedGroup -DisplayName "Sales Department" -Alias Salesdepartment
```

## Upgrade a distribution list to a Microsoft 365 group

**Distribution lists** have a long history in messaging for organizing people into groups to facilitate communication and collaboration. But distribution lists are limited to email messages, and available in SharePoint for distribution only. Turning a Distribution List into a Microsoft 365 Group adds more collaboration capabilities for users. It also has the benefit of keeping permissions and membership intact instead of creating a new group that you must add to your Access Control.

> [!NOTE]
> If you upgrade distribution lists to a Microsoft 365 Group, existing users will not receive a welcome mail when joining this group.

### Use Exchange admin center

To upgrade a distribution list to a Microsoft 365 Group, you need to log in to the Exchange admin center as an administrator such as Microsoft 365 global admin or Exchange admin and follow these steps:

1. Go to the Exchange admin center.

2. In the Exchange admin center, go to **Recipients** > **Groups**.

3. On the **Groups** page, select **Distribution list** tab. ‎You'll see a distribution lists (also called **distribution groups** ) that are eligible to be upgraded to Microsoft 365 groups.  

4. Select a distribution group list (also called a **distribution group**) that you want to upgrade to a Microsoft 365 group. 

5. Select **Upgrade distribution group** option from the top menu.

6. On the information dialog, select **Upgrade** to confirm the upgrade. The process begins immediately. Depending on the size and number of DLs, the process can take several minutes or up to some hours. 

    ‎‎:::image type="content" source="../media/upgrade-dist-group.png" alt-text="The picture shows the Upgrade Distribution group dialog from Exchange admin center":::


### Use PowerShell

You can also use PowerShell to upgrade distribution lists. For this, you must connect your PowerShell to Exchange Online or install the Exchange Online module. 

* To upgrade one or more distribution lists, run the ```Upgrade-DistributionGroup``` cmdlet. 
* As an alternative, you can also run ```New-UnifiedGroup``` cmdlet to convert a single distribution group. 

You can also pass multiple DLs as a batch and upgrade them together. For example, if you want to upgrade two distribution lists with SMTP address marketing-dl@contoso.com and finance-dl@contoso.com, run the following command:

```powershell
Upgrade-DistributionGroup -DlIdentities marketing-dl@contoso.com, finance-dl@contoso.com
```

#### Upgrade all eligible DLs
There are two ways in which you can upgrade all the eligible DLs.

* Get the eligible DLs in the tenant and upgrade them using the upgrade command:

    ```powershell
    Get-EligibleDistributionGroupForMigration | Foreach-Object{
        Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
    }
    ```
* Get the list of all DLs and upgrade only the eligible DLs

    ```powershell
    Get-DistributionGroup| Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
    }
    ```

A distribution list will not be eligible for an upgrade if it fulfills any of the following criteria:

|**Property**|**Eligible?**|
|:--|:--|
|On-premises managed distribution list.  <br/> |No  <br/> |
|Nested distribution lists. Distribution list either has child groups or is a member of another group.  <br/> |No  <br/> |
|Distribution lists with member **RecipientTypeDetails** other than **UserMailbox**, **SharedMailbox**, **TeamMailbox**, **MailUser**  <br/> |No  <br/> |
|Distribution list that has more than 100 owners  <br/> |No  <br/> |
|Distribution list that only has members but no owner  <br/> |No  <br/> |
|Distribution list that has alias containing special characters  <br/> |No  <br/> |
|If the distribution list is configured to be a forwarding address for Shared Mailbox  <br/> |No  <br/> |
|If the DL is part of **Sender Restriction** in another DL.  <br/> |No  <br/> |
|Security groups  <br/> |No  <br/> |
|Dynamic Distribution lists  <br/> |No  <br/> |
|Distribution lists that were converted to **RoomLists**  <br/> |No  <br/> |

   

## Manage a Microsoft 365 group

After the group has been created, administrators can add members and configure other settings. Also, users can add themselves or request approval for membership.

### Use Microsoft 365 admin center

1. In the Microsoft 365 admin center, on the **Groups** page, select the group that you want to configure.

2. On the selected group page, you can edit the settings, such as managing members and owners, changing group privacy, changing email sending permissions, or creating a team from the group.  
‎‎:::image type="content" source="../media/managing-o365group.png" alt-text="Managing O365 group":::  
‎
### Use PowerShell 
 
To manage Microsoft 365 Group with PowerShell, use the ```Set-UnifiedGroup``` cmdlet. For example, to configure "**Sales Department"** group to receive mail from unauthenticated (external) senders, run the following cmdlet:

```powershell
Set-UnifiedGroup -DisplayName "Sales Department" -RequireSenderAuthenticationEnabled $false
```

## Strategies for Microsoft 365 Groups creation

Organizations may have specific requirements about who can create Microsoft 365 groups. The following table lists the advantages of the different provisioning models:

| **Model**| **Advantages**| **When to use** |
| - | - | - |
| Open (default)| Users can create their own groups as needed| Most common if you do not want to restrict group creation in any way. |
| IT-led| Users can request a group from IT department, which will lead them in selecting the best collaboration tools for their needs| Very often done in large enterprises to control group creation centrally, and maybe add additional information such as internal back-charging numbers to charge for each group. |
| Controlled| Group creation restricted to specific people, teams, or services| An ideal approach to prevent uncontrolled group creation by users but be not as restrictive as with the IT-led model. For example, each department can decide on their own how to handle group creation. |
 

### Restrict creation of teams by modifying group creation permissions

You can restrict Microsoft 365 Group creation, for example, to the members of a particular security group. 

To restrict the creation of new teams, you need to modify the Microsoft 365 Groups creation permissions since all teams are based on Microsoft 365 Groups. 

If you want to restrict the creation of new Teams to a subset of users, you need to create a security group and use the AzureAD PowerShell module to modify the AzureAD Directory Settings on a tenant basis. If you run the following script in your environment, you will stop users from creating new Microsoft 365 Groups unless they are a member of the security group you specified in the first line of the script.


The script will perform the following actions:


1. Run ```Connect-AzureAD``` to connect to the AzureAD PowerShell

2. Get the ObjectID of the Directory Setting for Microsoft 365 Groups (unified groups) using ```Get-AzureADDirectorySetting```

3. Use ```New-AzureADDirectorySetting``` to create the setting from a template if it does not exist

4. Use ```Set-AzureADDirectorySetting``` to set the ```EnableGroupCreation``` setting to false and block the creation of Microsoft 365 Groups.

5. Allow a specific Security group to override the group creation restriction by modifying the Setting before applying it.

6. Display the results of the change.

```powershell
$GroupName = "<SecurityGroupName>"
$AllowGroupCreation = "False"

Connect-AzureAD

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id

if(!$settingsObjectID){

$template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}

$settingsCopy = $template.CreateDirectorySetting()

New-AzureADDirectorySetting -DirectorySetting $settingsCopy

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id

}


$settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
$settingsCopy["EnableGroupCreation"] = $AllowGroupCreation


if($GroupName)

{ $settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid

}


Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

 

For more information, see [Manage who can create Microsoft 365 Groups](/office365/admin/create-groups/manage-creation-of-groups). 


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”