# Analytics
Principles
- Make sure to keep the raw data with the analysis somewhere well documented as you will always need to do the analysis again or remember your assumptions

## SQL development 

### SQL query checks
- After every step, check to see whether there are duplicates (count or count distinct) introduced. Also, see if you added null values in your data. If so, understand why and make a decision as to delete or keep them 
- Make sure to keep the same number of rows when this should be the case
- Regularly refer to a few sample cases where you know the source of truth value. As you develop, ensure that this value doesn't change 

### SQL query investigation
- Run individual CTEs and see where the error creeps in 
- If the issue is more detailed, follow an individual case throughout your CTEs and identify where the issue creeps in. Break it down and go small
- If that doesn't work, try to rewrite the query differently 
- Ask others to sanity check as a final resort 

## Data checking 
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
- Make sure to consider the audience: 
    - What do they already know?
    - What do they want to get out of it? 
    - What questions may they have and what should I convince them of? 
    - Often, the audience wants to know two things: 
        - What’s your point? Give me value, not data
        - Based on your point, what do you want me to do? 
- Send an email clearly stating the results, approach and any supporting data / analysis and suggest the actions you’d recommend based off the analysis. This is impact focused and answers the question: what should the business do now? Be very clear on definitions and what calculations you have used 
- Offer to take them through it 
- Go through slides and answer any questions
- Present things as simple as possible 
- Have strong reasons for why you approached it in a certain way 


## Good analysis 
### Add context to analysis 
- Compare data over time. Potentially show moving averages to show the trend more clearly
- Segment the data. An overall trend isn't actionable. What specific segments can you identify that show actionable insights? Segments can include: 
    - Marketing channels/campaigns
    - Cohort
    - Device 
- Add context from business initiatives. Avoid sending an analysis where a stakeholder looks at it and says 'That's because of Y'. Have the business understanding to say this proactively 
- A good way to present data is by showing changes 








o	Trim the fat. Make your insights clear and concise and focus only on what matters most. The more you add, the less clear the main point becomes. 

Presenting insights
-	Presented simply so the business users understand it without too many issues and the business accepts the end result 


-	There is good context surrounding the analysis: is something up or down, is it relevant, is it specific to a certain segment, is it expected to happen – why did it happen, is it significant?


-	From these requirements, come up with a list of hypothesis for the questions/problems. Prioritize these and check in order of priority. 



Issues process
-	Is it a problem worth investigating? 
-	Do I know the cause / it is known? If yes, explain
-	If not, do some initial analysis that is searching for the obvious. Part of this is performing segmentation analysis 0
-	If that doesn’t answer it, ask around to understand context. Perhaps it is expected, perhaps it’s part of a bigger picture. Do you know why X could be the case? Have there been any changes that could have causes X? 
-	If that doesn’t answer it, will need to go deep and look at like for like comparisons on a granular level comparing different data sources 
