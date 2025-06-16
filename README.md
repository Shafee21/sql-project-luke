# Introduction

This dataset provided in Luke Barousse's SQL for Data Analytics course contains data on a collection of hiring posts for data analytic roles including job title, location, salary and skills. The goal in this guided project is to analyse the dataset to answer question like what are the top paying skills? I chose this project to help develop my SQL knowledge in a practical environment.

#background
The dataset and Luke Barousse's [SQL Course](https://lukebarousse.com/sql). 

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

'''sql
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
'''
