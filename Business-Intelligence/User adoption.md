# User adoption

## Links
What does “self-serve” in analytics mean to you?: https://discourse.getdbt.com/t/what-does-self-serve-in-analytics-mean-to-you/712

## Principles
- If you build it, they might come, but they probably won’t unless you’ve stepped into their shoes and answered, “Why should I use this?” and “Okay, so how do I use this?”
- If you teach someone to use a tool and they don’t get it or they later find it frustrating, they’ll look for another way to answer their questions. Before you know it, their alternate path to a solution will become a habit. Good luck getting them back to your tool!
- Be more proactive and figure out how you can support the teams by talking to them
- Take it step by step: sit with one team, work on a problem and solve that problem only. Rinse and repeat with different departments 
- When dealing with senior stakeholders who are hard to convert: 
  - Let them sit with their team and show what’s there
  - Let them figure out specifics that are missing and present that back to us 
  - We can then work on it.
  - Let them know they can always reach out with small questions we can help with 
- When helping people, let them do most of the work themselves. That's the best way for them to learn. 

## Elements of user adoption
### Data availability
Make sure that Looker has the data available for end users so they can answer their questions. This often means helping the business out by building initial dashboards. It also consists of ensuring the data is complete and current  

### Data reliability
Make sure that end users can trust the data in Looker is reliable. Especially at the start we need to ensure the source data and Looker matches, otherwise people might lose trust

### User Experience
Make sure that end users have a great experience using the data platform. It should:
- Be correct – end users trust that the data is correct 
- Have good documentation so that end users can self-serve their analytics needs. 
- Perform well. Queries should return results fast 
- Be easy to use. 
- Look good. Tools and reports should be clear and attractive. Implement the company's colour pallete 

### Support
Provide great support to end users. 
- Have a dedicated Slack channel used for Looker questions
- Make sure response times are practically instant
- Create custom homepages for end users with links to helpful documents. The homepage can also have the main KPIs compared to target and with last six months trended with really strong drill down functionality 
- Emphasize that people can reach out for more training, check their work or sit together and build something 

### Onboarding
### Intro meeting
- Hi - How are you?
- How have your first few weeks/days been?
- Introductions:
  - Joined Papier in July last year as a BI manager which translates into being responsible for all things BI. Very high level about BI it that we are a centralized team, supporting the different functions at Papier. We aim as much as possible for a self-service model and we use Looker as our BI tool which fits the self service goals quite well. Right now, I am the only person in BI - we have a new BI Executive joining in July this year. 
- Their intro
  - What will they be focusing on? How does data / Looker relate to this? 
  - Where were they before this role?
  - What is your BI experience?
- Let’s talk a bit about BI - we have a presentation that we can use to guide 
  - The mission of the BI team is to enable execution of Papier’s strategy by empowering better decisions, faster through data.
  - At Papier, we believe we have a very data driven culture, where we use data to inform decision making. To give you an idea, over 75% of the business are active users in Looker. We believe that being data driven will help Papier achieve its goals.  
  - The benefits of being data driven include: 
    - Framework for performance: we measure the performance of the business through data
    - Common language: we try to create a common language for all our reporting, in particular around definitions and KPI calculations. 
    - Framework for decision making: as already mentioned, we want data to be used to inform decision making
  - How do we build a data culture? 
  - Data infrastructure: we have all these tools used by teams across the business. We get this raw data into our data warehouse. We transform it into usable analytics tables and then we model it to be used in Looker for the business 
  - The way we work is twofold: 
    - Roadmap: we meet every start of the year with key stakeholders and we create a 12 months BI roadmap that we work on within the team. BI is a support function meaning that we build the roadmap after the business’s priorities are known. We allocate the projects into quarters and we revise our roadmap each quarter and alter it based on changing business priorities  
    - Ad-hoc: the majority of our time is spend on these strategic roadmap projects. In addition, we also spend a decent amount of time on ad-hoc requests that are usually smaller in size and not planned for. 
  - Operating model with the business - we prioritize projects, allocate across the team, engage with stakeholders to collect requirements, deliver incremental, handover to the user and then review if the requirements are met. 
  - Finally, we primarily work within Notion for users to add tickets and for us to track our work. We have a BI Inbox which is where requests come in and then we have our sprint board where we track our projects. Usually, the Inbox is the best place to add a ticket if you want something done! 
  - In terms of your onboarding: 
    - Session with Superhero 
    - LookerDocs - show this
    - Office Hours 
    - LookerPaps Slack channel with all updates

### Looker training session 
Looker training: 
- Kickoff: intro of me, and overview of what we’re going to do and get an understanding of how users want to use the data  
- Introduction: what is Looker and how is it helpful? How does it fit in, compare to other tools? 
- Looker demo: tour of what we have built so far in Looker  
- Essentials of Looker - dimension, measures, filters, pivots 
- Practical exercises for users to try. One can be guided by me and then they try themselves. Make sure they save it in own dashboard
  - Explore an existing dashboard 
  - Build a relevant use case from scratch and save it to a dashboard  
- Explanations of different Looker use cases and how this relates to what the users wanted to get out of the session. Show ‘Looker Blocks’ with dashboards that relate to their function
- Table calculations, scheduling
- Building dashboards 
- Dates
- Search for fields
- Caches
- Explore from here

#### Onboarding / training tips
- The goal of the intro meeting should really be for people to bring their own agenda primarily. 
- With new joiners, have them prepare a list of questions / list of things they'd like and then go through it with them rather than them asking ad hoc questions. 
- Set up training sessions specific to the requirements of the end user to be trained. Train early and often to make sure Looker is directly ingrained in their habits and workflows. When a tool is hard to use, they'll go back to the tools they know 
- Really get people involved
    - Generally slow down and allow lots of time for questions 
    - Make the data related to their daily life
    - Ask them to show for something and check what they've done - e.g. a completed dashboard
