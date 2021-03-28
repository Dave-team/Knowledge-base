# Data Science 

## Notes from Papier
Think about what variable you use. What could have an impact on e.g. acquisitions? Organic channels could Impact paid display acquisitions 

Once you have data for some channel, compare the model against other channels too. Does it seem realistic across channels? 

Understand the channels deeply before attempting to draw conclusions. Don’t measure acquisitions if you use channels that focus on remarketing. Similarly, make sure to focus on right targeting 
 
Think about the results - is it realistic? If you say that CPA is £3, then that’s simply wrong. That’s fine, that can be communicated but the intention of the meeting is different 

As long as R squared is low - the data shouldn’t be trusted. Again, that’s fine - find ways to improve it 


## Principles
- The point of data science is to make informed decisions. Decisions to do something. Say you develop a great churn model. If a customer is marked as 'risk of churn,' what are you going to do? Along those lines, think about how this hypothetical very good model is going to work in the actual workflow of the business. How often is it going to be run? Who is running out? Who is reading the output? What are they doing with the output? This needs to be thought out.

## Time series forecasting 
In a time series, there are often properties:
- Level: When you read about the “level” or the “level index” of time series data, it’s referring to the mean of the series.
- Seasonality: is there a periodic pattern? If there are regular and predictable fluctuations in the series that are correlated with the calendar – could be quarterly, weekly, or even days of the week, then the series includes a seasonality component
- Trend: is there a consistent upward or downward trend?
- Noise: are there any outliers or missing values not consistent with others? All time series data will have noise or randomness in the data points that aren’t correlated with any explained trends. 
- Cycle: Repeating periods that are not related to the calendar. This includes business cycles such as economic downturns or expansions 

Decomposition is the deconstruction of the series data into its various components: trend, cycle, noise, and seasonality when those exist.

**Forecasting methods**

*Simple moving average (SMA)*. The way a SMA is calculated is that it takes the subset of the data mentioned in the moving average model description, adds together the data points, and then takes the average over the subset of data. 

*In a cumulative moving average*, the mean is calculated from a data stream up to the current data point, which gets updated with each new data point that comes in from the stream.

Unlike the simple moving average that moves forward one data point and drops the oldest data point to take the average from, an *exponential moving average (EMA)* uses all data points before the current data point. Weights are associated with each data point and those further away from the current point are given less weight, in an exponentially decreasing fashion, than the data points closest to the current point.

*The Autoregressive Integrated Moving Average*, or ARIMA model, is a univariate linear function that is used for predicting future data points based on past data. 

**Prophet**
Facebook open sourced prophet as a way to forecast. The general flow is to fit the data then predict the future time series. With forecasting, you often want to change to a log scale. As part of prophet, it’s also really easy to plot components, which show the overall trend, weekly and yearly trends. Prophet also allows us to include information around seasonal data, i.e. holidays or releases (anything that would cause increase or decrease in volume can be marked as a holiday). 

## Machine learning process
**Define the problem**
Step 1: What is the problem? Describe the problem informally as if describing it to a friend. Then define it formally and list assumptions and similar problems.

Step 2: Why does the problem need to be solved? List your motivation for solving the problem, the benefits a solution provides and how the solution will be used.

Step 3: How would I solve the problem? Describe how the problem would be solved manually to flush domain knowledge: 
- What do we want to know or what problems are we trying to solve? What is the context?
- What are our hypotheses?
- What are our metrics of success?
- What results are you expecting to get back, and what would you do if you got the reverse answer?
- How much confidence do you need?

**Prepare data**
Describe in detail each attribute and relationships between attributes. This forces to think about the data in the context of the problem before it is lost to the algorithms. 

The actual data preparation process is three step as follows:

Step 1: Data Selection: Consider what data is available, what data is missing (we might be able to simulate/derive) and what data can be removed.
Step 2: Data Preprocessing: Organize your selected data by formatting, cleaning and sampling from it.
Step 3: Data Transformation: Transform preprocessed data ready for machine learning by engineering features using scaling, attribute decomposition and attribute aggregation.

