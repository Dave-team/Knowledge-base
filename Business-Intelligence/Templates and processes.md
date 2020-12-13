# Templates and processes 

## Templates
### Visualization/dashboard new request template
- What is the business question you are trying to answer? Example: Is there a relationship between the day of the week that deals close and the ability of the account manager to upsell them in the first month?
- What is the impact of this question and how will it help the company? Please link to where this (or these) performance indicator/s are defined in the handbook. Everything needs to be defined in the handbook.
- Who will be using this data? Example: SDRs need this to better understand X or VP of Product needs this to do Y
- What time frames are crucial here? Example: I would like to look at performance by month, but at the trends over the last year.
- Will this deliver business value within 90 days? If not, consider why you want this data.
- What is the visualization you are trying to create? Include any links or screenshots, if appropriate. As a rule of the thumb, the analytics team uses 12 visualization types. They are:
    - Simple Text
    - Table
    - Heat map (Table with Conditional Highlighting)
    - Scatterplot
    - Line graph
    - Slope graph
    - Vertical bar chart
    - Stacked vertical bar chart
    - Horizontal bar chart
    - Stacked horizontal bar chart
    - Waterfall chart
    - Square area chart
- What is the source of data behind the visualization? SFDC? ZenDesk? There may be more than one.
- What interactions/drill downs are required? Example: I'd like to be able to dig into the specific opportunity details (owner, account owner, IACV). I'd also like to be able to filter by region.
- Any caveats or details that may be helpful?

### Visualization / dashboard update request
- What is the original dashboard?
- What are your requested changes?
- The next elements are the same for a new dashboard – as outlined from the section above 

### New data source request
- Business Use Case (Please explain what this data will be used for / what questions this data will help answer)
- Business owner checklist
    - Do any objects in this data source need to be snapshotted? If yes, please open separate issues to have the objects snapshotted.
    - Does this data contain anything that is sensitive (Classified as Red or Orange in our Data Classification Policy)? Yes/No/I don’t know 
    - Is there anything else we should know about the data?
- Integration preparation
    - What is the data source?
    - Will there need to be access granted in order for a Data Engineer to extract this data? (example: New permissions or credentials to Salesforce in order to access the data) Yes/No/I don’t know 
    - If Yes:
        - Where will access be required?
        - Link to Access Request:
- Data use / Acceptance criteria
    - Who will be using this data, and where (dashboards, snowflake UI, etc.)?
    - What tables and fields of the source data are required? 

## Processes
### Dashboard creation 
- Add a dashboard with WIP: in the tile. Add it to a WIP topic in PM tool
- Once build, create a request in PM tool using the dashboard review template for approval
- Assign the template for review. If the business created / changed the dashboard, the data team should review. If the data team created or updated the dashboard, the stakeholder should review 
- Once approved, remove WIG from dashboard and push to Slack as newly created dashboard avaialable for use 

### Ticket process
**Ad hoc ticket**
- Stakeholder will ask a question by creating an issue in the project management tool using the right template. As a rule, create ticket for any task expected to take more than 30 minutes
- Analyst schedules discussion to further understand the needs of analysis. Figure out the overall goal of the analysis, not just respond to the question asked 
- All findings are recorded in the issue
- The business stakeholder signs this off 
- The project is then worked on and the SSOT will always be the issue. 

**Roadmap tickets**
- Tickets should be filled using a template depending on the type of ticket it is (bug, SQL query, feature, analysis, roadmap)
- Move tickets along its stages (backlog, in progress, in review, done) and keep the stakeholders up to date
- In review is when the business reviews. Completed is only after business approved functionality 
- Notify Slack after work is completed 
- At the end of the quarter, review the queue and prioritize accordingly. Spend a week going through prioritized tickets, or delete them or put them back in the backlog. 

**Other notes**
- Always follow up on tickets, even when it's not entirely your area to fix it. 
- Always know what's happening in each ticket as you move towards Head of BI role