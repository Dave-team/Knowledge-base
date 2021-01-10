# EDA

## Process
**Define the problem**
This should be a simple question to provide direction. Keep in mind when defining the problem: 
- The question can be qualitative, but the approach, must be quantifiable
- What am I looking for?
- What do I want to learn?
- Alright to be exploratory (and the best analysis often are)

From there: 
- Determine what defines success, and to which degree
- Brainstorm metrics to visualize / calculate. Clearly define the metric calculation here. For example: if we want to plot conversion rate, what is the data period and what are the numerators / denominators? 

**Prepare the data**
First, prepare the data for exploration. This is also called data wrangling and it’s where we clean up the data which make it easier to manipulate, visualize and model our data  

The goal is to have a tidy dataset to work with. A tidy dataset: 
- Each variable forms a column
- Each row is an observation
- Each table stores a single type of observation type

**Explore data**
- Run the summary statistic. Look at total counts, nulls, uniquids, duplicates.
  - Look out for outliers. E.g. 99% is 100 but then max is 9000. This is an outlier
  - Check is the data makes sense: e.g. negative unit price?
  - Are value null? Find out why and consider removing them
  - Are there inputs by human? Clean those up
- Think hard about the dataset and identify which combinations of values would be weird – e.g. chargeoff but not aged enough. Or debt sold but not charged off. Check for these possibilities. 

**Visualize the data**
- For numeric values, plot a histogram – what does the distribution look like? This will indicate whether the dataset has outliers. You’ll want to look into the details of these outliers and then make a decision as to whether they. Never just plot an average as it holds surprisingly little value  
- should be transformed / deleted 
- Plot the data over time – can we see any trends (focus on overall trend – better or worse, and any peaks / throughs – why do these happen?) ? Relate what we see back to what has been happing in the business – this is where business context is extremely important. Plotting over time can be: 
  - Period (weekly/monthly/daily) with a moving average
  - By day of week / day of month / hour of day  
- Segment the data (after plotting the aggregate data to see any high level trends): 
  - Country 
  - Channel
  - Device
  - Sex
  - Browser
  - Specific user attribute 
  - Cohort
  - Specific user behaviour (e.g. new vs existing customers)
  - Look at top performers 
  - Price range
  - Performance between different steps in the funnel
- Plot a correlation matrix where relevant

**Sanity check the data**
After the data is cleaned, do another round of data checking to validate you’ve done a good process. E.g.: 
- Why are values missing?
- Why do I see a peak at point X?
- What explains the correlation between two variables?
- How could we segment further?
- What other metrics could be relevant here?

## General tips 
- First, always check your data is clean and you agree with the output of your sample. You should not assume things – think back to the case study: a beer with alcohol % of 57% - is this possibly an outlier in the data set? 
- Check for massive outliers. This can e.g. be done by printing the percentiles. Also simply have a look at the summary statistics of your data set. 
- A good idea is always just to quickly check the standard deviation as well. Do you see anything odd? 
- Sometimes, you might just want to get of outliers if they are too far off to be any helpful to your analysis 

Helpful tips: 
-	As you analyse data, keep a trace of the findings. E.g 
  - Formatting of cancelled orders (big C in front of description) 
  - Weird descriptions in description field 
  - Non existing customer IDs
-	Fairly early in the process, identify the main drivers for the analysis. E.g. if some marketing channels barely drive visits to the website, it’s probably fair not to include them in the analysis 
-	Make use of statistical significance 
-	When plotting numbers, combine absolute values with ratios. 1/3 is 33% but it’s still irrelevant 
-	Be careful with ratios. A change in a ratio can be guided by massive shifts in the values you’re calculating - so throw in the raw numbers
-	The simplest solution is often best (and the one you should try first)
-	A good way to analyse data is to bring in bank holidays for example as that will impact the numbers 
- Before you even touch machine learning algorithms, look at the data. Graph it, look at individual customers, etc. Get very familiar with it .Pretend someone will quiz you on it later -- they probably will. 'What's the average value of X?' 'How long until the average customer does Y?'
- Preface data preparation with a data analysis phase that involves summarizing the attributes and visualizing them using scatter plots and histograms. 