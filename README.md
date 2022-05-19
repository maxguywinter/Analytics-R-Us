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
![image](https://user-images.githubusercontent.com/97530878/169287224-f12a3a43-a4ab-4858-9428-291749f33603.png)

Akin to Figure 1, figure 4 above displays box plots that summarise the five essential values of each variable's distribution: the minimum and maximum value, the first and third quartiles, and the median. All variables box plots are concentrated around its median. Variable Y has the largest median of 678.9, and C4 has the smallest median of -1.81. 

However, the box plots illustrate that all seven variables have outliers. According to Jim Frost (2022), outliers are uncommon values in a dataset and can distort statistical analysis and violate assumptions. Furthermore, Frost states that outliers increase the variability in the data, which decreases statistical power and thus, removing outliers can cause results to become statistically significant. The outliers are shown by the dots above and below the whiskers of the box plots. Nevertheless, Scribbr (2022) proclaim that some outliers are true outliers because they represent natural population variations.

Consequently, Frost argues that outliers are not necessarily unfavourable and should sometimes keep outliers in the dataset. Frost declares that outliers can capture valuable information and that removing outliers 'can distort the results by removing information about the variability inherent in the study area' (Frost,2022). Thus, Scribbr (2022) proclaims that outliers should only be removed if they represent measurement errors, data entry or processing errors, or poor sampling. However, due to lack of context (as discussed in section 1), it is problematic to tell if the outliers are natural and make sense and not data entry errors. Hence, for the statistical models discussed in the following section, the outliers are not excluded as they are not significantly extreme values and could be informative in revealing abnormal cases or rare traits.

# Section 3. Statistical Methods   

This report employs the statistical models' multiple regression, random forest and neural network to predict variable Y from variables C1 to C6. Regression tests examine cause and effect relationships and can be used to estimate the influence of one or more continuous variables on another variable. Hence, these three models use an appropriate statistical test as they employ statistical regression tests that can predict variable Y. Furthermore, section 3 defines and justifies using the three statistical models. Additionally, section 3 states the hypotheses each model plans to test. 

# 3.1. Multiple Regression  

Rebecca Bevans (2020) states that a regression model describes relationships between continuous variables by fitting a line to the observed data. Therefore, regression models can estimate how the dependent variable changes as the independent variable(s) change. Consequently, a multiple linear regression model is employed to estimate the relationship between two or more continuous independent variables (explanatory variables) and one continuous dependent variable (response variable).   

Bevans (2020) proclaims that multiple linear regression is used to predict the value of the response variable at a specific value of explanatory variables or to discover how strong the relationship is between two or more independent variables and one dependent variable. Therefore, as this report aims to predict variable Y from the other six covariates, a multiple regression model is a suitable model. Moreover, the data follows the assumptions of multiple linear regression. As demonstrated in section 2, there is no issue of multicollinearity, the independent and dependent variables are continuous numbers, and the data follows a normal distribution. Moreover, the selection process for the best multiple regression model is illustrated in 6.1 and shows that the assumptions of linearity and homoscedasticity are met. 

# 3.2. Random Forest  

According to Zach, non-linear model methods are better suited 'when the relationship between a set of predictor variables and a response variable is complex' (Zach, 2020). One non-linear model is a decision tree. James Le (2018) states that a decision tree is a supervised learning algorithm used in regression and classification problems. Additionally, decision trees function for both categorical and continuous input and output variables. Thus, a regression decision tree is appropriate for predicting variable Y. However, Zach declares that the downside of using a decision tree is that it tends to suffer from high variance. Therefore, Bradley Boehmke (2022) highlights that bagging regression trees is a technique that can turn a single tree model with high variance and poor predictive power into a reasonably accurate prediction function. However, Boehmke notes that bagging regression trees suffer from tree correlation, which reduces the model's overall performance.

Consequently, Andy Liaw (2002) proposes random forests as they add a layer of randomness to bagging and instead build an extensive collection of de-correlated trees. Random forests construct each tree using a different bootstrap sample of the data and change how the trees are constructed. Liaw states that each node is split using the best split among all variables in standard trees. Subsequently, Leo Breiman (2001) asserts that the random forests method is robust against overfitting and performs well compared to other models such as support vector machines and neural networks.

Moreover, Matt Russell (2020) maintains that random forests often perform better than regression methods. Therefore, it can be argued that the random forest model is a valid model to predict variable Y as the data is suitable for the model and theorised to perform as well and better than other models. Nonetheless, Le (2018) remarks that the main disadvantage of using random forests is that it is easy to overfit noisy datasets, especially for regression. Hence, the lack of context for the data makes it challenging to tell how noisy the dataset is. The selection process for the best tuned random forest model is depicted in section 6.2.

# 3.3. Neural Network 

Avinash Navlani (2019) describes a neural network consisting of simple input and output units called neurons inspired by human brain neurons. It follows the non-linear path and processes information in parallel throughout the nodes. These input and output units (neurons) are interconnected, and each connection has a weight associated with it. The neural network performs computations through "learning" inherent data structures. In the learning phase, the network learns by adjusting the weights to predict the correct class label of the given inputs. Therefore, a neural network is a complex adaptive system meaning it can change its internal structure by adjusting the weights of inputs. Marcus Beck (2018) states that a neural network model is typically used to predict the response of one or more dependent variables given to numerous independent variables. Akin to a random forest, a neural network can be used for both classification and regression as they can process categorical and continuous dependent and independent variables. Thus, a neural network model is a suitable statistical model to predict variable Y as the data is compatible with the model.   

Furthermore, Akshi Saxena (2020) proclaims that a neural network is generally a better predictive model than regression models. Saxena states that most regression models will not fit the data perfectly as they only work well when the regression equation is a good fit for the data. Whereas neural networks are flexible and can dynamically pick the best type of regression, hidden layers can also be added to improve prediction. Jason Brownlee (2018) defines hidden layers as the layers of neurons between the input and output units. Moreover, Beck (2019) declares that a neural network model can fit a smooth function with minimal residual error to any dataset. A neural network model is theorised to perform well in making predictions compared to other models, such as regression models. Thus it can be argued that a neural network is a viable model to predict variable Y. The selection process for the best tuned neural network model is presented in section 6.3. The following section discusses the results from the predictive models described above. 

# Section 4. Results and Conclusions

This section presents the best-tuned model results for each modelling method discussed above. Furthermore, section 4 examines each model's predictive performance using the metrics; R², MAE, MSE, and RMSE. 

# 4.1. Multiple Regression  
 
 Figure 5. Multiple Regression Summary
 ![image](https://user-images.githubusercontent.com/97530878/169287419-439ed3d2-d5af-49e0-98f3-8d3489e92812.png)

 Figure 6. Multiple Regression Residuals
 ![image](https://user-images.githubusercontent.com/97530878/169287452-62847993-b2b1-4b90-85e4-520f8e8dd5b9.png)

The selection process for the best multiple regression model is depicted in section 6.1. Figure 5 exhibits the multiple regression model summary. The best performing model had the lowest p-value of 5.397e-07 and consisted of only three explanatory variables (C1, C2 and C4) that were all statistically significant. Variables C1 and C4 were both statically significant at the 1 per cent level, and variable C2 was statically significant at the 10 per cent level. Figure 7 below illustrates the importance of each model's variables for predicting variable Y. Variable C4 is the most critical variable, closely followed by C1 and then C2. 

However, the final model chosen had a low R² of 0.2, indicating the model has a weak fit. Having a low R² and poor fit means that most of the variation in the data is not accounted for. Consequently, having a small R² and p-value means that the regression model does not explain much variation, but it is significant.

Figure 6 displays the best multiple regression model residuals. Firstly the QQ plot shows that the majority of residuals fall on the straight line. Therefore, the data appears to be normally distributed, and the assumption of normality holds. Additionally, the Residuals vs Fitted plot shows that linearity holds as the red line is close to the dashed line. Moreover, heteroskedasticity is not an issue as we move to the right on the x-axis. The spread of the residuals is not increasing.

Additionally, the NCV test shows that the p-value is significant at 0.57796, and thus the null hypothesis can be accepted. Therefore, the variance of the residuals is constant and infers that heteroscedasticity is not present. Consequently, the data satisfy the multiple regression assumptions of linearity, normality, and homoscedasticity.

Figure 7. Multiple Regression Variable Importance    
![image](https://user-images.githubusercontent.com/97530878/169287575-f7c3aed7-d325-4eca-94ed-178257de145a.png)

# 4.2. Random Forest

The process of tuning the random forest is illustrated in section 6.2. The tuned random forest had 1000 trees grown, and three variables randomly sampled as candidates at each split, with a minimum of twenty-one data points in a node required for the node to split further.

The random forest R² was 0.15 and thus lower than the multiple regression R² indicating an even poorer fit. However, Spiess & Neumeyer (2010) declare that R² should not be used to assess the goodness-of-fit for non-linear models. Frost (2017) states that R² for non-linear models is not necessarily between 0 and 100% as the explained variance + error variance do not add up to the total variance. Spiess & Neumeyer's study concluded that using R² lead to false conclusions about the best non-linear models. They reported that R² was consistently overestimated, and using R² to choose the best model only results in choosing the best model only 28-43% of the time. Therefore, other metrics such as RMSE are more suitable for assessing and comparing linear and non-linear model performance, as explored in section 4.4. 

Figure 8. Random Forest Variable Importance
![image](https://user-images.githubusercontent.com/97530878/169287662-eb95b737-5c42-4c4a-bb53-56d9b2adada4.png)

Figure 8 above depicts the importance of each random forest model's variables for predicting variable Y. Akin to the regression model; variable C4 is the most influential variable. Additionally, both models deem variable C1 to have relative high importance. However, variable C2 was considered the least important by the random forest but strongly influenced the regression model. 

# 4.3. Neural Network

The best neural network constructed (the method of tuning and selecting the best neural network model is described in section 6.3) had two hidden layers with three neurons on the first layer and two neurons in the second layer.

Figure 10 below is a graphical visualisation of the final tuned neural network model. Figure 10 illustrates the weights learned by the final neural network and displays the number of iterations before convergence and the sum of squares error (SSE). The black lines show the connections between each layer and the weights on each connection. In contrast, the blue lines show the bias term added in each step. Michy Alice (2018) proclaims that the bias can be considered the intercept of a linear model. Furthermore, Alice states that a neural network is essentially a black box and thus cannot say much about the fitting, the weights and the model. The SSE for the final neural network model was 0.725 and was the smallest SSE compared to other potential neural network models. The smaller the SEE means a lower error in the difference between observed and the predicted values. 

Figure 10. Neural Network Plot  
![image](https://user-images.githubusercontent.com/97530878/169287767-9a6edc29-853b-46e3-95de-27a069ac042e.png)

Figure 11. Neural Network Variable Importance  
![image](https://user-images.githubusercontent.com/97530878/169287810-441f8fdc-8b70-4f4f-86df-cef5520c3de2.png)

As discussed in section 4.2, R² is not the most suitable metric to evaluate non-linear model performance. Nevertheless, the neural network R² was 0.4 and thus had the best fit out of the three models. Zach (2019) maintains that a larger R² value means that the explanatory variables can predict the values of the response variable more precisely. Nonetheless, all models had a weak fit (low R² value) and thus little predictive power.

According to Julian Hatwell (2016), the flexible non-linear nature of neural networks complicate the appraisal of the relative importance of each explanatory variable. Hence, there have been several methods for assessing variable importance. Marcus Beck (2018) states that one method is the Garson's algorithm. This algorithm deconstructs the model weights and identifies the relative importance of explanatory variables for a single response variable. However, Beck highlights that Garson's algorithm can only be used for neural networks with one hidden layer. Therefore, the Olden method was utilised to assess the importance of variables as the algorithm can work with multiple hidden layers. Figure 11 displays the importance of each neural network model's variables for predicting variable Y using the Olden method. The neural network deemed variable C1 the most important variable, followed by C6 and C5. Therefore, all three models considered C1 the most and C2 the least necessary for predicting variable Y. 

# 4.4. Conclusion 

As discussed previously, R² is not the most suitable metric to evaluate non-linear and linear model performances. Therefore, table 1 employs the metrics; MAE, MSE, and RMSE to assess and conclude the best model for predicting variable Y. 

Yousef Nami (2020) asserts that the MAE is the sum of all the error magnitudes divided by the number of points and thus is essentially the average error. The MSE is the sum of the squares of all errors divided by the number of points. Consequently, Frost states that the MSE measures the error in statistical models to assess 'the average squared difference between the observed and predicted values' (Frost, 2022). The RMSE is the square root of the MSE. Zach (2020) declares that the RMSE is the most common way to measure the accuracy of a regression model and informs on average how far apart the predicted values are from the observed values in a model. The smaller the RMSE, the better a regression model can fit the data.

Moreover, for all three metrics discussed, the lower the score, the lower the error. Nami argues that the RMSE is the most useful metric. The RMSE is better at capturing large errors in the data as the RMSE has a squared term, and thus large errors will be squared. In comparison, MAE gives the average error and thus does not pick up on substantial errors. 

Table 1 reveals that the neural network had the lowest MAE, MSE and RMSE values. Consequently, the neural network model was the best fitting for predicting variable Y. The multiple regression model was the second-best performing model as it had lower MAE, MSE and RMSE values than the random forest. Furthermore, figure 12 shows each model's predicted vs actual observed values. Alice (2018) declares that points more concentrated around the line show better predictions. As points perfectly aligned with the line indicate an MSE of 0 and thus an ideal perfect prediction. Thus, the neural network has more scores closer to the line than the regression and random forest model, which means that the neural network model may be considered the better fitting model.

Additionally, table 1 illustrates the correlation tests employed to reinforce what is being seen in figure 12. Scores closer to 1 are betting fitting. The neural network model had a correlation score of 0.56. The regression model had a correlation score of 0.54,  and the random forest model had a correlation score of 0.39. Hence, the neural network model is considered the best fitting model. Nevertheless, the scores are very close to the regression model and may not show significance.


Table 1. Model Performance

	<img width="349" alt="image" src="https://user-images.githubusercontent.com/97530878/169287931-71257012-8701-4746-8414-a9419cdc41d6.png">

Figure 12. Predicted vs Actual Plots
![image](https://user-images.githubusercontent.com/97530878/169287985-60983fec-a1c1-4ece-a64b-57ae290f940e.png)

To conclude, the three models can predict variable Y from the other six covariates, C1, C2, C3, C4, C5 and C6. Furthermore, the neural network model is the best suited out of the three models to predict variable Y as it had the lowest MAE, MSE and RMSE values. However, according to the R² value, all the models had a weak fit. Nevertheless, as discussed above, R² is an unsuitable metric for non-linear models. In contrast, the RMSE is argued to be a superior metric in determining and comparing models' performance. The neural network model produced the lowest RMSE of 305.05. Zach (2021) discloses that the RMSE should be normalised to understand better whether an RMSE is a good value. The formula to normalise the RMSE: 

      Normalised RMSE = RMSE / (max value – min value) 

This formula produces a value between 0 and 1, where values closer to 0 represent better fitting models. The neural network normalised RMSE was 0.13, indicating that the model can accurately predict variable Y.

# Section 5. Reflection 

Section 5 highlights the customisation employed to produce the graphics in the report and reflects upon the report's limitations.   

# 5.1. Process of Plot Customisation 

The graphical plots used to visualise the data in this report were created using ggplot2. Wickham & Grolemund (2016) claim that ggplot2 is one of the most elegant and versatile systems for producing graphs. Christine Teng (2020) reports that the ggplot2 package implements the grammar of graphics, a coherent system for describing and building graphs. One of the main benefits of ggplot2 is using themes to customise graphs. The components of the theme function allow full customisation of the plot, such as the colours, fonts, titles, and line and point types.  

Figure 13. Box Plot
![image](https://user-images.githubusercontent.com/97530878/169288104-6d96270b-6e3c-429d-be2d-28d1d9f2f558.png)

Figure 14. Scatter Plot  
![image](https://user-images.githubusercontent.com/97530878/169288146-a379c85a-b2e8-46ec-9f2c-1189e0e922d9.png)

Figure 15. Predicted vs Actual Plots
![image](https://user-images.githubusercontent.com/97530878/169288170-36641730-51f7-446d-b8ce-8e7f7bc83045.png)

Figures 13 and 14 exhibit graphs made using the basic ggplot2 theme. It can be argued that the basic theme is unaesthetic. Hence, this report utilised the economist theme to have a unified and aesthetic colour theme throughout the report. As illustrated in figure 15, the plot background colour changed to a light blue and the grid to white horizontal lines. Furthermore, titles and labels were added and changed to improve the readability of the graphs. For example, Figure 13 box plot did not have a title or correctly labelled axis and was transformed to figure 5 to have an appropriate title and label axis. Moreover, for figure 15, the scales and colour points were changed to be the same for all three graphs for easier comparison to create figure 12. 

However, the multiple regression residuals (figure 6) and the neural network graphs (figures 10 and 11) did not use ggplot2. Therefore, these graphs did not follow the economist theme. Hence, these graphs' colours were changed to the same background colour (#d5e4eb) and points colour (#1380A1) as the economist theme to try and maintain a cohesive colour scheme.  

# 5.2. Limitations 

As examined in section 1.1, the main limitation of this report is the lack of information and context about the data and variables. The lack of information inhibits the informal inferential reasoning of this report. Furthermore, the shortage of information reduces the ability to ensure the data is credible and turns meaningless data into accurate information that provides insights for intelligent corporate decision-making. 

Another limitation of this report is the metrics used to evaluate each statistical model. As explored in section 4.2, R² is not a suitable metric to evaluate non-linear model performance. Therefore, as Frost (2017) argued, the standard error of the regression (S) is a superior metric. Frost maintains that, unlike R², the S can assess the precision of the predictions. Moreover, S is valid for both linear and non-linear models, thus able to make comparisons of the models' fit. 

The last primary constraint of this report is the model creation and tuning to select the best models for analysis. As discussed in section 6.1, the multiple regression model chosen for the final analysis may not have been the best as it had the lowest R². Moreover, the final neural network model may not be the best performing. As discussed in section 6.3, Jeff Heaton's (2017) recommendations were used to tune the model's hyperparameters (determining the number of hidden layers and neurons) which ultimately comes down to trial and error. Consequently, Brownlee (2018) states that an automated grid search across different layers and neurons could produce more optimised hyperparameters that improve the model's predictive performance. Thus, it can be argued that having better-tuned models could produce different predictions and hence offer different conclusions to this report. 

# Section 6. Appendix   

Section 6 clarifies the model selection methodology for each statistical model utilised in this report. Following this, section 6 displays the R code used for this report.  

# 6.1. Process of Multiple Regression Model Selection

The multiple regression model chosen for this report was created by firstly fitting a model with all six covariates. Subsequently, each new refitted model removed the explanatory variable with the largest p-value until the model only contained significant variables. As illustrated in figure 5, the final fitted model (model 4) only consisted of three explanatory variables, C1, C2 and C4, all statistically significant. Additionally, to double-check for collinear variables, a Variance Inflation Factors (VIF) test was used for model 3. No variables were removed as none of the VIFs were above ten, suggesting no multicollinearity issues.

Furthermore, a stepwise model selection from the full model was utilised to find the best Akaike information criterion (AIC) model by taking or adding variables. As exhibited in figure 16, the best AIC model was the same as model 2. Model 2 had an AIC score of 2065.1, consisting of five explanatory variables, C1, C2, C3, C4 and C6. Nevertheless, model 4 had an AIC score of 2065.3. An AIC score that differs by less than two from the minimal AIC is a plausible alternative model. Additionally, the Bayesian information criterion (BIC) score was used to evaluate the fit of each model. Figure 17 shows that model 4 had the best BIC score of 2080.099. 

Figures 16, 17 and 19 reveal that model 2 had the best AIC score and adjusted R². Whereas model 4 had the best BIC score and lowest p-value. Hence an ANOVA test was conducted to compare model 2 with model 4 to decide the best fitting model. The ANOVA results show that the simplest model (model 4) produces more accurate fitted values than the more complex model (model 2), as the p-value was 0.1375. Model 4 is favoured as the p-value was not sufficiently low as it was greater than 0.05. Therefore, model 4 was employed for predicting variable Y for this report. 

Figure 16. AIC Scores

![image](https://user-images.githubusercontent.com/97530878/169288340-1d0c6efe-a431-42b0-91d4-f471fe096284.png)

Figure 17. BIC Scores

![image](https://user-images.githubusercontent.com/97530878/169288368-3fb7a90f-93a9-4c86-8ee1-f47b127e1ec4.png)

Figure 18. ANOVA Test

![image](https://user-images.githubusercontent.com/97530878/169288392-2cb002c7-d312-4c06-bf32-ef7decd02075.png)

Figure 19. Regression Model Comparisons

![image](https://user-images.githubusercontent.com/97530878/169288416-21324711-9974-4d55-b3b8-6d6f8ba72700.png)

# 6.2. Process of Random Forest Model Selection

Figure 20. Ranger Recipe 
![image](https://user-images.githubusercontent.com/97530878/169288501-a2ee7767-5a99-4771-8a48-7c85e4416514.png)

Figure 21. Best RMSE Radom Forest Model
![image](https://user-images.githubusercontent.com/97530878/169288583-11bff41b-f81f-4969-9913-193aa4d7d9c7.png)

The random forest was implemented using the ranger package; as Marvin N. Wright (2021) states, the ranger is a faster implementation of random forests. Subsequently, as illustrated by figure 20, the use_model function was utilised to provide scaffolding for getting started with tidymodels tuning. The tuning process used a grid search that tired various candidate models of different mtry and min_n with the lowest RMSE. Figure 21 shows the best RMSE models and their performance estimates. Hence, model 1 in figure 21 was utilised to predict variable Y for this report as the model had the best RMSE and third-highest R². 

# 6.3. Process of Neural Network Model Selection

According to Jeff Heaton (2017), determining the number of neurons in the hidden layers is an integral part as they greatly influence the final output. Heaton proclaims that using too few neurons in the hidden layers will result in underfitting, and using too many neurons can result in overfitting. Heaton states that two layers will suffice for simple datasets. Therefore, the neural network uses two layers as it can be argued that the Ass2Dat dataset is simple. Furthermore, Heaton gives three rules to help choose the number of hidden neurons: 

‘The number of hidden neurons should be between the size of the input layer and the size of the output layer. 
              The number of hidden neurons should be 2/3 the size of the input layer plus the size of the output layer.
              The number of hidden neurons should be less than twice the size of the input layer’ (Heaton, 2017).

Figure 22. Neural Networks’ SSE   
![image](https://user-images.githubusercontent.com/97530878/169288656-ddb284a4-3713-4ffd-a9eb-1e0a59fe3700.png)

Consequently, models from two layers with one neuron and two neurons to five neurons and five neurons were constructed and tested. Figure 22 demonstrates that neural network model 9 had the lowest test and train SSE error. Therefore, model 9 was used as the final neural network model to predict variable Y for this report. 

6.4. R code   

##### Analytics’R’Us ###########################################################
# Code developed by Max Winter                                                 #
################################################################################

##### SET WORKING DIRECTORY ####################################################
# User should set the relevant working directory.                              #
# Either Session --> Set Working Directory --> To Source File Location         #
# To Source File Location means that the data will be imported and saved       #
# IN THE SAME FOLDER where you saved the R Script you're working with!         #
# OR                                                                           #
## setwd("")                                                                   #
# This code used setwd("~/Desktop/Results report") as the working directory    #     
# that contained the Analytics'R'Us data set.                                  # 
################################################################################

##### RELEVANT PACKAGES ########################################################
##### Users should install the relevant packages below                         #
#                                                                              #
# Use install.packages('') if unable install the required packages from        #
# library ()                                                                   #
################################################################################
library(corrplot) # For correlation matrix graph visualization.
library(ggplot2) # For graph visualizations. 
library(ggthemes) # For graph customisation.
library(Amelia) # For miss map of missing data.
library(naniar) # Shows missing values. 
library(janitor) # Shows rows of a data frame with identical values for the specified variables.
library(GGally)# For scatter plot matrix graph visualization. 
library(corrplot) # For correlation matrix graph visualization.
library(ggpubr) # To have multiple plots on one same page. 
library(caTools) # For sample.split function to create train and test populations for model validation and predication tests. 
library(car) # For VIF, plots and Outlier Test. 
library(MASS) # for AIC test.
library(stargazer) # To format regression output into a table.
library(tidyverse) # To make it easy to install and load multiple 'tidyverse' packages in a single step. 
library(flexmix) # To calculate BIC value. 
library(relaimpo) # For measuring the relative importance of each predictors in regression model. 
library(Metrics) # For MAE calculation.  
library(caret) # An aggregator package for performing many machine learning models.
library(vip) # Measure of variable importance based on partial dependence measures and is a common variable importance plotting framework for many machine learning models.
library(rsample) # Data splitting.
library(randomForest) # Basic implementation.
library(ranger) # A faster implementation of randomForest. 
library(tidymodels) # For modeling and statistical analysis.
library(usemodels) # For creating radomForest model. 
library(rlang) # A toolbox for working with base types, core R features like the condition system, and core 'Tidyverse' features like tidy evaluation.
library(neuralnet) # To create a Neural Network Model. 
library(NeuralNetTools) # Visualization and Analysis Tools for Neural Networks (variable importance analysis). 

##### DATA INPUT ###############################################################
data <- read.csv("Ass2Dat.csv", header = TRUE) # Imports the data set. The header=True command tells RStudio to use the first row of the data file as the names of each variable/column. 
attach(data) # Attaches the data to your environment so that you can directly refer to the variable by name.
names(data) # Shows the name of variables in the data set.
summary(data) # Produces summary data (Min, Median, Mean and Max) for the individual variables. 
str(data) # Shows the observations and variables of the data.

##### DATA CODING/ CLEANING ####################################################

##### checking for missing data ################################################
data[data == "" | data == " "] <- NA # Makes any missing data a NA. 
data[data == "N/A" | data == "n/a" | data == "N/a"| data == "-"] <- NA # Standardizes NA values (N/A, n/a, N/a) to NA. 

missmap(data) # Checks for missing data by producing a map
# Or (Missmap customisation) 
par(bg = "#d5e4eb") # Changes colour of plot background. 
missmap(data, col=c("red3", "#1380A1"), x.cex = 0.3,legend = TRUE) # Checks for missing data by producing a map (red points indicts missing data). 

pct_miss(data) # Percent of ALL data frame values that are missing.
pct_miss_case(data) # Percent of rows with any value missing.
pct_complete_case(data) # Percent of rows that are complete (no values missing). 
get_dupes(data) # Checks for duplicates and wrong input. 

##### Cleaned Data #############################################################
MyDataCleaned<-na.omit(data) # Removes NA's (missing data) from the original data frame and creates a new data frame (MyDataCleaned) that has no missing data. 
nrow(data) # Shows the number of observations in the original data frame (200).
nrow(MyDataCleaned) # Shows the number of observations in the new data frame (191) highlighting that the missing data has been removed.

na.fail(data) # Checks for missing values. If missing data is present then error message occurs stating their is 'missing values in object'.  
na.fail(MyDataCleaned) # Checks for missing values. If missing data is present then error message occurs stating their is 'missing values in object'. 

par(bg = "#d5e4eb") # Changes colour of plot background. 
missmap(MyDataCleaned,col=c("red3", "#1380A1"), x.cex = 0.3, legend = TRUE) # Checks for missing data by producing a map (red points indicts missing data). 
pct_miss(MyDataCleaned) # Percent of ALL data frame values that are missing.
pct_miss_case(MyDataCleaned) # Percent of rows with any value missing.
pct_complete_case(MyDataCleaned) # Calculate the percentage of cases (rows) that contain a complete value. 

names(MyDataCleaned) # Shows the name of variables in the new cleaned data frame to see if they're the same as the original data set.
names(data) # Shows the name of variables in the old cleaned data frame to see if they're the same as the new data set.
str(data) # Shows the observations and variables of the old data frame.
str(MyDataCleaned) # Shows the observations and variables of the new data frame. 

##### EXPLORATORY DATA ANALYSIS ################################################

##### Correlation Analysis ##################################################### 
lowerFn <- function(data, mapping, method = "lm", ...) {
  p <- ggplot(data = data, mapping = mapping) + geom_point(colour = "#1380A1") +
    geom_smooth(method = method, color = "red3", ...)
  p
} # Function for regression line. 

ggpairs(MyDataCleaned, lower = list(continuous = wrap(lowerFn, method = "lm")),
        diag = list(continuous = wrap("barDiag")), upper = list(continuous = wrap("cor",size = 5)))
# Or (Correlation customisation)  
ggpairs(MyDataCleaned, lower = list(continuous = wrap(lowerFn, method = "lm")),
        diag = list(continuous = wrap("barDiag", colour = "#1380A1")), upper = list(continuous = wrap("cor",size = 5))) + 
  labs(title = "Scatter plot matrix: Exploring distributions and correlations.") +
  theme(plot.background = element_rect(fill = "#d5e4eb")) # Correlation matrix graph visualization that checks for collinearity and multicollinearity of the explanatory variables (1 shows collinearity).  

##### Box plots ################################################################
box1 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$Y)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() 
box1
# Or (Boxplot customisation)
box1 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$Y)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() + 
  labs(title = "Variable Y\n", y = "") +
  theme_economist()
box1

box2 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$C1)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() + 
  labs(title = "Variable C1\n", y = "") +
  theme_economist()
box2

box3 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$C2)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() + 
  labs(title = "Variable C2\n", y = "") +
  theme_economist()
box3

box4 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$C3)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() + 
  labs(title = "Variable C3\n", y = "") +
  theme_economist()
box4

box5 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$C4)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() + 
  labs(title = "Variable C4\n", y = "") +
  theme_economist()
box5

box6 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$C5)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() + 
  labs(title = "Variable C5\n", y = "") +
  theme_economist()
box6

box7 <- ggplot(MyDataCleaned, aes(y = MyDataCleaned$C6)) +
  stat_boxplot(geom = "errorbar", width = 0.15) + 
  geom_boxplot() + 
  labs(title = "Variable C6\n", y = "") +
  theme_economist()
box7

ggarrange(box1, box2, box3, box4, box5, box6, box7 + rremove("x.text"), 
          ncol = 4, nrow = 4) # This code arranges the above figures into one plot in order to see all figures better and easier.

###### Scatter plots ########################################################### 
scat1 <- ggplot(MyDataCleaned, aes(x = MyDataCleaned$C2,  y = MyDataCleaned$C4)) + 
         geom_point() +
  geom_smooth(method='lm', formula= y~x, se= FALSE, colour = "red")
scat1  
# Or (Scatter plot customisation) 
scat1 <- ggplot(MyDataCleaned, aes(x = MyDataCleaned$C2, 
                                    y = MyDataCleaned$C4)) + 
  geom_point(colour = "#1380A1") +
  labs(title = "Fig.6a C2 and C4 scatterplot", 
       y = "C4", x = "C2") +
  geom_smooth(method='lm', formula= y~x, se= FALSE, colour = "red3") +
  theme_economist()
scat1  

scat2 <- ggplot(MyDataCleaned, aes(x = MyDataCleaned$C2, 
                                   y = MyDataCleaned$C5)) + 
  geom_point(colour = "#1380A1") +
  labs(title = "Fig.6b C2 and C5 scatterplot", 
       y = "C5", x = "C2") +
  geom_smooth(method='lm', formula= y~x, se= FALSE, colour = "red3") +
  theme_economist()
scat2  

scat3 <- ggplot(MyDataCleaned, aes(x = MyDataCleaned$C6, 
                                   y = MyDataCleaned$C1)) + 
  geom_point(colour = "#1380A1") +
  labs(title = "Fig.6c C6 and C1 scatterplot", 
       y = "C1", x = "C6") +
  geom_smooth(method='lm', formula= y~x, se= FALSE, colour = "red3") +
  theme_economist()
scat3  

scat4 <- ggplot(MyDataCleaned, aes(x = MyDataCleaned$C6, 
                                   y = MyDataCleaned$C3)) + 
  geom_point(colour = "#1380A1") +
  labs(title = "Fig.6d C6 and C3 scatterplot", 
       y = "C3", x = "C6") +
  geom_smooth(method='lm', formula= y~x, se= FALSE, colour = "red3") +
  theme_economist()
scat4 

ggarrange(scat1, scat2, scat3, scat4 + rremove("x.text"), 
          ncol = 2, nrow = 2) # This code arranges the above figures into one plot in order to see all figures better and easier.

##### MULTIPLE REGRESSION ######################################################

##### Data Train and Test sets #################################################
set.seed(123) # Makes simulations random numbers the same to ensure all results, figures  are reproducible.
split = sample.split(MyDataCleaned$Y, SplitRatio = 0.75) 
train = subset(MyDataCleaned, split == TRUE)
test = subset(MyDataCleaned, split == FALSE) # Sets up train and test populations for model validation and predication tests. 

##### Initial model ############################################################
model1 <- lm(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = train)
summary(model1)

# Initial model (model 1) performance and residuals/outliers checks
par(bg = "#d5e4eb")
par(mfrow = c(2, 2)) # Partitions your graphical display if you want to produce multiple graphs on a single plot.
plot(model1, col = "#1380A1") # Plots residual graphs for model 1. 

# Distribution of errors 
par(mfrow = c(1, 1))
residplot2 <- function(model1, nbreaks = 10) {
  z2 <- rstudent(model1)
  hist(z2, breaks = nbreaks, freq = FALSE, xlab = "Studentized Residual", main = "Distribution of Errors",
        col = "#1380A1")
       rug(jitter(z2), col = "red3")
       curve(dnorm(x, mean = mean(z2), sd = sd(z2)), add = TRUE, col = "blue", lwd = 2)
       lines(density(z2)$x, density(z2)$y, col = "red3", lwd = 2, lty = 2)
       legend("topright", legend = c("Normal Curve", "Kernel Density Curve"), lty = 1:2,
              col = c("blue", "red3"), cex = 0.5)
}
       
       residplot2(model1)

# Linearity 
par(bg = "#d5e4eb")
crPlots(model1, col = "#1380A1", col.lines = c("red3", "blue"), main = "Model 1 Linearity(Component + Residual Plots)") 

# Homoscedasticity
par(bg = "#d5e4eb")
ncvTest(model1)
         
par(bg = "#d5e4eb")
influencePlot(model1, id.method = "identify", main = "Influence Plot", sub = "Circle size is proportional to Cook's distance")

##### Model Selection ##########################################################
model2 <- lm(Y ~ C1 + C2 + C3 + C4 + C6, data = train) # removed C5 as had largest p-value. 
summary(model2)

model3 <- lm(Y ~ C1 + C2 + C4 + C6, data = train) # removed C3 as had largest p-value. 
summary(model3)

# vif test for collinear variables to remove (all fine if variables are below 10) 
vif(model3)

model4 <- lm(Y ~ C1 + C2 + C4, data = train) # removed C6 as had largest p-value. 
summary(model4)

# AIC best model
starting.model <- lm(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = train)
simple.model <- lm(Y ~ 1, data = train)
stepAIC(starting.model, scope = list(upper = starting.model, lower = simple.model),
        direction = "both") # Best AIC model same as model 2

stargazer(model1, model2, model3, model4, type = "text", report = "vc",
          header = FALSE, title = "AIC Values", single.row = TRUE, 
          keep.stat = c("rsq","n"), omit.table.layout = "n", add.lines = list(c("AIC", round(AIC(model1), 1), 
                                                                                round(AIC(model2), 1), round(AIC(model3), 1), round(AIC(model4), 1)))) # shows best AIC model is model 2
# Best BIC
BIC(model1, model2, model3, model4) # model 4 has lowest BIC thus best model 

# Model Comparisons 
stargazer(model1, model2, model3, model4, type = "text", dep.var.labels = c("Y"),
          title = " Model Comaparison", header = FALSE, report = "vcp*", style = "qje",
          column.labels = c("Model1", "Model2", "Model3", "Model4"), single.row = TRUE, font.size = "tiny")
   
# ANOVA Test 
anova(model4, model2) # model 4 vs model 2 

# If the resulting p-value is sufficiently low (usually less than 0.05), 
# we conclude that the more complex model is significantly better than the simpler model, 
# and thus favor the more complex model. If the p-value is not sufficiently low (usually greater than 0.05),
# we should favor the simpler model. Thus should favour model 4 (simplest model) as p-value was not low (0.13)

##### Model Validation #########################################################
par(bg = "#d5e4eb")
par(mfrow = c(2, 2))
plot(model4, col = "#1380A1") # Plots residual graphs for model 4. 

# Distribution of errors 
par(mfrow = c(1, 1))
residplot <- function(model4, nbreaks = 10) {
  z <- rstudent(model4)
  hist(z, breaks = nbreaks, freq = FALSE, xlab = "Studentized Residual", main = "Distribution of Errors",
        col = "#1380A1")
       rug(jitter(z), col = "red3")
       curve(dnorm(x, mean = mean(z), sd = sd(z)), add = TRUE, col = "blue", lwd = 2)
       lines(density(z)$x, density(z)$y, col = "red3", lwd = 2, lty = 2)
       legend("topright", legend = c("Normal Curve", "Kernel Density Curve"), lty = 1:2,
              col = c("blue", "red3"), cex = 0.7)
}
        residplot(model4)

# Homoscedasticity
par(bg = "#d5e4eb")
ncvTest(model4)
par(mfrow = c(1, 1))
influencePlot(model4, id.method = "identify", main = "Influence Plot", sub = "Circle size is proportional to Cook's distance")
        
# Importance of variables 
varImp(model1, scale = TRUE)
varImp(model4, scale = TRUE)
vip((model4),aesthetics = list(fill = "#1380A1")) + 
  ggtitle("Multiple Regression Variable Importancef") +
  theme_economist() # Variable of importance. 

##### Model Predictions ########################################################

# Model 4 Predictions 
reg4_pred_train <- predict(model4, train) # predictions using train data
reg4_pred_test <- predict (model4, test) # uses test rather than train subset of data

# Metrics 
caret::R2(reg4_pred_test, test$Y) # R2 test set
RMSE <- function(predicted, true) mean ((predicted-true)^2)^.5
RMSE (predict(model4, test), test$Y) # RMSE
caret::MAE(reg4_pred_test, test$Y) # MAE

# Predicted vs Actual 
par(bg = "#d5e4eb")
par(mfrow = c(1, 1))
 plot(test[, "Y"], predict(model4, test), xlim = c(-200, 1600), ylim = c(-200, 1600),
     xlab = "Actual", ylab = "Predicted", main = "Model 4", col = "#1380A1")
abline(0, 1, col = "red3") # Mode 4 Predicted vs Actual. 
# Or (Predicted vs Actual plot customisation) 
Reg4_pred_plot <- ggplot(test, aes(test$Y, reg4_pred_test)) + 
  geom_point(colour = "#1380A1") +
  geom_abline(color = "red3") +
  labs(title = "Model 4", y = "Predicted Y", x = "Actual Y") +
  theme_economist()
Reg4_pred_plot

# Correlation Tests
cor(test[, "Y"], predict(model4, test)) # Scores closer to 1 are betting fitting.

##### RANDOM FORREST ###########################################################
set.seed(123)# Makes simulations random numbers the same to ensure all results, figures  are reproducible.
data_split <- initial_split(MyDataCleaned, strata = Y, prop = .75)
data_train <- training(data_split)
data_test <- testing(data_split) # Sets up train and test populations for model validation and predication tests.

##### Build a model ############################################################
set.seed(123) # Makes simulations random numbers the same to ensure all results, figures  are reproducible.
## making resamples for tuning the model or comparing models. 
data_folds <- bootstraps(data_train, strata = Y) # 25 recent boostrap resamples. 
# cross validation fold (resampling setup)
data_folds

use_ranger(Y ~., data = data_train) # produces boilerplate code to see best practices for training a ranger randomForest (recipe, specification and workflow that puts them together and then the actual tuning). 

ranger_recipe <- recipe(formula = Y ~., data = data_train)

ranger_spec <- rand_forest(mtry = tune(), min_n = tune(), trees = 1000) %>%
  set_mode("regression") %>%
  set_engine("ranger")

ranger_workflow <- workflow() %>% 
                   add_recipe(ranger_recipe) %>% 
                   add_model(ranger_spec)

set.seed(123) # Makes simulations random numbers the same to ensure all results, figures  are reproducible.
ranger_tune <- tune_grid(ranger_workflow, resamples = data_folds, # add folds 
                         grid = 11) # grid = is the number of candidate models of different mtry and min_n.   

##### Explore results ##########################################################
show_best(ranger_tune, metric = 'rmse') # Displays the top sub-models and their performance estimates.
show_best(ranger_tune, metric = 'rsq')
select_best(ranger_tune) # Finds the tuning parameter combination with the best performance values.

autoplot(ranger_tune) # All the possible parameter combinations. 

final_rf <- ranger_workflow %>%
            finalize_workflow(select_best(ranger_tune)) # Finalise random forest workflow with the best performing parameters.
final_rf

data_fit <- last_fit(final_rf, data_split) # The function last_fit() fits this finalised random forest one last time to the training data and evaluates one last time on the testing data.
data_fit 

collect_metrics(data_fit) # The metrics in data_fit are computed using the testing data.
collect_predictions(data_fit) # The predictions in data_fit are also for the testing data.

metrics = collect_predictions(data_fit) # Makes data frame for to calculate metrics of the model. 
metrics

actual <- metrics$Y # Actual Y values.
predicted <- metrics$.pred # Model predictions for Y.
mse(predicted, actual) # MSE
caret::RMSE(predicted, actual) # RMSE 
caret::R2(predicted, actual) # R2
caret::MAE(predicted, actual) # MAE

# Predicted vs Actual 
RF_pred_plot <- ggplot(data_test, aes(actual, predicted)) + 
  geom_point(colour = "#1380A1") +
  geom_abline(color = "red3") +
  labs(title = "Predicted vs Actual Y", y = "Predicted Y", x = "Actual Y") +
  theme_economist()
RF_pred_plot

# Correlation Tests
cor(actual,predicted)

# To male predictions. 
predict(data_fit$.workflow[[1]], data_test[10,]) 

## Feature importance 
imp_spec <- ranger_spec %>% finalize_model(select_best(ranger_tune)) %>%
            set_engine('ranger', importance = "permutation") # For a ranger model, need to go back to the model specification itself and update the engine with importance = "permutation" in order to compute feature importance (this means fitting the model one more time).

workflow() %>% 
  add_recipe(ranger_recipe) %>% 
  add_model(imp_spec) %>% 
  fit(data_train) %>%
  pull_workflow_fit() %>% 
  vip(aesthetics = list(fill = "#1380A1")) + 
  ggtitle("Random Forest Variable Importance") +
  theme_economist() # Variable of importance. 

##### Artificial Neural Network ################################################

##### Data Train and Test sets #################################################
MyDataCleaned2 <- MyDataCleaned[,c(2,3,4,5,6,7,1)] # Moves variable Y to the last column for easier analysis. 

scale01 <- function(x){
  (x - min(x)) / (max(x) - min(x))
} # scales each feature to fall in the [0,1] interval.

MyDataCleaned3 <- MyDataCleaned2 %>%
  mutate_all(scale01) # normalises data before training a neural network.

# Split into test and train sets
set.seed(123)
MyDataCleaned3_Train <- sample_frac(tbl = MyDataCleaned3, replace = FALSE, size = 0.75)
MyDataCleaned3_Test <- anti_join(MyDataCleaned3, MyDataCleaned4_Train)

##### Initial Model ###########################################################
NN1 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train)
plot(NN1, rep = 'best')
# manually compute the SSE 
NN1_Train_SSE <- sum((NN1$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN1_Train_SSE, 4))
# Calculate the test error
Test_NN1_Output <- compute(NN1, MyDataCleaned3_Test[, 1:6])$net.result
NN1_Test_SSE <- sum((Test_NN1_Output - MyDataCleaned3_Test[, 7])^2)/2
NN1_Test_SSE # Comparing the test error of 0.553 to the training error of 1.112 we see that in our case our test error is smaller than our training error.

##### Regression Hyperparameters ###############################################
# 2-Hidden Layers, Layer-1 1-neurons, Layer-2, 2-neuron
set.seed(123)
NN2 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                       hidden = c(1, 2))
plot(NN2, rep = 'best')
## Training Error
NN2_Train_SSE <- sum((NN2$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN2_Train_SSE, 4))
## Test Error
Test_NN2_Output <- compute(NN2, MyDataCleaned3_Test[, 1:6])$net.result
NN2_Test_SSE <- sum((Test_NN2_Output - MyDataCleaned3_Test[, 7])^2)/2
NN2_Test_SSE

# 2-Hidden Layers, Layer-1 1-neurons, Layer-2, 3-neuron
set.seed(123)
NN3 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(1, 3))
plot(NN3, rep = 'best')
## Training Error
NN3_Train_SSE <- sum((NN3$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN3_Train_SSE, 4))
## Test Error
Test_NN3_Output <- compute(NN3, MyDataCleaned3_Test[, 1:6])$net.result
NN3_Test_SSE <- sum((Test_NN3_Output - MyDataCleaned3_Test[, 7])^2)/2
NN3_Test_SSE

# 2-Hidden Layers, Layer-1 1-neurons, Layer-2, 4-neuron
set.seed(123)
NN4 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(1, 4))
plot(NN4, rep = 'best')
## Training Error
NN4_Train_SSE <- sum((NN4$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN4_Train_SSE, 4))
## Test Error
Test_NN4_Output <- compute(NN4, MyDataCleaned3_Test[, 1:6])$net.result
NN4_Test_SSE <- sum((Test_NN4_Output - MyDataCleaned3_Test[, 7])^2)/2
NN4_Test_SSE

# 2-Hidden Layers, Layer-1 2-neurons, Layer-2, 2-neuron
set.seed(123)
NN5 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(2, 1))
plot(NN5, rep = 'best')
## Training Error
NN5_Train_SSE <- sum((NN5$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN5_Train_SSE, 4))
## Test Error
Test_N5_Output <- compute(NN5, MyDataCleaned3_Test[, 1:6])$net.result
NN5_Test_SSE <- sum((Test_N5_Output - MyDataCleaned3_Test[, 7])^2)/2
NN5_Test_SSE

# 2-Hidden Layers, Layer-1 2-neurons, Layer-2, 2-neuron
set.seed(123)
NN6 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(2, 2))
plot(NN6, rep = 'best')
## Training Error
NN6_Train_SSE <- sum((NN6$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN6_Train_SSE, 4))
## Test Error
Test_N6_Output <- compute(NN6, MyDataCleaned3_Test[, 1:6])$net.result
NN6_Test_SSE <- sum((Test_N6_Output - MyDataCleaned3_Test[, 7])^2)/2
NN6_Test_SSE

# 2-Hidden Layers, Layer-1 2-neurons, Layer-2, 3-neuron
set.seed(123)
NN7 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(2, 3))
plot(NN7, rep = 'best')
## Training Error
NN7_Train_SSE <- sum((NN7$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN7_Train_SSE, 4))
## Test Error
Test_N7_Output <- compute(NN7, MyDataCleaned3_Test[, 1:6])$net.result
NN7_Test_SSE <- sum((Test_N7_Output - MyDataCleaned3_Test[, 7])^2)/2
NN7_Test_SSE

# 2-Hidden Layers, Layer-1 3-neurons, Layer-2, 1-neuron
set.seed(123)
NN8 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(3, 1))
plot(NN8, rep = 'best')
## Training Error
NN8_Train_SSE <- sum((NN8$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN8_Train_SSE, 4))
## Test Error
Test_N8_Output <- compute(NN8, MyDataCleaned3_Test[, 1:6])$net.result
NN8_Test_SSE <- sum((Test_N8_Output - MyDataCleaned3_Test[, 7])^2)/2
NN8_Test_SSE

# 2-Hidden Layers, Layer-1 3-neurons, Layer-2, 2-neuron
set.seed(123)
NN9 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(3, 2))
plot(NN9, rep = 'best')
## Training Error
NN9_Train_SSE <- sum((NN9$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN9_Train_SSE, 4))
## Test Error
Test_N9_Output <- compute(NN9, MyDataCleaned3_Test[, 1:6])$net.result
NN9_Test_SSE <- sum((Test_N9_Output - MyDataCleaned3_Test[, 7])^2)/2
NN9_Test_SSE

# 2-Hidden Layers, Layer-1 4-neurons, Layer-2, 1-neuron
set.seed(123)
NN10 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                 hidden = c(4, 1))
plot(NN10, rep = 'best')
## Training Error
NN10_Train_SSE <- sum((NN10$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN10_Train_SSE, 4))
## Test Error
Test_N10_Output <- compute(NN10, MyDataCleaned3_Test[, 1:6])$net.result
NN10_Test_SSE <- sum((Test_N10_Output - MyDataCleaned3_Test[, 7])^2)/2
NN10_Test_SSE

# 2-Hidden Layers, Layer-1 5-neurons, Layer-2, 5-neuron
set.seed(123)
NN11 <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                  hidden = c(5, 5))
plot(NN11, rep = 'best')
## Training Error
NN11_Train_SSE <- sum((NN11$net.result - MyDataCleaned3_Train[7])^2)/2
paste("SSE: ", round(NN11_Train_SSE, 4))
## Test Error
Test_N11_Output <- compute(NN11, MyDataCleaned3_Test[, 1:6])$net.result
NN11_Test_SSE <- sum((Test_N11_Output - MyDataCleaned3_Test[, 7])^2)/2
NN11_Test_SSE

