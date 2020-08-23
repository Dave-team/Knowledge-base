Be a business partner and have processes in place:
o	People requests data in a form with required fields. This could be for bugs / broken reports / field requests 
o	Slack channel for general BI questions
o	Quarterly check-ins with power users / data champions in each team
- Problem reporting - a solid process to go through when end users discover issues prior to the data team (aim for a public channel here) - avoid in-person communication 

If there is downtime: 
•	Look where no one else is looking, but don’t spend too much time on it. It is not realistic for an analyst to go into a black box and come up with great results. Instead, it should come from a problem exploration with the stakeholder team 

Pushing code:
7.	Never allow untested code to go into production. If you don’t have existing reports to replicate, talk to the end- user and ask about their feelings of the data 

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
- Always prioritize pushing projects live that you're working on prior to moving on to the next project 



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

Development process: 


Flow of tickets: 
- Cerate ticket
- Work on ticket
- PR ticket
- Get feedback - this is when ticket is in review
- Business approved functionality 
- Ticket completed 
- Notify ticket completion channel on Slack 



## Career ladder 
### Junior

Scope of Influence	1:1 - Works directly with stakeholders to answer specific questions. 
Primary Deliverables. Data: Creates reports, models, and analyses.

**Technical**
- Proficient in SQL and reporting / analysis tools
- Keeps an audit trail: ensures that their work is easy to review and can always be replicated
- Follows style guides and best practices 
- Values accuracy and performs QA checks on data 
- Develops good knowledge of the data 

**Analysis & Business Acumen**
- Able to build queries from data independently to answer questions
- Communicates clear and relevant insights from data
- Has strong intuitive problem-solving skills

**Operational skills**
- Manages data requests in a timely manner
- Generally solves problems independently, but seeks help from team when needed
- Can identify potential data inaccuracies and will manage any engineering requests required to fix an error
- Can work efficiently by juggling priorities

**Mentorship & training**
- Teaches business users how to interpret and explore data on a 1:1 basis

**Communication & Interpersonal Skills**
- Responds to ad-hoc questions with training to make users more self-sufficient in the future
- Approaches work with a positive attitude and curiousity
- Demonstrates ability to learn quickly & work efficiently
- Communicates needs and timelines clearly

### Analyst
Scope of Influence: Team - Shapes strategy for a functional team through data. Key resource for single team. 
Primary Deliverables: Insights: Identifies takeaways that guide decision-making and inspire action for functions across the company 

**Technical**
- Is SQL "fluent" and has solid working knowledge of reporting/analysis tools
- Demonstrates good judgement in selecting methods & techniques to answer business questions
- Follows style guides and best practices 
- Deep understanding of data and data transformation process 
- Documentation of work so that it all can be integrated modelled and analysed 
- Familiarity with Git and the command line to help review PRs and set up good PRs independently  

**Analysis & Business Acumen**
- Understands which questions are most important to answer before beginning an analysis project
- Can create an effective story with data, maintaining objectivity in their analysis
- Can develop a team leads-ready analysis project, report or presentation with little instruction
- Explain trends across data sources, potential opportunities for growth or improvement, and data caveats for descriptive, diagnostic, predictive (including forecasting), and prescriptive data analysis

**Operational skills**
- Has a strong understanding of the amount of time required to produce certain deliverables and can set appropriate expectations
- Writes tests and creates proactive alerts to prevent or accelerate awareness of future potential data inaccuracies 

**Mentorship & training**
- Supports training of new Analytics team members in SQL and reporting tools
- Leads functional team training on how to interpret and explore data
- Proactively looks for ways to share their knowledge
- Provide data modeling expertise to all GitLab teams through code reviews, pairing, and training to help deliver optimal, DRY, and scalable database designs and queries

**Communication & Interpersonal Skills**
- Ability to communicate a sophisticated analysis in an impactful manner to a wide range of stakeholders
- Is seen as someone who is easy to collaborate with and adds value to cross-team projects
- Demonstrate capacity to clearly and concisely communicate complex business logic, technical requirements, and design recommendations through iterative solutions


### Senior 
Scope of Influence: Cross-Functional - Connects analyses and leverages insights across teams. Key resource beyond immediate team.
Primary Deliverables: Stories: Focuses on narratives and proactive insights that help drive prioritization.

**Technical**
- Advanced knowledge of SQL and reporting / analysis tools
- Proactively drives change in how business users approach analytical problems, improving their analyses and visualizations. 
- Holds Analytics teammates to high quality standards
- Solve technical problems of high scope and complexity
- Advocate for improvements to data quality, security, and query performance 
- Understand the code base extremely well in order to conduct new data innovation and to spot inconsistencies and edge cases

**Analysis & Business Acumen**
- Understands a specific area of the business better than anyone else, is an expert in their domain
- Is sought out for strategic advice or input, based on their expertise
- Can develop an executive-ready analysis project, report or presentation with little instruction
- Defines KPIs for their area of the business

