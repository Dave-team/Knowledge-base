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
- Communicate a lot with the stakeholder throughout the analysis - the goal is impact.
- Follow up with the stakeholder and close the loop 
- When making important changes, e.g. in LookML, consider making multiple versions (old and new) of the metric until this is checked by the business (e.g. v0 and v1)
- Change things at close as possible to the source to avoid inconsistencies and different definitions
  - Don’t create new logic in a CTE when that logic can also be build into a source view. Join it in instead. 
  - Aim to have logic in SQL rather than dimensions if data is being repeated across files 

## Prioritization
BI work on a high level is split between ad hoc requests and roadmap projects. These different types of work need to be balanced. 

**Data errors / bugs** 
Highest priority. When someone knows something is broken, it means they look at it and fixing it will have positive impact. These also tend to be quick fixes 

**Ad-hoc tickets**
These are the smaller requests you need to knock out day by day to get people the numbers they need. Could be a small, one off report, an update to a dashboard or a simple Excel analysis. These tend to not be particularly difficult, but if you aren’t careful they can eat up all of your time.

The key here is to challenge the use case: 
- Can they ask someone who has built something similar in the past? 
- What does the current solution not allow them to do? 
  - Is it better to just do this manually for now (e.g. lots of development work or doesn't fit in current structure)?
  - Is this worth doing (impact vs effort)? We'd only want to do things that are high impact.
- Do they need this now or can it wait? 

If we still want to do it: 
- Scope out how long they should take first thing in the morning. 
- If it's <2 hours, do it first thing.  
- If it takes more research, consider the urgency, otherwise put it in the backlog and communicate with stakeholder. Particularly chunky projects can also move back into the backlog.  

**Roadmap projects**
The projects you actually want to be working on as they are working towards the business's strategic priorities. Could be a new dashboard for a team that hasn’t been getting as much attention as you’d like, incorporating a new data source into your data model or a comprehensive deep dive into a question the business needs to answer. This is the non urgent but very important aspect of the job. This is where your team can have the most leverage and highest impact. Try to keep this to 80/20, whenever there is nothing urgent, allocate time for the team to work on these projects. Prioritizations: 

- Following timelines of the business: e.g. marketing running campaigns in month X > make sure data is ready by then
- Dollar impact: potentially influencing important decisions vs nice to have (these can be quick wins to push between projects)
- Following data teams strategy: the ultimate goal of the BI team is to allow people to make decisions. Reliable infrastructure is crucial in this 
- Think about timeline of usefulness: is this important now or will it be more important in the future? 

If it isn't obvious: 
- Make a recommendation and discuss with manager
- Ask the team to fill in the timelines. E.g. PM to fill in timelines as they work according to a schedule. Finance has a clear view too. Often, it doesn't really matter and it's more a case of when people can work on it. 
- If too much on the roadmap across teams, cross functional prioritization session. 

**Data governance**
This is the stuff you do to keep the lights on and data flowing through all your systems. This can mean debugging an ETL error, optimizing your Redshift cluster or performing manual csv uploads. Data governance is the kind of work that no one notices when you do well, but EVERYONE notices when you don’t. To that extend, make sure the necessary work is done on this front and communicate the efforts more widely. 

**Other guidelines**
- Projects that require cross functional project management will take long and should start early, if they're high impact. Large ambigious projects should be pushed back if the need isn't large enough as they're unlikely to get anywhere otherwise. 
- Projects without a clear goal should be pushed back - they rarely lead to impact and take up iterations of work. 
- Anything that we don't really know how to do - either put in a scoping ticket or move it towards later 
- Set priorities but also be realistic and flexible - we may not always have the full context and then the teams will reach out. And priorities change within the business so we need the ability to change approach. 

## Project kickoff
- Check in with business stakeholder over Slack
  - Is this project high priorty still?
  - Is now a good time to kick it off? 
  - Who should be involved? 
- Get the required context prior to sending a kickoff email as you want to include the relevant context in the email. Ideally: 
  - They send existing reporting and why it doesn't work. If they do something manually now, understand what they do and how important is it to get this right vs nice to have. Ideally get a copy of their reports. This saves me from making assumptions and spending lots of time going down initial rabbit holes.  
  - I get a clear sense of impact from this which needs to be communicated
  - I look into the data structures and form an initial opinion
  - Catch-up call to confirm it all makes sense and ask whether there are any curveballs/additional complexity to be aware off prior to the session. Goal is to have as few as possible surprises. 
- Check in with other critical stakeholders over Slack 
  - We want to kick-off this project - does this week work for you? Who else should be involved from your team? Fundamentally, you want to check in with key stakeholders who are critical to the project's success and you don't want them to explode as that would blow up the project. 
- Write up email to all stakeholders: 
  - Validate the email makes sense with key stakeholder
  - We want to kick of project X. The goal is to achieve Y and we're doing this because of Z, it likely involves X
  - This meeting is to discuss X - what we discuss is always pending on the project in question. 
  - Let me know if any questions or concerns beforehand. 
  - This email helps pre-wiring, gives people time to think about it, involve others who might need to be there and generally avoids questions and speeds up the project.
- Schedule meeting + agenda in description
- If there are any concerns, check in with those people. Are these things we’d need to figure out before kick-off? 
- Those who didn't respond to the invite, quickly reach out over Slack and ask if they're okay for the kickoff 
- Follow-up with what I believe we agreed and the follow up actions. Be very explicit in follow up and make sure that everything is obvious and can’t be worked around
- For recurring meetings (e.g. quarterly roadmap updates) - email people saying when we're doing these rather than individually Slacking people. This adds context to when they get an invite in their inbox. 
- With Tech, aim to not put in a ticket and Slack Joe first - he might know an easier solution and a ticket won't be looked at for a while. 

### Requirements gathering
- What is the question we are trying to answer / problem we're trying to solve?
- What is the impact of this question and how will it help the company? (This can be different from what's asked for)
- How big is the problem / How important is this? Does knowing the result of this analysis materially affect the company? Do we have an estimate of how much? E.g. how long does it take for you to do this? How is that time spend? Is it in the analysis or something else? Confirm whether it's a nice to have or really important and impactful. Priroritize and plan for accordingly. 
- When do they need this by? If there is a deadline, that will impact priority. Here, also try to get to know whether there are dependencies involved 
- How accurate do you need the answer to be? Making something approximately correct can save lots of time
- How feasbile is this to be implemented as requested? Clarify what it'll take for us to build this and what the consequences of that could be. There might be better ways and sometimes, the current solution isn't half bad. Key also is to think if someone else already has this - that should be the first direction too. 
- What type of end result are you looking for? How and when will you use the data? E.g. in a dashboard shown in weekly meeting, to import into email tool, to put in slides, to send as schedule, to create alerts from, to put into spreadsheet that then does further transformation?
- Predict what can be build in Looker within certain timeframes and confirm whether that would be a good solution for the stakeholder. 
- Who will be interested in the data and needs access? 
- Any visualization requirements? 
- How does this fit in the grander scheme of things? 
    - Will future business changes change this model again? 
    - Are we testing if something is even possible at all? Should we MVP? 
    - How important is it to get perfect? 
    - Any downstream effects? 

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

## Senior execs analytics support
They will be less likely to want to simply learn Looker - they need answer fast. Get them to ask specific questions they can't find the answer to even when asking people e.g. in their team. 
- Set up a call and ask questions. What are you trying to achieve? 
- Know a lot about the context - there’s different ways of doing this. This will show X but has these caveats. This is another way of doing it
- By jumping on a call rather than just answering the question, we can teach at the same time 

### Anlytics questions 
Finding out what analytics is possible:
- What data do we have / can we easily get / would be more difficult to get but still possible. 
- Understand and communicate the context of the data 
  - What does this data mean and what does it capture? 
  - What can we then do with this data - any metrics? 
  - What can we not do with this data that they might want to see? Explain what it would take to get to that level of analysis - e.g. modelling, work with Tech etc. 
  - Always close of by asking what KPI’s does the stakeholder want to see? 

## Working with Tech
- Tech often thinks about outliers and edge cases that complicate things. Key is to keep it simple and my role is to put it back on track to feasible solutions that could potentially be implemented relatively rapidly. 
- Think through what a simple solution could be - if historic data by default isn’t accurate, then don’t complicate it and aim for simple logic that can be communicated and assumed without too much complexity. 
- Make more use of Coaching questions in these technical sessions - ask for context: what do these things mean? Why do we need them? Can’t we just do X? 
- Also, use coaching questions back to Tech: what do you think what a good solution could be given these complexities? Try to avoid going down a rabbit hole
- Think from the perspective of the production database
- They'll work hard to do as little as possible 
- They tend not to consider backfills so consider what options we have and if we need something from Tech
- Think about the data structure - e.g. point in time fact tables vs dimension tables that would reflect all instances (i.e. if change happens, everything updates rather than keeping accurate historical records)
- If something isn't obvious and not too high impact, it's hard to get prioritized 

### Delivery process
- Have ticket with requirements. Potentially detailed with:
    - List of fields
    - Mock-up/wireframe of dashboard
- Sign this ticket off with the stakeholder prior to development
- Regular check-ins during the incremental build. Key is to keep your stakeholders informed. Both on what you're doing with ad-hoc projects and during longer term projects. They might feel that a project for example shouldn't quite take as much time and we might overcomplicate it / it is not as high a priority to take so much time. 
- Check-in prior to final delivery to ensure required impact is delivered. Always close the BI cycle. Remember to answer questions: 'So what' and 'Now what'? The end result should not be a deck summarizing findings, the end result should be recommendations or action items that lead to real impact. Closing the loop means pushing action items through, and following up after implementation to measure real impact.
- When data doesn’t line up - inform stakeholders before they find out about the differences themselves 

### Tickets
**What are we trying to achieve?** 
1. The PM team needs detailed ad data for Facebook (more granular than campaign level).
2. We want to report on our affiliate partner like we report on other channels
3. We launched Digital Foil as a new product in December and we want to add it into our Product reporting 
4. We want to create team wide KPI dashboards in Looker. 

**Why is this important?** It needs impact and it needs to relate to strategy
1. This will help them have more accurate reporting and make more detailed decisions to optimise our marketing 
2. Affilliate channels are a focal point of PM's strategy to grow marketing spend (and thus Papier's topline growth)
3. Since launch, digital Foiling has had early success, and is part of our future strategy to sell Stationery products and "Own the Desk".
4. The data team wants "Data at the heart of every decision".  It has been difficult to onboard new hires to our Looker data-culture, but we believe a KPI dashboard will help give more examples of Papier KPIs and how to use Looker

Suggested approach 
Checklist where appropriate

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
- Don't just check most recent data, go back in time too 
- Test for nulls in final table
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
    - Add good comments to the code 
- End users find Looker easy to use 
    - Naming conventions are applied
    - Explores are as short as possible, with groupings applied. Each explore answers specific questions
    - All relevant fields have a name used in the business and a useful description. Make sure this description makes all sense standalone and covers enough context. Always ensure that every single field has a description - even when seemingly obvious and hidden. Good way of getting descriptions is from the API docs
    - The labels are clear and describe the data 
    - Dashboards are easily accessible to end users 
    - Double check usability of the new Explores built

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
    - When modelling a view in an explore, think about the granularity and the joins required. Always aim for the least as possible joins to improve performance 
    - If a PDT is a pain to build, consider limiting the size of the tables in the where clause. 
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
- What is the impact and the so what of the change? 
- If it's changing data, is it communicated and approved with the stakeholder? 
- Screenshot of updated part of the DAG
- Validation of models: 
    - include output that confirms model does what is expected. E.g. link to in development Look, or a query that compares the data. 
    - Perhaps a screeenshot of content valdiator and LookML validator 
    - Screenshot of the dimensions and measures in action with their relevant links
    - Where possible, comparison between source data 
    - Where relevant, add any other QA relevant information here. When a screenshot and a link to a Look could help, include it. If the team could discover something that doesn't look right, be proactive and mention it directly. 
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
- Overall, focus on the positives in a PR review. “quick comment on X - all else looks great to me."

## Trouble shooting checklist 
Overall, just eliminate all simple options that could go wrong first. Wherever possible, put the work on someone else and protect your own time. 

### Missing data trouble shooting
Arrive in the morning and data isn't up to date 
- Did the PDTs run? If not, why not? If full disk errors, delete redundant tables in Redshift. 
- If they didn't run, what is the last date in source tables? Is anything wrong in the ETL - check Fivetran/Stitch
- If it's a tech issue and we need to verify whether the data is loaded correctly, test for: 
  - Connector succeeds
  - Max dates
  - Data by hour looks good 
  - No gaps in the data (e.g. subsequent order IDs) 

### SFTP jobs don't work
- Does Looker say it’s sent? If no, that's the issue. If yes, continue. 
- Send the files manually - does that work? If yes, might just be a one off schedule issue. If no, continue 
- Make sure the connection details are the same. Are they the same, continue
- Ask them: 
  - Show screenshots of the data being sent successfully 
  - What are they seeing? An error, seeing the file but no data in it, etc.?
  - Do we send it somewhere else in their system?
  - Can they confirm the structure is the same?
  - Do we have the right connection details? 

### Stakeholder notices differences against source data 
- What results do we expect to see? 
- Do we pull the right data? Are the different sources supposed to be comparable? Are we looking at the same definitions? 
- Is this a recent change? What is correct in the past?
- Does this happen across all segments? 
- Did anything change that could be the cause of it? 
- If that didn't answer it, consider whether it is a problem worth investigating - timebox an initial look into it. If it'll take more time, communicate and ask for importance first. 
- Look at our own data: 
  - Does the logic make sense? I.e. is the logic used the correct logic to answer the question at hand? E.g. with attribution - are the UTMs set-up correctly? 
  - Is our data correct? I.e. can we show it does what it's supposed to do, accurately? (no duplicates, etc.)
- Compare the outcome between sources at a low granularity. E.g. we can compare our attribution against Google Analytics. 
- It's possible that data is captured differently between different tools. E.g. attribution is not always position based, sessions are defined differently etc. 
- Sometimes, we simply don't know why something happens. And that should be okay too. 

### We doubt whether our web tracking data is accurate 
- Look at examples of journeys - is it something we model or do we specifically attribute it this way? 
- Segment the data: 
  - Only recently? 
  - Why channel, which campaign? 
  - Any other similarities 
- Bring this context back to the teams: do they know what's happening? 
- Look again using the new context and do some deeper research
- If not solved, involve the Tech team and/or the wider community and/or the vendors/sources directly.

## Changing important models
- Be clear on timelines with stakeholders: clarify that something is priority + when you expect to be able to show something 
- Don’t push something when its risky to push. E.g. don’t push Exec Explore changes when the Trading meeting is happening on the same day 
- Understand who else might be impacted and make sure that they are aware of the changes and have the context to avoid confusion 
- When some changes are large, realise that a review and build process may still have issues in them. Communicate with the stakeholder that ideally they’d also keep an eye out for the metrics 



