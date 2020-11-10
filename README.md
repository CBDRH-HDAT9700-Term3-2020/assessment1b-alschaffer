# General feedback

I will be reiterating some of the comments Mark made on Assessment 1a as they also apply to Assessment 1b.

### Comments on working with R Projects, GitHub, and reproducibility

* You can suppress unwanted code, messages and warnings in your R markdown file using the `echo = FALSE`, `message = FALSE` ad `warning = FALSE` options respectively. These can be set for individual chunks or globally for all chunks.

* It is good practice to comment your code.

### Comments on presentation and interpretation

* You should only quote decimal places to the degree they are meaningful. If you give 4 decimal places, this suggests that you were able to measure the data to that level of precision. If you aren’t sure, look at the original data and how it was presented, and use the same number of decimal places, or one more at most. Percentages should be given to one decimal place at most, or no decimal places if the number of observations is <100.

* It is generally insufficient to print statistical output without adding some sort of comment or brief interpretation. It is important to show that you understand what you have done and why, by justifying your analytic choices and providing evidence to back up any statements. Evidence can mean referring to a relevant plot or figure, or including estimates and measures of variability (e.g. 95% CIs) to accompany your text.

### Question 1 (Plot)

* This question was mostly well done. Make sure to think about whether it is better to have both series on the same plot, or different plots. By having two series on very different scales on the same plot, it can make it difficult to visualise any changes. In this cases, two separate plots, or one plot with two panels, was better than one plot.

* Always have descriptive labels and title, or add a legend if necessary. Figures should stand alone as much as possible so you don’t have to read the text to understand them.

### Question 2 (Describe the time series) 

* Make sure to highlight key findings from your output – it isn’t enough to just provide the raw output. For instance, if there is seasonality, describe it – which months have the highest/lowest value? If there are outliers, state the dates and provide the values. If possible, relate any observations to the intervention of interest (e.g. how did the time series change after the intervention?). 

* While ACF/PACF plots and tests of stationarity and/or autocorrelation weren’t necessary for this question, they are also useful ways to get an understanding of your data and what the most appropriate analytic approach might be.

* Everyone produced decomposition plots, but seasonal plots (i.e. using `ggseasonplot()`) and summary statistics (i.e. using `summary()` and `tapply()`) are also useful for describing and understanding the data.

### Question 3 (Segmented regression)

* The most important thing for this question was not just to provide output, but to summarise and comment on the most important bits from the output, and to well justify your choice of model. 

* Don't forget that with all linear regression it is important to test the model assumptions (that is, that the residuals are normally distributed with constant variance and no autocorrelation) using residual plots. The test of residual autocorrelation using a test such as the Ljung-Box test is especially important for timeseries data.

### Question 4 (ARIMA)

* For this question, there were several possible ARIMA models that fit the data; the important thing is to check the model fit using residual plots (e.g. with `sarima()`).

* Usually d and D should be the same, either d=1 and D=1, or d=0 and D=0. 

* You could have chosen either the segmented regression or the ARIMA model as the best option, as long as you gave a good reason. 

* Many students compared the segmented regression model to the ARIMA Model using AIC. Note that one requirement of comparing models using AIC is that they have the same observations – given that with ARIMA, when you difference the data you “lose” some observations, this means that the segmented regression and ARIMA models cannot be compared with AIC (see here for more information: https://robjhyndman.com/hyndsight/aic/). Thus you must rely on the underlying theory for why you would prefer segmented regression over ARIMA or vice versa.

### Question 5 (Interpretation)

* A good conclusion should provide all parameter estimates and their 95% CIs, and then interpret what they mean (don't just provide output). In this case, you should comment on the pre-intervention slope (if using segmented regression), as well as the step change and change in slope, and what they mean. 

### Question 6 (Negative control series) 

* Many people were able to give an example of a negative control but had more difficulty in understanding how they help with causal inference. The prereading by Shadish, Cook and Campbell has a section on negative controls, and there is also the paper by Lopez Bernal et al ([*The use of controls in interrupted time series studies of public health interventions*](https://academic.oup.com/ije/article/47/6/2082/5049576)) that I linked to in the tutorial. 
