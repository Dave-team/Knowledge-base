# Documentation 
Make sure that everything is documented well. This is needed: 
- Single source of truth
- Easy to handover or make sure new joiners can get up to speed quickly 
- To track assumptions on the data
- Easy to interpret by others 
- You will always need to revise why you did something in a certain way

## Documentation tips
- Start small and iterate. Focus on the essentials only. Maintaining documentation is work that should be avoided 
- Consider who will use the dictionary and how. 
- It should be a living document. 
- Collaborators should have access and be encouraged to update (version control?)
- Its importance should be acknowledged by the business and upkeep should be incentivized 
- Make sure to confirm any definitions with the business


## Data context
- Common ‘gotchas’. There will be things in the data that someone will eventually see. These things are hard to uncover and hard to understand. Track these in a doc and make it available to others. E.g. “we know that this logic is incorrect for some number of users, but the last time we checked it impacted less than 1% of users and so we ignored it”.
- Important context and history (“this is the story of why it takes 5 joins to connect our historical email data to our coupon code system”).
- Keep a running log of interesting cases: e.g. opportunities that have something unique about them that makes them hard to work with. In your models, check what happens to these opportunities 
- Keep track on what happened with the data in the past and why decisions have been made


## Business metric definitions
Create a KPI source of truth (KPI blueprint) that is signed off by the business and stored centrally, ideally in a place close to the busines (e.g. wiki / handbook). This is not about the technicalities, this is about the business logic that defines the KPIs, including the definition and the calculation.  Changes to this master KPI document could go via merge requests where relevant people are updated and can take action. Changes to KPIs should be approved by function head and a KPI review should happen perhaps every 3 months.    

Columns:
- Definitions:
    - KPI/Metric name 
    - Synonyms / abbreviations
    - Value - why do we measure this?
    - Use case – how will the data be used? 
    - Definition
    - Calculation
    - Chart views – how should it be visualized? E.g. standalone or compared to something else? Any vis preferences?
    - Grouping – by what do we want to see this data? Should that be a filter, one graph for all or one graph for each 
    - Drill down – do we need to enable drill downs to this data?
    - Format – e.g. £ or $ or duration in days, time by week / month / quarter or perhaps select in a filter? 
    - Last updated date
    - Planned next review date
- Data
    - Owner – who controls data 
    - Source – what sources are needed to get this metric
- Monitoring
    - Viewing period – how often will this be viewed?
    - Updating period – how often should the data be updated?
    - Alerts: how do we visualize good/bad (if we need it)? Do we compare e.g. against plan?
    - Security: how should be able to access / view this data? 
- Project Management
    - Priority
    - Project Owner
    - Status
    - Due date

## Data dictionairy 
Create a data dictionary that ideally is automated (e.g. from DBT and LookML combined). Items in data dictionary:  
- Desciption
- Data type
- Keys 
- Whether null values are accepted
- Sample values
- Source: source system, source table, source field name, source datatype
- Link to report 
- Transformation 
- Notes



Steps to create a dictionairy: 
- Collect dimensions and measures from the vairous reports people use
- Send the list to relevant business owners and ask to complete with remaining metrics. 
- Add defitions - use existing documentation, spreadsheets
- Send this back to the business and ask for help with the definitions not yet captured and improving existing defitions. Importantly, don’t ask “what is the current definition?” but “how should this be defined?” 
- Identify conflicts: This is a key step: root out any terms where its definition differs among teams.
- Get alignment: For those terms that differ among teams, bring the relevant teams into the same room (and lock the door). Have them discuss how and why they differ. For this meeting, there should be agreement with only 2 outcomes:
  - one team agrees to adopt definition of the other team.
  - they have legitimate reasons why they differ. In this case, agree on a new name for one or both terms.
- Get Sign off. Have the team heads sign off. This is crucial. 
- Publish the dictionairy in a central spaceaccessible to the whole company 
- If there are changes in definitions:
  - prepare a chart showing the metric with both the old and new definition of the metric to set expectations of how the numbers might change.
  - Treat that definition change like a product release: communicate the definition change in advance, tell people what to expect, and document the change in the data dictionary, such as with a change log at the bottom of the document.


## DBT 
- Comment SQL code that handles transformations
- Add table / fields descriptions 
- Other metadata will be added automatically by DBT 

## Looker
Comment any LookML transformations

## SQL
When writing a complex query, on the top of the editor, break it down: one sentence with the end goal and your approach below that. This should explain the purpose of the model 


## Other queries and scripts
Create a Github branch will all code from the data team (analysts and scientists). It shows:
- Examples of how to use data
- A great way to compare logic 
- Version control: 
    - You or someone else will probably need the same code again
    - Queries change over time so we need the ability to update them
    - The code will be useful to others  
- Make sure to create logically organized folders in the systems to ensure everyone has easy access to data – use a good naming convention with dates





