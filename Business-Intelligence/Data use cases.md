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


