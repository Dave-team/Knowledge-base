# Statistics

## Correlations and regression analysis 
Pearson correlation (coefficient) = the degree to which two sets of data are linked. A high correlation is when two sets of data are strongly linked together. A positive correlations happens when the values increase together (ice cream sales in summer). A negative correlation happens when one value decreases as the other increases (exercise vs weight), as such: 

![Correlation graph](https://user-images.githubusercontent.com/28791247/102183539-ebb58580-3ea5-11eb-9ece-7da06111c239.png)

In priciple, the correlation coefficient converts all data so that each observation is represented by its distance (in standard deviation) from the mean. Mean = 66. SD = 5 Obersation = 72. Distance from mean = (72-66) / 5 = 1.2 standard deviations above the mean. This number can be negative – then its below the mean. 

Regression to the mean: if a variable is extreme on its first measurement, it will tend to be closer to the average on its second measurement and it is extreme on its second measurement, it will tend to have been closer to the average on its first. 

**Regression analysis**
In statistical modeling, regression analysis is a set of statistical processes for estimating the relationships among variables. 

Three major uses for regression analysis are: 
- determining the strength of predictors. First, the regression might be used to identify the strength of the effect that the independent variable(s) have on a dependent variable.  Typical questions are what is the strength of relationship between dose and effect, sales and marketing spending, or age and income.
- forecasting an effect. Second, it can be used to forecast effects or impact of changes.  That is, the regression analysis helps us to understand how much the dependent variable changes with a change in one or more independent variables.  A typical question is, “how much additional sales income do I get for each additional $1000 spent on marketing?”
- trend forecasting. Third, regression analysis predicts trends and future values.  The regression analysis can be used to get point estimates.  A typical question is, “what will the price of gold be in 6 months?”

With regression, you want to make sure:
- There is an actual linear relationship. Plot your data first to check this off
- Remember that linear regression demonstrates an association between two variables. It does not proof any causation between variables
- Don’t forget to include important variables. When measuring the effect of golf on health, include the age factor in your analysis (age is making people less healthy, more old people play golf) 
- To understand whether a correlation coefficient found for a sample is a good representation for the population, we need to do some extra statistics. 
  - Calculate the standard error : (1 – correlation coefficient squared) / square root of sample size 
  - A sample correlation is significant at 5% when it exceeds: 2 x SE. The SE is: (1 – 0 squared) / square root of sample size. So: 2 x (1 / square root of sample size)  

**R squared**
When a regression analysis is performed, the output includes R squared. This is a measure of the total amount of variation explained by the regression equation. So if you compare how height influences weight, the R squared will tell you how much of the difference in weight is associated with height alone. This can be 25%. This means that 75% of the difference in weight cannot be ascribed to weight and multiple linear regression analysis needs to be done to understand which other factors influence weight of a person (age, sex, income, etc). 

**Linear regression**
Linear regression= an approach for modelling the relationship between the Y 
and X: y = ax + b. 

In statistics, linear regression is a linear approach to modelling the relationship between a scalar response (or dependent variable) and one or more explanatory variables (or independent variables). The case of one explanatory variable is called simple linear regression. For more than one explanatory variable, the process is called multiple linear regression, or multivariate regression analysis). Linear regression is a basic and commonly used type of predictive analysis.  The overall idea of regression is to examine two things:
- does a set of predictor variables do a good job in predicting an outcome (dependent) variable?
- Which variables in particular are significant predictors of the outcome variable, and in what way do they impact the outcome variable? 
	
Regression analysis often uses a methodology called ordinary least squares (OLS). OLD fits the line that minimizes the sum of the squared residuals. Residual is the vertical distance between regression line and the observation. What happens is that the formula takes the square of each residual and then adds them up. This also means that more weight is given to observations that are from the regression line – these are the outliers). By doing this, ordinary least squares gives us a line that minimizes the sum of the squared residuals and with that is gives us the best description of a linear relationship between two variables. The regression equation then is: y=ax+b. y is a independent variable, a is the y-intercept of the line (at x=0), b is the slope of the line (the regression coefficient) and x the dependent variable

