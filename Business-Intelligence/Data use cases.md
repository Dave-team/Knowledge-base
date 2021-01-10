# Data use cases 

## Data hierarchy of needs
- Business reporting. Companies know they need data but don’t have any structure. Export from tools and do analysis in spreadsheet or the tools themselves 
- Business intelligence. Data warehouse and ETL is in place which combine all data sources centrally and existing reports are automated in a BI tool. This is where data can start having an impact – good drill downs, data is embedded in other tools and data drives specific actions that move the needle
- Ad hoc analysis / insight. We collect large amounts of good data and people trust the data. This is where we can really start to dig in and start answering new questions that previously couldn’t be answered (using data transformations and python). 
- Hybrid data teams. Data analysis is sophisticated enough that each team has their own experts. Demand for data is high and most teams can self serve. We can move towards an environment of experimentation and statistical analysis which is what the data team can start focusing on. The company becomes data driven and has the BI tool as frame of mind when doing analysis 
- Predictive analytics and machine learning. This is where statistical analysis is then being pushed into production. This is where data is automatically making decisions that can help the company – e.g. forecast churn, automate some marketing channel. 

![Data hierarchy](https://user-images.githubusercontent.com/28791247/93708163-f624e500-fb2b-11ea-911d-dd353e9b9a16.png)

## BI use cases
- Pre-defined reports: e.g. dashboards displaying the status / current performance where we track performance against high level KPIs and against any metrics we aim to improve. In addition, we have actionable context for these high-level KPIs and the ability to drill-into the detail behind them. This can answer: 
    - Status: how are we doing. Are we doing well – compare against targets 
    - Trend: are we going up, down, or are we constant
    - Projection: given where we are and what is likely to happen, will we reach our objective in time? 
- Analysis: ad hoc queries that try to understand the why behind the metrics / KPIs. Understanding the why behind performance should indicate where improvements can be made. E.g. improvements to increase marketing performance (conversion rates, channel performance), reduction in operational costs thanks to optimizations, etc.  Enabling ad-hoc querying and analysis of our complete dataset by technical and non-technical users. Providing a trusted, integrated analysis-ready data platform for other internal projects
- Statistical analysis: consider how different actions impact the business and try to understand how the business can be improved. This can also include things like customer segmentation to get a better idea of the distribution of the customer groups and often it will include hypothesis testing as we test different options to improve the business. 
- Forecasting: understand different scenarios that are likely to happen and make strategic decisions of the back of these 
- Alerts: being aware when things are off and being able to take timely action
- Data actions to directly perform actions into Looker. E.g. we can create a report in Looker that shows all customers due an NPS score. Send that NPS email via NPS tool directly from Looker. No need to export data and import into email tool any longer. Mark contacts as inactive when they haven’t done something for a while
- Automations: if data actions are not solving the problem – there are options to run complete automations. Maybe you want to email users with falling engagement scores or offer a coupon code to high-value users, or flag habitual support users for your support team. This can be done with Segment and some Zapier integrations – essentially: if a value changes, this fires of an email automatically in the backend. A way to run your analysis, write the output back to the source system, and keep it updated with the latest results. Can also build out data in Looker > export to Segment > send customized emails via marketing tool. This can all be automated based on triggers. Or: someone clicks cancel, Segment identifies this, forces Drift cancellation flow, send notification to Slack, and lands into Looker
- Schedules: send data at a defined time so people don’t forget about the data 
- Embedding. Often, the business users are already used to certain tools and this might be where they spend most of their time. Don’t try to get them into Looker – go to them. Give Sales an overview of the customer from a Looker embed. bringing data and analytics to the problems they’re looking to solve rather than the other way around.
- Prediction. With data, we can give a score as to how likely someone is to convert or churn. We can add this score to the warehouse and map out exactly which leads are good and need priority, which customers are likely to churn and need immediate action (link to alerts or even better: automate a playbook) 
- Sharing. Having the ability to easily share data is big. Make sure it’s extremely easy for people to share within the comms tools that are used – e.g. Slack as well as email. 
- Present companywide on TV 

## Other
- A/B testing
- LTV models
- Process around measuring impact feature changes 

## Data Science
Use cases
- Forecasting: prophet (by Facebook).  
- Prediction: classification or regression models (see details below). E.g. churn prediction / lead scoring 
- Recommendation engine: 
- Marketing attribution: markov chains
- Measure LTV: Survival analysis 
- Clustering (e.g. RFM segmentation): K-means or others (see below for details)
- NLP / sentiment analysis 
- A/B testing 
- Scenario planning: Monte carlo simulation 
- Market basket analysis 
- Anomaly detection, e.g. fraud analysis 
- Google: 
  - Campaign optimization. E.g. different campaign approach depending on likely LTV of a customer
  - Bidding.
  - Keyword research
  - CAC reductions 

## Metrics by industry
**Ecommerce**
- Sales 
  - Overall 
  - New customer
  - Repeat customers 
- Average transaction value
- Website visits by channel
- Conversion rates by channel (shopping cart conversions)
- Trending product categories
- Category performance
- Items per order 

**SaaS**
- Revenue (ARR)
  - New 
  - Existing 
- Pipeline added 
- Leads added 
- Average deal value 
- Conversion rates
- Deals expecting to close 
- Deals expecting to churn 
- Sales cycle
- Costs per lead 
- Everything against target
- High level overview of rep performance 

**Subscription** 
- Subscribers
  - New
  - Existing
- Website conversions
- Conversion to first paid version 
- Average transaction value 
- CAC by channel
- Product performance 
- Retention / Churn rates 

**Application** 
- Downloads
- Average duration 
- % that did user behaviour 
- Milestones achieved
- CAC by channel 
- Customer engagement

## Metrics by team
**Sales**
- Rep performance / ramp
- Pipeline coverage
- Conversions
- Price evolutions
- Opportunities / pipeline 
- Forecasting what will likely close. They need a lot of data for this and it’s a massive win 
- Touches to advance a deal 
- CSM: how much outreach do we do vs how often do users use the platform? Also, identify who are the active users and reach out to them. Who had great support experience? Reach out. Those who haven’t logged in in a while, craft a different message 
- A good way of looking at what to chase: by industry, employee count, what is the win rate, what is the sales length, what is the average ARR? Then, focus on the ones aligned with the business priorities, and at the same time understand why some segments are successful and see how this can be replicated 
- What behaviour leads to successful outcomes? This is where BI comes in as it combines usage statistics with the actual Salesforce data 
- Monitoring activity by rep 
- What email subject lines perform well? 
- What pages do people look at when they become closed won?
- How often should be touch base by company segment? 
- Prioritization of opportunities based on likelihood of closing (or slipping) 

**Marketing**
- Budget and what % of that is spent
- Ad spent vs the result of that spend – i.e. combine the different ad tools (spend) with Salesforce (result). Also called ROI analysis 
- Customer segmentation
- CAC analysis
- Lifetime Value
- Channel attribution 
- Funnel conversions 
- Customer Journey
- Retention / Churn 
- Events 
- Cohort analysis (where a cohort can mean different things - first signup, marketing channel, discounted price, etc. )
- Ad spent from all various ad tools
- Find opportunities in marketing performance - e.g. certain users respond to certain ads. Or better on certain devices etc. 
- Understand customers and use that to select targets. E.g. well performing vs likely to churn: send an email. Also, treat good customers really well. 
- How do we allocate our marketing spend?
- Alerts when ads go wrong 
- A/B testing 
- Keyword performance 
- Duration and pages viewed on website 
- Visitor data (%new, %existing)
- Costs per lead
- Brand awareness
- Email marketing 
- Social 

**Finance** 
- Reduce operational costs by understanding where it all goes to a more granular level (e.g. by customer / module)
- Forecast vs budget vs actuals
- Easy to get data from the statements
- Margins 
- Sales efficiency 

**People**
- Headcount
- Attrition
- Satisfaction

**Hiring**
- Better understanding of when a role will be finalized and how that affects commercial metrics 
- Optimization of channels by role 
- Healths core by role: is this role likely going to be hired by month X? Then change approach based on the answer
- Time to hire 
- Employee satisfaction
- Costs per hire

**Customer service**
- Number of tickets created 
- Number of tickets resolved 
- First resolve rate
- Ticket duration
- Ticket replies
- NPS
- CSAT

**Product** 
- Usage
- Conversion
- Behaviour

