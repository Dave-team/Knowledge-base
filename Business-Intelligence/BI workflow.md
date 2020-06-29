Be a business partner and have processes in place:
o	People requests data in a form with required fields. This could be for bugs / broken reports / field requests 
o	Slack channel for general BI questions
o	Quarterly check-ins with power users / data champions in each team
- Problem reporting - a solid process to go through when end users discover issues prior to the data team (aim for a public channel here) - avoid in person communication 

If there is downtime: 
•	Look where no one else is looking, but don’t spend too much time on it. It is not realistic for an analyst to go into a black box and come up with great results. Instead, it should come from a problem exploration with the stakeholder team 

Pusing code:
7.	Never allow untested code to go into production. If you don’t have existing reports to replicate, talk to the end user and ask about their feelings of the data 

### Change in transformation logic 
- As always, create a pull request
- In the review, compare the dasbhoard pre and post change 
- Validate changes with audit macros. Compare columns and use the dbt equality utils macro to compare record by record. Consider using dbt helper. Things to compare can include: 
    - Row count
    - Sum of key column (e.g. revenue)
    - Distinct values in column 
- If a business user is impacted, involve them with the review process



## Issue communication 
**Stakeholder identifies issue**
First, understand the problem

- Wrong data doesn’t always mean wrong. It’s often just a mismatch between expectation and reality. ‘Wrong’ means a difference between expected and presented or with both, backed up with evidence. 
- Begin with questions. 
    - What results would I / you expect to see?
    - Where would I / you check this number to know it is correct? (i.e., source of truth)
- This often leads to three different buckets: 
    - The data is confusing (but not wrong). E.g. the definition of what is measured isn’t very clear. 
    - There might also be a delay in the data - it’s perhaps not completely recent. Make sure to always include the calculation and the data freshness when communicating with end users 
    - The stakeholder is using a faulty source to “check” the data (which is not wrong). E.g. different web tools might calculate things differently. It is not wrong, just different and this can be proofed looking at historical differences in the data 
    - The data really is wrong - this can happen and it’s normal given the complexity involved around data. Our goal is not to prevent all errors from happening, it’s to make sure that errors are small and get caught / resolved quickly 

If there is a problem, we need to go to issue communication
**Issue communication**
The most efficient way to inform your stakeholders is through the platforms / methods they use to consume the data. If your stakeholders consume the data through an automated report emailed to the team every morning, reply all with an explanation of the issue and the estimated time to resolution. If your stakeholders consume the data through your business intelligence tool, display a warning at the top of business intelligence tool (this is a very effective method of communication, but is not available on many systems). If the issue is severe, send out an email, send out a Slack message and even go round to people to tell them about the issue. It is your duty to ensure stakeholders are aware. 

When you catch a problem and correct it, notify the stakeholders in case they also saw something funny and didn’t mention it, and to demonstrate the pro-active monitoring to build trust.





•Prioritization: 
•	How important is this?
•	Is there a deadline? Here, also try to get to know whether there are dependencies involved 
•	How accurate do you need the answer to be?
•	What type of end result are you looking for?


Prioritization:
-	Prioritize these requirements. Take into account how feasible it is to implement what has been requested  
-	Because we work in agile, we first build anything that is high priority. Then, over time we just keep adding new things. 


Project delivery 
-	Deliver things that are small and look ahead to see if anything requires per-work early on. This will uncover whether you’ll be blocked or not and it can pre-ampt future actions



General

-	When end users create a ticket, make sure it includes a relevant tag and let them assign a person from their relevant data team 
-	Include a Slack channels where requests are automatically posted. Then review these requests and ask the necessary questions in a thread. 
-	When something requires back and forth, consider setting up a Google doc to work cross functionally



•	Make sure WIP is in the dashboard title whilst working on it 
•	When a dashboard has been updated, make a note in the Slack channel to keep people up to date
•	Add a badge to a dashboard when it is approved 


Keep dashboards up to date 
1.	Review your KPIs – track only what makes sense and what is important to the business 
2.	Track usage of your dashboard. If something used to be used but no longer, it has possibly become obsolete. Sometimes, the dashboard might not actually answer the relevant questions. Maybe people don’t understand it. Talk to people and understand their requirements 
3.	Speak to your users – what do they think of the dashboards? Talk through the users and identify how it is actually used 
4.	Build starter dashboards. Create different dashboards depending on the seniority of the people in the org. 

- Always make sure dashboards are up to date and relevant. Clean up anything that is no longer relevant or not used