Data Acquisition and Cleaning / Exploratory data analysis: see EDA file 

**Feature engineering**
Decide on features/variables that serve as input for your model. Note that all features should be numerical, meaning we might need to convert some rows to columns with 0s and 1s Consider:
- Fixed variables (age, gender, lifestyle)
- Aggregated variables (e.g. total spent)
- Evolutions (what is the trend of the spending – more last year vs this year?)

Also define the target variable – which is the goal of what we try to predict. Then arrange the data into a features matrix and target vector (this means that we we separate the feature matrix from the column that has the target)

**Pick a model**
This is depending on the goal – normally, we’ll try different models. Here, we also need to select the hyperparameters of the model. Typically run 10-20 standard algorithms from all the major algorithm families across all the transformed and scaled versions of the dataset I have prepared. The goal of spot checking is to flush out the types of algorithms and dataset combinations that are good at picking out the structure of the problem so that they can be studied in more detail with focused experiments.

Here we often look at two plots: 
- Validation curve 
- Confusion matrix 

**Split the data**
We want to split data between: 
- Training data set – this is used to ‘learn’
- Test data set – this is used to apply what has been learned on new data 
- Holdout data set. This is used for evaluation 

**Train the model to the data** 
Train a model by looking at historic data. 

**Test the data**
Now we apply the model to the test data. A useful approach here is to test on existing customers we know the data profile of. We have a model that e.g. predicts churn. We then test this model on old campaigns – would we have been able to predict who would churned?

**Model validation**
In the evaluation step, we use the model on the holdout data set. 

To mediate the risk of overfitting, we usually use cross-validation to assess how accurately a predictive model is able to predict for unseen data. In cross validation, we divide the holdout data in random partitions and train the data on each partition and then calculate the average prediction accuracy. 

Also use statistical significance tests to flush out meaningful results from noise. Box-plots are very useful for summarizing the distribution of accuracy results for each algorithm and dataset pair.

**Model improvement**
After you now the effectiveness of your model, you need to understand how to make it better. There are a few options: 
- Use a more complicated/more flexible model
- Use a less complicated/less flexible model
- Gather more training samples
- Gather more data to add features to each sample
- Tune the parameters or the model

In summary, the process of improving results involves:
- Algorithm Tuning: where discovering the best models is treated like a search problem through model parameter space.
- Ensemble Methods: where the predictions made by multiple models are combined.
- Extreme Feature Engineering: where the attribute decomposition and aggregation seen in data preparation is pushed to the limits.

**Productionizing the model**
After a model is built that works, it needs to be put in production. This is often done in managed (serverless) tools. And we can deploy in batch or live. In a batch deployment, a model is applied to a large collection of records, and the results are saved for later use. This is different from live approaches which apply models to individual records in near real-time. Usually, you’ll want to make the results of the model available to an endpoint, so that they can be used by an application. 

When doing staged rollouts testing, you’ll want to test to account for the biases in user groups with staged rollouts, we measured key metrics for the experiment groups before and after the new release, and compared the pre-experiment differences between these groups. We use two approaches for this analysis: 
- Time-Series Analysis to estimate absolute changes in key metrics using aggregate-level data
- Difference-in-Differences Estimation to perform significance testing on a collection of metrics using user-level data.

**Maintenance** 
Data changes quite often. Because of this, a data scientist must regularly review their model’s performance.

## Categories of machine learning
**Supervised** 
Supervised learning is model creation where the model describes a relationship between a set of selected variables (attributes or features) and a predefined variable called the target variable. The model estimates the value of the target variable as a function of the features. So, for our churn-prediction problem we would like to build a model of the propensity to churn as a function of customer account attributes, such as age, income, length with the company, number of calls to customer service, overage charges, customer demographics, data usage, and others.

Methods: 
- Classification
- Regression

**Unsupervised**
Unsupervised is when there is no specific target or purpose set. ‘Do our customers naturally fall into different groups?” There is nothing concrete as an outcome we measure against.	

Methods: 
- Clustering 

