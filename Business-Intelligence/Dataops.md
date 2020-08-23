# Dataops

## Data testing 

### Principles
- Don’t overload yourself with all sorts of alerts as over time we’ll be less likely to look into each in detail. 
- Implementing testing process: 
    - At first, test only the essentials. You often don't know what to test for and you don't want to test what won't be used. This is the V0 version
    - If the data gets used, you'll find out where we need to strengthen the test suite and this is where we apply specific testing tactics to the data 
- Implement testing at the lowest level so issues don't continue downstream
- Automate as much as possible 
- Think about how logic handles edge cases 

### Source data testing
- Create an initial gap analysis between source and BI data. This includes 
    - Raw metric numbers that are different
    - Logic that returns different results (e.g. some things show up that are not expected) 
- Sit with owners of source data tools and discuss business rules that can be implemented and we should test for. These are things that should not happen from a business perspective. The tests are daily queries that show the instances that break a test. Good practice is probably to send those queries to the business owner on a daily basis in an email that contains the dashboard with the checks.  

### Extract and Load testing 
- Monitor jobs within Fivetran and set up alerts when anything goes wrong with these jobs
- Check that data got loaded in the raw schemas (or staging environment): count by day within raw schemas. Even better is to count by day compared to source data. This will identify missing values, but also any duplicates. Another option is to compare row counts relative to previous days (new vs old). We’d expect this to be fairly consistent over time 
- Get proof of missing data from the business teams and then provide a screenshot

### Transformation testing
- Monitor jobs within DBT and set up alerts for when jobs fail 
- Data quality testing: Set up constraints tests within DBT: 
    - unique
    - not null 
    - referential integrity
    - accepted values
- Custom schema tests in DBT. For example: 
    - Revenue always being smaller than or equal to the gross revenue
    - Employee end data > start date 
    - Item levels summed up equal the total of the summed value in another table
    - Data freshness: last Fivetran updated date < 2 days ago 
- Run the entire DBT test and DBT run command regularly to make sure nothing is breaking. Do this as well just before pushing transformation logic to live.   
- Always sense check the table: 
    - Is the data what is expected and do they make sense? Look at the values in the columns 
    - Is all data there? For example, check that all dates are loaded correctly 
    - Are there any values that seem incorrect? Nulls, especially high or low values, weird dates etc. 
    - Do we count the same number of rows when we look at the same data in a different table or different environment?
    - Where required, perform unit tests compared to source. Any completely new model should have extensive checks like these - especially for the business cases that are non standard (as outlined in the 'common gotchas' document). 

### BI tool testing
**Automated tests**
- Create QA dashboards with tests on some commonly used metrics that should show whether your data makes correct. E.g. total revenue. Total number of employees in seat. Total customers. 
- Similarly to the above, we can extend this dashboard to show changes by time period. E.g. new revenue since yesterday / last week. If values are outside of telerated values, send out an alert. 
- Run a script with the API that regularly validates all our user-facing content and posts any errors in our #data-qa slack channel

**Tests when going live**
- Sanity check the data we output. Does it make sense? 
- Test calculations — add it up, do the division, and calculate the ratios. Make sure the report itself is internally consistent and correct.
- Test at different levels in the hierarchies. What adds up correctly at the summary level may not be right when you start to drill down to the details.
- Test edge parameters. For example, what happens to a report that compares data from a requested year to a prior year when the selected year is the earliest year in the database and there is no prior year?
- Compare to existing sources. E.g. Looker should return same results as Salesforce. This test needs to be done in the beginning especially and when you are building something new. If some elements of the report are available elsewhere, and if the results should match, make sure they do. If you expect the results to be different because of improvements in data quality or business rule definition, see if you can match the existing source by applying these improvements by hand. Review these differences with key business users and document them in the BI portal
- When required, perform unit testing: look at one instance and compare DWH vs source and identify where issues occur 
- Measure the same metrics in different ways – the data returned should be equal. E.g. worm graph today vs all opps in S2 today. 
- If something uses logic that has the potential of going wrong, make sure that someone else sense checks the logic I have implemented. Believe things are wrong until proven correct. 
- Comapre dev vs prod in the BI tool 