# Bar plot of results for NN models SSE
Regression_NN_Errors <- tibble(Network = rep(c("NN1", "NN2", "NN3", "NN4", "NN5", 
                                               "NN6", "NN7", "NN8", "NN9", "NN10", "NN11", "NN12"), each = 2), 
                               DataSet = rep(c("Train", "Test"), time = 12), 
                               SSE = c(NN1_Train_SSE, NN1_Test_SSE, 
                                       NN2_Train_SSE, NN2_Test_SSE, 
                                       NN3_Train_SSE, NN3_Test_SSE, 
                                       NN4_Train_SSE, NN4_Test_SSE,
                                       NN5_Train_SSE, NN5_Test_SSE,
                                       NN6_Train_SSE, NN6_Test_SSE,
                                       NN7_Train_SSE, NN7_Test_SSE,
                                       NN8_Train_SSE, NN8_Test_SSE,
                                       NN9_Train_SSE, NN9_Test_SSE,
                                       NN10_Train_SSE, NN10_Test_SSE,
                                       NN11_Train_SSE, NN11_Test_SSE,
                                       NN12_Train_SSE, NN12_Test_SSE))

Regression_NN_Errors %>% 
  ggplot(aes(Network, SSE, fill = DataSet)) + 
  geom_col(position = "dodge") + 
  ggtitle("Regression ANN's SSE") + 
  theme_economist() # NN9 best model as lowest train (0.89) and test (1.42) SSE