## Variables
The dependent variable is the variable that depends on other factors. The variables used to explain the dependent variable are the independent or control variables. 

Regression analysis helps understand how the value of the dependent variable changes when any one of the independent variables is varied. The regression coefficient tells us: one unit increase in the independent variable is associated with an x increase in the dependent variable. 

Two types of variables: category and quantitative. 
Category variable: any variable that involves putting individuals into categories (e.g. brand of shoe). Two types of category variables: nominal and ordinal. Nominal variable: you give the variable a name. Ordinal variable: you can order the variable and it is generally a comparative value (e.g. bad/good). 
Quantitative variables: variables you can assign a numeric value to. These are discrete (‘whole number’: e.g. you can have 2 kids, not 2.5). They can also be continuous (e.g. height – you can be any mm in height). Continues variables are measured, discrete variables are counted 

## Probability distributions
A distribution is usually quite symmetrical: most observations are recorded near the centre of the range of values and gradually thinning out towards the extremes. When the most observations are not in the middle, we say that the distribution is skewed. 

A normal distribution has the shape of a bell, is perfectly symmetrical and the mean is in the center. 
![Normal distribution](https://user-images.githubusercontent.com/28791247/102185868-a6935280-3ea9-11eb-9b40-a71f474ffa9a.png)

When looking at statistical difference between two means, we are basically plotting a distribution of the differences between the two means. This is a normal distribution and usually, the mean here would be zero (this basically equals the null hypothesis). 
When the difference in means is more than 2 SE from the 0 mean of the distribution of the differences of sample means, we can reject the null hypothesis (at 95% confidence interval). If the difference is less than 2 SE, it is more likely that the difference just comes from sampling variations. Note that the SE in these cases is the combined standard error: square root of SE 1 squared + SE 2 squared 

As a general rule, you always need to think about whether you are dealing with similar distributions. E.g. comparing one group on drugs vs another not on drugs will not show the same distribution when e.g. performance is measured. In this case, you might need to normalize the data, look at mean differences, as well as at standard deviation differences. When you assume a similar distribution, you are saying that the different groups are sufficiently similar in standard deviation. When the distributions are significantly different, you might not need to look at the mean – it is clear that there is a difference and you can leave it at that 

A probability distribution species the relative likelihoods of all possible outcomes. 
Random variable = a function that assigns a real number to each outcome in the probability space. 

There are two major classes of probability distributions: discrete and continuous. 
A discrete random variable has a finite (or countable) number of possible values. 
Different types of discrete distributions:
1. Bernoulli: a Bernoulli random variable takes the value 1 with probability of p and the value 0 with the probability of 1-p. It is often used for binary experiments, such as a coin toss. 
2. Binomial: a binomial random variable is the sum on n independent Bernoulli random variables with parameter p. It is used to model the number of successes in a specified number of identical binary experiments (such as 5 coin flips). 
3. Geometric: a geometric random variable counts the number of trials required to observe a single success, where each trial in independent and has success probability p. E.g. how many times to roll a dice before we observe a six? 
4. Poisson: a Poisson random variable counts the number of events occurring in a fixed interval given that these events occur with an average rate. Used to e.g. model meteor showers and goals in a football game. The timing of the next event is completely independent of when the previous event happened
5. Negative binomial: A negative binomial random variable counts the number of successes in a sequence of independent Bernoulli trials with parameter p before r failures occur. For example, this distribution could be used to model the number of heads that are flipped before three tails are observed in a sequence of coin tosses.

A continuous random variable takes on an uncountable infinite number of possible values. There are different types of continuous distributions: 

1. Uniform: The uniform distribution is a continuous distribution such that all intervals of equal length on the distribution's support have equal probability. For example, this distribution might be used to model people's full birth dates, where it is assumed that all times in the calendar year are equally likely.
2. Normal: The normal (or Gaussian) distribution has a bell-shaped density function and is used in the sciences to represent real-valued random variables that are assumed to be additively produced by many small effects. For example the normal distribution is used to model people's height, since height can be assumed to be the result of many small genetic and environmental factors. A normal distribution can be applied when the data are symmetrical around their mean value  
3. Student T: Student's t-distribution, or simply the t-distribution, arises when estimating the mean of a normally distributed population in situations where the sample size is small and population standard deviation is unknown.
4. Chi squared: A chi-squared random variable with k degrees of freedom is the sum of k independent and identically distributed squared standard normal random variables. It is often used in hypothesis testing and in the construction of confidence intervals.
5. Exponential: The exponential distribution is the continuous analogue of the geometric distribution. It is often used to model waiting times.
6. F: The F-distribution, also known as the Fisher–Snedecor distribution, arises frequently as the null distribution of a test statistic, most notably in the analysis of variance.
7. Gamma: The gamma distribution is a general family of continuous probability distributions. The exponential and chi-squared distributions are special cases of the gamma distribution.
8. Beta: The beta distribution is a general family of continuous probability distributions bound between 0 and 1. The beta distribution is frequently used as a conjugate prior distribution in Bayesian statistics.

## Reading statistical terminology 
![Stats terminology](https://user-images.githubusercontent.com/28791247/102183429-bb6de700-3ea5-11eb-87bd-be4d0c084fa2.png)
Σ= add all numbers up (a.k.a. the summation sign)
N= go to this value (end value)
i=1 = start at this value 
Once you have all the variances per number, you have to divide them by the amount of values, respresented here by 1/N 

## Hypothesis test
General notes
- Always make sure there is a test and a control group. They should be drawn from the same pool to ensure a like for like comparison  
- Once the test is run, make sure to check whether the groups were random and distributed evenly 
- Whenever you run an experiment, make sure the sample size can actually result in a statistically significant results  
- Bootstrapping means to take many small samples (it’s a resampling technique) within the actual population and making a distribution out of e.g. the mean of those bootstrapped samples. This is only required when you want confidence intervals 
- The way to generate a distribution assuming the null value is true is done by using permutation sampling: shuffling the test and control results and doing this e.g. 10,000 times. A permutation test is an option, so are t and z tests. With large samples, no difference between z and t test. In 99% they are fine – it saves a lot of computing power over doing an actual permutation test. When we compare groups that are not from the same distribution, we fundamentally cannot use a permutation test. To get to the actual p value from the permutation test, you sum (the amount of times the permutation replicates mean is greater than or equal to the actual difference in means) / how often you drew the permutation replicates 

Process
1. Set up your null (the observed data is due to chance - H0: μ1 = μ2) and alternative hypothesis (observations are the result of a real effect). This will clearly indicate what you’re testing for. Generally, include that you’re aiming for a 95% confidence interval (degree of significance in which we accept or reject the null hypothesis 
2. Collect the data between test and control 
3. Measure the difference (probably most often this is the difference in the mean)
4. Run a test that returns the p-value. This can be an independent t-test when you compare numbers, or a chi-square test when you compare proportions between two variants (e.g. conversion rate analysis from an A/B test) 
5. The P-value indicates the probability, assuming the null hypothesis is right (which usually means no difference between test and control group) that the result of that null hypothesis test returns at least a result as extreme as your sample. In other words, it is the probability that you would get the same results if the groups were exactly the same 
6. If the P-value is < 0.05, you can say that in fact there is a significant result between test and control. A small p value indicates strong evidence against the null hypothesis. It also says that you’re more than 95% sure that the null hypothesis is wrong. In this case, you want to look a bit deeper
7. Look at the distribution between the two groups, does this look different at all? This is good to present to stakeholders. 
8. If you want to conclude with certainty what the result would be, should the company run a similar result again, look at by how much the lesser performing group needs to increase to get to a p-value >0.05. This shows you up until which point you can be confident with the data that if you run it again, you are sure you would get the same results. 
9. Finally, also calculate the actual confidence intervals. You’ll want to calculate these intervals by bootstrapping the results many times, otherwise they probably will be too wide spread. 

**One vs Two tailed hypothesis test**
A two tailed hypothesis test is looking at whether something is true OR whether something different is true (e.g. weight is more OR less). Essentially, this is to identify whether something is different on either side of the distribution. A one tailed hypothesis test on the either hand will only look at one side of the curve. Right (higher) or left (lower). The difference here lies in whether you are looking at a full 5% from either side, or 2.5% from both sides, assuming a 95% significance level 

**One-sample tt test**
Probably one-sample tt test is the most basic and useful hypothesis tests. It can determine if the sample mean is statistically different from a hypothesized population mean for continuous random variables. To use one-sample tt test some assumptions are usually required. For example, the observations should be independent. Another assumption is the normality, i.e., the population should be normal distributed

Two-sample tt test is a bit of more complex than one-sample tt test. There are two types of tt tests commonly used in practice, i.e. paired tt test and unpaired tt test.

## Sample size testing
- The sample size calculation depends on the actual thing you want to measure (i.e. all different hypothesis testing methods will use a different calculation). 
- When you expect a small difference in your metric, you’ll need a large sample size and vice versa. This is because a small change can more easily be overshadowed by randomness 
- Generally, you need a baseline conversion rate, new conversion rate, a power, and a confidence interval to get a required sample size for analysis 
- Depending on: 
  -	Power
  -	Baseline conversion
  -	Minimal detectable effect

## More on P values / significance
Standard error = measures the dispersion of the sample means. How tightly do we expect the sample means to cluster around the population mean? So whereas the standard deviation measures dispersion in the underlying population, the standard error measures the dispersion of the sample means. Calculation = SD / square root of n (size of sample) 

Comparing two groups: 
- Calculate the difference between their means
- Divide the difference in mean by the standard error. E.g. if it's 3x: The normal distribution says that 99.7% of all cases fall within 3 standard errors of the population mean. That means that you can say with 99.6 confidence level that this sample is not drawn from the population mean. 
- A good way to visualize this significance is by seeing whether the confidence intervals overlap at any point. 

## Probability
The probability of multiple events happening at the same time or sequential (in a row): = P = P(A) x P(B)

The probability of one event or another event happening: P = P(A) + P(B)

Probability allows us to calculate expected value. E(x) = P(X1) + P(X2). This represent each possible outcome and the probability in which they would occur. If the expected value or outcome is greater than the initial investment, do the thin 

**Probability density function**
A probability density function (PDF) is a function whose value at any given sample (or point) in the sample space (the set of possible values taken by the random variable) can be interpreted as providing a relative likelihood that the value of the random variable would equal that sample. In a more precise sense, the PDF is used to specify the probability of the random variable falling within a particular range of values, as opposed to taking on any one value.

A PDF plots plots the different outcomes on the x axis and the expected probability of each on the y axis. The weighted probabilities – will add up to 1. 

**Cumulative distribution function **
In probability theory and statistics, the cumulative distribution function (CDF) of a real-valued random variable X is the probability that X will take a value less than or equal to x.

## Glossary 
- Central Limit Theorem - The CLT states that the sample mean of a sufficiently large number of random variables is approximately normally distributed. You get to this distribution essentially by bootstrapping. 
- Mean (μ ) = average and calculated in the same way. In the long run, the mean equals the expected value. Only looking at the mean is dangerous as it is prone to the effect of outliers. If there is reasonable evidence that you’re data set includes strong outliers that will influence the mean value significantly, look at the median instead. 
- Median ( )= middle value of a set of data containing an odd number of values, or the average of two middle values of a set of data with an even number of values. Example: 3,5,12, so the middle value is 5 (simply always the middle number in a set of data). If there is an even number of values, it is the average of the two most middle values 
- Range = difference between highest and lowest values within a set of numbers 
- Mode (Mo)= value which occurs most frequently
- Standard deviation (σX) = gives an idea of how close the entire set of data is to the average value. Data sets with a small standard deviation have tightly grouped, precise data. It is the square root of the variance. Calculation: SD = √(Variance). Once you the mean as well as the standard deviation of a population or sample, you have a lot. Assuming the data in normally distributed, you can infer that 34% of the cases lie between mean – 1SD and another 34% of the population/sample lie within the mean +1SD
- Variance  (σ2 )= measures how far a set of numbers is spread out. A small variance indicates that the data points tend to be very close to the mean and hence each other. Calculation: take the actual data and subtract from it the mean (average). The variance is calculated by (value-mean)². 
- A confidence interval gives upper and lower bounds on the range of parameter values you might expect to get if we repeat our measurements. Meaning: your confidence level can be 95%. Then, your confidence interval are the values at the 97.5% and the 2.5% percentile. You are 95% sure that the results are within the outer ends of these intervals when you do the same test again. 
- Permutation sampling is when you combine both the test and control results, and shuffle them around randomly. It is meant as a way of simulating a null-hypothesis. Instead, just used actual practical hypothesis tests, such as the t-test. 
- Statistical inference is when you take a sample of an actual population. It is also defined as observing some pattern or outcome and then using probability to determine the most likely explanation for that outcome. 
- Descriptive statistics is about taking data of the whole population and doesn’t require sampling. With statistical inference, we draw probabilistic conclusions about what we might expect if we collect the same data again. 
- Type I error: When we reject the null hypothesis, although that hypothesis was true.  Type I error is denoted by alpha.  In hypothesis testing, the normal curve that shows the critical region is called the alpha region.
- Type II errors: When we accept the null hypothesis but it is false.  Type II errors are denoted by beta.  In Hypothesis testing, the normal curve that shows the acceptance region is called the beta region.
- One sample test compares one set of data to a single number. Seems like permutation sampling is used for this More often, we have two sample tests, in which we compare two sets of data (e.g. A/B test) 
- A percentile (or a centile) is a measure used in statistics indicating the value below which a given percentage of observations in a group of observations falls. For example, the 20th percentile is the value (or score) below which 20% of the observations may be found. The 25th percentile is also known as the first quartile (Q1), the 50th percentile as the median or second quartile (Q2), and the 75th percentile as the third quartile (Q3). Percentiles are especially useful when trying to determine whether something is good or not. E.g. an exam score can only be good or bad based on in what percentile it is (because a 9 can still be bad if the test was easy and everybody else got a 10)
- Probability allows us to analyze chance events. It indicates how likely an event will occur. Probability lies between 0 and 1, where 0 indicates impossibility and 1 indicates certainty. A good example is the coin flip, where both head and tails have a probability of 0.5, or 50%. Probability is the study pf events and outcomes involving an element of uncertainty 
- Random variable: When we assign numbers to outcomes (e.g. 0 for tails, 1 for head)
- The expectation is a number the attempts to show the long run average of many independent samples from the given distribution. E.g. the mean of a large sample of dice rolling will return 3.5 (1+6 / 2). This is the expectation. 
- A distribution is nothing more than a representation of the data. After you have looked at the summary statistics, this is the next place to look at as here you would find possible outliers in the data 
- Desriptive statistics: summarize or describe the observations
- Inferential statistics: using observations as a basis for making estimates or predictions 
- Population = all the cases/situations we want to consider
- Sample = small selection from within the population. Always make sure the sample selected is random to avoid any bias 
- Variable = characteristics among individuals 
- Observation = each measurement for each individual in the sample 

## Technical
Bootstrapping options: dc_stat_think: draw_bs_reps. This same module also allows bootstrapping on linear regression using a different function
Another one for bootstrapping: sklearn.utils.resample
