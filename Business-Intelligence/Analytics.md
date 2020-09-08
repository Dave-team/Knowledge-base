# Analytics
## SQL development 
### SQL query checks
- After every step, check to see whether there are duplicates (count or count distinct) introduced. Also, see if you added null values in your data. If so, understand why and make a decision as to delete or keep them 
- Make sure to keep the same number of rows when this should be the case - e.g. compare against different tables
- Regularly refer to a few sample cases where you know the source of truth value. As you develop, ensure that this value doesn't change 

### SQL query investigation
- Run individual CTEs and see where the error creeps in - go step by step
- If the issue is more detailed, follow an individual case throughout your CTEs and identify where the issue creeps in. Break it down and go small (unit testing)
- If that doesn't work, try to rewrite the query differently 
- Ask others to sanity check as a final resort 

## Data checking 
- Does the data include all data (e.g. dates) required or are there gaps? 
- Does it make sense? Are the numbers intuitive, not many unexpected NULL values etc?
- Are the numbers consistent with what we got in the past? 
- Do the numbers match different sources?
- Ask yourself: 
    - Am I sure I'm not overlooking anything in my analysis? 
    - What aspects could be wrong? 
    - What assumptions am I making and can I even make these? 
    - What questions could the stakeholder possibly bring up? 
- Ask someone to sense check the analysis as an extra pair of eyes
- Go back to the requirements: is the questions answered? Can we impact the business in any other way now?
- Is the outcome relevant: 
    - Is it statistically relevant? 
    - It is practically relevant? 

## Presentation
- Go through the presentation with a peer prior to sending it 
- Before sending it, make sure that anything that could raise questions is either deleted or clearly explained
- Make sure to consider the audience: 
    - Who is the decision maker?
    - What do they already know? What background information is relevant?
    - What do they want to get out of it? 
    - What questions may they have and what should I convince them of? 
    - What biases do they have I should be aware of? 
    - Where are the risks: what factors could weaken our case and do we need to proactively address them? 
    - Often, the audience wants to know two things: 
        - What’s your point? Give me value, not data
        - Based on your point, what do you want me to do? 
- Send an email clearly stating the results, approach and any supporting data / analysis and suggest the actions you’d recommend based off the analysis. This is impact focused and answers the question: what should the business do now? Be very clear on definitions and what calculations you have used 
- Offer to take them through it 
- Present the big idea first. Tell your main story within 3 minutes 
- Go through slides and answer any questions
- Present things as simple as possible 
- Have strong reasons for why you approached it in a certain way 
- Powerpoint:
    - Title page
    - Introduction slide: goal of analysis and executive summary (main points from your analysis: this also shows what will be covered within the presentation). This answers: why should I pay attention and what's in it for me? 
    - Main analysis following a story. This gives proof for the need of action - you are convincing them why they should accept the solution you are proposing
    - Recommendations / executive summary with the key points from the analysis (i.e. repeating the executive summary at the start). Then, you specify the actions or decisions you need the audience to take. It answers the goal of the analysis. A good analysis deck will have a specific call to action here – this should the answer the ‘Now What’ as well as ‘So what – what is the business value here?’

## Good analysis 
### Add context to analysis 
- Compare data over time. Potentially show moving averages to show the trend more clearly. A good way is to show trend across multiple time frames: e.g. 2019 and 2020 over one another
- Segment the data. An overall trend isn't actionable. What specific segments can you identify that show actionable insights? 
- Add context from business initiatives. Avoid sending an analysis where a stakeholder looks at it and says 'That's because of Y'. Have the business understanding to say this proactively 
- A good way to present data is by showing changes 
- It can be handy to also display future plan values in a graph – this will show the stakeholders what is expected to happen in the near future 

### Show business value
- Don't present numbers - present actions and/or recommendations and show significance. Both practical and statistical 
- Trim the fat. Make your insights clear and concise and focus only on what matters most. The more you add, the less clear the main point becomes. 
- Insights need to be presented simply so the business users understand it without too many issues and the business accepts the end result 

## Issues process
First, consider whether it is a problem worth investigating. If it is, consider: 
- Do I know the cause? If yes, just explain it to the stakeholder. Domain expertise is the critical factor in this. Once you really know you're data it'll be easy to understand where problems occur
- If it's not an apparent issue, do some initial analysis. 
    - Segment the data (see segmentation ideas below) 
    - Look for any of the more obvious potential causes (see list below)
    - What can you see in the past? Does it line up with the trend?
- If analysis doesn't solve the problem, ask the relevant stakeholders for context and if they know why it happened. Perhaps it is expected, perhaps it’s part of a bigger picture. 'Do you know why X could be the case? Have there been any changes that could have caused X?' 
- If that doesn’t answer it, will need to go deep and look at like for like comparisons on a granular level comparing different data sources 

**Potential issues sources**
- Holidays – people might use something more or less during holiday periods
- Seasonality
- Marketing activities (e.g. campaigns, press release)
- Feature releases
- Feature changes
- Bugs in features
- Bugs in analytics tracking
- Broken ELT 

**Segmentation ideas**
- Products 
- Countries
- Marketing channels/campaigns
- Cohort
- Device 
- Customer segment

## Other
- Make sure to keep the raw data with the analysis somewhere well documented as you will always need to do the analysis again or remember your assumptions
- Keep a log of business initiatives. Any time something happens that causes data to shift, keep a note of this in a Google Sheet that gets pipelined into the warehouse. Columns could be data, type, notes. Things to include could be: marketing campaigns, feature releases, bugs, holidays, press. It also helps generally keep a log of events that happened as a source of truth

![Analysis context ](https://user-images.githubusercontent.com/28791247/92440452-7189ac80-f1a4-11ea-8f92-3898c3f2cad0.png)

![Analysis context ](https://user-images.githubusercontent.com/28791247/92440681-caf1db80-f1a4-11ea-8e08-a8aa5049c447.png)