- Answer their business questions live - focus on their specific use cases
- Make sure they are set up will all the right access prior to the session 
- In bigger team, team managers and Superheroes can be responsible for onboarding. BI preps a training doc for the high level Looker overview and then the data champion in the team guides through Looker - which is often specific by team  
- Provide great documentation (training recordings / slides, FAQs, data dictionary) and make this easily available to end users. For developers, have a best practice LookML document 
- Regularly check in with new users as they go through the change curve to ensure they remain enthusiastic and positive about what Looker can provide them. Track their usage in iLooker.
- Hold regular office hours where people can book a slot to go through something data related
- Always leave them with training docs that explain the Looker basics 
- Hold 'Show and Tell' sessions where someone presents a use case they've used Looker for successfully. Especially around relevant types of questions that people are answering
- Short videos showing common use cases. E.g. video embedded on Notion. Description: In this lesson, we'll cover:

### Evangelize BI
Monthly updates with new data / features in Looker. Main purpose here is that people find common things they weren’t aware of and now can use. Example framework of such a newsletter: 
- What’s new
- How can you find and use it?
- What's coming by when?

Really sell the results you’re getting – at all hands and in emails. You want to be able to ask anyone what meaningful achievement you did lately and they should be able to answer this for you.  

Have a dedicated Looker Slack channel where any new updates are listed to keep the business informed on what is happening. Tag relevant people. 

### User feedback
Gather user feedback from end users to increase the value that Looker adds. Send this to inactive users
- Has Looker been useful to you? If not, what could we add or change that would make it more useful?
- Have you experienced anything frustrating or confusing in Looker that I could help with?
- Do you have any other questions or requests about Looker or data at the company more broadly?
- Ideally, survey people and ask. Otherwise, 15 minute chat. This is both more valuable than surveys. 

### Data champions
Create a hub and spoke model where each team has data champions
- They can: support with training, business analytics support, answering questions on Slack, minimal changes to LookML, and drive adoption in their teams. 
- They arise organically because they are keen on diving in data and gathering data for their respective teams. Keen an eye out via the Looker user engagement dashboards 	
- We will provide them with the support they need and we’ll hold regular feedback session and get their input to guide our roadmap. E.g. regular consulting 1:1 work 

### Measure engagement
- Measure Looker engagement in iLooker and proactively reach out to see any changes in engagement or general disengagement. 
- Executive support - Get executives to buy into Looker and have them use it in their meetings 

### Embedding
Get Looker into the lives of our end users. 
- Schedule data from Looker with our end users 
- Embed Looker (iFrames) into the tools that end users are already using (e.g. Wiki)

## User adoption techniques when user adoption is hard
Replace the reports of your stakeholders - work with them on building out the solution. Key here might be to really first just replicate what they have even when it's not perfect. This will win over their trust
- Email team leads: we are doing BI and would like to see how your team uses data and see if we can support in any way. Support could come in automation of reports to reduce load on team 
- Meet with team leads and look at all reports done in last 3 monhts 
- Meet with report owners and shadow them. Clarify how automation can help
- Get access to the reports and aim to automate this. If we can't, it's an item for the backlog
- Regularly communicate and build the relationship with the stakeholder during this process
- Optional: Evolve the report. You have full understanding of the data. Can this report be improved in any way? Make it more accurate, comprehensive and impactful - which may also mean that reports can change KPIs because something else is more impactful 
- Optional: Start to build out insights. Start off by adding comments to an email used to send reports. Proactively answer questions that your stakeholders always seem to have. Then layer on more robust analysis that builds off the existing report. This is evolving yourself into a trusted partner 
    
## NPS survey
These questions are rated on 1-5 scale: 
1. Strongly Disagre
2. Disagree
3. Neutral
4. Agree
5. Strongly Agree

**How do you use data today?** 
- I rely on data to make decisions in my job
- I can easily and independently answer my own questions with data
- I am confident that I understand the meaning of the metrics and the data fields I use
- I trust the data 
- I am satisfied with my ability to use Looker
- Looker has reports that are useful to me
- Looker has reporting on everything I want
- It’s easy to find reports on specific things in Looker
- I am confident that I understand the meaning of the metrics and data fields I use
- I trust the accuracy of the reporting in Looker
- I am satisfied with the speed that my data questions are answered
- If you could wave a magic wand and change one thing about our data work at Help Scout, what would it be? (optional)
- Anything else you would like to add? (optional)
- What department are you in? (optional)
- What’s your name? (optional)

**How is the analytics team doing?** 
-	The analytics team is a reliable resource of information about our data 
-	The analytics team helps me understand our data and how to access it 
-	The analytics team is responsive to my requests 
-	I am satisfied with the performance of the analytics team overall 

Other questions
- Is all the data you want available?
- Is it difficult to find the data your want?
- Do you trust the metrics/calculations presented?
- Do you ever get confused about what metric or dimension means?
- Do you know where to go for help with data questions
- Do you feel like our data platform hinders your job performance?
- Are you happy with our data platform?
- How frequent do you use Looker Reports 
- How much confidence do you have in the accuracy of the Looker reports?
- Do you feel that the reports at your disposal give you meaningful insights and enable you to do your job better? 
- Where do you use/view Looker reports the most? 
- How would you rate Looker as a BI tool
- Have you ever 'explored' data, or build your own report? 
- What could be added to improve either your Looker experience or your data experience?
