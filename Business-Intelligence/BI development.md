# BI development

## Requirements gathering 

### Context setting
BI has some capacity to work with teams – this team might have a strong need for analytics support 

### Get context around business area
- What is their responsibility / objectives / what does their job look like? 
- How does data play a role in this? How do they view data – what does it mean for their team and how does it help? 
- What analysis / reports do they currently use? 
    - 
- What is their longer term vision of using data in their team? What would the ideal solution look like and what would that enable you to do? Think operational and strategic again – this should tie back to their main challenges when reaching their objectives 

### Map out the stakeholder's current world
Whiteboard with: 
- Job area
- Important metrics in this area 
- Source of the metric
- Indication of how they’re tracking this now 
- Indication of how well that works 

### Map out the stakeholder's desired new world
Withboard with: 
- Metric name
- Metric calculation / logic to implement / assumptions to build in 
- Go in detail about the fields. Write down:
    - Dimensions
    - Measures
- What the metric needs to be grouped by 

### Get business context (optional)
Examples: 
- How are conversion rates calculated?
- What are the distinct stages
- What are most important channels, etc. 

### Set up a plan and get the right access 
- Can I get access to that existing solution? This way, I’d be able to look at the logic and have a comparison for my data  
- Can I sit in on sessions where the data is used to get first hand experience? 
- Can I get access to the source tool?

### Security:
- Who should have access to this data and what kind of access would that be? 
- Any teams that should specifically should not have access to the data? 


### Remaining questions 
- What defines success here?
- Any other relevant things - e.g. do we need to keep a history?

## Development process
### Understand custom data sources (where relevant)
- Where does the source data live?
- How to get access to that data?
- How to get Fivetran access to that data?
- Data itself: 
    - What format is the data / the file containing the data in? 
    - Can we track history? 
    - Can we join it on a common id field?
    - Does it include calculated / derived data – can we do these in BI tool? 
    - What happens when the underlying logic changes?
    - Is any of this data sensitive? 
    - Is it accurate?

### Explore data from Fivetran (or custom sources)
- Pipeline the data from Fivetran into Snowflake 
- Explore this data in Snowflake 
    - Is there any PII? If so, we can either build a transformation in Fivetran to remove the PII or we work with the stakeholders to change name of certain fields to e.g. IS_PII (this avoids us having to remove an entire column which might be needed to analyze some data) 
    - Go through the data and make sure it makes sense:
        - Does it seem reasonable – e.g. row counts
        - Have all tables been pipelined? 
        - What are min and max dates? 
        - Basically, perform EDA on the data set
    - Make initial high level transformation jobs in SQL and identify where fields are joined (where obvious joins are required, get these in directly) 
    - Ask yourself: Do I understand what the data tells me? If not, go to the documentation and look up fields. Otherwise, when the data seems relevant, prepare a list of questions to ask stakeholder 
- Understand the high level architecture 
    - Draft a rough dimensional model from the source to identify what the fundamental tables are and their related dimensions 

### Replicate existing reports
Using the existing reports from the stakeholders, see if you can get to the same numbers. This might uncover source data issues and defintion questions. 

