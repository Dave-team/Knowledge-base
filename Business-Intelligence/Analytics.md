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
- Present things as simple as possible and don't leave the interpretation to the audience. 
- Have strong reasons for why you approached it in a certain way 
- Powerpoint:
    - Title page
    - Introduction slide: goal of analysis and executive summary (main points from your analysis: this also shows what will be covered within the presentation). This answers: why should I pay attention and what's in it for me? 
    - Main analysis following a story. This gives proof for the need of action - you are convincing them why they should accept the solution you are proposing
    - Recommendations / executive summary with the key points from the analysis (i.e. repeating the executive summary at the start). Then, you specify the actions or decisions you need the audience to take. It answers the goal of the analysis. A good analysis deck will have a specific call to action here – this should the answer the ‘Now What’ as well as ‘So what – what is the business value here?’
- Google Doc / non slides presentation: 
  - Objective
  - Key findings 
  - Recommendations
  - Analysis performed 

## Analysis doc 
- Objective
- Approach
- Summary
- Recommendations
- Analysis 

## Good analysis 
### Add context to analysis 
- Compare data over time. Potentially show moving averages to show the trend more clearly. A good way is to show trend across multiple time frames: e.g. 2019 and 2020 over one another
- Segment the data. An overall trend isn't actionable. What specific segments can you identify that show actionable insights? 
- Add context from business initiatives. Avoid sending an analysis where a stakeholder looks at it and says 'That's because of Y'. Have the business understanding to say this proactively 
- A good way to present data is by showing changes 
- It can be handy to also display future plan values in a graph – this will show the stakeholders what is expected to happen in the near future 
- Can also show business goals/targets as a reference line

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

## Analysis that changes metrics significantly
When big changes are about to happen you want to make sure the business knows about it. Prepare a slide deck with:
- Exec summary
- Changes in detail
- Approach

Then send an email clarifying approach, Exec Summary. Add more details in PPT and offer to go through in a call 

## Web analytics
Look into: 
- Long term trends in visitors / unique visitors
- Where are visitors coming from? Look at Referring URLs and Search Keywords 
- What do I want visitors to do on the website?
  - Why does the website exist?
  - What are the top 3 acquisition strategies? 
  - What do you think should be happening on your website?
- What are visitors actually doing? Look at: 
  - Top entry pages. Most likely, these won’t actually be the homepage as direct traffic isn’t that much any more 
  - Top viewed pages 
  - Site overlay analysis – for the top viewed pages, analyze the click patterns. This will help understand navigational challenges, help understand visitor intent and suggest optimization actions 
  - Abandonment analysis – check the funnels and see where the highest abandonment is happening – visitor behavior there identify opportunities that can improve outcomes fast 

**Actionable tips:**
- Look at top entry pages and analyze their bounce rates
- Look at top keywords and analyze their bounce rates. Here you have visitor intent – why do they visit? Maybe you’re ranked for the wrong keywords or you might e.g. not have the right CTAs. Key here of course is to test different versions  
- Look at the site overlay report to get an idea of where your users are clicking on your pages. 
  - Look at where the people click the most and compare that to where you want / expect people to click. 
  - Also, compare above and below the fold clicks. 
  - Look at where people went to before the likelihood of conversions increases.
  - Really put yourself in your users shoes and see how they are clicking 
- Look at visits to purchase and days to purchase – how many visits need to be made, on average before your users decide to purchase something? Learn what it takes to convince people to buy 

**Sessions**
- A visit is basically someone entering the website
- Whatever this person does within 30 minutes on the website is called a session
- Time on page is measured from entering the page to going to a next page. If they never go to a next page, time on page is null. If they do the dishes and come back > 30 minutes later, its a new session 
- Unique visitors are identified by their cookies. This makes it harder to identify them when they don't accept cookies 

**Different tools will provide different results**
- Data collected from web logs vs Javascript tags
- First party or third party cookies (determined generally by the tool)
- Imprecise Website Tagging 
- Different definitions of different metrics. Ask your vendor e.g. how conversion rates are defined
- Sessionization: different tools define sessions differently
- URL parameters: make sure all tools identify the right parameters you set 
- Campaign parameters: make sure all tools identify the right parameters you set. Marketing campaigns are tracked using campaign tags. You also need to include additional information to the links used in the marketing campaign. See below. There is a url building tool and supports creating these marketing activity related links 

**User research**
With user research, there are three basic questions that probably should be asked:
- What is the purpose of your visit to our website today?
- Were you able to complete the task?
- If you were not able to complete your task, why not? 

## Attribution modelling 
There are several attribution strategies
To pick to one right for the company, consider:  
- Media Mix Modelling: run tests with different mixes of channels (e.g. by area). Then, compare the conversion numbers and calculate the CAC 
- Marginal Attribution Analysis. Spend X amount more on a certain channel than before and calculate the differences in conversion rates. With this, it is crucial to only change one variable. 

**Notes from Papier**
- Replicate GA sessionanization logic
- Campaign names in a file need to match UTM campaign names that we get from sessions data for the data to go into attribution 
- When working with partners, the partners are responsible for setting up these parameters. 

