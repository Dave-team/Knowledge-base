# BI development

## Principles
- Always work incrementally. Build out a single feature. Get that live and in front of the end user. Get their feedback and then go on to improve the product. 
- Keep your SQL simple until it works for one use case. Then add additional complexity only when the simple proofs to work
- Never make a change promptly. Keep different versions and decide what’s best over time
- Don’t build something slightly complex in SQL until the approach is confirmed across the board. Whenver you're code starts to look complex, take a step back and see if we can prove an easier solution and whether we can simplify the complexity
- Don’t aim for perfection – aim for making it good enough (i.e. meeting requirements) and prioritize speed. Realize that it’s hard to make a perfect model that works for all cases. Build it for 80% of the cases first. You can always make it better 
- The worst thing in data is sending out bad numbers. Don't skip tests, don't skip peer reviews, don't take shortcuts and make sure you fully understand what you're doing, what that means and the impact that has. It takes an experienced data analyst to know when to slow down. Even when facing large amounts of pressure and urgency.
- When changing something, try not to change too many things at the same time. Be able to keep track of and audit changes one by one 
- When changing infrastructure, don't change business logic as you want to compare like for like first. E.g. don't change logic when moving from PDTs to dbt. 
- When testing something and it seems sub-optimal, take a step back. How can we do this better? Test small. 
- If a business user is impacted, involve them with the review process
- BI in short: 
  - Manage expectations
  - Demonstrate small success
  - Communicate the results 

## Project charter
Create an initial high level project charter with the project objectives, scope, approach, involved parties and team staffing, success criteria, constraints, assumptions, and risks. This should include a high level architecture of the different data sources and ideally the most important dimensions (high level bus matrix). It should also have a list of high level priorities: teams / processes to get BI for and in what phase these will be implemented - this could be a high level gannt chart out of which individual tasks will be added to a backlog / PM tool. Note that this starts of as a draft and will be updated incrementally 

## Requirements gathering 

### Introductions (optional)
- Informal intro: What they did previosuly?	Journey so far at Tessian? Experience with data / BI tools at prior companies?
- Clarify goal of project and set high level expectations. BI has some capacity to work with teams – this team might have a strong need for analytics support 

### Get context around business area
- What is their responsibility / objectives / what does their job look like? 
- How does data play a role in this? How do they view data – what does it mean for their team and how does it help? 
- What analysis / reports do they currently use and how is it used? 
- What are the main challenges with this current data solution? 
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

## Business requirements doc
Create a business requirements doc that answers all questions asked including an initial feasibility assessment and potential acceptance criteria. 

## Kickoff (optional)
Speak to the executives of the team whose process is prioritized:
- Clarify the goal of the project
- Stakeholder mapping: understand who in their team uses data. Goal here is to really discover who to talk to and whether I could talk to multiple people at once. 
- Make sure that they are supportive of me spending time with their team members to gather data requirements. My job is here to be specific as to whom I’ll be meeting for how long and how often
- Clarify the deadlines that need to be met so full support is available from the start
- Make sure the expectations are set and met for everyone involved

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
- Pipeline the data from Fivetran into Snowflake. If the data isn't too large, pipeline all fields and transform less as people often change their mind as to what fields they want  
- Explore this data in Snowflake 
    - Is there any PII? If so, we can either build a transformation in Fivetran to remove the PII or we work with the stakeholders to change name of certain fields to e.g. IS_PII (this avoids us having to remove an entire column which might be needed to analyze some data) 
    - Go through the data and make sure it makes sense:
        - Does it seem reasonable – e.g. row counts
        - Have all tables been pipelined? 
        - What are min and max dates? 
        - Basically, perform EDA on the data set
    - Make initial high level transformation jobs in SQL and identify where fields are joined (where obvious joins are required, get these in directly) 
    - Ask yourself: Do I understand what the data tells me and does it make sense? Is the data in line with other tables? Really sanity check the data here. If not, go to the documentation and look up fields. Otherwise, when the data seems relevant, prepare a list of questions to ask stakeholder 
- Understand the high level architecture 
    - Draft a rough dimensional model from the source to identify what the fundamental tables are and their related dimensions 

### Replicate existing reports
Using the existing reports from the stakeholders, see if you can get to the same numbers. This might uncover source data issues and defintion questions. Keep a running record of any potential issues I find that should be discussed with stakeholders

The steps in this process: 
- Compare raw data first without transformations - i.e. just write SQL queries that should output the same results.
- Understand the logic deeply and verify with users
- Implement the new logic step by step - don't change too much at the same time

## Modelling the data 
After the initial reports are replicated correctly, I should have a good understanding of the data structures to now model the final tables.  
- Build incrementally: only build out the required fields and tables to answer the questions
- Test the data thoroughly before pushing to live and communicate test results with stakeholders
- Update a company wide Slack channel with the additions or changes to the data 

## WIP: If all this was a migration
If this was a migration: 
- Understand the end goal from the business and what needs to change to get there
- Map our current solution and create good documentation: 
    - High level ERD 
    - Map out fact and dimension tables with their description, data type, size, key, whether nulls are accepted, sample values, source system, source table, source field name, source datatype, example data, transformation rules, notes and where this data is used 
