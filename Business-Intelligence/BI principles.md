# BI principles

## Links
- Gitlab data team: https://about.gitlab.com/handbook/business-ops/data-team/
- Gitlab models: https://gitlab.com/gitlab-data/analytics/-/tree/master/transform/snowflake-dbt
- Rittman Analytics: https://github.com/rittmananalytics
- Fishtown Analytics: https://github.com/fishtown-analytics

## Mindset
Think about BI as if it's a SaaS product and the users are your customers. Approach it as running the growth team where you improve your offering step by step by running experiments and analysing the results and always solving solutions for your end users first. 

## Principles
### Data principles
- Data is correct/accurate and quality controlled. Shipping out bad data quickly destroys the team's credibility. The business needs to trust the data 
- Data is available/accesible to answer relevant questions 
- Data is current and timely (e.g. up to date with no gaps)
- Data is consistent/coherent when looking at it in different ways and there are SSOT 
- Data is complete (i.e. no missing data)
- Data tools are fast and easy to use 
- Data is democratized and the BI tool is self service
- Data is well documented and defined with a clear, unambigious meaning 
- Automate as much as possible 
- As much as possible is defined in code
- Data is version controlled

### Process principles
- Great support, documentation, onboarding / training
- Great business partnering to help improve business
- Code is version controlled and development is approved through pull requests with code review
- Code is modular - there should be one version that is used throughout an entire project - data needs to be conformed
- We work incrementally: 
    - Deliver continiously 
    - Demonstrate early success 
    - Communicate results 
    - Get feedback 
    - Improve

## Values
- Humility. Be humble and nice. Realize we are not the domain expert - the stakeholder is. When we make mistakes, be honest and build a deep of trust. 
- Helpfulness. Business Intelligence is a support function to help the business make decisions from data. Don't be afraid to do some chores to help others as it will greatly improve relationships and you will get more context. Also be very mindful of the burden on other teams. If you come with a request or an ask from another team, it’s important that you let them know you’re interested in partnering with them to make the process as easy on them as possible to minimize disruption to their workflow.

## BI definition
Business Intelligence is about making sure that people get the insights from the data they need to perform their job, in an easy way. 

Business Intelligence: delivering the right support to the right people at the right time. It’s about having the ability to execute, monitor and control business processes, along with insights about how to improve them. 

Data is needed to:
- Make decisions – you don’t want to rely on your gut. Do we invest in more people? Do we cut this product? Do we invest in a marketing strategy similar to the previous one? Should this sales person be let go? 
- Solve problems – diving in the idea can help getting to the root cause of a problem you’re seeing
- Track performance – without data, you don’t know where you are going 
- Improve business – by deeper analysing the performance (e.g. by segment, by time) you can uncover trends that lead to ideas to improve the business. E.g. improve customer experience, reduce costs, improve conversion rates.
- Understanding the customer / market: we can track how customers behave, you can identify your personas

**BI benefits**
- Central space for multiple data sources that can be combined. No more information islands and a more holistic view over entire business (e.g. marketing funnel) and customer journey. What happens to the customer we spent so much on to acquire? How do we attribute it? 
- Scalable. Everything is written in code with documentation that is easy to debug. Spreadsheets are hard to maintain and bedug as well as to understand for others 
- Time saver. Saving lots of time doing analysis when people can use a tool like Looker - time can now be spend doing higher impact activities
- Improve data quality and quality control as the data sits in a central environment managed by analyst and best practices in data testing are employed
- Single source of truth documented centrally. Instead of different spreadsheets created by different people with different definitions/logic. This documented environment allows scaling and increases transparency across the business 
- Easy access to insights 
- Allow more complex analysis using data transformations
- Increased data security – no more spreadsheets flying around over email and in the cloud 

**Why do we need data?**
- To make decisions based on facts rather than our gut 
- To track performance
- Ultimate to help improve business performance 
- To sell BI let the stakeholders jump in. Your stakeholders can say exactly how much value you bring to the table and it’s incredibly hard to try and convince others what you think you’re bringing to the table. Let them do the talking and when you need more resources, let the business convince the CFO why they want more data support. 

