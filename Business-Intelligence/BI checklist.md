# BI checklist

## General

### Requirements gathering
- What is the question we are trying to answer?
- What is the impact of this question and how will it help the company?
- How and when will you use the data? E.g. in a dashboard shown in weekly meeting, to import into email tool, to put in slides, to send as schedule, to create alerts from, to put into spreadsheet that then does further transformation?
- Who will be interested in the data and needs access? 
- Any visualization requirements? 

### Delivery process
- Have ticket with requirements. Potentially detailed with:
    - List of fields
    - Mock-up of dashboard
- Sign this ticket off with the stakeholder prior to development
- Regular check-ins during the incremental build 
- Check-in prior to final delivery to ensure required impact is delivered. Always close the BI cycle. Remember to answer questions: 'So what' and 'Now what'?

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
- Good data:
    - The data doesn’t raise any questions (e.g. no null values) 
- Has impact: 
    - Does the dashboard deliver the required impact? This is checked with the stakeholder 
    - Can the user perform actions, filters, drill down, links as required?

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
    - Table names are dim_, fact_, stg_
    - Tables names are singular: dim_customer
    - IDs are described as: object_id
    - CTE names should be specific to the table it represents
- Fields: 
    - Count (measures): Number of  
    - Sum: Total
    - Count distinct: Unique count
    - Average: Average
    - Ratios: Over or Per, E.g. Revenue per number of items
    - Booleans: Is_ of Has_. E.g. Is_sold
    - Always be descriptive
    - Time: <event>_at
    - Time zones: suffix: created_at_utc. This helps keeping things organized in BI tool (which is alphabetical after all)
    - Currency – suffix with *_usd 
    - Include type of measurement in column name: duration_in_secs, weight_in_kgs

## DBT
### Development 
- Everything is developed with proper naming conventions
- The SQL has a good style 
- The code is well documented – a new joiner should understand what is happening 
- Every model in production has tests running on a schedule 

### Changes checklist
- Run all models (low – high in DAG) include testing in Dev
- Look at the tables in Dev – does it make sense and did we not change the data?
- Run all models (low – high in DAG) include testing in Prod
- Push the changes in the models to Github so DBT Cloud runs updated jobs
- Check the data pre and post change: are the differences expected? 
- Depending on changes, make relevant changes in LookML (e.g. renamed fields or new columns in the table) 
- Run the new fields in Looker and make sure they run as expected 

## Looker

### Development
- LookML is well organized 
    - Good grouping of related dimensions and measures 
    - We apply DRY principles to the code 
    - Users have the minimum access to the data to not create cognitive overload
- End users find Looker easy to use 
    - Naming conventions are applied
    - Explores are as short as possible, with groupings applied. Each explore answers specific questions
    - All relevant fields have a name used in the business and a useful description 
    - The labels are clear and describe the data 
    - Dashboards are easily accessible to end users 

### Changes checklist 
- Changes to LookML 
    - Before pushing anything to live, make sure that all best practices are implemented (definitions, tests, good UX) 
    - Validate LookML 
    - Test Looker explores with new changes (no errors in dimension / measures)
    - Content validation 
    - Push to production so all Looker users use most current models  
    - Quickly check most used dashboards 
    - Update model sets where required 
- Spend time each week for Looker management: 
    - Access control: do the right people have access to the right models?
    - Do the dashboards still work as expected? 
    - Do I find Looker easy to use – am I following my best practices? Would a new joiner be able to easily get to everything he / she needs?
    - Is LookML still clean? Is there code that can be made redundant, do we group logically, is everything DRY? Can we combine some explores? 


