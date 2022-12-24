# Cluster Analysis



 I used a dataset developed by IBM data scientists which was used to look at factors related to employee job satisfaction and attrition. The original dataset is accessible through Kaggle. 

 Background: Your business question is: “How can our 
  company effectively target strategies to improve employee satisfaction to specific groups of 
 employees based on their characteristics and performance?”

The first step to creating those strategies is to segment the company’s 1,470 employees into clusters based on key characteristics and performance indicators. 

 Variables: The variables you will use for this analysis are:
 Age: Age of employee in years
 MonthlyIncome: How much the employee earns per month
 PercentSalaryHike: The percentage increase in salary over two years
 YearsAtCompany: The total number of years the employee has been with the company


 # Part one: Segment customers using the four variables Age, MonthlyIncome, PercentSalaryHike, YearAtCompany.

install.packages("tidyverse")
install.packages("cluster")
install.packages("fpc")
install.packages("factoextra")
install.packages("janitor")

library(tidyverse)
library(cluster)
library(fpc)
library("factoextra")
library("janitor")

#create data frame
jobdf <- read.csv("Employees.csv")
View(jobdf)
set.seed(42)


What is the best way to segment these subscribers by key characteristics Age, MonthlyIncome, YearsAtCompany, PercentSalaryHike?




Name new data frame without non-continuous data points (variables of interest)
quantdf <- jobdf[c(1,16,20,25)]
View(quant

normalize each variable
quantdfn <- scale(quantdf)
View(quantdfn)

set number of seed in order to replicate the analysis
set.seed(42)

create a function to calculate total within-cluster sum of squared deviations
to use in elbow plot
wss <- function(k){kmeans(quantdfn, k, nstart=10)} $tot.withinss

range of k values for elbow plot
k_values <- 1:10


run the function to create the range of values for the elbow plot
wss_values <- map_dbl(k_values, wss)

create a new data frame containing both k_values and wss_values
elbowdf <- data.frame(k_values, wss_values)

graph the elbow plot
ggplot(elbowdf, mapping = aes(x = k_values, y = wss_values)) +
  #lines and points
  geom_line() + geom_point()

run k-means clustering with 4 clusters (k=4) and 1000 random restarts
k4 <- kmeans(quantdfn, 4, nstart =1000)

display structure of the k-means clustering object
str(k4)

display info on k means clustering
k4


display cluster statistics
cluster.stats(dist(quantdfn, method = "euclidean"), k4$cluster)
focus on , average.distance for within, and
longer distances are better for  between cluster distance of ave.between.matrix
(smaller number is tigher grouping)


combining each observation's cluster assignment with unscaled data frame
quantdfk4 <- cbind(quantdf, clusterID=k4$cluster)
View(quantdfk4)


write data frame to CSV file to analyze excel
write.csv(quantdfk4, "magazine_kmeans_4clusters.csv")

calculate variable averages for all non-normalized observations
summarize_all(quantdfk4, mean)

calculate variable averages for each cluster
quantdfk4 %>%
  group_by(clusterID) %>%
  summarize_all(mean)
  
# Part 2

avg_salary <- mean(quantdfk4$MonthlyIncome)
# Results
Cluster1+ Investor, larger investments, oldest.
Cluster2 = Financial conservatives, more income. Youngest.
Cluster3 Less resources readers, less invested. Second oldest.
Cluster4 Up and comers but a lot invested just like others that are older. Second youngest.

This is helpful to be able to understand your subscribers and can add insight into
 where to market your advertising targeting different demographics.
