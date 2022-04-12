Organizational data provides context to the workplace analysis created by Microsoft Viva Insights. When analysts upload organizational data into Viva Insights, they can use aggregated employee data for more complete analysis. Viva Insights can then map that data to the collaboration data from Microsoft 365.

Organizational data supports Viva Insights analysis in many ways, including:

 -  Group and filter collaboration results by employee attributes of interest.
 -  Create custom collaboration metrics.
 -  Understand time allocation across groups of employees.
 -  Compare collaboration data to business outcomes.

Some representative organizational data categories include:

 -  **Background**. For example, employee type, full-time or part-time status, and tenure.
 -  **Location**. For example, region, country, city, and building.
 -  **Organization**. For example, business unit, cost center, division, and department.
 -  **Role**. For example, function, job family, level, and grade.
 -  **Outcomes**. For example, engagement score, performance rating, and sales-quota attainment.

Organizational (HR) data is uploaded into Viva Insights as a .csv file.

### Required data attributes

The following data attributes are required as part of the organizational data file that you upload to Microsoft Viva Insights:

 -  **PersonId**. The employee's primary SMTP email address. When the data is uploaded, this field is hashed and deidentified to maintain employee privacy.
 -  **EffectiveDate**. The date is a "snapshot" for when the row of the Organization descriptor is valid. It helps analysts understand HR changes, such as job promotions, relocations, and changes in management. It also enables analysts to see how these changes may affect employee-collaboration patterns. The effective date must be in the mm/dd/yyyy format.
    
    The first organizational data file uploaded to Viva Insights should include multiple rows for employees that capture changes over time. Each row in your organizational data file has a different EffectiveDate that represents a different point-in-time snapshot. For example, in the chart that appears after this list, Ann was a Senior IC (individual contributor) in May and June. However, Ann was promoted to Manager before July.
    
    You should use the latest organizational descriptor if you're only able to provide one row of data for each employee. However, keep in mind the EffectiveDate is overridden to at least 13 months prior to map to available historical data. For example, if you're creating an organizational upload file for January 2022, set the EffectiveDate to December 2020 for each organizational descriptor. Optionally, if the EffectiveDate value is left blank, Viva Insights automatically adds the upload date for all EffectiveDate values while processing the newly uploaded data.
 -  **ManagerId**. A manager's primary SMTP email address. Viva Insights uses this data to measure how much time an employee spends with their direct manager. This ManagerId field is hashed and deidentified to maintain employee privacy.
 -  **Organization**. Among other things, this data is used to calculate network breadth, the number of organizations where an employee has had meaningful interactions in the last 28 days. Organizations that are broadly defined, such as Finance and HR, result in fewer cross-organization interactions and smaller network breadth. Narrowly defined organizations, such as Financial Planning and Finance Region 1, Finance Region 2, result in more cross-organization interactions and larger network breadth.
 -  **LevelDesignation**. Although this attribute is optional, it's required for some of the more advanced analysis available in Viva Insights. An example of advanced analysis includes manager and team collaboration. The LevelDesignation attribute defines an individual's level as represented by Executive, VP, Director, Manager, IC, and so on. For example, LevelDesignation and Organization together are used to calculate Redundant Meeting Hours (meeting hours where there are attendees from 3+ levels in the same organization).

For the following attributes, every row in the file must have a non-blank value. If data isn't available, you can leave EffectiveDate blank, or for the other fields, you can enter a dummy value such as "Missing" or "NoManager@contoso.com" to keep the data valid for the upload.

:::image type="content" source="../media/employee-attribute-chart-3c254d84.png" alt-text="chart showing the data file for organizational data":::


### Other data attributes

The first time that you activate Microsoft Viva Insights, you need just the five required attributes. There are more than 100 other optional attributes that you can also use. The attributes you select should be based on the analysis you want to conduct and how you want to group your data. The following table shows some examples of these attributes. Although they're optional, and you can append them to the organizational file at any time.

:::row:::
  :::column:::
    **Type**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    **Example attributes**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Background
  :::column-end:::
  :::column:::
    Employee type, status, and job history. Frequently used to scope an analysis.
  :::column-end:::
  :::column:::
    

 -  Tenure
 -  Employee type (Regular, Contingent, Intern)
 -  Hourly wage, Exempt/Non-Exempt


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Location
  :::column-end:::
  :::column:::
    Where the employee sits geographically.
  :::column-end:::
  :::column:::
    

 -  Region, Country, City
 -  Campus
 -  Building


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Level
  :::column-end:::
  :::column:::
    The employee's position in the organizational reporting structure.
  :::column-end:::
  :::column:::
    

 -  Division, Department, Cost center
 -  Level, Layer, Span
 -  Leader reports to


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Role
  :::column-end:::
  :::column:::
    The employee's skills, function, and responsibilities.
  :::column-end:::
  :::column:::
    

 -  Function, Title
 -  Manager flag
 -  Career level
 -  Level designation


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Outcomes
  :::column-end:::
  :::column:::
    Includes measures that are driven by *how* an employee works and that contribute to overall business results.
  :::column-end:::
  :::column:::
    

 -  Performance rating, Engagement survey score
 -  Sales quota attainment
 -  Manager effectiveness score
 -  Time and Attendance


  :::column-end:::
:::row-end:::


### Best practices for creating and refreshing the organizational data file

There are several considerations to keep in mind both the first time you create the organizational data file and when you refresh it. These considerations are summarized in the following table.

:::row:::
  :::column:::
    **Area**
  :::column-end:::
  :::column:::
    **Best practice**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Scope
  :::column-end:::
  :::column:::
    

 -  Initial organizational file should include one snapshot for each of the past 13 months to map to initial historical collaboration data load.
 -  Include descriptive organizational data for all employees in the company, even if they're not part of the analysis population. This design will help enrich the custom collaboration metrics.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Updates
  :::column-end:::
  :::column:::
    

 -  Include one snapshot for each month historically and going forward to capture changes to employee attributes.
 -  Upload files including "net new" employees, effective dates, and columns using the Append option. Ensure there are no missing values or that all values are left blank for EffectiveDate.
 -  Avoid renaming columns.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Quality
  :::column-end:::
  :::column:::
    Avoid columns with:

 -  Too many missing values
 -  Too broad or detailed to be useful for grouping and filtering (such as company code or job title)
 -  Redundant attributes (such as department name or code)
 -  Dirty data (such as multiple spellings of one value, like "Mktg" and "Marketing")


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Formatting
  :::column-end:::
  :::column:::
    

 -  Ensure fields are properly formatted for the type of data they contain (dates, text strings, or numbers).
 -  Ensure each data source or field has a unique identifier.
 -  For optional fields, if values aren't available, leave them blank or empty. (Replacing with "0" will affect average values.) 


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Privacy
  :::column-end:::
  :::column:::
    To help ensure privacy, don't include employee names or ID numbers in the file.
  :::column-end:::
:::row-end:::


You're now ready to upload the organizational data (.csv) file to Workplace Analytics.

### Example scenario

You're a member of Contoso's Microsoft Viva Insights pilot project team. You received input from the workplace analysts on what organizational data they need and how best to structure it to meet their goals. Specifically, the analysts want last year's quarterly performance assessment for each employee coded as a numeric value (from 1 to 5). By implementing this coding scheme, you'll need multiple snapshots of the organizational data for each quarter to reflect the composition of Contoso and the performance assessments based on the Effective Date values.

You received the organizational data from HR, after which you formatted it and then uploaded it into Viva Insights.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”