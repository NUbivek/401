
# Executive Summary


This report is a part-2 to the original report on the observational study of Abalones. The part-1 report attempted to analyze and investigate data from the unsuccessful study of Abalones. We had learned from the part-1 report that physical measurement alone would not be able to accurately able to determine the age of abalones. However, with the introduction of additional tools such as the Analysis of Variance, Regression analysis, and ROC, we are able to categorize the abalones population into classes of adults and infants. 
We picked up the data analysis from where we left before and attempted to run different analysis to determine the economic viability of harvesting Abalones based on their age classes. We started with a Chi-Square function, and computed quantiles form the function to compute the p-value. We then ran an analysis of variance on SHUCK using the CLASS and SEX as dependent variables. This analysis led us to be confident on our hypothesis that male and female abalones can be combined into a single category and be labeled as adults. We immediately threw the data point in scatter plot and eventually, log-transformed the data sets, performed regression analysis to better understand the data, and determine the coefficient estimates. The next step was to perform an analysis of the residuals and plot in various data visualization formats to evaluate the regression analysis. 
The final steps involved evaluating the cut-off points and trade-offs. We started with peak difference and volume value. Eventually, we tested various cut-off points and evaluated trade-offs. Ultimately, we are able to conclude that we can effectively estimate the harvest volume and age of Abalones. Attached report along with the conclusion section will elaborate on the analysis and recommended strategy moving forward.

Data Preparation:
A random sample of 500 data sets was taken to perform the study. R was used to sample 500 data from the set of abalone data sets. Here’s the result of the sample:


**Figure 1**  ![image](https://cloud.githubusercontent.com/assets/26909910/25392714/65b7c914-29a7-11e7-8526-7ca14f9ef043.png)


An exploratory study such as this one requires a good understanding of the randomly sampled data from the observational study. Therefore, upon taking the sample, it is useful to summarize the data sets by using the summary (mydata) code in R. A clean “30,000 feet” information about the data set can be derived from the summary exercise. The exercise also provides a good understanding of the nature and basic facts of the data we are dealing with.


**Figure 2**  ![image](https://cloud.githubusercontent.com/assets/26909910/25392912/028e8c14-29a8-11e7-85c2-a8e59fb85220.png)

**Question 1:**

Write a function in R to calculate the Pearson chi square statistic on 2x2 contingency tables which have the marginal totals. Use this function to test for independence of SHUCK and VOLUME. Show the chi square value and p-value and discuss the results. What conclusion results from rejection of the null hypothesis? What does this indicate about the relationship between SHUCK and VOLUME?
Answer:

Function to calculate the Pearson chi square statistic:

**Figure 3**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393121/a379f578-29a8-11e7-948f-bf5696a1672e.png)

In order to calculate the chi square value to determine the interdependence of SHUCK and VOLUME, I established a 2x2 contingency tables function of x, and used the chi square formula on the function to return the value of Chi Square for SHUCK and VOLUME. The Chi square function I used resulted in a chi square value of 323.2132. Upon identifying the chi square value, I plugged in the identified chi square value to calculate the p-value; the p-value resulted in 2.895373e-72. The Chi-square test would allow us to test how likely it is that SHUCK and VOLUME affiliation are completely independent. It also tells us how likely it is that the distribution of SHUCK and VOLUME in each category is due to chance i.e. if the null hypothesis is correct/incorrect. The chi square value of 323.2132 and p value of 2.895373e-72 indicate that the hypothesis is very unlikely to happen by chance. Hence, we could reject the null hypothesis that SHUCK and VOLUME are independent, and accept the alternative hypothesis that SHUCK and VOLUME are dependent.

**Question 2**

Perform an analysis of variance with aov() on SHUCK using CLASS and SEX as the independent variables. Assume equal variances. Perform two analyses. To what extent do these results suggest male and female abalones can be combined into a single category labeled as “adults”?

Answer:

**Figure 4**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393207/dcf6b46c-29a8-11e7-88b7-617ed33fbb66.png)