##### Predict the values for the test set and calculate the MSE ################

# scales data back in order to make a meaningful comparison.
train.r <- (MyDataCleaned3_Train)*(max(MyDataCleaned2)-min(MyDataCleaned2))+min(MyDataCleaned2) # For train set predictions 
test.r <- (MyDataCleaned3_Test)*(max(MyDataCleaned2)-min(MyDataCleaned2))+min(MyDataCleaned2) # For test set predictions 

# Initial Model 
pr.nn <- compute(NN1,MyDataCleaned3_Test[,1:7])
pr.nn_ <- pr.nn$net.result*(max(MyDataCleaned2$Y)-min(MyDataCleaned2$Y))+min(MyDataCleaned2$Y) # scales data back in order to make a meaningful comparison.
caret::RMSE(pr.nn_, test.r$Y) # RMSE 

# 2-Hidden Layers, Layer-1 3-neurons, Layer-2, 2-neuron
pr.nn2 <- compute(NN9,MyDataCleaned3_Test[,1:7])
pr.nn2_ <- pr.nn2$net.result*(max(MyDataCleaned2$Y)-min(MyDataCleaned2$Y))+min(MyDataCleaned2$Y)
caret::RMSE(pr.nn2_, test.r$Y) # RMSE 

##### Model NN9 Predictions ####################################################
plot(NN9, rep = 'best')

