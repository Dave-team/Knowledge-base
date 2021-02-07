# Dataops
## Links
- How to review an Analytics Pull Request: https://blog.getdbt.com/how-to-review-an-analytics-pull-request/

## Data testing 

### Principles
- Don’t overload yourself with all sorts of alerts as over time we’ll be less likely to look into each in detail. 
- Implementing testing process: 
    - At first, test only the essentials. You often don't know what to test for and you don't want to test what won't be used. This is the V0 version
    - If the data gets used, you'll find out where we need to strengthen the test suite and this is where we apply specific testing tactics to the data 
- Implement testing at the lowest level so issues don't continue downstream
- Automate as much as possible 
- Think about how logic handles edge cases 
- First build anything that is high priority. Then, over time we just keep adding new things. 
- Always prioritize pushing projects live that you're working on prior to moving on to the next project 
- Make sure to test properly on a few critical reports 
- Create a playbook for some of the most often occurring issues 
- When checking data, keep things constant to compare like for like and to be correct on principles. Only after, make change to logic. When trying to replicate something existing, make sure to first completely understand the logic. Look at the spreadsheet, map your thinking and then verify with users. Only then start to aim a replication
- Don't change too many things at the same time. 
- Keep a running log of interesting cases: e.g. opportunities that have something unique about them that makes them hard to work with. In your models, check what happens to these opportunities. These cases are very useful in future tests you perform 
- Test requirements
  - Specific, so it’s clear what a test failure means. One test that tests three conditions will always be harder to debug than three tests for individual conditions.
  - Automated, so it can be put into a test suite and run easily. Having an automated test suite means you can quickly assess the data warehouse-wide impact of introducing new SQL.
  - Fast, so you’re not waiting forever for the test suite to finish. If a test takes longer than a minute or so, I’ll attempt to break it up into multiple tests or I’ll test a smaller sample.
  - Independent, so it can be run at any time and in any order.
- Optimise for performance - check the query/execution plan 

### Source data testing
- Create an initial gap analysis between source and BI data. This includes 
    - Raw metric numbers that are different
    - Logic that returns different results (e.g. some things show up that are not expected) 
- Sit with owners of source data tools and discuss business rules that can be implemented and we should test for. These are things that should not happen from a business perspective. The tests are daily queries that show the instances that break a test. Good practice is probably to send those queries to the business owner on a daily basis in an email that contains the dashboard with the checks.  

### Extract and Load testing 
- Monitor jobs within Fivetran and set up alerts when anything goes wrong with these jobs
- Check that data got loaded in the raw schemas (or staging environment): count by day within raw schemas. Even better is to count by day compared to source data. This will identify missing values, but also any duplicates. Another option is to compare row counts relative to previous days (new vs old). We’d expect this to be fairly consistent over time 
- Consider seeing whether any jobs have failed - e.g. if we usually load data every hour, see if there are gaps or if there are timestamps without loaded rows. 
- Get proof of missing data from the business teams and then provide a screenshot

### Transformation testing
- Monitor jobs within DBT and set up alerts for when jobs fail 
- Data quality testing: Set up constraints tests within DBT: 
    - unique
    - not null 
    - referential integrity
    - accepted values
- Where to test for data: 
  - When in doubt, have more rather than too few tests 
  - Staging level: relationships, uniqueness, not null, and other custom schema tests that we've written for our use cases.
  - Mart level: test everything that we changed with our business logic. So if we added a new column, we check that it matches what we expect to see. If we significantly changed the granularity of the model, we test that it still contains all the information that we want and that we didn't lose anything.
- Custom schema tests in DBT. For example: 
    - Revenue always being smaller than or equal to the gross revenue
    - Employee end data > start date 
    - Item levels summed up equal the total of the summed value in another table
    - Data freshness: last Fivetran updated date < 2 days ago 
- Run the entire DBT test and DBT run command regularly to make sure nothing is breaking. Do this as well just before pushing transformation logic to live.   

### BI tool testing
**Automated tests**
- Create QA dashboards with tests on some commonly used metrics that should show whether your data makes correct. E.g. total revenue. Total number of employees in seat. Total customers. Last date a certain data source was updated
- Similarly to the above, we can extend this dashboard to show changes by time period. E.g. new revenue since yesterday / last week. If values are outside of telerated values, send out an alert. 
- Run a script with the API that regularly validates all our user-facing content and posts any errors in our #data-qa slack channel

