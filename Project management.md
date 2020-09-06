# Project Management

## Stakeholder management
- When I need others to do things, always ask when something can be completed by. Make sure to indicate clearly how important it is to get done
- When important, can follow up on this with an email with actions. If so, mention in the meeting that you'll send this follow up to keep track of actions and to keep people in the loop. Do this when: 
    - There are numerous actions to take between people. Having them in an email helps each other stay organized and it means that they can confirm whether they agree with the actions 
    - If and when it is a large ongoing project, consider setting up a Google Doc with minutes and actions by person
- Once we know when something can be completed by, I can follow up around that time to check in - after all, it should be done.
    - 'Hey I wanted to check in and see if there is an update on X'?
    - 'Hey I am planning my week - do you think progress will be made on X'?
- If things don't get done, make sure to clarify priority and potentially get exec support. Sometimes, things just naturally take long and that might be okay
- When a project is ongoing but it's importance isn't really there - the business doesn't need it that much, it's okay to cancel the project
- When working on something, block out 15 minutes to go through things - otherwise it won't happen. Asking them over email / Slack is just less effective
- Follow up - Blocked on stakeholder project: Hey. I currently have an open ticket for X. I am blocked on it because I have a few questions that I sent over on X. Just wanted to see if you saw those. If this project is currently not too of priority, let me know so I’ll deprioritize on my end
- Follow up - Blocked on data project: Hey we are currently working on the board pack and part of that is ramp. It would be ideal if we could get this in Looker but I am blocked with a few open questions I sent on X. Do you think this could be looked into by you / Tom in the short term or should we plan on doing ramp manually in this board pack?
- Emails can get lost in a clutter and Slacks get lost too
    - Email is sent but no reply: follow up on Slack few days after 
    - Really important: send email and directly follow up in Slack 
- A big part of the job is managing expectation. You have responsibilities but so do their team. Make sure this is clearly defined. 

## Scrum
The most popular project management methodology that follows agile principles. 
Here is how it works: 
1. Backlog refinement / backlog grooming: look at the backlog of tasks / projects and prioritize these. 
2. Sprint Planning Meeting: plan the next two week sprint. This is making sure the tasks get estimated properly (based on effort) and assigned an owner to fulfil the requirements within the sprint. The requirements are often defined as user stories. 
3. Daily Scrum Meetings: Daily meetings to discuss what is done, what will be done and any blockers. An alternative approach is:
- Did anyone work on this item yesterday? Did anyone managed to push it closer to Done?
- Will anyone work on this item today? Will anyone push it closer to Done?
- Does anyone see anything blocking this item? Do we all think it's still feasible to get it done by the end of the Sprint?
4. Sprint Review: Goal here is that the individual tasks have been presented and are approved by the various stakeholders. Scrum is about constant development, releasing quickly and getting feedback quickly 
5. Sprint Retrospective: After a sprint is completed, review it: what has been completed, how did it go, what are the next steps and what can be done better? 


### Timeline
- Wednesday sprint start
- 2nd Tuesday - Midpoint: Any issues that are at risk of slipping from the milestone must be raised by the assignee
- 2nd Friday: request need to be ready for review including documentation and testing - nothing is pushed to live 
- 2nd Monday - everything is merged /pushed 
- 2nd Tuesday: sprint planning 

### Sprint planning 
- Review open tickets: they are either deleted, moved into the backlog or moved into the next sprint 
- Pull items from backlog into the new sprint depending on priority and complexity. This priority is set:
    - The relevant business stakeholder should have a say in how important individual tasks are. If there is no business representation, data team decides on priority. Business involvement has great benefits: 
        - Stakeholders know what’s worked on 
        - Ticket quality will increase the more things are discussed with people from around the business 
    - In general, aim for high impact and urgent issues.  
- Point issues depending on the amount of complexity
    - Very complex projects should be broken down 
    - Projects that are very new shouldn't be scoped too much. Instead, make it a task to understand the problem more deeply
    - Include research tasks (i.e. research how to analyze effectiveness of TV campaign in R) 
- Inform stakeholders around what is in the next sprint 