# Using the NN5 hyperparameters to construct 10 different ANNs, and select the best of the 10.
set.seed(123) # By setting the same seed, prior to running the 10 repetitions of ANNs, it forces the software to reproduce the exact same NN9 ANN for the first replication. 
final_NN <- neuralnet(Y ~ C1 + C2 + C3 + C4 + C5 + C6, data = MyDataCleaned3_Train, 
                      hidden = c(3, 2), rep = 10)
plot(final_NN, rep = 'best') # The subsequent 9 generated ANNs,use a different random set of starting weights. 
# Comparing the ‘best’ of the 10 repetitions, to the NN%, there is a decrease in training set error indicating we have a superior set of weights.

pr.final <- compute(final_NN,MyDataCleaned3_Test[,1:7]) # Predictions on test set 
pr.nn_final_ <- pr.final$net.result*(max(MyDataCleaned2$Y)-min(MyDataCleaned2$Y))+min(MyDataCleaned2$Y)

caret::RMSE(pr.nn_final_, test.r$Y) # RMSE 
mse(pr.nn_final_, test.r$Y)# MSE
caret::MAE(pr.nn_final_, test.r$Y) # MAE
caret::R2(pr.nn_final_, test.r$Y) # R2

pr.final_train <- compute(final_NN,MyDataCleaned3_Train[,1:7]) # Predictions on train set 
pr.nn_final_train <- pr.final_train$net.result*(max(MyDataCleaned2$Y)-min(MyDataCleaned2$Y))+min(MyDataCleaned2$Y)
caret::R2(pr.nn_final_train, train.r$Y) # R2 train set