**Tests when going live**
- Sanity check the data we output. Does it make sense? 
- Test calculations — add it up, do the division, and calculate the ratios. Make sure the report itself is internally consistent and correct.
- Test at different levels in the hierarchies. What adds up correctly at the summary level may not be right when you start to drill down to the details. Sum of the parts should always equal the grand total
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
- Performance: how fast are the individual processes (ETL, how long do queries take). E.g. any query in Looker should take < 1 minute, if webapp < 5 minutes. X % of queries finish in < Y seconds  
- Delivery: how fast and predictable are turnaround times from request to working functionality)
- Quality: how accurate do we expect the data to be? If there are very complex models, can we do with slightly less quality for the sake of speed? 
- Availability of the BI team: how easy is it to reach them when questions arise? What is the response time?
- Business relevance: what can BI do for the business? 
- Data freshness: how current is the data? 
- Support speed: how quickly are tickets turned around? Use a severity scale with associated response times. Severity is depending on impact (e.g. who is impacted, what is the effect, how urgent is it) 

## Issue tracking
Use an issue tracker. This can be as simple as a Google Sheet and over time, you'll want something more robust. 

## Contingency 
You don't want a single person to be the only one capable of solving issues that break things. So instead: 
- Create a doc around most common issues and how to fix them
- Train someone in the team to solve these issues 
- MAke sure communication channels have been set up to inform the right people if things go wrong
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
- Usually done in Looker by selecting which parts of the code to keep - can also be done in Github by deleting the irrelevant code 
- Even if there are no merge conflicts, never merge a branch that has updated changes as you'll likely lose all the new changes you made. Instead, pull and merge and deal with conflicts as they pop up. 

### Git technical
Copying and changing a repository locally: 
- Create a repo
- Match this repo name in local directory
- Git init 
- Git clone (https from Github)
- Git add
- Git merge
- Git push

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
- Never allow untested code to go into production. If you don’t have existing reports to replicate, talk to the end- user and ask about their feelings of the data 
- Be critical in the review - if something looks weird - mention it. Look for: 
  - consistency
  - good user experience
  - understand how it fits in the model and if there are better ways 
  - check that there are no downstream effects 

### Prioritization
BI work on a high level is split between ad hoc requests and projects. You'll need to find a balance between the two. 

**Feature requests**
On a high level, tasks get prioritized based on the impact and the work required. Ask these questions: 

- How important is this? Does knowing the result of this analysis materially affect the company? Do we have an estimate of how much? 
- Is there a deadline? Here, also try to get to know whether there are dependencies involved 
- How accurate do you need the answer to be? Making something approximately correct can save lots of time
- What type of end result are you looking for?
- How feasbile is this to be implemented as requested?
- Key is to keep your stakeholders informed. Both on what you're doing with ad-hoc projects and during longer term projects. They might feel that a project for example shouldn't quite take as much time

**Data governance**
This is the stuff you do to keep the lights on and data flowing through all your systems. This can mean debugging an ETL error, optimizing your Redshift cluster or performing manual csv uploads. Data governance is the kind of work that no one notices when you do well, but EVERYONE notices when you don’t.

**Ad-hoc tickets**
These are the smaller requests you need to knock out day by day to get people the numbers they need. Could be a small, one off report, an update to a dashboard or a simple Excel analysis. These tend to not be particularly difficult, but if you aren’t careful they can eat up all of your time.

- Scope out how long they should take first thing in the morning. 
- If it's <2 hours, do it first thing 
- If it takes more research, consider the urgency, otherwise put it in the backlog and communicate with stakeholder

**Data errors / bugs** 
Highest priority. When someone knows something is broken, it means they look at it and fixing it will have positive impact. They also tend to be quick fixes 

**Strategic objectvies**
The projects you actually want to be working on. Could be a new dashboard for a team that hasn’t been getting as much attention as you’d like, incorporating a new data source into your data model or a comprehensive deep dive into a question the business needs to answer. This is the non urgent but very important aspect of the job. This is where your team can have the most leverage and highest impact.Try to keep this to 80/20, whenever there is nothing urgent, allocate time for the team to work on these projects. E.g. 1 hour each morning or Friday afternoons 

**Other**
Tasks without a clear goal should be pushed back - they rarely lead to impact and take up iterations of work. 

## Tracking fundamental changes 
Sometimes, fundamental changes happen to data. E.g. we changed our categories at Papier. We would then create a snapshot of all categories at a certain point in time first in the database. E.g. cateoory X and then old_category X. Similar to Tessian, calc and previous calc. This way we keep history and can compare like for lille. 

