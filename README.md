# HR Data Analytics Project

## Overview
This project utilizes four essential data analysis tools: **Power BI, Tableau Desktop, SQL, and Excel** to analyze HR data from a medical components manufacturing company. The primary objective is to develop key performance indicators (KPIs) and visualizations that help the HR department monitor workforce trends and employee attrition.

## Dataset
- **Data Source**: Open-source HR Data 2022
- **Industry**: Medical Components Manufacturing

## Problem Statement
The HR department needs a structured approach to monitor employee data and analyze critical HR metrics. The project addresses this need by developing KPIs and data visualizations to improve workforce planning and employee retention strategies.

## Key Performance Indicators (KPIs) & Insights
The following KPIs and analyses were developed to enhance HR decision-making:

- **Employee Count**: Total number of employees for workforce assessment.
- **Attrition Count & Rate**: Measures employee turnover and compares it to industry benchmarks.
- **Active Employees**: Differentiates between active and inactive employees to assess workforce capacity.
- **Average Age**: Helps in succession planning and talent retention.
- **Attrition by Gender**: Identifies gender-based disparities in employee attrition.
- **Department-wise Attrition**: Highlights departments with high turnover rates.
- **Employees by Age Group**: Analyzes workforce age distribution for demographic insights.
- **Job Satisfaction Ratings**: Measures employee engagement and satisfaction.
- **Education Field-wise Attrition**: Determines if certain educational backgrounds are linked to higher attrition.
- **Attrition Rate by Gender & Age Group**: Provides insights into retention challenges across different age groups.

## Project Workflow
### 1. Power BI
- Created a dynamic and interactive dashboard.
- Focused on data integration and visually appealing reports.

### 2. Tableau
- Developed custom charts and interactive dashboards.
- Created advanced calculations for trend analysis.

### 3. SQL
- Extracted key HR metrics using SQL queries.
- Validated Power BI and Tableau reports with SQL-based checks.

### 4. Excel
- Built an interactive dashboard with pivot tables and charts.

## SQL Queries Used
### Database Setup
```sql
CREATE TABLE hrdata (
    emp_no INT PRIMARY KEY,
    gender VARCHAR(50) NOT NULL,
    marital_status VARCHAR(50),
    age_band VARCHAR(50),
    age INT,
    department VARCHAR(50),
    education VARCHAR(50),
    education_field VARCHAR(50),
    job_role VARCHAR(50),
    business_travel VARCHAR(50),
    employee_count INT,
    attrition VARCHAR(50),
    attrition_label VARCHAR(50),
    job_satisfaction INT,
    active_employee INT
);
```

### Import Data
```sql
COPY hrdata FROM 'C:\Users\YourPath\Projects\Complete_Project\SQL' DELIMITER ',' CSV HEADER;
```

### Key Queries
#### Employee Count
```sql
SELECT SUM(employee_count) AS Employee_Count FROM hrdata;
```

#### Attrition Count
```sql
SELECT COUNT(attrition) FROM hrdata WHERE attrition = 'Yes';
```

#### Attrition Rate
```sql
SELECT ROUND(((SELECT COUNT(attrition) FROM hrdata WHERE attrition='Yes') / SUM(employee_count)) * 100, 2) FROM hrdata;
```

#### Attrition by Gender
```sql
SELECT gender, COUNT(attrition) AS attrition_count FROM hrdata WHERE attrition='Yes' GROUP BY gender ORDER BY COUNT(attrition) DESC;
```

#### Department-wise Attrition
```sql
SELECT department, COUNT(attrition), ROUND((COUNT(attrition) * 100.0 / (SELECT COUNT(attrition) FROM hrdata WHERE attrition = 'Yes')), 2) AS pct FROM hrdata WHERE attrition='Yes' GROUP BY department ORDER BY COUNT(attrition) DESC;
```

#### Attrition Rate by Gender & Age Group
```sql
SELECT age_band, gender, COUNT(attrition) AS attrition, ROUND((COUNT(attrition) * 100.0 / (SELECT COUNT(attrition) FROM hrdata WHERE attrition = 'Yes')), 2) AS pct FROM hrdata WHERE attrition = 'Yes' GROUP BY age_band, gender ORDER BY age_band, gender DESC;
```

## Conclusion
This project demonstrates how HR analytics can provide actionable insights to improve workforce planning and employee retention. By leveraging **Power BI, Tableau, SQL, and Excel**, this analysis enhances HR decision-making through data-driven insights and visually appealing dashboards.

## Repository Structure
```
📂 HR-Data-Analytics
│── 📁 PowerBI_Dashboard
│── 📁 Tableau_Dashboard
│── 📁 SQL_Scripts
│── 📁 Excel_Dashboard
│── 📁 HR_Data csv
│── 📜 README.md
```

## License
This project is open-source and available for educational and non-commercial purposes.
