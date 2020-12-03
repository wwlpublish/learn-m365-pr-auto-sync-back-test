Organizational data is needed to add context to analyses that are performed with Workplace Analytics. By uploading organizational data to Workplace Analytics, you provide descriptive information about employees. Workplace Analytics then maps that data to the collaboration data from Office 365. 

Organizational data supports Workplace Analytics analyses in many ways: it allows you to group and filter collaboration results by employee attributes of interest, create custom collaboration metrics, understand time allocation across groups of employees, and compare collaboration data to business outcomes.

Some representative organizational data categories include:
- Background: For example, employee type, full-time/part-time status, tenure
- Location: For example, region, country, city, building
- Organization: For example, business unit, cost center, division, department
- Role: For example, function, job family, level, grade
- Outcomes: For example, engagement score, performance rating, sales-quota attainment

Organizational data is uploaded into Workplace Analytics in a .csv file.

## Required data attributes
There are five required data attributes to include as part of your organizational data file upload to Workplace Analytics.

1. **PersonId** - This field must be the employee’s primary SMTP email address. Once data is uploaded, this field will be hashed and deidentified to maintain employee privacy.
2. **EffectiveDate** – This is the date of the “snapshot” in which the row of the Organization descriptor is valid. It helps analysts understand the effect that promotions, relocations, changes in management, and so on, might have on employee-collaboration patterns. It must be in the mm/dd/yyyy format. 

   The first organizational data file that you upload to Workplace Analytics should include multiple rows per employee to capture changes over time. Each row in your organizational data file has a different EffectiveDate that represents a different point-in-time snapshot. For example, in the following table, Ann was a senior individual contributor in May and June, but before July she was promoted to manager. If you are only able to provide one row of data per employee, we recommend that you use the latest organizational descriptor, but EffectiveDate is overridden to at least 13 months prior, to map to historical data that is available. For example, if you are creating an organizational file in October 2020, the EffectiveDate should be set to September 2019 for each row of organizational descriptor.
3. **ManagerId**: This field must be the employee’s manager’s primary SMTP email address. Workplace Analytics uses this column to measure how much time an employee spends with their direct manager. It is also hashed and deidentified once the data is uploaded.
4. **Organization**: Among other things, this field is used to calculate network breadth, a count of the number of organizations where an employee has had meaningful interactions in the last 28 days. Broadly defined organizations – for example, Finance or HR – result in fewer cross-org interactions and smaller network breadth. Narrowly defined organizations – for example, Financial Planning, Finance Region 1, Finance Region 2 – result in more cross-org interactions and larger network breadth.
5. **LevelDesignation**: Typically, the individual’s level as represented by Executive, VP, Director, Manager, IC, and so on. LevelDesignation and Organization together are used to calculate Redundant Meeting Hours (meeting hours where there are attendees from 3+ levels in the same organization).

For these five required attributes, every row in the file must have a non-blank value. If data is not available, fill it in with a dummy value such as "Missing" or "NoManager@contoso.com."

|PersonId|EffectiveDate|ManagerId|Organization|LevelDesignation|
|-|-|-|-|-|
|ann@contoso.com|05/01/2018|jered@contoso.com|Marketing|Senior IC|
|ann@contoso.com|06/01/2018|jered@contoso.com|Marketing|Senior IC|
|ann@contoso.com|07/01/2018|carolina@contoso.com|Marketing|Manager|

## Which employees to include
Employees to include: **all employees should be included in your organizational data file**, whether or not they are assigned Workplace Analytics licenses. This allows you to measure how licensed employees work with other employees across the organization.

US employees infographic

## Additional data attributes
You can include more than 100 different attributes, based on the analyses you want to conduct and how you want to group your data. The following table shows examples of attributes that you can include. Additional data attributes are optional and can be appended to the organizational file at any time. Only the required five attributes are needed to activate the Workplace Analytics system the first time.

Data attributes graphic/table 

## Best practices for creating and refreshing the organizational data file
 
There are several other considerations to keep in mind both when creating the organizational data file for the first time and when refreshing it, as shown in the following table:
 
Best practices table/graphic thing. (Probably need to recreate as actual text table)

After the organizational data file is created (including at least the five required attributes as column headers), the Workplace Analytics administrator can upload it to Workplace Analytics.

## Example scenario 
In the working group, you and Taylor receive input from the Workplace Analytics analysts on what organizational data they will need and how best to structure it to meet their analysis goals. Specifically, the analysts want the last year’s quarterly performance assessment of each employee coded as a numeric value from 1 to 5 to aid their analysis. This also means that Taylor must have multiple snapshots of the organizational data for each quarter to reflect the composition of Contoso and the performance assessments at each Effective Date.

Taylor obtains the organizational data from the HRIS, formats it for Workplace Analytics, and then uploads it to the tool.