Analysis of variance on SHUCK using CLASS and SEX as independent variables allows comparing the differences between CLASS’s and SEX’s means. Two analyses were conducted to gauge the extent to which the two independent variables – SEX and CLASS – could be combined into a single category labeled “adults”. The results were then presented in ANOVA table as shown in Figure 4. The first ANOVA table shows the results of ANOVA analysis performed by adding an interaction term -- CLASS*SEX – to the model. Figure 4 shows the difference between the ANOVA table with and without the interaction term. The significance level, however, stays the same at different ANOVA analyses. The model was further refined using “TukeyHSD ()” function to adjust unequal sample sizes on the “CLASS” and “SEX” variables without the interaction term. Figure 5 shows the results of analysis using the TukeyHSD function without the interaction term.

**Figure 5**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393244/f77aea1a-29a8-11e7-884e-a8923fa1c6b9.png)

**Question 3:**

Use ggplot2 to form a scatterplot of SHUCK versus VOLUME and a scatterplot of their logarithms labeling the variables as L_SHUCK and the latter as L_VOLUME. Use color to differentiate CLASS in the plots. Compare the two scatterplots. Where do the various CLASS levels appear in the plots? What are the implications of the observed patterns regarding harvesting of abalones?  

Answer:

SHUCK and VOLUME variables are plotted in the Figure 6 scatter plot, and their respective logarithmic values are plotted in Figure 7 scatter plot as L_SHUCK and L_VOLUME respectively.

**Figure 6**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393301/2133c714-29a9-11e7-9b4b-ef01ed0d6bae.png)

Above Figure depicts the relationship between SHUCK and VOLUME variables. The variables are further categorized into different CLASS – A1, A2, A3, A4, A5, A6. Each CLASS is color coded, and we can deduce from Figure 6 that class A1 is concentrated mostly in the 0.0-0.025 VOLUME area and 0.0 – 0.3 SHUCK area; whereas, CLASS A2, A3, A4, A5, and A6 tend to spread heavily between 0.01 – 0.075 in VOLUME area. CLASS A2 – A6, however, tend to differ a lot in SHUCK area while belonging to similar VOLUME area. Meaning, a lot of abalones in CLASS A2 – A6 have similar volume but different shuck. CLASS A2, for example, is heavily concentrated in SHUCK area between 0.0 and 0.3; whereas, CLASS A3 and A6 are heavily concentrated in SHUCK area 0.3-0.6. The SHUCK as a function of VOLUME results an increasing variability in SHUCK as the values of VOLUME increases. The transformed, logarithmic, value of the same relationship between SHUCK and VOLUME separated by CLASS is, however, much different from the untransformed values. The transformed plot is much more stable than the untransformed plot. As indicated in Figure 7, the logarithmic values of the VOLUME and SHUCK for abalones in CLASS A1-A6 hold a more stable distribution than the one in Figure 6. This is important because the stabilization of variability in SHUCK as a function of VOLUME helps us discover statistically significant coefficients for each CLASS and facilitates further calculations and analysis.

**Figure 7**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393405/5e44bb36-29a9-11e7-81fa-f9c515df4bad.png)

**Question 4**

Regress L_SHUCK as the dependent variable on L_VOLUME, CLASS and SEX.

Answer:

The log transformed values for regression shown in Figure 8 enhances the stability of the variability of the model and hence, the validity, of the regression analysis. The difference between very small values (as in this analysis) is logarithmically scaled and this helps to notice and understand minute differences in analysis. The other main reason to use log-transformed values for regression is for the purpose of interpretation, using a log-transformed value allows the regression coefficients to vary in a set pattern. 

**Figure 8**!  [image](https://cloud.githubusercontent.com/assets/26909910/25393440/7810feb2-29a9-11e7-9113-a951875987f8.png)

The data in Figure 8 shows the estimated standard deviation, error, and t-value, among others of the different classes including the SEX I and SEX M. SEX in this model is an important predictor of this regression model. Logarithmic transformation has made it evident to see the impact of SEX variable in the overall model. The estimated effect per fold increases logarithmically for us to see the impact of SEX in the model. The coefficients CLASS levels show the differences in the standard error and t-value, among other differences. The CLASS level differences in t-value show the difference in the observed sample statistic of the CLASS levels and hypothesized population statistic of the CLASS levels parameter in the units of standard error. 

**Question 5**

Perform an analysis of the residuals.

Answer:

Upon developing a multiple regression model, the data is produced in a histogram to show the normal distribution of the model. The histogram in Figure 9 shows the regression residuals in a normally distributed pattern. The data is further expressed in a normal QQ plot (Figure 10) that further confirms the normal distribution of the residuals data. The dark black area in the middle of the QQ plot line shows the theoretical quantiles between -1 and 2, and sample quantiles between negative 0.2 and positive 0.2. The model is symmetrical and the distribution is normal.

**Figure 9**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393676/1885fa1e-29aa-11e7-9da8-47b1ae276993.png)