### Backlog grooming: 
- Constantly keep your ears open for things that people want built and add these items to the backlog
- Regularly bring in stakeholders to review the backlog priorities. 
- The backlog is always closely linked to the data roadmap based on business priorities 
- Have a rough indication of priority per ticket in the backlog
- The ticketing tool is always the single source of truth for all projects/tasks you're working on 

### Best practices
- Apply scrum loosely: 
    - Allow lots of time for exploration. This is often high impact for the business and should be prioritized. An example could be that Fridays are not spent on sprint items - the team just clarifies what they're working on at the beginning of the day and share results at end of day 
    - Allow decent amount of time BAU support  
    - Often, the objective and scope of a task changes after looking into an issue. There might be data issues that need investigating or solving, there might be a better way of looking at things that takes longer. Be flexible in the scrum approach
- Assign estimated efforts for each task. Once we are going over significantly, discuss with a wider grouper whether it's worth it and reprioritize accordingly. Especially research projects should be strictly timed to avoid spending too much time going down a rabbit hole.
- Include acceptance criteria in each ticket. AC from business requests are clear. Here is what to include for research projects: 
    - Write up results from research
    - Recommend a strategy for our company
    - Write next AC for a subsequent story 
- The most important thing is generating valuable work, and whatever process you use should be subordinate to that goal. To the extent the process helps you generate valuable work, you should use it, and to the extent that it distracts you from that prime directive, you should adjust it!
- Tickets can still be deprioritized during the sprint: ill defined tickets or technically not feasible, internal data team work is priority, lack of resources 
- Agile is a set of values and principles around how to develop software. It's iterative project maanagement where a big project is split into smaller tasks and each task is delivered continiously: 
    - Do analysis – what should be built 
    - Design that solution
    - Write code and testing. These 3 steps make up one iteration
    - Show the result to the customer 
    - Adjust your understanding based on what you learned
    - Repeat

## Other
- Have visibility in status of tickets. Both in own team as well as other teams - gain access to their ticketing systems
- The tickets are always the SSOT for each task including requirements and acceptance criteria
- Everything always takes longer than expected: start working on projects early 
- Dependencies are hard and annoying: start early to understand dependencies and work from there. Avoid being blocked in the future 
- Be proactive when you're about to miss a deadline
- Keep a lessons learned document
- Every project should end with a post mortem: what have we learned? What went well / what could have been done better? 
- Deliver things that are small and look ahead to see if anything requires per-work early on. This will uncover whether you’ll be blocked or not and it can pre-ampt future actions
- Always ask yourself: what if the project failed. Please explain in 5-10 minutes how we would look back on it. This will really help seeing the identified and unidentified risks
- If we had to actually complete this in two weeks, what would our approach be?

## Project approach
1. Define the problem
2. Get the requirements (what do we need) in a requirements document. Split this between functional (what it should do) and non functional requirements (how it needs to be done). Requirements should be: 
- Clear
- Complete
- Concise
- Achievable
- Unambiguous (more people shouldn’t be able to interpret the requirements differently)
- Verifiable (include measurable goals)
- Prioritized 
3. Feasibility study (can we do it)
4. Develop a business case (should we do it)
5. Set up a kick-off meeting: 
- What are our goals for this project? (aka purpose)
- Who are the stakeholders, and how to best get them involved?
- What deadlines do we have to meet?
- What roles will team members play? Does everyone know their role?
- Have expectations been set clearly for everyone involved?
6. Develop a charter. Goals / objectives, scope, approach, stakeholders, risks, constraints, acceptance criteria etc. 
7. Create a project plan with specific tasks, efforts, dependencies. This can be as simple as a Gantt chart with clear owners. 
8. Execution: From this plan, start with the priorities in scrum – kept within a PM tool
9. Meet daily with the key stakeholders for catch-ups on progress and update PM tool 
10. Meet weekly with business stakeholders to update and change course where need be  
11. Keep an issues log / lessons learned document
12.	Testing / customer acceptance 
13.	Closure of the project
14.	Review: what have we learned? What went well / what could have been done better? 

## Kanban
Kanban is an agile methodology – things are separated by Backlog – In Progress and Done. It is about doing incremental development but unlike scrum, it focused on less meetings and less on deadlines. The Kanban cards should be users stories with a checklist to sign things off. The cards are ordered in terms of priority 