## Impact 
The real value of data comes into play when it actually helps the business. The goal is to answer" 'So what?' and 'Now what?' and the end result should be recommendations or actions to be taken to improve the business. And then we need to follow through to ensure this impact has been delivered. Closing the loop means pushing action items through and following up after implementation to measure real impact. Watch out for taking the data for granted is the biggest bad habit to watch out for when analysts join the team. This leads to incomplete business logic and bad data that leaks into analysis. Shipping out bad data is adding negative value to the company, and very quickly destroys an analyst’s credibility.

To get the maximum impact from data on the business, I first need to understand the business well: 
- Understand each team's main priorities and their KPIs  
- Think as a stakeholder - what are their main business goals? Be curious around their business function (Google, YouTube, Looker Blocks) and figure out how to make their lives easier and help them achieve their goals 
- Regularly meet the different stakeholders to understand what is in their pipeline and how data can help

Once I have the context, I can establish myself as a business partner - the goal is always to support them reaching their goals. This can come in the form of: 
- Automations: when building solutions, make sure that it integrates seamlessly in the stakeholder's life to ensure maximum impact - a dashboard doesn't impact the business, the actions from the dashboard do. Use actions, integrations, and other automations to make decision making automated. 
- Data and analytics improvement. 
    - Knowing the context and knowing the data well, I can suggest ways to further improve the reporting in place. A huge sign of effectiveness as you progress in your role is the ability to identify and answer the questions that influence decisions – this is not always what someone asks for
    - I can also start to provide insights to various reports we send out. Add comments to analysis, proactively answer questions and become a trusted business partner. As long as data team is being updated on this, we can follow the crumbs, go deeper in the analysis and provide insights 
    - I can start to find new use cases for high impact data analytics project based on knowing the goals of the stakeholders. For example, are we doing manual forecasting? The data team could support. Or I can explore some data that leads to new insights and present this to the business 

*Case in point*
- Reactive: Stakeholder: ‘Please give me data on X’. Me: Okay – here it is. End of discussion. This is extremely entry level 
- Good analyst: Stakeholder: ‘Please give me data on X.’ Me: ‘What do you want to get out of the data? Is it to help guiding a decision? Why are you looking at this specifically? Them: For reason X,Y,Z. Me: Okay so you want to know whether X? Stakeholder confirms. Me: okay, there are some other things you might want to consider and previously we’ve seen this. Them: okay, can you show? Me: yes. Then get back and agree on some additional analysis required to solve the problem at hand. 

## BI monthly sessions
- Review dashboard
- Review roadmap 
- Good / Better next time 
- Review content validator 

## Quarterly Sprint revision
- Duplicate current sprint
- Move duplicate to Archive
- Rename current sprint to the right quarter 

## Roadmap 
- Meet people who might have something, even if we don’t know specifically yet. The goal is to keep the relationship warm and to make sure people feel heard 
- Meet with Tech after the roadmap is completed as things will have implications on their team 
- Be wary of putting too much on our plates 
- Slack people to get an update on projects on the roadmap 

### Yearly roadmap planning 
**Create an initial list of projects from the business's / team's roadmap**

**Meet Heads of Teams for 30 minutes** 
See agenda email below. During these meetings, let them lead and be able to refer back to the initial list of pointers we already planned. Ask for a copy of the team’s roadmap for reference and to inform own roadmap 
The end goal of what I need to know from these sessions: I need to lead a team to the successful completion of the projects. Questions to ask: 
- Get context 
  - I haven't been involved with this, can you give a two minute summary of what we're trying to achieve?
  - What does this mean? 
  - When is this expected to happen?
  - How far in the process are you?
  - What are the next steps on your end?
  - If teams are looking to do something but nothing specific > when are you planning to look into it? We can put it in as a placeholder so we’re aware of it 
