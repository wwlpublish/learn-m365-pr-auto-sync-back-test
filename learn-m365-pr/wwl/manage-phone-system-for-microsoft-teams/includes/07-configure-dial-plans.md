It's sometimes useful to have small, easy to remember extension numbers for employees. Users can dial a three or four-digit extension number to reach specific people or a call queue. Organizations can implement this type of calling feature in Microsoft Teams by creating a dial plan.

A dial plan is a named set of normalization rules that translate dialed phone numbers by an individual user into an alternate format (typically E.164) for purposes of call authorization and call routing. It consists of one or more rules that define how phone numbers expressed in various formats are translated to an alternate format. 

The same dial string may be interpreted and translated differently in different dial plans. As a result, the same dialed number may be translated and routed differently depending on which dial plan is assigned to a given user. There can be a maximum of 1,000 tenant dial plans.

## Scopes of dial plans 

There are two types of dial plans in Microsoft Teams:

* **Service-scoped dial plans**. A service-scoped dial plan is defined for every country or region where Phone System is available. Each user is automatically assigned the service country/region dial plan that matches the usage location assigned to the user. You can't change the service country/region dial plan.

* **Tenant-scoped dial plans**. As clients are provisioned, they obtain an "effective dial plan." This dial plan is a combination of the service country/region dial plan and the appropriately scoped tenant dial plan. This option doesn't require an organization to define all normalization rules in tenant dial plans because they may already exist in the service country/region dial plan. 

The following sections examine in greater detail how organizations should plan for each of these dial plan types. 

### Plan for Service dial plans

An organization can plan for the following service dial plans:

- **Service Country/Region**. If no tenant scoped dial plan is defined and no tenant user scoped dial plan is assigned to the provisioned user, the user will receive an effective dial plan mapped to the service country/region associated with their usage location.

- **Service Country/Region + Tenant Global-scoped**. If a tenant user dial plan is defined but not assigned to a user, the provisioned user will receive an effective dial plan consisting of a merged tenant dial plan and the service country/region dial plan associated with their usage location.

- **Service Country/Region + Tenant User-scoped**. If a tenant user dial plan is defined and assigned to a user, the provisioned user will receive an effective dial plan consisting of the merged tenant user dial plan and the service country/region dial plan associated with their usage location.


### Plan for tenant dial plans

An organization should complete the following steps when planning for a tenant dial plan:

1. Decide whether a custom dial plan is needed to enhance the user dialing experience. Organizations typically support non-E.164 dialing, such as extensions or abbreviated national dialing.

1. Determine whether tenant global or tenant user-scoped dial plans are needed, or both. User-scoped dial plans are needed if users have different local dialing requirements.

1. Identify valid number patterns for each required dial plan. Only the number patterns that aren't defined in the service level country dial plans are required.

1. Develop an organization-wide scheme for naming dial plans. Adopting a standard naming scheme assures consistency across an organization and makes maintenance and updates easier.


## Configure a dial plan

Dial plans can be configured using either the Teams admin center or Windows PowerShell.

### Use Teams admin center

Complete the following steps to configure a dial plan using the Teams admin center:

1. In the left-hand navigation pane of the Microsoft Teams admin center, select **Voice** > **Dial plan**.
2. Select **Add**, and then enter a name and description for the dial plan.

    ‎:::image type="content" source="../media/create-dial-plan.png" alt-text="Screenshot showing the Add page for creating a dial plan":::

3. Under **Dial plan details** section, specify an external dialing prefix if users must dial one or more leading digits (for example, 9) to get an external line. To configure a dial plan prefix, update the following fields:
    * **External dialing prefix**. Enter an external dialing prefix. The prefix can be up to four characters (#,*, and 0-9).
    * **Optimized device dialing**. Turn this option On. If you specify an external dialing prefix, you must also turn on this setting to apply the prefix so that calls can be made outside your organization.

4. Under **Normalization rules**, configure and associate one or more normalization rules for the dial plan. There can be a maximum of 50 normalization rules in a given tenant dial plan.

    Normalization rules use .NET Framework regular expressions to specify numeric match patterns that the server uses to translate dial strings to E.164 format. 
    
    The following table shows sample normalization rules that are written as .NET Framework regular expressions. For more examples, see [Sample normalization rules](https://docs.microsoft.com/microsoftteams/what-are-dial-plans#sample-normalization-rules?azure-portal=true).


    | Rule name<br/> | Description<br/> | Number pattern<br/> | Translation<br/> | Example<br/> |
    |:--|:--|:--|:--|:--|
    |4digitExtension  <br/> |Translates four-digit extensions.  <br/> |^(\\d{4})$  <br/> |+1425555$1  <br/> |0100 is translated to +14255550100  <br/> |
    |5digitExtension  <br/> |Translates five-digit extensions.  <br/> |^5(\\d{4})$  <br/> |+1425555$1  <br/> |50100 is translated to +14255550100  <br/> |
    |7digitcallingRedmond  <br/> |Translates  seven-digit numbers to Redmond local numbers.  <br/> |^(\\d{7})$  <br/> |+1425$1  <br/> |5550100 is translated to +14255550100  <br/>|


    ‎:::image type="content" source="../media/normalization-rules.png" alt-text="Screenshot showing the Normalization rules for creating a dial plan":::

5.  Select **Move up** or **Move down** to change the position of rules in the list.

    Normalization rules are matched from top to bottom. As such, the order in which they appear in a tenant dial plan is important. Arrange the normalization rules in the order in which you want them applied. 


6. Select **Save**.
7. If you want to test the dial plan, under **Test dial plan**, enter a phone number, and then select **Test**.

8. You can assign then dial plan to users.

### Use PowerShell
To configure dial plans using Windows PowerShell,  use the following PowerShell cmdlets:

* To create a new dial plan, run: ```New-CsTenantDialPlan```
* To edit the settings of an existing dial plan, run: ```Set-CsTenantDialPlan ```
* To add users to a dial plan, run: ```Grant-CsTenantDialPlan```
* To see the settings of the effective dial plan, run: ```Get-CsEffectiveTenantDialPlan```


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”