## Monitoring
The easiest way to promote data quality is to have as many eyes on as many pieces of data as possible – this way potential issues are quickly identified and fixed rather than “festering” and slowly degrading trust in the entire system. There is monitoring responsibility for the data team but also the business. 

**Data team**
- Look at the most important reports and dashboards every morning to sanity check the data and if anything needs checking or escalation 
- Live in Looker – explore things constantly and double check the data. It will uncover issues

**Business**
- Looker should be the primary source of truth and KPI owners are measured against their performance. If the data looks off, they are incentivized to report this to the data team 
- Encourage people to reach out when things look off. When stakeholders look at data, they'll likely also review it. Scheduled reports could be a good way to increase data checking from the business 

## SLOs, SLIs and SLAs 
Use Service Level Objectives (SLO), Service Level Indicators (SLI) and Service Level Agreements (SLA). Only apply these standards to things that users actually care about. Examples of things to include: 
- Functionality: what reporting functionalities will we provide? 
- Accessibility: how can people access the data? 
- Performance: how fast are the individual processes (ETL, how long do queries take) 
- Delivery: how fast and predictable are turnaround times from request to working functionality)
- Quality: how accurate do we expect the data to be? If there are very complex models, can we do with slightly less quality for the sake of speed? 
- Availability of the BI team: how easy is it to reach them when questions arise? 
- Business relevance: what can BI do for the business? 
- Data freshness: how current is the data? 
- Support speed: how quickly are tickets turned around? Use a severity scale with associated response times. Severity is depending on impact (e.g. who is impacted, what is the effect, how urgent is it) 

## Issue tracking
Use an issue tracker. This can be as simple as a Google Sheet and over time, you'll want something more robust. 

## Contingency 
You don't want a single person to be the only one capable of solving issues that break things. So instead: 
- Create a doc around most common issues and how to fix them
- Train someone in the team to solve these issues 
- Intermediate solution could be to not develop anything new prior to responsible person going on leave 

## Git process  
New project
- Start a new branch off master. Name of branch is similar to title of ticket
- Commit and create PR. Also add a reviewer to a PR 

Changes to project: 
- Create a branch off the original branch to ensure only the improved and the to-improve version are compared by reviewer 
- When that branch is approved, merge back to the original branch and then merge to master  

Keep in mind: 
- Make sure to pull changes from production when working in a branch. When you created a branch off a branch, make sure to pull the changes first in the original branch. Otherwise, the changes made in different branches will show up as changes in the current branch. This should go in sequence from the most original branch upward. E.g. working in branch 4? Pull from remote first in origin, 1,2,3 before pulling from remote in 4 

Solving merge conflicts
- Usually done in Looker by selecting which parts of the code to keep 

## PR review checklist 
- Does the table run? 
- Does primary key constraint hold? : count(*), count (distinct PK should be the same)
- Check the joins: how many rows in the newly created table? Make a comment of that. Then, start with the FROM table. How many rows? Comment that. Then add each join to it and keep commenting the rows to see if something changes. 
    - If there are differences in row count, it could be a timing issue. Look into data quality dashboard and see if the tables are up to date. Perhaps the DQ dashboard shows a potentially different reason why the data might be out of sync? Otherwise, look into the cases that are different and see what characteristics they have 
- Go into the explore and run the data - does this make sense?
- Segment the data, compute aggregates and compare between dev and prod. This might mean we’d need to get this data into Excel to compare more accurately 
- Are the row counts and min and max values between prod and dev the same or explainable? 
- Spot check a few values to sanity check the logic of the model  
- Depending on the changes introduced, stress test these changes and see if anything breaks anywhere. 















