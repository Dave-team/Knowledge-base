# BI principles

## Mindset
Think about BI as if it's a SaaS product and the users are your customers. Approach it as running the growth team where you improve your offering step by step by running experiments and analysing the results and always solving solutions for your end users first. 

## Principles
### Data principles
- Data is correct and quality controlled. Shipping out bad data quickly destroys the team's credibility. The business needs to trust the data 
- Data is available to answer relevant questions 
- Data is current 
- Data tools are fast and easy to use 
- Data is democratized and the BI tool is self service
- Data is well documented 
- Automate as much as possible 
- As much as possible is defined in code

### Process principles
- Great support, documentation, onboarding / training
- Great business partnering to help improve business
- Code is version controlled and development is approved through pull requests with code review
- Code is modular - there should be one version that is used throughout an entire project
- We work incrementally: 
    - Deliver continiously 
    - Demonstrate early
    - Communicate results 
    - Get feedback 

## Values
- Humility. Be humble and nice. Realize we are not the domain expert - the stakeholder is. When we make mistakes, be honest and build a deep of trust. 
- Helpfulness. Business Intelligence is a support function to help the business make decisions from data. Don't be afraid to do some chores to help others as it will greatly improve relationships and you will get more context. Also be very mindful of the burden on other teams. If you come with a request or an ask from another team, it’s important that you let them know you’re interested in partnering with them to make the process as easy on them as possible to minimize disruption to their workflow.

## BI definition
Business Intelligence is about making sure that people get the insights from the data they need to perform their job, in an easy way. 

**BI benefits**
- Central space for multiple data sources that can be combined. No more information islands and a more holistic view over entire business (e.g. marketing funnel) and customer journey
- Scalable. Everything is written in code with documentation that is easy to debug
- Time saver. Saving lots of time doing analysis when people can use a tool like Looker
- Improve data quality and quality control as the data sits in a central environment managed by analyst and best practices in data testing are employed
- Single source of truth documented centrally 
- Easy access to insights 
- Allow more complex analysis using data transformations

**Why do we need data?**
- To make decisions based on facts rather than our gut 
- To track performance
- Ultimate to help improve business performance 

## Impact 
The real value of data comes into play when it actually helps the business. The goal is to answer" 'So what?' and 'Now what?' and the end result should be recommendations or actions to be taken to improve the business. And then we need to follow through to ensure this impact has been delivered 

To get the maximum impact from data on the business, I first need to understand the business well: 
- Understand each team's main priorities and their KPIs  
- Think as a stakeholder - what are their main business goals? Be curious around their business function (Google, YouTube, Looker Blocks) and figure out how to make their lives easier and help them achieve their goals 
- Regularly meet the different stakeholders to understand what is in their pipeline and how data can help

Once I have the context, I can establish myself as a business partner. This can come in the form of: 
- Automations: when building solutions, make sure that it integrates seamlessly in the stakeholder's life to ensure maximum impact - a dashboard doesn't impact the business, the actions from the dashboard do. Use actions, integrations, and other automations to make decision making automated. 
- Data and analytics improvement. 
    - Knowing the context and knowing the data well, I can suggest ways to further improve the reporting in place. A huge sign of effectiveness as you progress in your role is the ability to identify and answer the questions that influence decisions – this is not always what someone asks for
    - I can also start to provide insights to various reports we send out. Add comments to analysis, proactively answer questions and become a trusted business partner. As long as data team is being updated on this, we can follow the crumbs, go deeper in the analysis and provide insights 
    - I can start to find new use cases for high impact data analytics project based on knowing the goals of the stakeholders. For example, are we doing manual forecasting? The data team could support. Or I can explore some data that leads to new insights and present this to the business 

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
- Make sure the data team is up to date on any changes or important events in the business. The data team is the owner of the model. If things change, it's crucial to update this
- Stakeholders should feel ownership over the data they use. If they see issues, it should be communicated with the data team
- Underpromise and overdeliver. Because of the nature of data it's hard to estimate how long projects will take. Give an estimate that assumes that everything will take longer than plannedand keep the stakeholders in the loop throughout the project
- Make sure to create understanding that data projects take long and that we need to prioritize what to work on 


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

## BI team 
### Organization
Hub and spoke model works well, where some analysts are part of the central data team (hub) while others are embedded (spoke) or distributed (spoke) throughout the organization.
- Central - those in this role report to and have their priorities set by the Data team. They currently support those in the Distributed role, cover ad-hoc requests, and support all functional groups (business units).
- Embedded - those in this role report to the data team but their priorities are set by their functional groups (business units).
- Distributed - those in this role report to and have their priorities set by their functional groups (business units). However, they work closely with those in the Central role to align on data initiatives and for assistance on the technology stack.

### OKR planning
- Coming from the higher level BizOps/Finance KPIs and the needs of the data team
- Best way to get them is brainstorm with the data team

### Workload 
- 60% of time is spent on achieving the OKRs, 40% is spent on ad hoc / exploratory analyses

### Sources for work 
- Communication with the business - both formal and informal that can lead to projects or insights 
- Being up date on business initivates can spark investigations where data can help. 
- Explore something that could lead to insights. Look where no one else is looking
- BI platform optimization - testing, automation, documentation, identify best practices and new tools



### Communication
- Analytics weekly
    - Show and tell. Use time during your team meeting to have a team member present something they have learned or done. It's beneficial to plan this meeting around the end of each sprint. This has many benefits: 
        - Team can ask claryfying questions
        - Team can poke holes in methodology
        - Suggest areas for future research
        - Holds people accountable
        - Spreads the knowledge in the team
        - Allows cross team input
        - More opportunity for review and it can catch errors (‘I have done something similar before with different end results’)
    - Discuss blockers
- Slack channel
    - Open channel for anything - it is a safe place to ask questions and discuss shortcomings 

 ## Other
 ### Data readiness
- Strong business sponsorship
- Clear data use cases that warrant a data function. I.e. without data the business will suffer and there are no other ways of answering the questions
- Source data has been looked at as is in a fairly good state 

### Measuring BI success 
- Whether employees get their questions answered
- Number of users of BI platform
- How often people use the BI tool 
- Centralized definitions and increased consistency 
- Number of uses of the data 