# Predicted vs Actual
Final_NN_pred_plot <- ggplot(test.r, aes(test.r$Y, pr.nn_final_)) + 
  geom_point(colour = "#1380A1") +
  geom_abline(color = "red3") +
  labs(title = "Predicted vs Actual Y", y = "Predicted Y", x = "Actual Y") +
  theme_economist()
Final_NN_pred_plot

# Correlation Tests
cor(test.r$Y,pr.nn_final_ )

# importance of each variable
olden(final_NN)

##### Regression vs Random Forest vs Neural Network ############################
# Regression Model metrics  
mse(reg4_pred_test, test$Y) # MSE
caret::RMSE(reg4_pred_test, test$Y) # RMSE 
caret::MAE(reg4_pred_test, test$Y) # MAE
caret::R2(reg4_pred_train, train$Y) # R2 train set
caret::R2(reg4_pred_test, test$Y) # R2 test set
cor(test[, "Y"], predict(model4, test)) # Correlation Tests

# Random Forest Model metrics 
mse(predicted, actual) # MSE
caret::RMSE(predicted, actual) # RMSE 
caret::MAE(predicted, actual) # MAE
caret::R2(predicted, actual) # R2 test set
cor(actual,predicted) # Correlation Tests

# Neural Network Model metrics
mse(pr.nn_final_, test.r$Y) # MSE
caret::RMSE(pr.nn_final_, test.r$Y) # RMSE 
caret::MAE(pr.nn_final_, test.r$Y) # MAE
caret::R2(pr.nn_final_train, train.r$Y) # R2 train set
caret::R2(pr.nn_final_, test.r$Y) # R2 test set
cor(pr.nn_final_ , test.r$Y) # Correlation Tests

