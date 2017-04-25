
# Executive Summary


This report is a part-2 to the original report on the observational study of Abalones. The part-1 report attempted to analyze and investigate data from the unsuccessful study of Abalones. We had learned from the part-1 report that physical measurement alone would not be able to accurately able to determine the age of abalones. However, with the introduction of additional tools such as the Analysis of Variance, Regression analysis, and ROC, we are able to categorize the abalones population into classes of adults and infants. 
We picked up the data analysis from where we left before and attempted to run different analysis to determine the economic viability of harvesting Abalones based on their age classes. We started with a Chi-Square function, and computed quantiles form the function to compute the p-value. We then ran an analysis of variance on SHUCK using the CLASS and SEX as dependent variables. This analysis led us to be confident on our hypothesis that male and female abalones can be combined into a single category and be labeled as adults. We immediately threw the data point in scatter plot and eventually, log-transformed the data sets, performed regression analysis to better understand the data, and determine the coefficient estimates. The next step was to perform an analysis of the residuals and plot in various data visualization formats to evaluate the regression analysis. 
The final steps involved evaluating the cut-off points and trade-offs. We started with peak difference and volume value. Eventually, we tested various cut-off points and evaluated trade-offs. Ultimately, we are able to conclude that we can effectively estimate the harvest volume and age of Abalones. Attached report along with the conclusion section will elaborate on the analysis and recommended strategy moving forward.

Data Preparation:
A random sample of 500 data sets was taken to perform the study. R was used to sample 500 data from the set of abalone data sets. Here’s the result of the sample:

![image](https://cloud.githubusercontent.com/assets/26909910/25392714/65b7c914-29a7-11e7-8526-7ca14f9ef043.png)
                  **Figure 1**

An exploratory study such as this one requires a good understanding of the randomly sampled data from the observational study. Therefore, upon taking the sample, it is useful to summarize the data sets by using the summary (mydata) code in R. A clean “30,000 feet” information about the data set can be derived from the summary exercise. The exercise also provides a good understanding of the nature and basic facts of the data we are dealing with.

![image](https://cloud.githubusercontent.com/assets/26909910/25392912/028e8c14-29a8-11e7-85c2-a8e59fb85220.png)
                  **Figure 2**