## Data science methods
### Classification 
Predict, for each individual in a population, which of a (small) set of classes this individual belongs to. E.g. “which customers are likely to respond to a given offer?” Or “Which customers are likely to churn”. For a classification task, a data mining procedure produces a model that, given a new individual, determines which class that individual belongs to.

A closely related task is scoring or class probability estimation. Here, we would give each item a probability score of belonging to a class (e.g. individual X is 80% likely to churn) 

**Naive Bayes**
A group of extremely fast and simple classification algorithms that are often suitable for very high-dimensional datasets. 

Bayes’ Theorem provides a way that we can calculate the probability of a hypothesis given our prior knowledge

Naive Bayes is a classification algorithm for binary (two-class) and multiclass classification problems.
It is called naive Bayes or idiot Bayes because the calculation of the probabilities for each hypothesis are simplified to make their calculation tractable. Rather than attempting to calculate the values of each attribute value P (d1, d2, d3|h), they are assumed to be conditionally independent given the target value and calculated as P (d1|h) × P (d2|h) and so on. This is a very strong assumption that is most unlikely in real data, i.e. that the attributes do not interact.

Perhaps the easiest naive Bayes classifier to understand is Gaussian naive Bayes. In this classifier, the assumption is that data from each label is drawn from a simple Gaussian distribution. Usually, this is the model to start with before exploring whether improvements can be found through more sophisticated models 

Another useful example is multinomial naive Bayes, where the features are assumed to be generated from a simple multinomial distribution. The multinomial distribution describes the probability of observing counts among a number of categories, and thus multinomial naive Bayes is most appropriate for features that represent counts or count rates.

Naive Bayes can be extended to real-valued attributes, most commonly by assuming a Gaussian distribution. This extension of naive Bayes is called Gaussian Naive Bayes. Other functions can be used to estimate the distribution of the data, but the Gaussian (or Normal distribution) is the easiest to work with because you only need to estimate the mean and the standard deviation from your training data.

Bayes are an example of generative classification

**Support Vector machines**
rather than modeling each class, we simply find a line or curve (in two dimensions) or manifold (in multiple dimensions) that divides the classes from each other.

Linear SVM works by maximizing the distance between classes and drawing a line down the middle. New data is categorized by how it falls along that line. Non-linear SVM is used for more complex functions (like those with exponents) to more accurately find the widest point between data.

SVMs are an example of discriminative classification

The Maximal-Margin Classifier is a hypothetical classifier that best explains how SVM works in practice. The numeric input variables (x) in your data (the columns) form an n-dimensional space. For example, if you had two input variables, this would form a two-dimensional space. A hyperplane is a line that splits the input variable space. In SVM, a hyperplane is selected to best separate the points in the input variable space by their class, either class 0 or class 1. In two-dimensions you can visualize this as a line and let’s assume that all of our input points can be completely separated by this line. Then, whether a value falls above or below the line determines the class of the instance. 

**Random forests**
Random forests are an example of an ensemble method, meaning that it relies on aggregating the results of an ensemble of simpler estimators.

Random forests are an example of an ensemble learner built on decision trees. These are what you’d expect: a tree based on binary decisions. Random forest can be used for both classification and regression 

Random forest Simply put, a random forest is a group of decision trees that all have the same response variable, but slightly different predictor variables. The output of a random forest model is calculated by taking a “vote” of the predicted classification for each tree and having the forest output the majority opinion.  

Essentially, random forests involve bagging, which is like bootstrapping – this is why random forests is an ensemble method  

**Logistic regression**
it performs a class probability estimation task
It is the go-to method for binary classification problems (problems with two class values)
Logistic regression models the probability of the default class (e.g. the first class).

**Decision trees (CART)**
Decision tree Decision trees are a supervised segmentation technique that places observations in the data into subgroups. 
CART (Classification and Regression Trees) is a well-known version of a decision tree that can be used for classification or regression. Once the data scientist chooses a response variable, the computer program will make partitions through the predictor variables. The program automatically chooses the number of partitions to prevent underfitting or overfitting the data to the model. Decision trees are useful in situations where  interested parties need to see the entire logical reasoning behind a decision.
Think of a decision tree as pure logic (yes / no decisions in a tree form)

