# Job_Analysis

## Table of Contents
- [Project Overview](#project-overview)
- [The Questions](#the-questions)
- [Data Source](#data-source)
- [Tools Used](#tools-used)
- [The Analysis](#the-analysis)
- [What I learned](#what-i-learned)
- [Insights](#insights)
- [ Challenges](#challenges)
- [Conclusion](#conclusion)
- [Reference](#reference)

## Project Overview

This data analysis aims to provide insights into  data job market, focusing on data analysts roles. The project was created out of a desire to navigate and understand the job market more effectively, it delves into top paying and in-demand skills to help and find optimal job opportunities for data analysts.


### The Questions

1.	What are the skills most in demand for the top 3most popular data roles?
2.	How are in-demand skills trending for data Analysts
3.	Highest paid and most demanded skills for Data Analysts?
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

#### Data preparation and cleanup
This section outlines the steps taken to prepare the data for analysis, ensuring accurancy and usability

#### Import and Clean up data
Importing necessary libraries and loading the dataset, followed by data cleaning tasks.
#### Filter for UK jobs
Apply filter to the dataset, narrowing down to roles based in the United Kingdom

df_UK = df[df['job_country'] == 'United Kingdom']

### The Analysis

Each Jupyter notebook for the project aimed at investigating specific aspects of the data job market. Here is how I approched each questio;

#### 1. What are the most demanded skill for the top 3 most popular data roles

To find the most demanded skill for the top 3 most popular data roles. I filtered out those position by which ones popular and got the top 5 skills for these top 3 roles. This query highlights the most popular jobs titles and their top skills.

View my notebook with detailed steps here:  [Skills_Demand.ipynb](Skill_Demand.ipynb)

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

#### Results

<img width="488" alt="Skills_Demand" src="https://github.com/user-attachments/assets/8464ee4f-5910-4c7e-9cd3-2a960d505d77" />

#### Insights;

- Python is the most requested skill for Data Scientist (69%) and Data Engineer (55%), which make it a versatile skill
- SQL is the most requested skill for Data Engineer, appearing in 60% of job postings
- Data Analysts are expected to be proficient SQL and Excel, and analysis tools, Power bI.

#### 2.How ara in-sdemand skills trending for Data Analysts
To find skills are trending in 2023 for Data Analysts, I filtered data analyst positions and grouped the skills by job postings. The top 5 skills of data analysis by month, showing how popular skills were througout 2023.

View my notebook with detailed steps hrer:  [Skills_Trend.ipynb](Skills_Trend.ipynb)

#### Visualize Data
~~~python
from matplotlib.ticker import PercentFormatter
df_plot = df_DA_UK_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))
   
plt.show()
~~~

#### Results

<img width="518" alt="Skills_Trend" src="https://github.com/user-attachments/assets/8a9e2bcb-d0b2-4b7d-98bf-b2d6ba399fd6" />


#### Insights:

- Excel experienced a significant increase in demand starting around July, surpassing SQL
- SQL remain the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand
- Python and power bi show relatively stable demand throughout the year with some fluctuations but remains essential skills for data analysts. Tableau, less demanded compared to the others


#### 3. Highest paid and demanded skills for Data Analysts.

Identify the highest paying roles and skills, I filtered for jobs in United Kingdom, looked at their median salary and most demanded skills.   

View my notebook with detailed steps here:  [Salary_Analysis.ipynb](Salary_Analysis.ipynb)

#### Visualize Data

~~~python
fig, ax = plt.subplots(2, 1)
sns.barplot(data = df_DA_top_pay, x='median', y=df_DA_top_pay.index, ax=ax[0], hue='median', palette='Oranges_d')
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, ax=ax[1], hue='median', palette='Oranges')
plt.show()
~~~

#### Results

<img width="484" alt="Salary Analysis" src="https://github.com/user-attachments/assets/caf13eba-f6b9-4ba5-8ee5-2cfda919a05d" />


#### Insights:
- The top graph shows specializes technical skills like pandas, tensorflow and c++ are associated with higher salaries, some reaching up to £175k, suggesting that advanced technical proficiency can increase earning potential.
- The bottom graph highlights that the skills like tableau, sql and looker are the most in-demand, even though they may not offer the highest salaries. This demonstrates the importance of these core skills for employability in data analysis roles.
- There is a clear distinction between the skills that are highest paid and those that are most in-demand. Data analysts aiming to maximize their career potential should consider developing a specialized skills and widely demanded foundational skills.


#### 4.What are the most optimal skills for Data Analysts to learn

Grouped skills types in UK, to determine the median salary and likelihood of being in postings,
Visualize median salary vs percent skills demand.
(Optional) Determine if certain technologies are more prevalent

View my notebook with detailed steps here:  [Optimal_Skills.ipynb](Optimal_Skills.ipynb)

#### Visualize Data

~~~python
from adjustText import adjust_text
sns.scatterplot(data=df_plot, 
    x='skill_percent', 
    y='median_salary', 
    hue='technology'
)
ax.xaxis.set_major_formatter(PercentFormatter(decimals=0))
plt.show()
~~~

#### Results

<img width="548" alt="Optimal_Skills" src="https://github.com/user-attachments/assets/135d6ebf-4ca7-492b-851c-2773cf026d80" />


#### Insights:
- The scatter plot shows that most of the programming skills (colored blue) tend to clutter at high salary levels compared to other categories, indicating that programming expertise might offer greater salary benefits within the data analytics field.
- Analyst tools (colored orange), including Tableau and Power BI are prevalent in job postings and offer competitive salaries, showing that visualization and data analysis software are crucial for current data roles. This category not only has good salaries but is also versatile across different types of data tasks.
- The database skills (colored purple), sql Server, associated with some of the highest salaries among data analyst tools. This indicates a significant demand and valuation for data management and manipulation expertise in the industry.

### What I learned

During this project, I improved my technical Python skills, particularly in data manipulation and visualization, and broadened my knowledge of the data analyst job market. Here are some particular things I discovered. 
- #### Advanced Python usage:
I was able to complete complex data analysis tasks more quickly by using libraries like Seaborn and Matplotlib for data visualization, and pandas for data manipulation.
- #### Importance of Data Cleaning:
I discovered that in order to ensure the accuracy of the insights obtained from the data, extensive data preparation and cleaning are essential before any analysis can be carried out.
- #### Strategic Skill Analysis:
The project stressed how crucial it is to match one's abilities with the demands of the market. In the tech sector, more strategic career planning is made possible by an understanding of the relationship between skills demand, salary, and job availability.

### Insights
Several broad insights into the analyst job market were offered by this project: 
- Salary Correlation and Skill Demand: There is a direct relationship between the salaries that certain skills are valued for and the demand for those skills. Higher salaries are frequently associated with advanced and specialized skills like Python and SQL.
- Market Trends: The demand for certain skills is fluctuating, which emphasizes how dynamic the data job market is. In order to advance in your data analytics career, you must stay abreast of these trends. 
- Economic Value of Skills: Data analysts can prioritize learning to optimize their financial returns by knowing which skills are both in-demand and highly compensated.

### Challenges

Despite some difficulties, this project offered worthwhile educational opportunities: 

- Data inconsistencies: To maintain the integrity of the analysis, handling missing or inconsistent data calls for careful thought and meticulous methods. 
- Complex Data Visualization: It was difficult to create an engaging visual representation of a complex dataset that effectively communicated insights.
Maintaining equilibrium in order to guarantee thorough coverage without becoming bogged down in specifics, it was necessary to constantly balance how deeply to delve into each analysis while keeping a broad overview. 

### Conclusion
The critical skills and trends that shape this changing field have been highlighted in this highly informative investigation of the data analyst job market. The knowledge I gained broadens my perspective and offers practical advice to anyone hoping to progress in the data analytics field. To stay ahead in data analytics, continuous analysis will be necessary as the market changes. This project emphasizes the value of ongoing learning and adaptation in the data field and provides a solid basis for further research. 

### Reference

Luke Barousse
- Python for Data Analytics



