# BI checklist

## General
- Get context and deep understanding of the problem / request. If you feel like you miss general business process context, get this first before working on the requests. The analysis takes a long time and it’s worth getting deeper into this to ensure the final result is a helpful conclusion  
  - Take the time to take a step back, think about what you’re doing, and why. 
  - Don’t pick the first solution you came up with, but take some time to think about other options.
  - What is the easiest way of thinking about this? Especially when getting a request by the business, realise the answer is probably quite simple. Present that first and they'll challenge when that doesn't suffiece 
  - Only start when you're confident you have a good understanding.  
- Build solutions asking yourself 'so what' - what are we trying to achieve here?
- Whilst developing, break it down and build incrementally so it's easy to spot where things break. If things break, perform unit tests. 
- Check the data multiple ways - does this make sense and does this answer the question?
- When in doubt, ask others too
- Communicate a lot with the stakeholder throughout the analysis - the goal is impact. Don't go all rough 
- Follow up with the staekholder and close the loop 
- When making important changes, e.g. in LookML, consider making multiple versions (old and new) of the metric until this is checked by the business (e.g. v0 and v1)
- 

### Requirements gathering
- What is the question we are trying to answer?
- What is the impact of this question and how will it help the company? (This can be different from what's asked for)
- How and when will you use the data? E.g. in a dashboard shown in weekly meeting, to import into email tool, to put in slides, to send as schedule, to create alerts from, to put into spreadsheet that then does further transformation?
- Who will be interested in the data and needs access? 
- Any visualization requirements? 
- How does this fit in the grander scheme of things? 
    - Will future business changes change this model again? 
    - Are we testing if something is even possible at all? Should we MVP? 
    - How important is it to get perfect? 
    - Any downstream effects? 


### Delivery process
- Have ticket with requirements. Potentially detailed with:
    - List of fields
    - Mock-up/wireframe of dashboard
- Sign this ticket off with the stakeholder prior to development
- Regular check-ins during the incremental build 
- Check-in prior to final delivery to ensure required impact is delivered. Always close the BI cycle. Remember to answer questions: 'So what' and 'Now what'? The end result should not be a deck summarizing findings, the end result should be recommendations or action items that lead to real impact. Closing the loop means pushing action items through, and following up after implementation to measure real impact.


### Dashboard checklist
- Good design: 
    - Test for the use case – is the sizing correct? 
    - Are tiles logically grouped? 
    - Are headers applied?
    - Are best practices applied to the graphs? 
    - Is design applied consistently? E.g. board plan values are blue 
- Tells a story: 
    - Is the data logically grouped (high level at top, more granular at the end)? 
    - Does it look at one specific area of the business? 
    - If there are outliers, is the analysis clarified in the dashboard? 
    - Is good and bad clearly separated?
    - Are tooltips / notes added where relevant?
- Good data:
    - The data doesn’t raise any questions (e.g. no null values) 
    - Is the data correct? 
    - Is the data in line with other sources?
- Has impact: 
    - Does the dashboard deliver the required impact? This is checked with the stakeholder 
    - Can the user perform actions, filters, drill down, links as required?
    - Are the definitions in line with the business definitions?
- Other
  - User permissions are reviewed
  - Are axes labelled correctly? 

### Testing
- Never assume data to be correct – check it and be confident its correct. Check it when it is in the source as the source might be wrong. Check manual input from other. Check own logic. 
- Ideal scenario: proof that data is in line with source 
- If we can’t check vs source, does the data make sense? 
    - Look at the graph itself 
    - Look at the underlying data – anything unusual? E.g. NULLs, duplicates, high values? Make sure to perform some unit tests against source 
- If I am running a calculation, is the math right?
- Is the data up to date? 
- Calculate it in a different way, do the results match?
- What assumptions am I making that might be incorrect? Check these 
- If something is fairly complex or I am unsure, ask others. 
- How are the ‘edge’ cases (i.e. unique cases) threated in my data?

### Naming conventions
- Conventions: 
    - Naming should be descriptive of the data
    - Naming should be based on business terminology 
    - Be consistent 
- General: 
    - Use snake_case
    - Everything is lowercase
    - Table names are dim_, fact_, stg_ (always snake case with pre-fixes)
    - Tables names are singular: dim_customer
    - IDs are described as: object_id
    - CTE names should be specific to the table it represents
    - The same field name across objects should get a label that is object specfic: "Ad Status" and "Campaign Status"
    - Explores: names indicate type of information contained in the Explore
    - Always be descriptive
- Fields: 
    - Count (measures): Number of  
    - Sum: Total
    - Count distinct: Unique count
    - Average: Average
    - Ratios: Over or Per, E.g. Revenue per number of items
    - Booleans: Is_ of Has_. E.g. Is_sold
    - Time: <event>_at
    - Time zones: suffix: created_at_utc. This helps keeping things organized in BI tool (which is alphabetical after all)
    - Currency – suffix with *_usd 
    - Include type of measurement in column name: duration_in_secs, weight_in_kgs

## DBT model organization 
1. Primary data - Primary data is the key information describing the table. The primary key should be in this group along with other relevant unique attributes such as name.
2. Foreign keys - Foreign keys should be all the columns which point to another table.
3. Logical data - Logical data is for additional data dimensions that describe the object in reference. For a Salesforce opportunity this would be the opportunity owner or contract value. Further logical groupings are encouraged if they make sense. For example, having a group of all the variations of contract value would make sense. Within any group, the columns should be alphabetized on the alias name.
4. Metadata

Example is here: 

` SELECT
   id                    AS account_id,
   name                  AS account_name,
     
   -- Foreign Keys
   ownerid               AS owner_id,
   pid                   AS parent_account_id,
   zid                   AS zuora_id,
     
   -- Logical Info
   opportunity_owner__c  AS opportunity_owner,  
   account_owner__c      AS opportunity_owner_manager,
   owner_team_o__c       AS opportunity_owner_team,
     
   -- metadata
   isdeleted             AS is_deleted,
   lastactivitydate      AS last_activity_date
 FROM table`

## Looker view organization 
- Keys 
- Dates
- Dimensions (grouped together with comments on top)
- Measures (grouped together with comments on top)
- Within each group, order alphabetically 


## DBT
### Development 
- Everything is developed with proper naming conventions
- The SQL has a good style 
- The code is well documented – a new joiner should understand what is happening 
- Every model in production has tests running on a schedule 
- Be explicity rather than implicity: define data types and ensure they are as small as possible 

### Changes checklist
- Run all models (low – high in DAG) include testing in Dev
- Look at the tables in Dev – does it make sense and did we not change the data? Is the data requested and accurate?
- Run all models (low – high in DAG) include testing in Prod
- Push the changes in the models to Github so DBT Cloud runs updated jobs
- Check the data pre and post change: are the differences expected? 
- Depending on changes, make relevant changes in LookML (e.g. renamed fields or new columns in the table). Also drop anything that is now outdated from Snowflake 
- Run the new fields in Looker and make sure they run as expected 

## Looker

### Development
- LookML is well organized 
    - Good grouping of related dimensions and measures 
    - We apply DRY principles to the code 
    - Users have the minimum access to the data to not create cognitive overload. At the same time, when something could be relevant, keep it. 
    - In explore join design, aim to have all joins going to the initial explore to limit joins required to get data 
    - Keep in relevant IDs so that end users can troubleshoot where required
    - Always keep a number of measures for easy troubleshooting as well 
- End users find Looker easy to use 
    - Naming conventions are applied
    - Explores are as short as possible, with groupings applied. Each explore answers specific questions
    - All relevant fields have a name used in the business and a useful description. Make sure this description makes all sense standalone and covers enough context. Always ensure that every single field has a description - even when seemingly obvious and hidden. Good way of getting descriptions is from the API docs
    - The labels are clear and describe the data 
    - Dashboards are easily accessible to end users 

### Changes checklist 
- Changes to LookML 
    - Before pushing anything to live, make sure that all best practices are implemented (definitions, tests, good UX) 
    - Validate LookML 
    - Test Looker explores with new changes (no errors in dimension / measures). When possible, compare new dev vs old prod
    - Content validation 
    - When changing fields, do a run on the previous field name and make sure to update all old references with the new version
    - Push to production so all Looker users use most current models  
    - Quickly check most used dashboards 
    - Update model sets where required - make sure that relevant stakeholders still have relevant access 
- Spend time each week for Looker management: 
    - Access control: do the right people have access to the right models?
    - Do the dashboards still work as expected? 
    - Do I find Looker easy to use – am I following my best practices? Would a new joiner be able to easily get to everything he / she needs?
    - Is LookML still clean? Is there code that can be made redundant, do we group logically, is everything DRY? Can we combine some explores? 

## Github 
### Pull request design 
- Title. E.g. "Feature", "Fix", "Update": X
- Description provides context. Should be able to understand the PR without looking at the code: 
    - What are you changing 
    - Why are you changing it? 
    - Link to the source ticket of the feature - e.g. in Notion
- Screenshot of updated part of the DAG
- Validation of models: 
    - include output that confirms model does what is expected. E.g. link to in development Look, or a query that compares the data. 
    - Perhaps a screeenshot of content valdiator and LookML validator 
    - Screenshot of the dimensions and measures in action with their relevant links
    - Where possible, comparison between source data 
    - Where relevant, add any other QA relevant information here. 
    - Ideally, CI tests are set up and these are completed successfully
- Always add a reviewer to a PR 
- Include table granularity when building a new PDT / table 

### PR checklist 
- Each PR is one logical piece of work - don't solve multiple problems in one PR. Reasons: 
  - understanding multiple unrelated changes is an enormous pain for your reviewer,
  - rolling back changes becomes much more challenging,
  - and any delays in getting part of the PR approved end up delaying the entire batch of changes.
- Style guide is applied with the right naming conventions 
- Tests are added and run sucessfully 
- Documentation is added 
- Code is DRY
- Data returns expected results 
- Continiuosly integrate PRs. Don't wait to complete a project. Instead, break the project down to manageable pieces that get their individual PRs