## Dashboard management 
- Make sure WIP is in the dashboard title whilst working on it 
- When a dashboard has been updated, make a note in the Slack channel to keep people up to date
- Add a badge to a dashboard when it is approved and actively managed by data team 
- Track usage of your dashboard. If a dashboard is no longer used, find out why. Find out why they used it, how they get that info now
- Always make sure dashboards are up to date and relevant. Clean up anything that is no longer relevant or not used

## Redshift tuning 
- Understand the problem. When do we run out of space - which models run then?
- Research how to identify problems as automated as possible - query plans, alerts, skew, unsorted rows, distribution errors etc. 
- Research what causes the problems 
- Implement best practices incrementally. Make single changes to single tables to specifically measure the impact. 
- Roll out measurable improvements to other tables 
- Keep full track of the changes implemented such that we can measure the impact and keep a log 

## SFTP issues
- What do our Looker logs say? 
- Confirm the data by going into the SFTP 
- Can't connect? Figure out why
  - IPs whitelisted?
  - Correct credentials? 
  - Can we connect through other means? E.g. Fivetran


**Other things to check for (e.g. during interviews)**
- Min and max dates
- Window function with date difference to see if days data wasn’t loaded 
- Day on day percentage changes 
- Day on day absolute changes
- Primary keys 
- Referential integrity 
- Potentially percentiles to sense check the data is accurate

## Dataops manifesto 
“DataOps is an automated, process-oriented methodology, used by analytic and data teams, to improve the quality and reduce the cycle time of data analytics.”

DataOps Principles
1. Continually satisfy your customer:
Our highest priority is to satisfy the customer through the early and continuous delivery of valuable analytic insights from a couple of minutes to weeks.

2. Value working analytics:
We believe the primary measure of data analytics performance is the degree to which insightful analytics are delivered, incorporating accurate data, atop robust frameworks and systems.

3. Embrace change:
We welcome evolving customer needs, and in fact, we embrace them to generate competitive advantage. We believe that the most efficient, effective, and agile method of communication with customers is face-to-face conversation.

4. It's a team sport:
Analytic teams will always have a variety of roles, skills, favorite tools, and titles. A diversity of backgrounds and opinions increases innovation and productivity.

5. Daily interactions:
Customers, analytic teams, and operations must work together daily throughout the project.

6. Self-organize:
We believe that the best analytic insight, algorithms, architectures, requirements, and designs emerge from self-organizing teams.

7. Reduce heroism:
As the pace and breadth of need for analytic insights ever increases, we believe analytic teams should strive to reduce heroism and create sustainable and scalable data analytic teams and processes.

8. Reflect:
Analytic teams should fine-tune their operational performance by self-reflecting, at regular intervals, on feedback provided by their customers, themselves, and operational statistics.

9. Analytics is code:
Analytic teams use a variety of individual tools to access, integrate, model, and visualize data. Fundamentally, each of these tools generates code and configuration which describes the actions taken upon data to deliver insight.

10. Orchestrate:
The beginning-to-end orchestration of data, tools, code, environments, and the analytic teams work is a key driver of analytic success.

11. Make it reproducible:
Reproducible results are required and therefore we version everything: data, low-level hardware and software configurations, and the code and configuration specific to each tool in the toolchain.

12. Disposable environments:
We believe it is important to minimize the cost for analytic team members to experiment by giving them easy to create, isolated, safe, and disposable technical environments that reflect their production environment.

13. Simplicity:
We believe that continuous attention to technical excellence and good design enhances agility; likewise simplicity--the art of maximizing the amount of work not done--is essential.

14. Analytics is manufacturing:
Analytic pipelines are analogous to lean manufacturing lines. We believe a fundamental concept of DataOps is a focus on process-thinking aimed at achieving continuous efficiencies in the manufacture of analytic insight.

15. Quality is paramount:
Analytic pipelines should be built with a foundation capable of automated detection of abnormalities (jidoka) and security issues in code, configuration, and data, and should provide continuous feedback to operators for error avoidance (poka yoke).

16. Monitor quality and performance:
Our goal is to have performance, security and quality measures that are monitored continuously to detect unexpected variation and generate operational statistics.

17. Reuse:
We believe a foundational aspect of analytic insight manufacturing efficiency is to avoid the repetition of previous work by the individual or team.

18. Improve cycle times:
We should strive to minimize the time and effort to turn a customer need into an analytic idea, create it in development, release it as a repeatable production process, and finally refactor and reuse that product.