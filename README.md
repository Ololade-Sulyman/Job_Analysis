# Job_Analysis

## Project Overview

This data analysis aims to provide insights into  data job market, focusing on data analysts roles. The project was created out of a desire to navigate and understand the job market more effectively, it delves into top paying and in-demand skills to help and find optimal job opportunities for data analysts.


### The Questions

1.	What are the skills most in demand for the top 3most popular data roles?
2.	How are in-demand skills trending for data Analysts
3.	How well do jobs and skill pay for Data Analysts?
4.	What are the optimal skills for Data Analysts to learn (High demand AND High paying)

### Data Source

The The primary dataset used for this project is from Hugging face website, https://huggingface.co/datasets/lukebarousse/data_jobs

### Tools Used
To deep dive into the data analyst job market, I harnessed the power of several key tools:
- Python: The backbone of my analysis, allowing me to analyze the data and find critical insights, I also used the following python libraries:
  - Pandas Library: This was used to analyze the data
  - Matplotlib Library: For visualization
  - Seaborn Library: For more advanced Visuals
- Jupyter Notebooks: To run and executing my python scripts, including my notes 

### Data preparation and cleanup
This section outlines the steps taken to prepare the data for analysis, ensuring accurancy and usability

#### Import and Clean up data
Importing necessary libraries and loading the dataset, followed by data cleaning tasks.
#### Filter for UK jobs
Apply filter to the dataset, narrowing down to roles based in the United Kingdom

df_UK = df[df['job_country'] == 'United Kingdom']

### The Analysis

Each Jupyter notebook for the project aimed at investigating specific aspects of the data job market. Here is how I approched each questio;

### 1. What are the most demanded skill for the top 3 most popular data roles

To find the most demanded skill for the top 3 most popular data roles. I filtered out those position by which ones popular and got the top 5 skills for these top 3 roles. This query highlights the most popular jobs titles and their top skills.

View my notebook with detailed steps here;[Skills_Demand.ipynb](Skill_Demand.ipynb)

Visualize Data

~~~python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    #df_plot.plot(kind='barh',x='job_skills', y='skill_percent', ax=ax[i], title=job_title)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='Oranges_d')
    ax[i].set_title(job_title)
plt.show()
~~~

### Results

<img width="488" alt="Skills_Demand" src="https://github.com/user-attachments/assets/8464ee4f-5910-4c7e-9cd3-2a960d505d77" />

### Insights;

- Python is the most requested skill for Data Scientist (69%) and Data Engineer (55%), which make it a versatile skill
- SQL is the most requested skill for Data Engineer, appearing in 60% of job postings
- Data Analysts are expected to be proficient SQL and Excel, and analysis tools, Power bI.

### 2.How ara in-sdemand skills trending for Data Analysts
To find skills are trending in 2023 for Data Analysts, I filtered data analyst positions and grouped the skills by job postings. The top 5 skills of data analysis by month, showing how popular skills were througout 2023.

View my notebook with detailed steps hrer; [Skills_Trend.ipynb](Skills_Trend.ipynb)

### Visualize Data
~~~python
from matplotlib.ticker import PercentFormatter
df_plot = df_DA_UK_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))
   
plt.show()
~~~

### Results

<img width="518" alt="Skills_Trend" src="https://github.com/user-attachments/assets/8a9e2bcb-d0b2-4b7d-98bf-b2d6ba399fd6" />


    
    