- Why is this important? 
  - Look for impact
    - What decisions does it drive?
    - What happens with the data? 
    - Does it become more important over time? 
    - What is the dollar value of this? 
  - How does it relate to strategy 
  - If this isn't clear, or the effort may not be worth it, it's not being prioritized 
- How can BI help with this? 
- Provide data context: 
  - Do we already have the data? 
  - Is there an easier way to achieve the goal?
  - If new marketing partner, clarify that the stakeholder needs to set up good UTM parameters 
  - If we integrate new data, do we need to get it into attribution too?
  - If a new channel, can we track in checkout survey? Or by discount codes? Try to think through ways in which BI can help achieve the goal
- If anything more important than others? Try to get their understanding of priority between all relevant projects 

Speaking with execs: they won’t know the details so avoid forcing them to give details and timelines. Often, what is required is some initial kickoff meeting with a key stakeholder and then details will follow. Also, often you’ll find that things aren’t obvious that they need to be done at all / how long it might take etc. Say ‘We don’t know if we can fix this. We can look at. We’ll put it in there and see if we can something.’

**Take notes in a doc**
- Context of the project. 
  - Data involved. Where it is or where we can get it
  - Make sure you understand the data
- Why is it important?
  - What is the impact 
  - How does it relate to strategy
- What needs to happen? Have a high level understanding of how I'd solve this. 
- When does it need to happen? 

**Plot projects on an excel BI roadmap by quarter**
- Anything we’d want to do, but not sure how: italics 
- When a project is likely to take longer (e.g. tech) - extend to the next period 
- Mind the formatting: nicely outline different cells. 
- If projects fall under a parent but if it consists of separate pieces of work, break the work down, especially if there are not sequential and will be done in different time periods. 

**Confirm with stakeholder**
Once the draft roadmap is ready, email it back to each stakeholder (for their team) to see if it works for them

**Divide the projects across the team**
- Assign projects to others even when I’d be a blocker initially to e.g. get some integration set up
- Anything that is hard and technical, me. Anything that can be done in Looker, other team member. 

**Share it to BI, more broadly, put it in Notion, and start making tickets**
Tickets include:  
- What are we trying to achieve? This is high level what we try to do 
- Why is this important? This needs to be both in terms of impact and linked to the strategy. If it doesn’t fit in the pillars of the company, it should feed into data’s strategy  ‘Data is at the heart of every decision’. This means that data needs to be: Accurate, Actionable, Easy to use, Timely  
- Stakeholder
- Suggested approach
- Examples to tie back to impact and strategy: 
  - Affilliate channels are a focal point of PM's strategy to grow marketing spend (and thus Papier's topline growth).  So we need reporting on this like other key channels (FB and Google)
  - Digital Foiling has had early success, and is part of our future strategy to sell Stationery products and "Own the Desk".  Therefore we need to be able to report on these designs better
  - The data team wants "Data at the heart of every decision".  It has been difficult to onboard new hires to our Looker data-culture, but we believe a KPI dashboard will help give more examples of Papier KPIs and how to use Looker

*Other tickets notes*
- For projects planned for later in the year: take (*) out and put back in roadmap queue at the end so we have it for next quarter. Add a (Q2) in front so it’s clear
- For projects no longer in roadmap: normal queue as they’re probably still relevant. 