**Figure 10**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393706/2ec030a6-29aa-11e7-902f-ea4259cc18d2.png)

The residuals data is further expressed in box plots separated by CLASS and SEX variables. The notion that the residuals are normally distributed is further confirmed by the distribution of data in the box plot separated by CLASS variables. All six (6) CLASS – A1-A6 – tend to align in the 0.0 residual line with very few outliers in each CLASS. A similar trend is seen in the box plot separated by SEX variable. The box plots are presented in the exhibition below in Figure 11 and Figure 12.  Figure 11 box plot is separated by CLASS and Figure 12 box plot is separated by SEX variables. In order to keep the visual and text flow constant, I have attached the scatter plot showing the residual data in the appendix section. Please refer to the appendix section to view the scatter plot data.

**Figure 11**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393740/4533449a-29aa-11e7-8f36-317a37cf9e0e.png)

**Figure 12**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393766/53699e7e-29aa-11e7-94b3-97eca2ba3fa9.png)

**Question 6:**

There is a tradeoff faced in managing the abalone harvest. The infant population must be protected since that represents future harvests. On the other hand, the harvest should be designed to be efficient with a sufficient yield to justify the effort.

Answer:

**Figure 13**![image](https://cloud.githubusercontent.com/assets/26909910/25393801/69a73430-29aa-11e7-8993-1878f25d1cac.png)

A modified code to show the count of adults is presented in the Appendix section. The first part of the modified code resulted in the output shown in Figure 13. The original code result of infant’s proportion is shown in the appendix section. Please refer to the appendix section for the data on infant’s proportion. A plot showing the adult proportion versus volume is presented below. The calculation also involves the computation of 50% “split” volume value for the adults. A detailed result of the calculation of the plots below in figure 14 shows the adult proportion versus volume whereas the figure 15 shows the infant proportion versus volume.

**Figure 14**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393853/98b41de2-29aa-11e7-8997-d44bb10d9be5.png)

**Figure 15**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393883/adfc7b5e-29aa-11e7-9b66-fc29ba1da796.png)

**Question 7:**

This part will address the determination of a volume.value that corresponds to the observed maximum difference in harvest percentages of adults and infants.

Answer (a):

The plot of difference that shows the adult proportion and infant proportion in one plot is shown below in Figure 16. The two proportions seem to converge as the volume increases -- in their respective high volumes. This signifies the proportion of protected adults and infants is high and equal when the volume of abalones is higher.

**Figure 16**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393919/cd73087c-29aa-11e7-9491-8299062c7eab.png)

Answer (b):

> max(difference)
[1] 0.5664237
> which.max(difference)
[1] 24
> volume.value[24]
[1] 0.02498325

The peak difference for the above analysis is 0.5664237 and lies in the 24th element of volume.value. The volume.value that corresponds to the maximum difference in “harvested” proportions is 0.02498325.

Answer (c): 

With the cut-off point of 0.02498325, which is the volume.value, the harvest proportion for infants and adults would result to zero (0). Other cut-off points discussed below in question 9 will need to be considered. 

**Question 8:**

Construct an ROC curve.

Answer:

