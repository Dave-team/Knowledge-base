# A/B testing

## Process
### Ideation for A/B tests
- User behavior 
- Where do they drop off? 
- On page surveys around why customers interact with website  
- Focus groups 
- Brainstorming 
- Surveying existing users

### Preparation
Define when a change will be implemented. So pick a main metric and if all else is equal, launch if success metric X is true 

Understand your metrics better by trying to predict how changes will impact them. But if you have to make a prediction beforehand, you’re forced to consider all of the factors. In this example, what do our email conversion rates typically look like? Is it 0.5% of 2% of 5%? Have we tried something similar in the past? Are there other channels that we can learn from? Do we expect this new campaign to have higher or lower conversion rates?

### Metric selection
Define metrics by what the change should be responsible for. Think about the definition of the metric – be very specific – this is one of the harder aspects of A/B testing: click through rate: clicks or unique visitors / number of page views? For example, if a page is slow a user might end up clicking five times. 

You’ll want to focus on a single main metric but you’ll keep an eye out on any further downstream metrics too 

Determine both the metric change you want to see. Also determine invariant metrics – the metrics that shouldn’t change by running the test. For every quantity metric you should also strive to have an associated quality metric.
- Quantity Metric: New Trials
- Quality Metric: Trial to Paid Conversion Rate

Make sure to join two metrics that closely relate. E.g. just looking at visitors might cause anxiety as the number might have dropped. However, you got rid of poor performing affiliates and actually the conversion rate went up. You’ll surely want to show this (again e.g. using a thick black line for visits but a secondary line for the conversion rates in the background 

### Set-up
- Choose subject. In this part, understand how the test is implemented: e.g. randomized at page load might mean that users who reload see something different. Often, the subject should then be people, not events. And to quantify a user, the best proxies are probably cookies and user ids  
- Choose population. This will be an A and a B group. You can consider this further to ensure you pick the same cohort / segment of people to compare. If you selected a few segments to test on, run another test afterwards on the global population to ensure there aren’t any unintended effects. Use a cohort when you want to analyse changes in behaviour of users from a certain history: e.g. retention, activation  
- Calculate required sample size: if the variability of a metric is small, it would take a long time to get significance from a population. However, say the experiment is around site speed. You could then take the population with the 90th percentile in site speed (i.e. slow) and run the test on them - in this case, there should be a significant change. Then you can see whether it’s running a larger experiment here  
- Duration. Whenever you run an experiment, consider running a very small test first or check the first two days of data to ensure things don’t break. Duration is very much depending on how quickly you can reach the required size but you also need to consider when exactly you want the test to run: e.g. not on weekends 

When you run an A/B test, you generally want a dataset with:
- memberId
- When the entered the test
- A/B test name 
- A/B test version (control vs test)

Then, when the A/B test is run, you want to see by user Id, and whether they converted or not and you want to see by when they have converted. 

**Roll-out plan**
- From this sample size, start with a small percentage (e.g. 10%) of users that see the actual feature. This is to make sure that the feature is implemented properly, tracking is in place and nothing essentially breaks – all of this can be tracked in the data 
- Wait a short period of time to make sure that everything is checked and everyone is happy to increase traction on the test group
- Increase the test group now to 50% (and 50% control group)  
- Allow time to collect enough data – this is basically when the test group has hit the required sample size. Analyse the results between test and control group and check for statistical significance. 
- If the test group performs better, increase the total population that will see the test version (not yet 100% as there might always be random factors that influence the data) 
- After a while, measure the difference again between test and control. If test again/still performs better, arrange for the feature to be implemented for the entire user base. 
- Don’t stop the test when you have results – stop the test when the sample size is completed. To do this, don’t peek at the results too often, just make sure that nothing is completely broken. 

### Statistics
- We can assume that the binomial distribution is similar to a normal distribution as we will have a large enough sample size 
- We need to set up a hypothesis test 
- We need to estimate probabilities 
- Calculate confidence intervals 
- Depending on what your distribution looks like, you decide on what summary metric you want to compute. If there is a normal distribution, the mean is fine. It’s it’s left skewed, maybe look at 25% percentile, etc. 
- Sign test: for each day during which the test is run, determine whether the results were statistically significant 

Student t-test for A/B test: print('T-test:\t', ttest_ind(a=control_page, b=experiment_page, equal_var=False))

## Review
Experimentation is not just plotting the mean and see if there is a difference, you need to perform sanity checks:
- Has the test been run correctly, with the appropriate distributions between test and control? 
- Was data capture correct?
- Did we filter correctly? And are only the right people filtered?

And then you want to consier:
- Other than statistical significance, we also need to check for practical significance and see whether it warrants making a change. To test whether a change should be implemented, you can look at the lower bound confidence level and compare that with the change you’d like to see 
- Look at the data by different intervals – e.g. day on day, week on week to spot any trends. Then segment down to see if there is difference in behaviour between segments. Does the result differ segmented? Where can we see the most differences? Device, region, channel, time of day etc. When an A/B test returns s too high p value, don’t be too quick to just neglect the data. Instead, segment the data and see if you can spot interesting findings. E.g. it could be that a test version didn’t work on browser. Then, you’ll want to run the A/B test again excluding the browser that failed and see if its significant
- You’ll also want to check that invariant metrics didn’t change. I.e. when you run an experiment, some variables should be the same across both groups. If this isn’t the case, it's a big flag. In general, anything that happens on the platform prior the step that is being tested will be a good invariant. 
- Are there any second order effects we need to consider? 
- There is also an opportunity to fine tune an experiment prior to launching. For example, if a test is positive for 70% then perhaps you should change the versions prior to rolling out the change 
- What metrics are the most important? 
- What do we learn from the test that we can now experiment further? 

## Other notes
- Cannibalization is when you eat away something from something by doing something else. E.g. starting with PPC might eat away some of your organic clicks
- Keep an A/B testing log to track everything tested historically

**Improvement cycle**
- Identify the goal (transactions, sales leads, etc.)
- Measure your baseline for each of the five conversion funnel steps
- Brainstorm hypotheses and ways to improve the customer experience
- A/B test your hypothesis
- Roll out positive test results to all users

**Types of tests**
A/B testing: Test two or more versions of a page on the website. Split randomly who sees the page and track/measure which one performs better. They are best for big changes to the website or when you want to test different experiences (e.g. a 4 instead of 5 step funnel). 

Multivariate testing: Testing changes to many different elements all at the same time on a page 

Two techniques to MVT testing:
- Full factorial: you test all combinations of pages that might occur as a result of the experiment (e.g. four elements with 4 variants leads to 4x4x4x4 = 256 options
- Partial factorial: you test fewer combinations and infer results for what might happen with other combinations 