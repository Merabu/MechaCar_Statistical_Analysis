# MechaCar_Statistical_Analysis

## Part1. Linear Regression to Predict MPG

### Import dplyr library
library()
library(dplyr)

### Read in csv file
MechaCar <- read.csv(file='MechaCar_mpg.csv', check.names=F, stringsAsFactors = F)

### Perform linear regression
lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD,data=MechaCar)




![Perform linear regression](https://user-images.githubusercontent.com/115379848/232673142-8d7e5a1e-96d6-4041-872d-b6dd1acc2cde.png)


### Determine the p-value and the r-squared value for the linear regression model
summary(lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD,data=MechaCar))

![Determine the p-value and the r-squared value for the linear regression model](https://user-images.githubusercontent.com/115379848/232673137-fc7e45b6-af5f-4344-893a-505aaf842db6.png)



#### Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?

The vichicle length and vehicle ground cleaance provide non random amount of variance to the model.



#### Is the slope of the linear model considered to be zero? Why or why not?

The p.value for te model is 0.05% therefore the slope of the linear model is not zero because P-value is smaller than our significance level.




#### Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?

Our model will prodict MPG correlation to other factor 70% of the time.



## Part 2: Create Visualizations for the Trip Analysis


## Summary Statistics on Suspension Coils,lot_summary 

### Read in csv file

SuspCoil <- read.csv(file="Suspension_Coil.csv", check.names=F, stringsAsFactors = F)

### Write an RScript that creates a total_summary dataframe using the summarize() function to get the mean, median, variance, and standard deviation

#of the suspension coil’s PSI column
total_summary <- SuspCoil %>% summarize(Mean=mean(PSI),Median=median(PSI), Variance=var(PSI), SD=sd(PSI), .groups = 'keep')




<img width="343" alt="Total_summary" src="https://user-images.githubusercontent.com/115379848/232675306-ef839424-8f59-4e5e-b65c-6060157cbcc7.png">




### Write an RScript that creates a lot_summary dataframe using the group_by() and the summarize() functions to group each manufacturing lot by the mean, median, variance, and standard deviation

<img width="242" alt="lot_summary" src="https://user-images.githubusercontent.com/115379848/232675291-c20c84ae-d01a-4a95-9224-675cb87851a7.png">






## Part 3: T-Tests on Suspension Coils

## T-Tests on Suspension Coils

### of the suspension coil’s PSI column.
lot_summary <- SuspCoil %>% group_by(Manufacturing_Lot) %>% summarize(Mean=mean(PSI),Median=median(PSI), Variance=var(PSI), SD=sd(PSI), .groups = 'keep')

### T Test all lots
t.test(SuspCoil$PSI, mu=1500)

![T Test all lots](https://user-images.githubusercontent.com/115379848/232677376-9a1239ea-f4a9-4938-a4ef-3caccfa299b9.png)






### T Test for lot 1
t.test(subset(SuspCoil, Manufacturing_Lot=="Lot1")$PSI, mu=1500) 





![T Test for lot 1](https://user-images.githubusercontent.com/115379848/232677383-d2967c38-683c-4a87-91cf-52a6496616ee.png)






### T Test for lot 2
t.test(subset(SuspCoil, Manufacturing_Lot=="Lot2")$PSI, mu=1500)






![#T Test for lot 2](https://user-images.githubusercontent.com/115379848/232677411-4c844838-bb75-4cb7-a111-b2571805c57a.png)







### T test for lot 3
t.test(subset(SuspCoil, Manufacturing_Lot=="Lot3")$PSI, mu=1500)


![T Test for lot 3](https://user-images.githubusercontent.com/115379848/232677422-331f3bda-3ccc-40db-9633-c9cbdd4e1e29.png)


Lot 1 has variance of 0.98 and Lot 2 has 7.47 and are within the 100 PSI variance requirement;
However, it is Lot 3 that is showing alot bigger variance in performance and consistency, with a variance of 170.29. It is Lot 3 that is disproportionately causing the variance at the full lot level.

## Part 4: Design a Study Comparing the MechaCar to the Competition

## Study Design: MechaCar vs Competition



### What metric or metrics are you going to test?


PG (Gasoline Efficiency): Independent Variable
Safety Feature Rating: Independent Variable
Engine (Electric, Hybrid, Gasoline / Conventional): Independent Variable
Resale Value: Independent Variable
Average Annual Cost of ownership (Maintenance): Independent Variable
Current Price (Selling): Dependent Variable
Drive Package : Independent Variable

### What is the null hypothesis or alternative hypothesis?


null hypothesis : According to the genre, Mechacar is correctly priced 




### What statistical test would you use to test the hypothesis? And why?





### What data is needed to run the statistical test?