**Marketing parameters**
- “Medium” communicates the mechanism, or how you sent your message to the user. You could include “email” for an email campaign, “cpc” for paid search ads, or “social” for a social network.
- “Source” communicates where the user came from. This could be a specific web page or a link in an email. Source could also differentiate the type of medium. So if the medium was “cpc” (or “cost per click” paid traffic), the source might be “google,” “bing,” or “yahoo.” If the medium was “email,” the source might be “newsletter”.
- “Campaign” can communicate the name of your marketing campaign such as “2015-Back-To-School” or “2015-Holiday-Sale”.
- “Content” can be used to differentiate versions of a promotion. This is useful when you want to test which version of an ad or promotion is more effective. If you’re running a test between two different versions of a newsletter, you might want to label these tags “v1-10dollars-off” and “v2-nopromo” to help differentiate which newsletter the data is associated with in Google Analytics.)

## Multichannel analysis (Nonline world)
Here are some tricks:
- Use vanity URLs (also called redirects). E.g. create a simple URL that you put in a TV ad. Then, when someone searches for the URL, it redirects to  www.quickbooks.intuit.com/?campaign=tv_nbc_dec_2009
- Use unique redeemable coupons and offer codes that are specific to the channel. E.g. TV, TUBE, or Taxi
- Online surveys (‘How did you hear from us?’)
- Correlating Traffic Patterns and Offline Ad Schedules. We know where and when ads run. This helps setting up a baseline and we can then measure the impact when campaigns are live. In addition, you can also correlate the impact from offline channels (use vanity URLs) with visits to website via other channels (such as organic, or PPC). You want to compare the reach of the ad to direct traffic to vanity URL, When you do this type of analyses, try to minimize the impact of other things – so when you compare radio, make sure to keep other channels at least equal. 
- Leveraging controlled experiments. Plan an experiment. Then, collect data 30 days worth of data before and after the experiment. You want to see uplift during the experiment and ideally you’d also want to see permanent uplift after the experiment.

## Lead and lag indicators
A lag indicator is the thing you care about (like monthly revenue), but can only be measured in hindsight. A lead indicator has a predictive association to the lag indicator — site visits, unit sales, or page traffic behavior patterns may be lead indicators to a monthly sales lag metric. Lag measures are scoreboards that tell you if your decision making was successful. But lag measures are not inherently useful for data-driven decision making; that is what you need lead indicators for. Identifying these lead indicators is at the core of asking good questions.

## Other
- Make sure to keep the raw data with the analysis somewhere well documented as you will always need to do the analysis again or remember your assumptions
- Keep a log of business initiatives. Any time something happens that causes data to shift, keep a note of this in a Google Sheet that gets pipelined into the warehouse. Columns could be data, type, notes. Things to include could be: marketing campaigns, feature releases, bugs, holidays, press. It also helps generally keep a log of events that happened as a source of truth
- When showing data over time, consider comparing different time periods in the same graph 
- Similarly, show the future plan 
- Never show data that looks off/raises questions. Either remove these things or have a clear simple explanation ready. Where required, make clear that things are an outlier.  
- Conversion rates should be tracked at point in time - e.g. conversion rate within 30 days after first visit
- Make sure to define success metrics for new projects and how these are expected to be influenced  

### Marketing understanding
- Marketing add utm source / utm campaign names / utm medium to an ad 
- These variables are added to when a page is loaded 
- Each session will have the same variables  
- There will be a way to connect the utm parameters loaded to the marketing campaigns / ads as naming conventions will sort this 
- 
![Analysis context ](https://user-images.githubusercontent.com/28791247/92440452-7189ac80-f1a4-11ea-8f92-3898c3f2cad0.png)

![Analysis context ](https://user-images.githubusercontent.com/28791247/92440681-caf1db80-f1a4-11ea-8e08-a8aa5049c447.png)

## Mathematics notes 
- Moving averages: great for smoothing out a time series and remove noise from short term observations. With non percentage figures, just add the relevant figures and divide by three. 
- Be aware of percentages and averages: you often can't calculate with them directly and need to use the absolute numbers instead. 
- Percentage change = (New Figure– Old Figure) / Old Figure 
- Numerator = part of the calculation prior to the division
- Denominator = the bottom part of the fraction 
- Price increase = old price * percentage increase 
- Price decrease = old price * (1-pecentage decrease). A 25% discount on a £100 article leads to 100*75 = £75 as the new price
- Percentage change calculation can be confusing. A percentage can go up in percentage points: a rate can increase by some percentage points (from 3% add 2 percentage points to get to 5%). You can also say that the rate increased by 67%

## Funnel metrics
- Think about conversion rates: Won = Won /(Won+SAO). Reason: From SAO to Won we want to have the entire population in the denominator - which then includes both SAO and Won
- Conversion rate dates are based on the date of the first step in the conversion. The business might look at this in another way: from the origination of the opportunity, but that always depends on the company’s logic  
- Usually includes the absolute counts by step
-	Generally, the product team will want to verify the performance on each step – they need to know whether people convert from each page or step. This means they want to know what the % conversion is from each step to the next.
-	It can be that a team wants to look at conversion rate that spans multiple steps. In this case, the team is happy to not isolate performance of a step but the combination of multiple step’s performance is helpful to them. E.g. deposits / completes, rather than deposits / approved to also account for the credit quality that the marketing team is acquiring. 
-	In general: use absolutes by step, use conversion % step to step and use stepwise and overall final conversion rate (deposits / leads and deposits / approved). This way, you measure the overall performance, as well as the performance of the last step.


