# Introduction

This dataset provided in Luke Barousse's SQL for Data Analytics course contains data on a collection of hiring posts for data analytic roles including job title, location, salary and skills. The goal in this guided project is to analyse the dataset to answer question like what are the top paying skills? I chose this project to help develop my SQL knowledge in a practical environment whilst also gaining an introduction to git and github

# background
The dataset and Luke Barousse's [SQL Course](https://lukebarousse.com/sql) covering jobs posted over 2023. 

# To be exact the questions I wanted to answer through SQL queries were:  
1. What are the top-paying data analyst jobs?  
2. What skills are required for these top-paying jobs?  
3. What skills are most in demand for data analysts?  
4. Which skills are associated with higher salaries?  
5. What are the most optimal skills to learn?

## 🛠 Tools I Used
For my deep dive into the data analyst job market, I harnessed the power of several key tools:

- **SQL**: The software of my analysis, allowing me to query the database to achieve critical insights.
- **PostgreSQL**: This was the database management system that Luke Barousse chose to use which was perfect for handling the job posting data.
- **Visual Studio Code**: The projects chosen database management and executing SQL queries.
- **Git & GitHub**: Essential for sharing my SQL scripts and analysis, ensuring I could show others what I have been trying to develop in my free time and essentially share to LinkedIn

# The Analysis

### 1. Top Paying Data Analyst Jobs

Data analyst positions by average yearly salary and location, focusing on remote jobs. This query highlights the high paying opportunities in the field.

```sql
select  job_id,
    job_title,
    job_location,
    job_schedule_type,
    salary_year_avg,
    job_posted_date,
    name as company_name  
from job_postings_fact

left join company_dim as company 
  on job_postings_fact.company_id = company.company_id

where 
   job_title_short = 'Data Analyst'
   and job_location = 'Anywhere'
   and salary_year_avg is not null

order by 
   salary_year_avg desc

limit 10;
```
![image](https://github.com/user-attachments/assets/5e53b33d-18b7-49ca-b2f0-4d101ec591fc)
This query outputs the top 10 jobs by salary with the highest salary at $650000 - the data analyst role posted by Mantys 

In 2023, the top data analyst jobs showcase impressive earning potential, with salaries ranging from \$184,000 to \$650,000 annually. These high-paying roles are offered by well-known companies such as SmartAsset, Meta, and AT\&T, indicating strong demand for data analysts across various industries. The job titles also reflect significant diversity, spanning from entry-level Data Analyst positions to senior roles like Director of Analytics, highlighting the wide array of career paths and specializations available within the field of data analytics.

### 2. skills required for top paying Data Analyst jobs
This SQL query identifies the top 10 highest-paying data analyst jobs and shows the skills linked to each one by joining the job and skill tables. Every job already has related skills stored in a separate table, and the query brings them together to display job titles, companies, salaries, and their required skills.

![image](https://github.com/user-attachments/assets/c662440c-e3e5-4809-a650-689aed4fd3b0)

 By counting how often each skill appears in the results, **SQL** is the most in-demand (8 times), followed by **Python** (7 times), and **Tableau** (6 times). Other important skills like **R**, **Snowflake**, **Pandas**, and **Excel** also show up, helping us understand which skills are most valued in these high-paying roles.

### 3. Skills that are most in demand
This query shows which skills are asked for the most in job ads, helping people know what to focus on learning.

![image](https://github.com/user-attachments/assets/9cf07a53-0f2d-4942-8070-27fbcdfde207)

