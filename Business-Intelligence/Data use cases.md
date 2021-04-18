# Data use cases 

## Data hierarchy of needs
- Business reporting. Companies know they need data but don’t have any structure. Export from tools and do analysis in spreadsheet or the tools themselves 
- Business intelligence. Data warehouse and ETL is in place which combine all data sources centrally and existing reports are automated in a BI tool. This is where data can start having an impact – good drill downs, data is embedded in other tools and data drives specific actions that move the needle
- Ad hoc analysis / insight. We collect large amounts of good data and people trust the data. This is where we can really start to dig in and start answering new questions that previously couldn’t be answered (using data transformations and python). 
- Hybrid data teams. Data analysis is sophisticated enough that each team has their own experts. Demand for data is high and most teams can self serve. We can move towards an environment of experimentation and statistical analysis which is what tfhe data team can start focusing on. The company becomes data driven and has the BI tool as frame of mind when doing analysis 
- Predictive analytics and machine learning. This is where statistical analysis is then being pushed into production. This is where data is automatically making decisions that can help the company – e.g. forecast churn, automate some marketing channel. 

![Data hierarchy](https://user-images.githubusercontent.com/28791247/93708163-f624e500-fb2b-11ea-911d-dd353e9b9a16.png)

## BI use cases
- Standard (backward looking) reports: e.g. dashboards displaying the status / current performance where we track performance against high level KPIs and against any metrics we aim to improve. In addition, we have actionable context for these high-level KPIs and the ability to drill-into the detail behind them. This can answer: 
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
- Prediction (forward looking data). With data, we can give a score as to how likely someone is to convert or churn. We can add this score to the warehouse and map out exactly which leads are good and need priority, which customers are likely to churn and need immediate action (link to alerts or even better: automate a playbook) 
- Sharing. Having the ability to easily share data is big. Make sure it’s extremely easy for people to share within the comms tools that are used – e.g. Slack as well as email. 
- Present companywide on TV 

Reporting = The process of organizing data into infor­ma­tional summaries in order to monitor how different areas of a business are performing
Analysis = Transforming data assets into competitive insights that will drive business decisions and actions using people, processes and technologies


## Common analytics approaches 
**Data comparisons**
- This week vs Last Week
- This week vs same week last year
- Performance against budget 
- Where applicable, against forecast

**LTV** 
- Cohorts = Month of First Purchase, First purchase Category One 
- LTV = first order GM2 + (number of repeat orders  x average GM2)  
- Average Repeat GM2 defined by last 6 month average
- Repeat rate average since 2017

**Cohort/Repurchase analytics**
- By customer first order month and first product category, what is the cumulative number of orders placed by these customers by months since first order month 

**Mixed basket analysis** 
- Affinity analysis 

**Conversion analytics** 
Product conversion counts
- Add to Cart
- Checkout started
- Customize product
- Orders

Product conversion rates 
- Add to checkout
- Checkout conversion
- Customise to Add
- View to Customize
- View to Buy Rate 

Web conversion rates - this is on session level, not necessarily including products 
- Conversion rate (converted sessions / total sessions)
- Page analytics (exits, time on page, bounces)

**Attribution**
- Position based attribution model
- Checkout surveys
- Discount codes 

**A/B testing**
See AB testing file 

## Metrics by industry
**Ecommerce**
- Sales: new and repeat customers
- Orders: Average transaction value, mixed baskets, upsells 
- Marketing: attribution, CAC 
- Products: catalogue performance 
- Retention: repeat rates / churn rates
- Web: page analytics, conversions

**SaaS**
- Revenue (ARR): new and existing 
- Sales pipeline: Pipeline added, Leads added 
- Deals: Average deal value, Deals expecting to close, Deals expecting to churn, Sales cycle
- Conversion rates
- Costs per lead 
- Sales rep performance

**Application** 
- Downloads
- Average duration 
- % that did user behaviour 
- Milestones achieved
- Customer engagement

## Metrics by team
**Marketing**
- ROAS: Return on Ad Spend (revenue/spend)
- Customer Acquisition Costs (spend/acquisitions)
- CPO: spend/orders
- Lifetime Value
- Attribution 
- Customer Journey
- Retention / Churn 
- Cohort analysis (where a cohort can mean different things - first signup, marketing channel, discounted price, etc. )
- CTR (clicks/impressions)
- CPC (spend/clicks)
- Brand awareness
- Other
  - Email metrics  
  - Social metrics
  - Keyword performance 

**Product** 
- Funnel conversions 
- Usage analytics 
- Event analytics 
- User behaviour analysis (pages journey, checkout journey)
- Page analytics (visits, bounces, exits, time on page, attractiveness rate, scrolls, clicks)
- A/B testing 
- Session recordings 
- NPS
- CSAT

**Finance** 
- Gross Margin
- Contribution: Total Gross Margin 2 - Total Marketing Spend.

**People**
- Headcount
- Attrition
- Satisfaction

**Hiring**
- Time to hire
- Employee satisfaction
- Costs per hire
- Hiring channel performance

**Customer service**
- Number of tickets created / resolved
- First resolve rate
- Ticket duration
- Ticket replies

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

## Data Science
Use cases
- Forecasting: prophet (by Facebook).  
- Prediction: classification or regression models (see details below). E.g. churn prediction / lead scoring 
- Recommendation engine: 
- Marketing attribution: markov chains
- Measure LTV: Survival analysis 
- Clustering (e.g. RFM segmentation): K-means or others (see below for details)
- NLP / sentiment analysis 
- Scenario planning: Monte carlo simulation 
- Anomaly detection, e.g. fraud analysis 
- Google: 
  - Campaign optimization. E.g. different campaign approach depending on likely LTV of a customer
  - Bidding.
  - Keyword research
  - CAC reductions 