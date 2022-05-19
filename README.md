# Analytics’R’Us

# Section 1. Introduction 1.1. Dataset Description and Background
This report contains and analyses sensitive commercial data from the Ass2Dat dataset for Analytics'R'Us. The dataset contained seven numeric variables and 200 observations. Due to the sensitive nature of the data, the seven variables are labelled uninformatively in order not to know what the variables represent. Therefore, the variables are instead classified from C1 to C6, with the first variable labelled Y.
However, according to Maxine Pfannkuch (2011), data context and learning-experience-contexts play a significant role in developing informal inferential reasoning. Therefore, not knowing what the variables represent and the lack of context hinder the informal inferential reasoning of this report. Moreover, Wild & Pfannkuch (1999) proclaim that a statistical investigation aims to learn more about a real situation. Hence, the capability to philosophise over data, argue about perceived patterns and suggest new avenues to explore depends on sound statistical and contextual knowledge foundations. Hence, not knowing the data context reduces the ability to spot outliers and make sure the data makes sense and is credible. For example, a value of 200 would highly likely be an outlier if the variable represents the age of humans and would need to be removed. However, if the variable represents the age of tortoises, the value is unlikely to be an outlier.
Accordingly, Alissa Lorentz (2013) declares that for a business to survive, they have to contextualise its data to transform senseless data into real information that provides actionable insights that foster intelligent corporate decision-making. For example, Lorentz highlights that a doctor diagnosing a patient with diabetes based solely on body temperature alone is incorrect and needs to consider the patient's age, lifestyle, diet, weight, family history, and more to make a probable and guarded diagnosis and prognosis. Therefore, it can be argued that Analytics'R'Us should provide more context and information about the variables. Making business decisions derived from data out of context can lead to inaccurate insights resulting in poor business decision-making.

# 1.2. Aims and Objectives
Consequently, this report aims to predict variable Y (response variable) from the other six covariates, C1, C2, C3, C4, C5 and C6 (explanatory variables). Therefore, this report employs three models (multiple regression, random forest and neural network) that utilise statistical regression tests. Additionally, this report utilises the metrics; R-Squared (R2), Mean Absolute Error (MAE), Mean Squared Error (MSE) and Root-Mean Square Error (RMSE) to assess each statistical model and conclude the best prediction model. Lastly, the report aims to uncover which explanatory variables are the most significant for predicting variable Y.

# 1.3. Overview
Firstly, section 2 illustrates the exploratory data analysis techniques employed to check the data quality to uncover and mitigate any problems in the data and provide a clearer understanding of the data. From the insights gained from the exploratory data analysis, the data was cleaned and transformed to make the data suitable for the statistical models used in the following section. Subsequently, section 3 explains and justifies the three statistical models utilised, multiple regression, random forest and neural network, to predict variable Y from variables C1 to C6. Section 4 presents the modelling results and discusses each model's performance using the abovementioned metrics. Section 4 concludes that the neural network is the best model for predicting variable Y.
Moreover, all three models considered variable C1 the most and C2 the least necessary for predicting variable Y. This report concludes that variable Y can be predicted accurately due to all models suffering from respectable MAE, MSE and RMSE values. Ultimately, section 5 explains the customisation process employed to produce the graphics in the report. Moreover, section 5 reflects upon the limitations of the report. Section 6 contains the appendix that depicts the model selection method and the R script used in this report.

# Section 2. Exploratory Data Analysis
Section 2 describes the EDA and data cleaning conducted in this report. Firstly, section 2.1 below looks at the data summary to get an overview of the data. Subsequently, section 2.2 looks at missing values and section 2.3 analyses the correlations and distributions of the seven variables. Lastly, section 2.4 employs box plots to check for outliers.
Hadley Wickham and Garrett Grolemund (2016) assert that exploratory data analysis (EDA) investigates the quality and systematically explores your data through visualisation and transformation. Overall, EDA aims to check statistical assumptions, data quality, trends, patterns, and outliers to ultimately choose the appropriate statistical tools to analyse the data further and test the hypotheses.

# 2.1. Numerical Summary
Figure 1. Data Summary
![image](https://user-images.githubusercontent.com/97530878/169286709-088196a4-f77b-4da8-9732-6dea50f51530.png)

Figure 1 displays the seven variables as discussed above. The data summary shows each variable's median, mean, minimum and maximum values or outcomes to comprehend the data better. The summary shows that the response variable (variable Y) has an extensive range from -569.2 to 1814.0 and that the other variables (C1 to C6) all have different ranges and averages. Additionally, the summary highlights that variables C1 to C6 had missing values (N/A's) and thus were further examined in the following section. 

# 2.2. Missing Data  
Figure 2. Missing Values Map
![image](https://user-images.githubusercontent.com/97530878/169286826-26a22150-efe4-46f0-87f1-10169c019a8f.png)

Peng (2013) proclaims that missing data can decrease statistical power, increase standard errors, and weaken generalisability. Thus, a missing plot (figure 2) was employed to check for missing data. Firstly, any missing observations were standardised and converted to N/A so that all missing values would show up on the missing plot. The missing plot x-axis shows the variables, and the y-axis displays the observations. If there were missing data, the block would be red rather than blue. Therefore, figure 2 confirms figure 1's conclusion that the data has missing values.

Moreover, according to the pct_compele_case function, that data had 95.5% complete rows. Consequently, the rows containing missing values were removed for the data to be suitable for developing statistical models. Additionally, the data was checked and showed no duplicate observations using the get_dupes function. 

# 2.3. Scatterplot Matrix
Figure 3 below checks for collinearity and multicollinearity of the seven variables. Figure 3 shows that the variables are not highly correlated or have a strong linear relationship with one another, as none of the absolute values of the correlation is greater than 0.9. Hence, multicollinearity is not an issue in this model. Furthermore, figure 3 highlights the distribution of each variable, showing that the variables follow the assumptions of normal distribution. Therefore, multiple regression is a viable model to predict variable Y.  
 
Figure 3. Scatter Plot Matrix: Exploring Distribution and Correlations
![image](https://user-images.githubusercontent.com/97530878/169286895-4bded333-161a-402f-80e3-4fb0c3982fec.png)

# 2.4. Variable Analysis 
Figure 4. Box Plots























