Organizational data provides context to analyses that are performed with Workplace Analytics. By uploading organizational data to Workplace Analytics, you provide descriptive information about employees. Workplace Analytics then maps that data to the collaboration data from Microsoft 365.

Organizational data supports Workplace Analytics analyses in many ways, including the following:

- Group and filter collaboration results by employee attributes of interest.
- Create custom collaboration metrics.
- Understand time allocation across groups of employees.
- Compare collaboration data to business outcomes.

Some representative organizational data categories include:

- Background: For example, employee type, full-time/part-time status, tenure
- Location: For example, region, country, city, building
- Organization: For example, business unit, cost center, division, department
- Role: For example, function, job family, level, grade
- Outcomes: For example, engagement score, performance rating, sales-quota attainment

Organizational data is uploaded into Workplace Analytics in a .csv file.

## Required data attributes

There are five required data attributes to include as part of your organizational data file upload to Workplace Analytics.

- **PersonId** - The employee's primary SMTP email address. When the data is uploaded, this field is hashed and deidentified to maintain employee privacy.
- **EffectiveDate** – The date of the "snapshot" in which the row of the Organization descriptor is valid. It helps analysts understand the effect that things like promotions, relocations, changes in management might have on employee-collaboration patterns. It must be in the *mm/dd/yyyy* format.

   The first organizational data file that you upload to Workplace Analytics should include multiple rows per employee to capture changes over time. Each row in your organizational data file has a different EffectiveDate that represents a different point-in-time snapshot. For example, in the table after this list, Ann was a senior individual contributor in May and June, but she was promoted to manager before July. If you are only able to provide one row of data per employee, use the latest organizational descriptor, but be aware that **EffectiveDate** is overridden to at least 13 months prior, to map to available historical data. For example, if you're creating an organizational file in October 2020, set the **EffectiveDate** to *September 2019* for each row of organizational descriptor.
- **ManagerId**: The employee's manager's primary SMTP email address. Workplace Analytics uses this data to measure how much time an employee spends with their direct manager. It's also hashed and deidentified once the data is uploaded.
- **Organization**: Among other things, this field is used to calculate network breadth, the number of organizations where an employee has had meaningful interactions in the last 28 days. Organizations that are broadly defined – for example, Finance or HR – result in fewer cross-org interactions and smaller network breadth. Narrowly-defined organizations – for example, Financial Planning, Finance Region 1, Finance Region 2 – result in more cross-org interactions and larger network breadth.
- **LevelDesignation**: The individual's level as represented by Executive, VP, Director, Manager, IC, and so on. **LevelDesignation** and **Organization** together are used to calculate **Redundant Meeting Hours** (meeting hours where there are attendees from 3+ levels in the same organization).

For these five required attributes, every row in the file must have a non-blank value. If data isn't available, fill it in with a dummy value such as "Missing" or "NoManager@contoso.com."

|PersonId|EffectiveDate|ManagerId|Organization|LevelDesignation|
|-|-|-|-|-|
|ann@contoso.com|05/01/2018|jered@contoso.com|Marketing|Senior IC|
|ann@contoso.com|06/01/2018|jered@contoso.com|Marketing|Senior IC|
|ann@contoso.com|07/01/2018|carolina@contoso.com|Marketing|**Manager**|

## Which employees to include

**All employees should be included in your organizational data file**, whether or not they are assigned Workplace Analytics licenses. This lets you  measure how employees in the analysis population work with other employees across the organization.

:::image type="content" source="../media/which-employees-include.png" border="false" alt-text="A graphic shows first an example scenario - the admin assigned licenses to only employees in the United States, but they want to understand how those US employees invested their time with employees across the globe. Then there are two pie charts that compare the time those US employees devoted to other US employees versus all users.":::

## Additional data attributes

The first time that you activate Workplace Analytics you need just the five *required* attributes. There are more than 100 additional *optional* attributes that you can use, based on the analyses you want to conduct and how you want to group your data. The following table shows some examples of these attributes. Additional data attributes are optional, and you can append them to the organizational file at any time.  

|Type|Description|Example attributes|
|-|-|-|
|Background|Employee type, status, and job history. Frequently used to scope an analysis.|- Tenure <br>- Employee type (Regular, Contingent, Intern)<br>- Hourly wage, Exempt/Non-Exempt|
|Location|Where the employee sits geographically|- Region, Country, City <br>- Campus <br>- Building|
|Organization|The employee's position in the organizational reporting structure|- Business unit<br>-Division, Department, Cost center<br>- Level, Layer, Span<br>- Leader reports to|
|Role|The employee's skills, function, and responsibilities|- Function, Title<br>- Manager flag<br>- Career level<br>- Level designation|
|Outcomes|Includes measures that are driven by *how* an employee works and that contribute to overall business results|- Performance rating, Engagement survey score<br>- Sales quota attainment<br>- Manager effectiveness score<br>- Time and Attendance|

## Best practices for creating and refreshing the organizational data file

There are several considerations to keep in mind both the first time you create the organizational data file and when you refresh it, as shown in the following table:

|Area|Best practice|
|-|-|
|Scope|- Initial organizational file should include one snapshot for each of the past 13 months to map to initial historical collaboration data load. <br>- Include descriptive organizational data for all employees in the company, even if they're not part of the analysis population, to enrich custom collaboration metrics.|
|Updates|- Include one snapshot for each month historically and going forward to capture changes to employee attributes.<br>- Upload files including "net new" employees, effective dates, and columns using the **Append** option. Ensure there are no missing values in the **Effective Dates** attribute.<br>- Avoid renaming columns.|
|Quality|Avoid columns with:<br>- Many missing values<br>- Too broad or detailed for useful grouping and filtering (like company code or job title)<br>- Redundant attributes (like department name or code)<br>- Dirty data (for example, multiple spellings of one value, like "Mktg" and "Marketing")|
|Formatting|- Ensure fields are properly formatted for the type of data they contain (dates, text/strings, or numbers). <br>- Ensure each data source or field has a unique identifier. <br>- For optional fields, if values aren't available, leave empty. (Replacing with "0" will impact average values.)|
|Privacy|To help ensure privacy, don't include employee names or ID numbers in the file.|

You're now ready to upload the organizational data file to Workplace Analytics.

## Example scenario

In the working group, you and Taylor receive input from the Workplace Analytics analysts on what organizational data they need and how best to structure it to meet their goals. Specifically, the analysts want the last year's quarterly performance assessment for each employee coded as a numeric value (from 1 to 5). This also means that Taylor needs multiple snapshots of the organizational data for each quarter to reflect the composition of Contoso and the performance assessments at each **Effective Date**.

Taylor gets the organizational data from the HRIS, formats it for Workplace Analytics, and then uploads it to the tool.