**Operational skills**
- Understands team priorities and proactively identifies when work queues need to be adjusted to match team priorities. Proactively communicates project risk. 
- Helps unblock team members
- Can identify unmet data needs and work with data engineering team to fill them, acting as the project manager from ideation to completion.
- Influence and implement our service level framework SLOs and SLAs for our data sources and data services

**Mentorship & training**
- Leads SQL and database teaching for new Analytics team members
- Creates functional team training on how to interpret and explore data
- Proactively looks for ways to improve Analytics team tools and methods; reports back to team

**Communication & Interpersonal Skills**
- Is an effective communicator, demonstrates ability to influence decision making at all levels of the company 
- Sought out as a consultant for cross-team projects
- Build close relationships with other functional teams to truly democratize data understanding and access

### Lead 
Scope of Influence: Company - Holistic view of company enables work with impact across organization. Thought leader for entire company. 
Primary Deliverables: Strategy: Uses data to create and expand competitive advantages of the company.
Represent GitLab and its values in public communication around broader initiatives, specific projects, and community contributions

**Technical**
- Technical resource for Analytics team; sought out for particularly thorny problems
- Advises Analytics teammates on improving selection of methods and techniques
- Create documentation and standards for what "high quality" means
- Seek out difficult impediments to our efficiency as a team ("technical debt"), propose and implement solutions that will enable the entire team to iterate faster
- Be an advocate for best pratices and hold everyone accountable for it. Evolve company docs around best practices where applicable  
- Be diligent in code review; review code depending on expertise level of analyst 
- Maintains the Data Team Business Intelligence (BI) tool environment (permissions, access, etc.)
- Develop improvements to data quality, security, and performance that have particular impact across your team and others.
- Vigorously identify and solution impediments and opportunities that impact the velocity and quality of the work done on the entire data team

**Analysis & Business Acumen**
- Understands several areas of the business better than anyone else; is an expert in the company's data generally
- Serves as a thought leader
- Creates & executes against a long term (12+ mo) plan to improve our understanding of their area of the business
- Defines company-level KPIs

**Operational skills**
- Understands Company priorities and proactively identifies when work queues or need to be adjusted to match team or Company priorities

**Mentorship & training**
- Develops new tools and training programs that empower functional teams and Analytics team to use data more effectively
- Introduces new analysis tools & methods to enable team to add more value to the company
- Provide mentorship for all analysts at GitLab to help them grow in their technical responsibilities, remove blockers to their autonomy, and share your knowledge across the organization
- Represent GitLab and its values in public communication around broad initiatives, specific projects, and community contributions.
- Interact with customers and other external stakeholders as a consultant and spokesperson for the work of your team.

**Communication & Interpersonal Skills**
N/A

### Management
Scope of Influence: Team 

**Managemnt**
- Manages Analysts at all levels
- Effectively manages workstreams for self and analysts, reflecting Analytics team and Company priorities
- Proactively initiates and manages cross-functional team projects
- Hold regular 1:1’s with all members of the Data Team

**Mentorship & training**
- Identifies development and training opportunities within analytics team and leads creation of plans to address


**Planning & Infrastructure**	
- Executes projects to improve the company's analytics capabilities
- Working with management to define and measure KPIs and other operating metrics
- Proactively identifies how to improve Analytics team operations and increase productivity (tools, processes, etc)
- Exert significant influence on the long-range goals of the business
- Triage and manage development priorities of analytics dashboards and data pipelines

**Strategy**
- Represent the Data Team in different company functions - be an advocate for holistic dataflow systems thinking
- Regularly give Data group conversations and participate in Monthly KPI meetings
- Collaborate with all functions of the company to ensure data needs are addressed

**Other**
Be the data specialist supporting cross-functional teams, gathering data from various sources, and enabling automated reporting to democratize data across the company

### Director
Scope of Influence: Company 

**Management**
- Leads the Analytics team as a whole; responsible for team output, manages team resources & hiring
- Sets Analytics priorities and roadmap
- Defines the role of Analytics within the organization
- Collaborates with executives and other senior managers to make strategic decisions; drives data-driven approach to setting company priorities
- Collaborate with all functions of the company to ensure data needs are addressed and the required data is modeled and available to analysts and end-users.
- Responsible for understanding, forecasting & communicating overall company performance

**Mentorship & training**
- Guides development of the entire Analytics team. Creates career ladders. 
- Creates and executes training plans to enhance the knowledge and analytical skills of the Company as a whole

**Planning & Infrastructure**	
- Sets Analytics priorities and roadmap: Creates & executes against a long term (12+ mo) plan to improve the company's analytics capabilities
- Proactively identifies how to improve Analytics team operations and increase productivity (tools, processes, etc)