**Figure 17**  ![image](https://cloud.githubusercontent.com/assets/26909910/25393992/08093f60-29ab-11e7-98c0-a671694791ac.png)

The ROC curve above shows the true positive rate as a function of a false positive rate, and enables us to examine the trade-off of harvesting versus not harvesting.  As evident in the ROC diagram in Figure 17, lower volume threshold has lower trade-off. For example, if we lower the volume threshold of our model cut-off of zero infants, we start to harvest adults first, and gradually move towards some infants. The true positive rate is true and false positive rate is false in the above ROC. The cut-off in here is zero whereas the cut-off point in question number 7 is 0.02498325; however, the cut-off value is still zero. Meaning, the cut-off in this diagram will take into account zero infants and harvest adults accordingly at the start and the cut-off of question number 7 will also do the same. 

**Question 9**

An additional calculation will be performed. Harvesting of infants in classes A1 and A2 must be minimized.

Answer:

**Figure 18**  ![image](https://cloud.githubusercontent.com/assets/26909910/25394049/2e3ed5a0-29ab-11e7-8d52-99935c649e3a.png)


**Question 10**

Present a table of the cutoffs determined in #7), #8) and #9) with your interpretation. What tradeoffs and considerations would you present to study investigators?

Answer: 

**Figure 19**  ![fdafd](https://cloud.githubusercontent.com/assets/26909910/25394151/75b043f6-29ab-11e7-98a6-e15ea59ea381.PNG)


The cut-off of zero presented in question number 7 is derived from the volume.value that corresponds to the peak difference and 24th element of the vector. However, the cut-off point in question number 7 is derived from the ROC – the least point in ROC. The cut-off points in question 9 were given in the question. The cut-off value of zero (0) indicate that the we won’t harvest any infants, the trade-off with this approach is that our we capture more adults first, and gradually start to harvest some infants – the proportion of infants harvested at low end of the threshold. The cut-off value of 0.00877193 is not much different since we will start with more adults and gradually shift towards harvesting some infants. The trade-off is the same, increasing rates of infants harvested at the lower end of the threshold. 

# Conclusion

Abalones are a unique species of mollusks that carry a significant economic and environmental importance. Due to the structure of Abalones, determining the age of Abalones has become cumbersome for investigators. Investigators use inefficient drilling procedure to determine the age of the Abalones, and are keen to explore areas where they might be able to determine the age of Abalones using the physical measurements data. The study, however, has not been successful yet. Through the data analysis assignment, we have attempted to use the physical attributes of Abalones to determine a “CLASS” where we can identify and group Abalones as Adults or Infants. Dividing the pool into two categories helps investigator’s economic objective to harvest Abalones when appropriate, and evaluate trade offs at various stages.

Upon analyzing the physical attributes data from the random sample of 500 Abalones, we have identified interesting findings that might certainly help investigators get a deeper insight to make an educated decision. When we set the cut-off point to zero based on the volume-proportion analysis, we found that the ideal move in order to maximize the volume of abalones to harvest is to harvest adults first, and eventually, harvest some infants to meet the volume requirement. We are fairly confident on our analysis of classification into adults and infants class, and the cut-offs vs. trade-offs analysis.

I would, however, recommend taking a “bird-walk” – testing and evaluating as you go – approach. I would first set the cut-offs to zero, and start capitalizing on the adult Abalones. As we start to make our way into infants class, I would go back to the drawing board and perform the analysis again with changed population size, and take a random sampling again. I would repeat all the steps we did in here with changed data and evaluate the cut-offs vs. trade-offs.
  
The major disadvantage of the observational study involving different classes or cohorts of subjects is the challenge surrounding the replication of the study. Since, one of my recommendations included replicating the study and starting over after harvesting the adult Abalones, I am more worried about the limitation of the observational study involving many different classes to be replicated and iterated. Having said that, I am, however, positive that if we keep the location and other factors constant, we will most likely be able to iterate the study with changed sample and population. 

The other challenge is the amount of confusion and ambiguity that exist around the observational study involving different classes, and this challenge too can be mitigated using project management approach, research best practices and scheduling like management system. Therefore, observational study, such as the one presented to us in our data analysis assignment, can be accused of being too simple, too ambiguous, too primitive, and overly complicated, among many other comments; the reality, however, is that observational study is very useful for certain kinds of research study. Therefore, it is important to understand the nature of the study and choose an approach that best fits the need. 


# Appendix

![image](https://cloud.githubusercontent.com/assets/26909910/25394370/dbd394da-29ab-11e7-978a-d4a0e7a32a3e.png)


![image](https://cloud.githubusercontent.com/assets/26909910/25394380/e129edee-29ab-11e7-8af4-1870bfdf038f.png)


![image](https://cloud.githubusercontent.com/assets/26909910/25394397/e5ecd0ee-29ab-11e7-931b-f48a84815063.png)
