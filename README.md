# Cluster Analysis (K-means, hierarchical)


 I used a dataset developed by IBM data scientists which was used to look at factors related to employee job satisfaction and attrition. The original dataset is accessible through Kaggle. I conducted a cluster analysis (K-means & hierarchical) in order to answer the business question,  “How can our 
 company effectively target strategies to improve employee satisfaction to specific groups of 
 employees based on their characteristics and performance?”
 


My first step to creating those strategies is to segment the company’s 1,470 employees into clusters based on key characteristics and performance indicators such as:

 Variables: The variables I used for this analysis are:
 
 -Age: Age of employee in years
 
 -MonthlyIncome: How much the employee earns per month
 
 -PercentSalaryHike: The percentage increase in salary over two years
 
 -YearsAtCompany: The total number of years the employee has been with the company
 
Part 1 consisted of conducting a k-means cluster analysis using the four variables above.
 -This analysis enabled us to ascertain demographic information about each cluster as well as sizes.
 
 -Cluster 1 = 247 has the second highest income, the oldest age, average salary hike, and the least years at the company.
 
 -Cluster 2 = 717 has the lowest income, and 3rd oldest with the lowest percent salary hike.
 
 -Cluster 3 = 135 has the highest income, longest years at the company, and average salary hike.
 
 -Cluster 4 = 371 has the second lowest income, and youngest age, the highest salary hike, and the least years at the company.

Part 2 consisted of conducting a hierarchical cluster analysis uising previous continous variables.

 This helped us to get the avergaes for the variables in the clusters.
 
 - Age = 37 years
 - MonthlyIncome = $6503
 - PercentSalaryHike = 15.2%
 - Years at company = 7 Years
 
# Conclusion:
Cluster 2 is the biggest cluster at 717 which accounts for almost half of all the employees (49%). Cluster 3 is the smallest cluster at 135 which accounts for less than 10% (9.2%) of employees but they have the highest income and longest years at the company.

This data can be used to target strategies that improve employee satisfaction by understanding that employees in Cluster 2 account for just under half of all employees. Cluster 3 which only represents 9.2% of all employees.  This can help to aid strategies that focus on improving employee satisfaction because it offers insight into which groups are more imporant to focus on.