### Regression
Essentially, this is value estimation. Attempts to estimate or predict, for each individual, the numerical value of some variable for that individual. “How much will person X use the product / pay for it?” A regression procedure produces a model that, given an individual, estimates the value of the particular variable specific to that individual. 

Regression is related to classification, but the two are different. Informally, classification predicts whether something will happen, whereas regression predicts how much something will happen.

**Linear regression**
predict an output variable using one or more input variables. This is represented in the form of a line: y=bx+c.

Simple linear regression: when there is a single input
Ordinary Least Squares: used to estimate values of the coefficients of more than one input 
The Ordinary Least Squares procedure seeks to minimize the sum of the squared residuals. This means that given a regression line through the data we calculate the distance from each data point to the regression line, square it, and sum all of the squared errors together. This is the quantity that ordinary least squares seeks to minimize.

Gradient descent
When there are one or more inputs you can use a process of optimizing the values of the coefficients by iteratively minimizing the error of the model on your training data.

### Clustering
Attempts to group individuals in a population together by their similarity, but not driven by any specific purpose. An example clustering question would be: “Do our customers form natural groups or segments?” 

**K-means**
This fits a model consisting of k cluster centers; the optimal centers are assumed to be those that minimize the distance of each point from its assigned center	

K-means clustering K-means clustering is a machine learning algorithm that forms groups of observations around geometric centers called centroids. The “k” refers to the number of clusters, which is determined by the individual conducting the analysis based on domain knowledge. This type of clustering is often used in marketing and market research as an approach to uncover similarity among customers or to uncover a previously unknown segment.
		
**Gaussian mixture models (GMMs)**
A Gaussian mixture model (GMM) attempts to find a mixture of multi-dimensional Gaussian probability distributions that best model any input dataset.

**Hierarchical clustering**
Hierarchical clustering This method produces a tree-shaped structure known as a dendrogram. Each node in the dendrogram is a cluster based on the similarity of the observations in it.

## Monte Carlo simulation
A monte carlo simulation is a way of running lots of scenarios with random inputs and summarizing the distribution of the results. E.g. can be used to predict how much sales commission to forecast for next year by running scenarios on what percentage of targets are achieved

There are two components to running a Monte Carlo simulation:
- the equation to evaluate
- the random variables for the input

