# Pewlett Hackard Succession Planning Analysis

This week we helped Pewlett Hackard organize and analyez their employee database so they could understand how many PH employees were nearing retirement and what positions they would be leaving behind.  This is important for PH to know since they plan to build a mentorship program where their recently retired staff would mentor the generation behind them as they take on the positions of those retiring.  

For this challenge, we put together 4 tables for PH to use in their succession planning.  The first two, retirement_titles and unique titles produced a clean list of unique job titles that will soon be open by PH's retiring staff (those born between 1952 and 1955).  The third is a total count of each of those positions.  And the fourth is a list of PH employees born in 1965 who PH has deemed eligible to be mentored by those in the unique_titles list.  


## Results 
When condusting these quereies, there were a few major conditions that we neeed to keep in mind to ensure that we collected the correct information.  They are as follows:  

1. When creating the retirement_titles table, we were querying infromation from the employees table and the titles table- two tables that held information about all of PH's employees, not just the ones ready to retire.  Thus, we needed to make sure that we added a **WHERE** statment to pull only employees with birth dates within the years 1952 and 1955.  

insert image 

2. Once we created the retirement_titles table with employees born in the years 1952 and 1955 only, we realized that list also included employees who were no longer at the company.  To comabt this, we created another query to filter the retirement_titles table by the employee's "to date" with another **WHERE** function.  This returned only the employees who were still at the company, ready to retire.  

insert image

3. In the same query as above, we also used the **DISTINCT ON** function (highlighted in the image above) within our **SELECT** statement to only pull the first occurence/the most recent occurance of each employee number which eliminated the duplicate records.  

In the image below, you can see that the retirement_titles table includes employees multiple times, making the list longer and the unique_titles table does not.  

insert image

insert image

4. From these queries we were able to utilize the **COUNT** funtion within our **SELECT** statement to get a clean, total count of how many uniqe titles are ready for retirement. 

insert image

insert image

5. Finally, the mentroship_eligibility query required us to inner join three tables, employees, titles, and department_employees to get a list of the employees eligible to participate in the mentorship program.  For this, we had to keep all of the points above in mid as well.  
   a. We needed to used the **DISTINCT ON** funtion to ensure we only returned the first occurence of each employee id.
   b. Filtered with the **WHERE** statement on the to-date column to collect only employees still with the company.
   c. Then filtered again with *another* **WHERE** statement to collect employees born in the year 1965 only.  

## Summary 

After running this analysis we learned how many of PH's employees are getting ready for retirement and how many we have ready to take thier place.  with this information we can answer two of PH's burning questions: 

##### Hot Questions:
**1. How many roles will need to be filled as the "silver tsunami" begins to make an impact?**
According to the retiring_titles table, it looks as though PH is going to have about 72,458 employees retire in the next few years.  To offset this impact, PH will need to both move up current or bring on new ~50,000-70,000 employees in the next few years.    

**2. Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?**
As ~72,000 employees get closer to retirement, they are also toeing the line of becoming mentors for those to who are eager to take their place.  As per the mentorship eligibility table, there are 1,550 current employees eligible to be mentored by those retiring.  Therefore, if PH wants ever remaining employee born in 1965 to receive a mentor, they **will** have enough mentors.  

to take the analysis one step further, I reccomend that PH starts to prioritize who of the eligible gets mentored by who.  I believe that there are two ways PH can go about this:

1. The first way is to look at who is ready to move into leadership based on seniority of title.  The query pictured below will help PH see all their mentorship eligible employees with 'Senior' titles ordered by their tenure in the company.  

insert picture 

2.  The other way that PH could organize thier program is with the querey pictured below that returns a list of all the eligible employees by title and from_date.  

insert image