# Predicted vs Actual Plots (non customised)
Reg4_pred_plot_2 <- ggplot(test, aes(test$Y, reg4_pred_test)) + 
  geom_point() +
  geom_abline(color = "red3") +
  labs(title = "Regression Model", y = "Predicted Y", x = "Actual Y")  # Regression Model

RF_pred_plot_2 <- ggplot(data_test, aes(actual, predicted)) + 
  geom_point() +
  geom_abline(color = "red3") +
  labs(title = "Random Forest Model",y = "", x = "Actual Y") # Random Forest Model

Final_NN_pred_plot_2 <- ggplot(test.r, aes(test.r$Y, pr.nn_final_)) + 
  geom_point() +
  geom_abline(color = "red3") +
  labs(title = "Neural Network Model",y = "", x = "Actual Y") # Neural Network Model

# For Side by side model comparison 
ggarrange(Reg4_pred_plot_2, RF_pred_plot_2,Final_NN_pred_plot_2 + rremove("x.text"), 
          ncol = 3, nrow = 1)

# Predicted vs Actual Plots (customised)
Reg4_pred_plot_2 <- ggplot(test, aes(test$Y, reg4_pred_test)) + 
  ylim(-200,1900) + 
  xlim(-600, 1900) +
  geom_point(colour = "#1380A1") +
  geom_abline(color = "red3") +
  labs(title = "Regression Model", y = "Predicted Y", x = "Actual Y") +
  theme_economist() # Regression Model