## Other data science methods
- Similarity matching attempts to identify similar individuals based on data known about them. Similarity matching can be used directly to find similar entities. For example, IBM is interested in finding companies similar to their best business customers, in order to focus their sales force on the best opportunities. They use similarity matching based on “firmographic” data describing characteristics of the companies. Similarity matching is the basis for one of the most popular methods for making product recommendations (finding people who are similar to you in terms of the products they have liked or have purchased). Similarity measures underlie certain solutions to other data mining tasks, such as classification, regression, and clustering. We discuss similarity and its uses at length in Chapter 6.		
- Co-occurrence grouping (also known as frequent itemset mining, association rule discovery, and market-basket analysis) attempts to find associations between entities based on transactions involving them. An example co-occurrence question would be: What items are commonly purchased together? While clustering looks at similarity between objects based on the objects’ attributes, co-occurrence grouping considers similarity of objects based on their appearing together in transactions. For example, analyzing purchase records from a supermarket may uncover that ground meat is purchased together with hot sauce much more frequently than we might expect. Deciding how to act upon this discovery might require some creativity, but it could suggest a special promotion, product display, or combination offer. Co-occurrence of products in purchases is a common type of grouping known as market-basket analysis. Some recommendation systems also perform a type of affinity grouping by finding, for example, pairs of books that are purchased frequently by the same people (“people who bought X also bought Y”). The result of co-occurrence grouping is a description of items that occur together. These descriptions usually include statistics on the frequency of the co-occurrence and an estimate of how surprising it is.	
- Profiling (also known as behavior description) attempts to characterize the typical behavior of an individual, group, or population. An example profiling question would be: “What is the typical cell phone usage of this customer segment?” Behavior may not have a simple description; profiling cell phone usage might require a complex description of night and weekend airtime averages, international usage, roaming charges, text minutes, and so on. Behavior can be described generally over an entire population, or down to the level of small groups or even individuals.	
Profiling is often used to establish behavioral norms for anomaly detection applications such as fraud detection and monitoring for intrusions to computer systems (such as someone breaking into your iTunes account). For example, if we know what kind of purchases a person typically makes on a credit card, we can determine whether a new charge on the card fits that profile or not. We can use the degree of mismatch as a suspicion score and issue an alarm if it is too high	
- Link prediction attempts to predict connections between data items, usually by suggesting that a link should exist, and possibly also estimating the strength of the link. Link prediction is common in social networking systems: “Since you and Ka‐ ren share 10 friends, maybe you’d like to be Karen’s friend?” Link prediction can also estimate the strength of a link. For example, for recommending movies to customers one can think of a graph between customers and the movies they’ve watched or rated. Within the graph, we search for links that do not exist between customers and movies, but that we predict should exist and should be strong. These links form the basis for recommendations.	
- Data reduction attempts to take a large set of data and replace it with a smaller set of data that contains much of the important information in the larger set. The smaller dataset may be easier to deal with or to process. Moreover, the smaller dataset may better reveal the information. For example, a massive dataset on consumer movie-viewing preferences may be reduced to a much smaller dataset revealing the consumer taste preferences that are latent in the viewing data (for example, viewer genre preferences). Data reduction usually involves loss of information. What is important is the trade-off for improved insight.			
- Causal modeling attempts to help us understand what events or actions actually influence others. For example, consider that we use predictive modeling to target advertisements to consumers, and we observe that indeed the targeted consumers purchase at a higher rate subsequent to having been targeted. Was this because the advertisements influenced the consumers to purchase? Or did the predictive models simply do a good job of identifying those consumers who would have purchased anyway? Techniques for causal modeling include those involving a substantial investment in data, such as randomized controlled experiments (e.g., so-called “A/B tests”), as well as sophisticated methods for drawing causal conclusions from observational data. Both experimental and observational methods for causal modeling generally can be viewed as “counterfactual” analysis: they attempt to understand what would be the difference between the situations—which cannot both happen —where the “treatment” event (e.g., showing an advertisement to a particular individual) were to happen, and were not to happen.				
- In all cases, a careful data scientist should always include with a causal conclusion the exact assumptions that must be made in order for the causal conclusion to hold (there always are such assumptions—always ask). When undertaking causal modeling, a business needs to weigh the trade-off of increasing investment to reduce the assumptions made, versus deciding that the conclusions are good enough given the assumptions. Even in the most careful randomized, controlled experimentation, assumptions are made that could render the causal conclusions invalid. The discovery of the “placebo effect” in medicine illustrates a notorious situation where an assumption was overlooked in carefully designed randomized experimentation.

## Glossary 
- Machine learning is about building mathematical models to understand data. These models look at previous encountered data and are then used to predict and understand aspects of newly seen data. 
- Model: simplified representation of reality created to serve a purpose. a predictive model is a formula for estimating the unknown value of interest: the target.
- Target: the dimension we want to predict 
- Training data: The input data for the induction algorithm, used for inducing the model. They are called labeled data because the value for the target variable (the label) is known. You use train to develop the model and test to validate the model. This split is done using train_test_split from sklearn.model_selection. The train model generally gets better the more variables you include in the analysis.
- Test data: However, the test model is more representative of the real world. If the test performs worse than train, you know there is overfitting 
- Overfitting is when we have a model that works really well on the current dataset but it not really applicable outside of it. In other words, the training score will be high but the validation score is low. Happens often with small datasets. that is, it has so much model flexibility that the model ends up accounting for random errors as well as the underlying data distribution; another way of saying this is that the model has high variance.
- Underfitting happens when we have a model that performs not great on the current data but really well outside of it. This is often the case with large datasets and it means that the training score is low but the validation score is very high. that is, it does not have enough model flexibility to suitably account for all the features in the data; another way of saying this is that the model has high bias.
- Feature: each column of the data refers to a particular quantitative piece of information that describes each sample. 
- Samples: rows in a table
