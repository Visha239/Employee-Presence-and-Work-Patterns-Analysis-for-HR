Problem Definition:
The Human Resources department plays a crucial role in ensuring the well-being and productivity of the workforce. One essential aspect is understanding the distribution of employee presence within the company. The goal is to analyze the percentage of in-office presence, work-from-home (WFH), and sick leave patterns to optimize HR strategies and improve overall employee experience.

Target Audience:
This analysis targets HR professionals, department managers, and organizational leadership who seek insights into employee attendance patterns for effective workforce management.

Background:
Understanding the dynamics of employee presence is vital for creating a conducive work environment and promoting a healthy work-life balance. The COVID-19 pandemic has accelerated the adoption of remote work, making it imperative to assess the distribution of in-office and remote work and identify trends in sick leave patterns.

Steps followed:

1.Data Collection:
Gather the required data for analysis.

2.Data Formatting:
Since the data spans three months and column names align across sheets, copy-pasting data from one month to another maintains alignment. Ensure uniformity in column names across all sheets.

3.Power BI Data Loading and Template Creation:
Load the data into Power BI and create a template. This template will be applicable to future sheets, streamlining the analysis process for added data.
Date Column Preparation:
Consolidate all dates into a single column to facilitate data appending.

4.Column Filtering:
Remove all columns except the date column.

5.Data Cleaning:
Clean the data by eliminating blank top rows and ensuring proper column naming.

6.Data Alignment:
Unpivot the date column to ensure alignment.

7.Date Format Standardization:
Filter the date column to remove any non-date data by selecting the date format in the filter option.

8.Parameter Creation:
Establish a parameter with the same sheet name.

9.Function Implementation:
Develop a function for universal application across all entities.

10.Function Invocation:
Create a new column and apply the function to the original sheet.

11.Data Loading for Visualization:
Load the processed data for visualization purposes.

12.Measure Creation:
Formulate measures using DAX formulas.
a. Total Working Days:

Total Working Days = 
VAR totaldays = COUNT('Finaldata'[Value]) 
VAR holidays = CALCULATE(COUNT('Finaldata'[Value]), 'Finaldata'[Value] IN {"WO", "HO"})
RETURN
totaldays - holidays

b.Percentage of Presence Employee:

Present days = 
VAR Presentdays = CALCULATE(COUNT('Finaldata'[Value]), 'Finaldata'[Value] = "p")
RETURN 
Presentdays + [WFH]

13.Percentage of Sick Leave Calculation:

a. Create a new column to identify sick leave and half sick leave.

SL count = SWITCH(TRUE(),
'Finaldata'[Value]="SL", 1,
'Finaldata'[Value]="HSL", 0.5, 0)

b. Calculate the % of Sick Leave.

SL % = DIVIDE([SL], [Total Working Days], 0)

14.Percentage of Work from home Calculation:

a. Create a new column to identify WFH and half WFH.

WFH count = SWITCH(TRUE(),
'Finaldata'[Value]="WFH", 1,
'Finaldata'[Value]="HWFH", 0.5, 0)

b. Calculate the percentage of WFH.

WFH % = DIVIDE([WFH], [Total Working Days], 0)

Project link:![Screenshot 2024-03-03 222217](https://github.com/Visha239/Employee-Presence-and-Work-Patterns-Analysis-for-HR/assets/93894680/2f43a620-9578-465c-9651-82ae234b5d20)