- Understand gaps by doing own analysis and talking to stakeholders. 
    - Which field are no longer required?
    - Is the logic correct?
    - What new fields are required to satisfy business needs? 
- Discuss gap analysis with relevant people in the business
- Create final warehouse design: 
    - Description of the business process modelled
    - High level overview of the business requirements 
    - High level diagram
    - Excel worksheet with details on each table
    - Open issues log highlighting unresolved issues
    - Discussion of known limitations in the design 

## DBT development 
- Look at existing PDTs: how are they used? 
  - If joined in Explore, its a fact / dimension table 
  - If not joined, its an intermediate table 
- Before starting, make sure you know how you can test what you're building. What is the easiest way of testing this? You don't want to test huge transformations that are taxing and take ages. 
- Always sense check the table: 
    - Is the data what is expected and do they make sense? Look at the values in the columns 
    - Is all data there? For example, check that all dates are loaded correctly - between source and transformed table
    - Are there any values that seem incorrect? Nulls, especially high or low values (validation tests - e.g. weird dates, weird prices), weird dates etc. 
    - Do we count the same number of rows when we look at the same data in a different table or different environment?
    - Where required, perform unit tests compared to source. Any completely new model should have extensive checks like these - especially for the business cases that are non standard (as outlined in the 'common gotchas' document). 

### PDT to dbt migration
- We always test dbt in a dev schema. Incremental models are compared between two models in dbt dev
- Create a new dev branch 
- Limit the data in parent tables. 
  - Limit parents models to data for e.g. last month only - this avoids rebuilding full parents tables in the dev schema 
  - Limit data is source CTE to also e.g. data of last month
- Set up two versions of the model to test where both versions ultimately select from the parent table with limited data: 
Incremental model and Full model 
- First run the two models. Both models will be built as a full table at first as it's the first time the incremental model is run. 
- Allow enough time for the source data to update 
- Run the two models: 
  - dbt run --models +int_webapp_pages_session --target dev. This will update parent tables and then build the model to test incrementally
  - dbt run --models int_webapp_pages_session_full --target dev. No need to update the parent models again 
- Compare the two tables in Redshift / Looker 
- Delete the additional logic from the dev branch and create a PR 
- Include window functions as a check and ensure PDT == dbt 
- Compare output of dbt model next the PDT. Look out for:
  - Total table count 
  - Count of IDs by day 
  - New sessions / day > X 
  - No gaps in timestamps? 
  - All values by field identical on a row level? 
  - Key aggregate metrics 
- When testing a model in dbt prod, don't add it to an existing job as that consequently may fail. 
- Change references to tables in Looker to point to your local schema
- Run the Content Validator in Looker to ensure that all field references still work. This is great for catching other reports that depend on the table you just changed. 
- Compare key dashboards / Looks between dev and prod to ensure key KPIs are similar 
- Merge the table reference to dbt 
- Once we replaced the Looker PDT, make sure to still be able to test against external data sources - such as Google Analytics. Especially e.g. with incremental models. 

**Incremental models**
- To test incremental models, make sure that the initial model has data until e.g. a few days before the current date. That way, we can test the incremental logic easily within the development environment

**Checklists**
- When rebuilding an incremental model, drop the table first from Redshift. 
- Mind any characters you might be adding to the model. Whenever we copy from Apple Notes, these characters will be added and a weird error message will be the result: https://pteo.paranoiaworks.mobi/diacriticsremover/
- When we receive an error 'aggregates not allowed in the where clause' - confirm that the column in the where clause is actually part of the model first 
- Think about the sequence of the model runs. What does a  model select from and how is that updated? How does that change when we run all the child models too?
- In dev, also look at the logs and make sure they represent what you expect. E.g. when we expect to run an incremental model, do we actually? 
- Make sure the config for each model is complete and accurate. E.g. materialize as incremental for incremental models. 
- Incremental 
  - Make sure to run incremental models on the columns you know works 
  - Make sure to update all parent tables when running an incremental model - this avoids joining old to new data. 

## Updates from Papier
When people don't know the data yet: 
- Quick sessions to understand high level requirements
- BI team to develop what makes sense as we understand roughly what the business is looking for 
- This gets sent to the stakeholder for review 

When there is existing data: 
- Quick sessions to understand high level requirements, KPIs
- Use existing reports to replicate the data 
- Send to stakeholders for review and build from there 

When business knows data well: 
- Send spreadsheet with all API fields 
- Do they want this as:
    - Dimension
    - Measure?
        - What measure type?
- What calculated fields would they like to see?

With all of this, remember it's iterative and the business will get back to BI if they want things changed  

## Building a SQL query request
- People will always want more filters etc. So rather than building a bespoke solution, look to build something that is higher level - give them instructions to use the data. 
- Use LookML fields in the SQL to avoid having to rewrite SQL myself 
- Keep it high level and simple for me rather than specific to a solution. 