**Communication and check-ins**
- Check in with stakeholders ~Quarterly (dependent on amount of tasks and what's upcoming) to keep the roadmap up to date. When there is limited clarity on what needs to happen on projects, discuss over a quick call or in a regular meeting what the next steps are. 
- Communicate context, impact, and strategic importance constantly. 

**Common projects**
- Integrations of new tools. This can relate to helping the decision, set-up, integration. However, it’s also important to define how BI works with the tool - who has ownership over requests, what type of questions should be answered in Looker versus in Content Square. What are the rough differences in metrics between the tools? Who will drive this tool and take full ownership? Is this something that’ll sit with the Product Manager directly? 
- New features on the website and working with tech to ensure the right fields are available for ETL and impactful reporting 
- More advanced analytics
- Support in automation of reports 
- Support in testing (e.g. A/B tests) 
- If teams plan new campaigns, understand how they will be testing the performance of these 
- If new things are being developed (e.g. NPD) - will that change anything in our reporting structure? 
- If we want to use e.g. a new agency, we’ll likely have to support getting them the required data 

### Quarterly revision
- Always revise what has been done previous quarter first 
- Go through the planned roadmap as per the beginning of the year 
- If something is no longer a priority, it goes back into the backlog. Only keep what has a clear reason, context and next steps 
- Priority is based on estimated £ impact - PM gets priority over brand 
- Whenever someone requests something, make sure they still put in a ticket 
- Roadmap sits in an Excel sheet 
- Questions to discuss during session: 
  - Are there any projects we had planned we can de-prioritize?
  - Is there anything additional I'm missing for Q4?
  - Looking ahead to 2021, when do you think you will start planning the new year?

## Relationships
Build strong realtionship with the tech and the business teams. The goal is to establish trust that makes me a business partner they want to work with to achieve their goals. 

**What to discuss**
- What the team is working on - updates on projects
- What is in the roadmap
- Whether data support is needed
- Anything that could influence data: new product / campaign releases, A/B tests, new KPIs 

**Why build relationships:**
- It will go a long way to increase their effectiviness when things need to be done
- People will be more likely to come to you to ask for help and to tell you when something is wrong because people want to work with you and are comfortable to be honest 
- Context and understanding of the goals which make an analyst better equipped to help the team get impact from data 
- The analyst will understand the business complexity and take it into consideration when doing his / her work 
- Can more easily pick up projects where data can be of benefit or can easily identify opportunities for improvement with all context 
- It is a lot easier to get good insights from data. If someone without real understanding produces data, they just provide data, no insight. You need analyst to really know about the team and their goals and processes and complexities. You want to get to ‘aha’ moments

### Expectations management and stakeholder commitment 
- Business teams are responsible over quality of source data. Ideally, this is part of a process that happens regularly on e.g. calendar invites so there are more eyes to ensure it gets done  
- The business should work with data team to evaluate vendors: do they have an api we can use? Are they supported by Fivetran / Stitch? Think about how it fits in the existing architecture
- Source data should contain unique identifiers to join the data accross sources 
- Changes to KPI defintions need to happen centrally 
- Make sure the data team is up to date on any changes or important events in the business. The data team is the owner of the model. If things change, it's crucial to update this. Help the Data team to be a partner in those changes, not an afterthought
- Stakeholders should feel ownership over the data they use. If they see issues, it should be communicated with the data team
- Underpromise and overdeliver. Because of the nature of data it's hard to estimate how long projects will take. Give an estimate that assumes that everything will take longer than plannedand keep the stakeholders in the loop throughout the project
- Make sure to create understanding that data projects take long and that we need to prioritize what to work on 
- People want more than is asked for? Mention that wasn’t scoped - for now we focus on smaller scope
- When we deal with manual data or otherwise source data that needs to change, make it either the responsibility of the team to change things (i.e. changing Xero data fields) or make something part of a process (e.g. onboarding process: add data to sheet with new joiners). Always try to keep things maintained in the source data and avoid using manual interventions whenever possible.  
- Don't be afraid to push back - if utm campaign names and normal campaign names need to match - push this back to the stakeholder 

**Ways to build relationships:**
- Informal: 
    - Lunch, kitchen chat, informal coffees 
    - Ask the about their lives outside work - kids, commute, anything relevant to the person. 

- Formal
    - Attend meetings
    - Pairing sessions to shadow the business user and learn about their thought process, learn the tools and their limitations. This will give the analyst great context and understanding of data complexity 
    - Catch-ups
    - Quarterly session with the business to work on data roadmap

**Evangelize - always evangelize**
Sell your work – have a pitch ready at all times. Explain the value of data and what we’re working on. Once we build something useful, share with others who might benefit from this data too 

From: “I am helping teams reaching their objectives by making using their data”. To: “Most teams are currently struggling with their analytics. The data sits in Google Sheets, doing the analysis is taking a lot of time and most teams are not currently getting the most value from their analysis. What I will help you with is getting a centralized solution in place, that combines the data from the various source systems. All your reports will then sit in a BI tool that gets automatically updated. The benefits include:
- You can analyse more things as we bring various sources together and we can combine data from these sources
- Creating your reports goes from hours to seconds 
- Because it’s centralized, there won’t be any differences between definitions and calculations, meaning that teams won’t be reporting on different numbers for the same things. Practical introductions to new company:

## BI team 
### Organization
Hub and spoke model works well, where some analysts are part of the central data team (hub) while others are embedded (spoke) or distributed (spoke) throughout the organization.
- Central - those in this role report to and have their priorities set by the Data team. They currently support those in the Distributed role, cover ad-hoc requests, and support all functional groups (business units).
- Embedded - those in this role report to the data team but their priorities are set by their functional groups (business units).
- Distributed - those in this role report to and have their priorities set by their functional groups (business units). However, they work closely with those in the Central role to align on data initiatives and for assistance on the technology stack.

### Roles
Data Engineer: Data Engineers build custom data integrations and manage over pipeline orchestration in order to ensure that the data brought into the data warehouse or data lake is correct. They develop and deploy machine learning endpoints, perform data warehouse optimizations, and maintain the data platform. Data Engineers are technically minded and always looking for ways to improve the technological aspects of the data stack.

Analytics Engineer: The analytics engineers deliver well-defined, transformed, tested, documented, and code-reviewed data sets to the organization. Because of the high quality of this data and associated documentation, business users are able to do their own analysis while getting reliable, consistent answers. Analytics Engineers apply software engineering best practices to analytics code through the use of version control, testing, and continuous integration. They also train business users on how to best use their business intelligence tools.
 
Data Analyst: Data Analysts perform deep insight work, such as determining the reasoning behind observed trends. They work with the business users to understand data requirements and then translate that information to the rest of the data team. They build critical dashboards, perform forecasting, and push the limit of end-user analytics in order to derive the most value out of the data warehouse. Analysts can provide the most value when they have ownership over the decisions being made from data. This means having a deep understanding of the system and a close working relationship with stakeholders, so that they know enough to provide recommendations and proposals for changes and actions. Analysts should have a strong stake in the success and failure of the teams they support.

### OKR planning
- Coming from the higher level BizOps/Finance KPIs and the needs of the data team
- Best way to get them is brainstorm with the data team

### Workload 
- 60% of time is spent on achieving the OKRs, 40% is spent on ad hoc / exploratory analyses
- Use a ticketing system and insist anything that takes 30+ minutes is in there. This is to track performance of BI team and to see where the time goes 
- Add stakeholder teams and owner and any tags to tickets 

### Sources for work 
- Communication with the business - both formal and informal that can lead to projects or insights. Ask them what they have in the roadmap, whether I can support in that or whether there is something else I can help with during catch-ups. 
- Being up date on business initivates can spark investigations where data can help. Work closely with the business team to understand priorities, changes made and strategy of the business. Know the marketing calendar so data peaks won’t surprise you. Instead, you can be proactive and directly measure the impact a certain campaign had to then report this back to marketing. E.g. the business starts to hire a Head of Retention or a business focus is Brand Awareness - advise on how data can support. 
- Explore something that could lead to insights. Look where no one else is looking. People often don't know what's available until you show it to them
- BI platform optimization - testing, automation, documentation, identify best practices and new tools
- Constantly keep your ears open for things that people want built and add these items to the backlog
- Be more aware of changes that are happening. I might get an email from someone – go deeper and understand how my field of work will be affected 
- Make sure to really know what data you have at work:
  - Follow crumbs: when you hear something about data you don’t know, follow up and understand their process to get the data 	
  - Track the trackers: people who own tools, make sure to build a good relationship and keep up to date with the changes they’re making. 
  - Know the code. This allows better conversations with those actually creating the code. Keep an open line of communication and share the code desired most often 

### Communication
- In any BI communication - with senior stakeholders, to the entire team, to the BI team focus on the sell, the vision and the impact. Why do we do certain things? How does it relate back to our goals? What is the so what?  
- Key is to create a safe place for team members to ask questions and be vulnerable. Set the example by sharing your own struggles. 
- Make sure that everyone gets feedback from others early on and regularly during their projects. Especially when doing new or complex or highly important 
- Analytics weekly
    - Talk about the business: everyone should understand what drives revenue and profit, which parts of the business drive this, what is the focus / priority of top management 
    - Show and tell. Use time during your team meeting to have a team member present something they have learned or done. It's beneficial to plan this meeting around the end of each sprint. This has many benefits: 
        - Team can ask claryfying questions
        - Team can poke holes in methodology
        - Suggest areas for future research
        - Holds people accountable
        - Spreads the knowledge in the team
        - Allows cross team input
        - More opportunity for review and it can catch errors (‘I have done something similar before with different end results’)
    - Discuss blockers
- BI Slack channel
    - Open channel for anything - it is a safe place to ask questions and discuss shortcomings 
- BI Business Slack 
    - Inform about updates to e.g. Looker
    - Inform about outings/issues. E.g. Looker / AWS down, Facebook job delayed
    - General BI questions 
- Quarterly check-ins with power users / data champions in each team
- Form for end users to fill in. This can be simple requests as well as bugs / issues. Include a Slack channels where requests are automatically posted. Then review these requests and ask the necessary questions in a thread. 

## Education
There are three main types of education you need to master before you can call yourself an expert analyst: mentoring your data team, empowering your end users and enlightening your executives.
- Data team: your job is to take their innate curiosity and help them use it to find answers. On a practical level this means lots and lots of questions to answer. Be patient (remember how long it took you to get this stuff!), but also avoid immediately showing them the answer as soon as they ask. Rather, point your junior analyst in the right direction and let them figure it out themselves.
- End users:  The important thing for these people is to make sure they understand the metrics and information contained in your reports and have a sense of the nuances contained. You want them to be able to spot trends, notice irregularities, and point out mistakes you may have made. With these folks, it’s best to focus on the business applications of the individual reports you make for them. The best way to do this is to have a number of review sessions after creating a report where you view it together with them and point out interesting factors. That not only helps your end user gain a sense of how the report works, but helps you spot things you may have missed.
- Executive team: They are less likely to care about individual reports and more interested in the overall story of the business and the insights which metrics can bring them.

## Strategic input by BI 
- Challenge the numbers and see where opportunities lie. Product X is performing well/bad >> do we know the root cause behind that change? 
- General things cared about by executive team: 
  - Trends: week on week %, year on year for week %, variance to forecast. Segmented over store/category
  - Focus on anything relevant to the business at that time: e.g. newly launched products, marketing calendar 
  - Way to outline focus points: scorecards with key KPIs - green or red with next steps especially when something is red 

### Issue communication 
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

**Fixing issues with Tech**
- What is the challenge
- What are the next steps to fix the issue
- How could we have captured it proactively rather than retroactively 
- If this went wrong, what else could have gone wrong? Perform a health check
- Backfill the data. 
  - Create a backup of data you’re trying to change
  - Only change what really needs changing (e.g. only the orders affected)
  - Test changing a few orders first - then roll it out to the rest
- Impact analysis 
- Post mortem
- When communicating:
  - High level alert: we noticed this is an issue - we’re looking into it 
  - When providing more context: Flesh out the impact and context with Tech first and then communicate the scope of the issue: This impacts X&Y, but it doesn’t touch anything else. Next steps are YY and we’ll keep you updated here 

## Partner meetings
- What data do we/they need? 
- How do we extract or send this data? SFTP, S3? 
- Replication frequency
- Clarify next steps in an email 
- Clarify who the main POC is 

**Fivetran meeting**
When working with a vendor, have regular (e.g. monthly catchups). Make sure to track their performance. If and when something looks odd, you’ll have proof and you can ask for refunds when reasonable.

Monthly catchup questions:
- Does the team have questions?
- Any performance issues? E.g. connectors not working? 
- How is MAR looking? Any outliers? Are the MAR in Looker equal to MAR in Fivetran account?
- Any new projects our end? E.g. new connectors / resyncs, etc
- Anything else from either side? 

 ## Other
 ### Data readiness
- Strong business sponsorship
- Clear data use cases that warrant a data function. I.e. without data the business will suffer and there are no other ways of answering the questions
- Source data has been looked at as is in a fairly good state 
- Available resources: people are in a state where they know that BI is needed and spend time on it 
- The available data needs to warrant a BI system and the implementation needs to be feasible 

### Indicators that BI is needed 
- Out of the box reporting by tools is no longer sufficient and creates knowledge silos
- Heavy maintenance to sustain in Google Sheets / Excel
- Increase in data volume exceeds limits of current solutions
- Unclear definitions of core KPIs resulting in conflicting analysis and communication
- Growing demand for more advanced analytics
- Frequent data inconsistencies issues and consequent lack of trust in reports
- Increased complexity of calculations / logic due to more advanced business logic
- Requirements to create dashboards visualize performance from multiple sources. Or in general: requirements to combine data from multiple sources 
- Lots of time consumed on data analysis
- Many manual tasks such as manual historicizing of KPIs per week

### Reproducability 
Each piece of work should benefit the wider team / company. Often that means that we should spend 30% more time to make something reproducible: 
- Do things in Looker rather than SQL so others can access it. Eventually people will use the queries wrong and get inconsistent data or it will break often and becomes hard to maintain. If we can't use Looker without doing something custom and complex, can they combine Looker to pull and Excel to manipulate?   
- Add dimensions to Looker and let the whole business access it 

This will mean that everyone can access the data, people will build on top of your work rather than you having to build from scratch each time. It helps soklving business problems faster and encourages collaboration between the business and BI 

If we cannot have something centrally stored and managed (e.g. in Looker) we want to make it reproducible in notebooks: 
- Makes it easy to run code again with the different tiles that run independently 
- Different people running the code should output the same results
- It's much easier to read and you can create a story going through all the different steps 
- Each tile can have multiple outputs making it much more efficient to actually develop 

### Measuring BI success / BI KPIs
- Improved business performance: more revenue / less costs 
- Time savings in doing analytics 
- Whether employees get their questions answered
- Number of users of BI platform / time spent in BI platform 
- How often people use the BI tool - dashboard/explore usage statistics
- Centralized definitions and increased consistency 
- Number of uses of the data 
- Delivery performance: roadmap/project completion, Number of tickets / FTE or team
- Ticket bucketing: feawtures, error resolvement, analysis (and % time spent on each of these)
- Time resolve these bucketed ticket types
- Data quality: recorded issues, time spent maintaining quality 

### Other
When explaining differences, use the language and the tools people know, use and trust. Use Looker instead of showing people SQL and add a note in screeenshots to emphasise things
Looker is great for static reporting, less so for ad hoc and generally it isn't great at really understanding our customers - we'd need more web analytics and survey data for this. Mapping the customer journey and understanding all steps within the process. Asking the why rather than the what. 

Some data models like attribution model are built over time and gotten larger and larger. Over time, different challenges are overcome and build in the code. This repeats and the model gets build iteratively. Now everything may be fine, but you'd still want to account for the historical data that cannot be changed. It's a difficult balance of consistency, simplicity and scalability. 

### Product Analytics tool 
ContentSquare vs Looker
- Page types are defined by tags set by Tech 
- Map definitions between the tools: bounce rate is the same? 
- Check values: conversions, sessions high level. Are they directionally correct? 
- Define ways of working: Looker is used for sessions and attribution as the Source of Truth rather than CX - no need to know the differences exactly 
- Important to make it self service - defining goals, segments, etc. it’s easy to do but needs to be scalable, shared definitions etc. 