RF_pred_plot_2 <- ggplot(data_test, aes(actual, predicted)) + 
  ylim(-200,1900) + 
  xlim(-600, 1900) +
  geom_point(colour = "forestgreen") +
  geom_abline(color = "red3") +
  labs(title = "Random Forest Model",y = "", x = "Actual Y") +
  theme_economist() # Random Forest Model

Final_NN_pred_plot_2 <- ggplot(test.r, aes(test.r$Y, pr.nn_final_)) + 
  ylim(-200,1900) + 
  xlim(-600, 1900) +
  geom_point(colour = "orange") +
  geom_abline(color = "red3") +
  labs(title = "Neural Network Model",y = "", x = "Actual Y") +
  theme_economist() # Neural Network Model

# For Side by side model comparison 
ggarrange(Reg4_pred_plot_2, RF_pred_plot_2,Final_NN_pred_plot_2 + rremove("x.text"), 
          ncol = 3, nrow = 1)

Section 7. Bibliography 

Alice, M., 2018. Fitting a Neural Network in R; neuralnet package. [Online]  Available at: https://datascienceplus.com/fitting-neural-network-in-r/ [Accessed 4 5 2022].
Beck, M. W., 2018. NeuralNetTools: Visualization and Analysis Tools for Neural Networks. Journal of Statistical Software, 85(11), pp. 1-20.
Bevans, R., 2020. Multiple Linear Regression. [Online]  Available at: https://www.scribbr.com/statistics/multiple-linear-regression/ [Accessed 4 5 2022].
Boehmke, B., 2022. Random Forests. [Online]  Available at: http://uc-r.github.io/random_forests [Accessed 4 5 2022].
Breiman, L., 2002. Random Forests. Machine Learning, 45(1), pp. 5-32.
Brownlee, J., 2018. How to Configure the Number of Layers and Nodes in a Neural Network. [Online]  Available at: https://machinelearningmastery.com/how-to-configure-the-number-of-layers-and-nodes-in-a-neural-network/ [Accessed 4 5 2022].
Frost, J., 2017. R-squared Is Not Valid for Nonlinear Regression. [Online]  Available at: https://statisticsbyjim.com/regression/r-squared-invalid-nonlinear-regression/ [Accessed 4 5 2022].
Frost, J., 2017. Standard Error of the Regression vs. R-squared. [Online]  Available at: https://statisticsbyjim.com/regression/standard-error-regression-vs-r-squared/ [Accessed 4 5 2022].
Frost, J., 2022. Guidelines for Removing and Handling Outliers in Data. [Online]  Available at: https://statisticsbyjim.com/basics/remove-outliers/ [Accessed 4 5 2022].
Frost, J., 2022. Mean Squared Error (MSE). [Online]  Available at: https://statisticsbyjim.com/regression/mean-squared-error-mse/ [Accessed 4 5 2022].
Garrett Grolemund, H. W., 2016. R for Data Science. 1st ed. Sebastopol: O'Reilly Media, Inc..
Hatwell, J., 2016. Artificial Neural Networks in R. [Online]  Available at: https://rstudio-pubs-static.s3.amazonaws.com/214482_7b51dfba415d4b6a8bb304083ce64de1.html [Accessed 4 5 2022].
Heaton, J., 2017. The Number of Hidden Layers. [Online]  Available at: https://www.heatonresearch.com/2017/06/01/hidden-layers.html [Accessed 4 5 2022].
Le, J., 2018. R Decision Trees Tutorial. [Online]  Available at: https://www.datacamp.com/community/tutorials/decision-trees-R [Accessed 4 5 2022].
Lorentz, A., 2013. With Big Data, Context is a Big Issue. [Online]  Available at: https://www.wired.com/insights/2013/04/with-big-data-context-is-a-big-issue/ [Accessed 4 5 2022].
Marvin N. Wright, S. W. P. P., 2021. Package ‘ranger’. [Online]  Available at: https://cran.r-project.org/web/packages/ranger/ranger.pdf [Accessed 4 5 2022].
Nami, Y., 2020. How to choose the best Linear Regression model. [Online]  Available at: https://towardsdatascience.com/how-to-choose-the-best-linear-regression-model-a-comprehensive-guide-for-beginners-754480768467 [Accessed 4 5 2022].
Navlani, A., 2019. Neural Network Models in R. [Online]  Available at: https://www.datacamp.com/community/tutorials/neural-network-models-r [Accessed 4 5 2022].
Peng, Y. D. a. C.-Y. J., 2013. Principled missing data methods for researchers. Springerplus, 2(222).
Pfannkuch, C. W. a. M., 1999. Statistical Thinking in Empirical Enquiry. International Statistical Review, 67(3), pp. 233-265.
Pfannkuch, M., 2011. The Role of Context in Developing Informal Statistical Inferential Reasoning: A Classroom Study. Mathematical Thinking and Learning, Volume 13, pp. 27-46.
Russell, M., 2020. Random forests in a nutshell. [Online]  Available at: https://arbor-analytics.com/post/random-forests-in-a-nutshell/ [Accessed 4 5 2022].
Saxena, A., 2020. How Neural Networks are used for Regression in R Programming?. [Online]  Available at: https://www.geeksforgeeks.org/how-neural-networks-are-used-for-regression-in-r-programming/ [Accessed 4 5 2022].
Scribbr , 2022. When should I remove an outlier from my dataset?. [Online]  Available at: https://www.scribbr.com/frequently-asked-questions/when-to-remove-an-outlier/ [Accessed 4 5 2022].
Spiess, A.-N. N. N., 2010. An evaluation of R2 as an inadequate measure for nonlinear models in pharmacological and biochemical research: a Monte Carlo approach.. BMC Pharmacology, 10(6).
Teng, C., 2020. Visualize Tumor Response Data using ggplot2 R Package through Examples, s.l.: PHUSE.
Wiener, A. L. a. M., 2002. Classification and Regression by randomForest. R News , 2(3), pp. 18-22.
Zach, 2019. What is a Good R-squared Value?. [Online]  Available at: https://www.statology.org/good-r-squared-value/ [Accessed 4 5 2022].
Zach, 2020. How to Build Random Forests in R. [Online]  Available at: https://www.statology.org/random-forest-in-r/ [Accessed 4 5 2022].
Zach, 2020. Regression vs. Classification: What’s the Difference?. [Online]  Available at: https://www.statology.org/regression-vs-classification/ [Accessed 4 5 2022].
Zach, 2021. What is Considered a Good RMSE Value?. [Online]  Available at: https://www.statology.org/what-is-a-good-rmse/ [Accessed 4 5 2022].
















