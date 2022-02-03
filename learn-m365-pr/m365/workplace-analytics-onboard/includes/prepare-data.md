Organizational data provides context to the analyses created by Workplace Analytics for Viva Insights. By uploading organizational data to the Workplace Analytics web app, analyses can use aggregated employee data for more complete analysis. Workplace Analytics can then map that data to the collaboration data from Microsoft 365.

Organizational data supports Workplace Analytics analyses in many ways, including the following:

- Group and filter collaboration results by employee attributes of interest.
- Create custom collaboration metrics.
- Understand time allocation across groups of employees.
- Compare collaboration data to business outcomes.

Some representative organizational data categories include:

- Background: For example, employee type, full-time or part-time status, and tenure
- Location: For example, region, country, city, and building
- Organization: For example, business unit, cost center, division, and department
- Role: For example, function, job family, level, and grade
- Outcomes: For example, engagement score, performance rating, and sales-quota attainment

Organizational (HR) data is uploaded into Workplace Analytics as a .csv file.

## Required data attributes

The following data attributes are required as part of your organizational data file upload to Workplace Analytics.

- **PersonId** - The employee's primary SMTP email address. When the data is uploaded, this field is hashed and deidentified to maintain employee privacy.
- **EffectiveDate** – The date is a "snapshot" for when the row of the Organization descriptor is valid. It helps analysts understand HR changes, such as job promotions, relocations, and changes in management, and how they might effect employee-collaboration patterns. It must be in the *mm/dd/yyyy* format.

   The first organizational data file uploaded to Workplace Analytics should include multiple rows for employees that capture changes over time. Each row in your organizational data file has a different EffectiveDate that represents a different point-in-time snapshot. For example, in the table after this list, Ann was a Senior IC (individual contributor) in May and June, but she was promoted to Manager before July. If you are only able to provide one row of data for each employee, use the latest organizational descriptor, but be aware that **EffectiveDate** is overridden to at least 13 months prior to map to available historical data. For example, if you're creating an organizational upload file for January 2022, set the **EffectiveDate** to *December 2020* for each organizational descriptor. *Optionally*, if the **EffectiveDate** value is left blank, Workplace Analytics will automatically add the upload date for all EffectiveDate values while processing the newly uploaded data.

- **ManagerId**: A manager's primary SMTP email address. Workplace Analytics uses this data to measure how much time an employee spends with their direct manager, which is also hashed and deidentified to maintain employee privacy.
- **Organization**: Among other things, this data is used to calculate network breadth, the number of organizations where an employee has had meaningful interactions in the last 28 days. Organizations that are broadly defined, such as Finance and HR, result in fewer cross-organization interactions and smaller network breadth. Narrowly-defined organizations, such as Financial Planning and Finance Region 1, Finance Region 2, result in more cross-organization interactions and larger network breadth.
- **LevelDesignation**: Optional, but required for some of the more advanced analysis available in Workplace Analytics, such as manager and team collaboration. This defines an individual's level as represented by Executive, VP, Director, Manager, IC, and so on. For example, **LevelDesignation** and **Organization** together are used to calculate **Redundant Meeting Hours** (meeting hours where there are attendees from 3+ levels in the same organization).

For the following attributes, every row in the file must have a non-blank value. If data isn't available, you can leave EffectiveDate blank, or for the other fields, you can enter a dummy value such as "Missing" or "NoManager@contoso.com" to keep the data valid for the upload.

|PersonId|EffectiveDate|ManagerId|Organization|LevelDesignation|
|-|-|-|-|-|
|ann@contoso.com|05/01/2020|jered@contoso.com|Marketing|Senior IC|
|ann@contoso.com|06/01/2020|jered@contoso.com|Marketing|Senior IC|
|ann@contoso.com|07/01/2020|carolina@contoso.com|Marketing|Manager|

## Which employees to include

**All employees should be included in your organizational data file**, whether or not they are assigned Workplace Analytics or Viva Insights licenses. This allows you to measure how employees in the analysis population work with other employees across the organization.

:::image type="content" source="../media/which-employees-include.png" border="false" alt-text="A graphic shows first an example scenario - the admin assigned licenses to only employees in the United States, but they want to understand how those US employees invested their time with employees across the globe. Then there are two pie charts that compare the time those US employees devoted to other US employees versus all users.":::

## Additional data attributes

The first time that you activate Workplace Analytics you need just the five *required* attributes. There are more than 100 additional *optional* attributes that you can use, based on the analyses you want to conduct and how you want to group your data. The following table shows some examples of these attributes. Additional data attributes are optional, and you can append them to the organizational file at any time.  

|Type|Description|Example attributes|
|-|-|-|
|Background|Employee type, status, and job history. Frequently used to scope an analysis.|- Tenure <br>- Employee type (Regular, Contingent, Intern)<br>- Hourly wage, Exempt/Non-Exempt|
|Location|Where the employee sits geographically|- Region, Country, City <br>- Campus <br>- Building|
|Level|The employee's position in the organizational reporting structure|- Business unit<br>-Division, Department, Cost center<br>- Level, Layer, Span<br>- Leader reports to|
|Role|The employee's skills, function, and responsibilities|- Function, Title<br>- Manager flag<br>- Career level<br>- Level designation|
|Outcomes|Includes measures that are driven by *how* an employee works and that contribute to overall business results|- Performance rating, Engagement survey score<br>- Sales quota attainment<br>- Manager effectiveness score<br>- Time and Attendance|

## Best practices for creating and refreshing the organizational data file

There are several considerations to keep in mind both the first time you create the organizational data file and when you refresh it, as shown in the following table:

|Area|Best practice|
|-|-|
|Scope|- Initial organizational file should include one snapshot for each of the past 13 months to map to initial historical collaboration data load. <br>- Include descriptive organizational data for all employees in the company, even if they're not part of the analysis population, to enrich custom collaboration metrics.|
|Updates|- Include one snapshot for each month historically and going forward to capture changes to employee attributes.<br>- Upload files including "net new" employees, effective dates, and columns using the **Append** option. Ensure there are no missing values or that all values are left blank for **EffectiveDate**.<br>- Avoid renaming columns.|
|Quality|Avoid columns with:<br>- Too many missing values<br>- Too broad or detailed to be useful for grouping and filtering (such as company code or job title)<br>- Redundant attributes (such as department name or code)<br>- Dirty data (such as multiple spellings of one value, like "Mktg" and "Marketing")|
|Formatting|- Ensure fields are properly formatted for the type of data they contain (dates, text strings, or numbers). <br>- Ensure each data source or field has a unique identifier. <br>- For optional fields, if values aren't available, leave them blank or empty. (Replacing with "0" will impact average values.)|
|Privacy|To help ensure privacy, don't include employee names or ID numbers in the file.|

You're now ready to upload the organizational data (.csv) file to Workplace Analytics.

## Example scenario

In the working group, you and Taylor get input from the Workplace Analytics analysts on what organizational data they need and how best to structure it to meet their goals. Specifically, the analysts want the last year's quarterly performance assessment for each employee coded as a numeric value (from 1 to 5). This also means that Taylor needs multiple snapshots of the organizational data for each quarter to reflect the composition of Contoso and the performance assessments based on the **Effective Date** values.

Taylor gets the organizational data from the HRIS, formats it, and then uploads in Workplace Analytics.
