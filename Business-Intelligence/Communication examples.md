# Communication templates

## Slack messages 
We’re looking into X but it’s worth fleshing out what options we have before putting in a ticket. OK if I put in 15 mins to go through this? 

Quick question: I see that Dafne is joining on Monday - do you think she’ll want/need a Looker account? If so, we can create her an account and send her all the relevant intro material in advance

## Executive data quality updates
Hi both, 
 
Thanks for flagging this. I can see that this is caused by MentionMe campaigns that went live in the last 3 days and that we haven't yet modelled in Looker. I'll follow up with Mathilde and update in Lookerpaps when the fix is live. 
Also FYI - we are going to implement more rigorous data quality tests this quarter that should help us proactively spot issues like these. 
 
Dave



## Onboarding and access email
Hi Saneesh, 
 
I hope you're settling in nicely :)
 
I've added you as a user to our BI platform, Looker - the setup email should have landed in your inbox and you'll need to set up 2-factor authentication following this doc. 
 
To help you get started using Looker, we have three intro docs I would highly recommend going through: 
Introduction to Looker
Looker Worksheet 
Looker Worksheet Answer
In addition, Kiyani (cc'ed) will be able to guide you through Looker and provide context/help with any questions you may have. 
 
Do let me know how you're getting along and just ping me if there are any issues.

Thanks, 

Dave



## Roadmap 
**Roadmap invitation**  
Hi Tony,

Booking in 30 minutes to go through BI requirements/implications from your 2021 roadmap and any additional data needs you may have.  We are specifically wondering:

- Do you have any additional needs outside of what we have listed below?
- Do you have any pain points in your current work with data that you wish were improved?
- Longer term is there anything we should keep in the back of our mind?

The projects we have on our list are:
- Payment processor (stripe) Q1/Q2
- LTV model (Q1)

**Roadmap follow-up**
PM <> BI 2021 roadmap

HI, 

To follow up on our roadmap session last week, these are the PM projects we believe should go in the BI 2021 roadmap: 
Thanks for your time yesterday. These are the PM projects we believe should go in the BI 2021 roadmap: 

 A few questions around these:
Is there anything missing that we haven't listed above? 
Can you indicate when you'd like these done by (Q1, Q2, H2) and if there are any timeline dependencies and/or other priorities we need to consider? 

Let me know if you have any questions!

Thanks, 

Dave 

Hey Molly, 

To follow up on our roadmap session yesterday, these are the projects that we believe should go in the BI 2021 roadmap:

More + better insights from qualitative data (with a focus on demographic data). This project is depending on the successful hire of the Customer Insights role. 
A 'Product Performance Grid' dashboard. We can look into what the possibilities are for this - either within Looker or with Tech. Do you have any timeline in mind for this? 


Let me know if anything is missing from the list above! 
Let me know if this looks good and if anything is missing.


Thanks, 

Dave 

**Roadmap reminder**
Hi Gaby,

Can you confirm the projects below look good on your end? We’re building the roadmap now and I want to make sure we don’t miss anything.  

Thanks, 

Dave 

**Quarterly roadmap email**
Hey Neil and Nikita, 

For tomorrow's check-in, I'd love to use the time to 1) see how the Looker introduction sheets have worked, and 2) do a quarterly review on the BI roadmap.  

Below is what we had planned for Q4, a few extra projects on my list to discuss are:
- Web KPI kickoff reporting (Neil)
- Bytedance A/B integration
- Remove Digitbrew reporting from Looker
- SEO & Search Reporting

A few questions on my mind are:
- Are there any projects we had planned we can de-prioritize?
- Is there anything additional I'm missing for Q4?  
- Looking ahead to 2021, when do you think you will start planning the digital product roadmap?

Cheers!
Will


Hey Neil and Nikita, 

Can you confirm this looks good on your end?
 
I updated our BI Q4 roadmap to reflect our conversation last week.  
 
I deprioritised App and Product Performance reporting due to strategic priorities, kept the user journey reporting, and added Bytedance and Web KPI reporting.  
 
SEO and on-site search reporting are Q1 2021 top priorities.
 
Cheers!
Will

Fwd: BI / Finance Quarterly Review
Hi Tony, 

Since you're on holiday, I thought it was easier to send your quarterly review by email.  I'm happy to catch up in person on this if you want to discuss anything in more detail.
 
BI was able to complete everything we had on the Finance roadmap for Q3, including the Checkout.com reporting ahead of schedule.  
 
For Q4, the additional priorities from team Finance are Papier KPIs, Kickoff Inventory and Finance ERP (this will carry into 2021), finalise Emma's tax metrics, and help Alice transition trading over to the Exec explore.
 
For Q1 2021, we'll work on incorporating freight and import duty.  
 
Let me know how this looks and if there's anything I missed,
Will

**Company wide roadmap email** 
Hi all, 

The BI 2021 Roadmap can be found below (PDF version attached for reference).

Our biggest priority this year remains to support you with the data you need to make better decisions. In addition, we will be working on: 
- Building a data infrastructure that can accommodate our growth 
- Answering difficult questions using advanced analytics

We’ll regularly update the roadmap to stay in line with changing priorities of the business and to track the progress of projects. The most recent version of the roadmap will be on our Notion page.

Let me know if you have any questions! 

Dave

(Add a well sized image to the email - people are less likely to open attachments. Still do add an attachment as PDT so people can reference and store it should they want to.)


## Announcement messages
**Important FYI in Slack**
Really Important FYI: 

This evening at 6pm, we will resize our data warehouse to add more space.  Looker can continue to be used from this evening at 6pm. However, our underlying data sources will not update until the resize job is completed. This means that data will be only as recent as it is tonight around 6pm until the job is completed.

We expect the job to not take too long (although there aren’t any guarantees) and we’ll provide updates here on the progress. By Monday morning, we aim to have all source data updated again. 

Let me know if you have any questions on this!  More details on why we are doing this to our data warehouse below for those interested:

What has been done so far
We have been optimising our data tables over the last ~4 weeks and have been able to measure significant performance improvements in Redshift (our data warehouse) following these efforts. We have also continued to move transformation jobs over from Looker to dbt which we believe will be the single biggest factor in making our data infrastructure future proof. 

What’s next
We are now ready to test moving over the most troublesome transformation, which has often resulted in Redshift running out of disk space. In order to test this transformation, we need more space in the data warehouse to: 
Compare the dbt model against the table in Looker
Ensure the current Looker tables remain usable and update overnight, minimising user disruption

What’s required to get there
With the increase in data from our new Facebook Dynamic Ads reporting and to effectively quality check this changeover, we need more space in our data warehouse to facilitate this work. We will resize our data warehouse cluster and add another 320gb of storage to Redshift.


## Invitation announcements 
**BI monthly invitations**
Hi Nikita, 

We are planning towards our next Looker BImontly session in February and wonder whether you would be up for presenting how you use Looker? These are a few use cases that would be great to cover (in addition to anything else you may want to present):

- KPI Reporting dashboard including the period comparisons and the annotations
- Experiments mega boards and how this plays a role in the A/B testing framework/process
- Conversion funnel report 

Let me know if you have any questions around this; if you could let me know soon, that would be ideal as we can start booking in a timeslot. 

Thanks, 

Dave 

Hey Nikita, 

Booking in an hour (might not need the full hour) to go through your slides for next week's BI monthly meeting. The plan is to speak for 15 minutes about: 
- An intro to the CRO team 
- What are CROs KPIs and why 
- A few examples of how CRO uses data. Some ideas I thought of (feel free to present on anything else you would like though):
- KPI Reporting dashboard including the period comparisons
- Experiments mega boards and how this plays a role in the A/B testing framework/process
- Conversion funnel report 

Let me know if you have any questions! 

Dave 

## Requesting stakeholder input
**How to do sessionization**
Hi Both, 

I would like to **get your opinion on a reporting issue** I'm running into.  I wanted to email first to give you the time to think about this instead of jumping into a meeting.  If it is horribly confusing (since I'm deep in the weeds on this and have way more context), just let me know and we can do a 15min stand up to talk through it.

As we've discussed a few weeks ago, I've been testing changing our definition of a session to better align with reality and GA.  Currently, all traffic within 30 minutes is one session.  What I am testing, is if someone comes back to the website within 30 minutes from a different marketing channel, call it a different session.  

The original use case was Email, where a common User Journey on-site would be: Click on Google Ad -> Purchase -> Click on CRM Transactional Email -> Come back to the site within 30 minutes.  As of now, this is one session, but the rationale is this customer would not have come back without the CRM email, and thus the Email should be its own session (and touchpoint in attribution).

In testing the results, this increases Paid Affiliate attributed sessions by ~15% and value by ~80%.  From speaking with Rupert, it sounds like common user behavior is to: Be on the site -> add to basket -> go to affiliate sites for discounts -> come back and purchase. **I believe we should exclude counting Affiliate in this situation as an additional touchpoint.**  Since they were already on site and the affiliate site did not incrementally bring them back to site.  **Do you agree with this?**

Cheers, 
Will

Notes: 
Answer first = I want your opinion. This shows what is expected in the email. It's a technical topic - could have done a better job adding context more to the bottom though. 

**Getting feedback on attribution changes**
Hi all, 
 
We have been working on the allocation of checkout answers between paid and organic to fairly attribute between all mediums. We have the Looker update ready to go live but I wanted to clarify our approach and the impact this change will have on the metrics prior to releasing this update.
 
*Approach*
We allocate orders with the 'Search Engine' or 'Social Media' checkout survey group as their source **based on the ratio of organic vs paid converted sessions by day**. As an example, say that 20% of all converted sessions on 01/09/2020 came from an organic search medium. Then we allocate 20% of orders with the 'Search Engine' checkout survey group to the 'Organic Search' medium and 80% of the orders to the 'Paid Search Non-Brand' medium. We used the same approach to allocate between the mediums 'Organic Social Brand' and 'Organic Social Other'.
 
**Impact summary**
Allocating Checkout Survey answers between Organic and Paid reduces paid acquisitions by 3%
Organic Social is now the 6th largest channel; 75% driven by the “Organic Social Other” medium
Paid Social Prospecting and Paid Search Non-Brand are the largest mediums negatively impacted by the changes
More details around both approach and impact can be found in these Slides.
 
Please let me know if there are any questions or concerns before we push this live. Because of the slightly technical approach and the impact, I am more than happy to clarify any questions or concerns in more detail during a call. 
 
Thanks, 

Dave 


## BI development delivery 
**Delivery of explore**
Hi Rupert and Bhav, 
 
We pushed the initial version of the Facebook Ads explore live this morning - it can be found in the 'Facebook Ads' explore. This isn't a final product as we haven't yet modelled certain fields - see 'Next steps' for what's missing. Your feedback on this is much appreciated as we continue to work on this. There are probably two things worth highlighting in addition to any other feedback you may have:   
The Ad Creative images brought in are large. Would you like these to look similar to the product images sizing?
We only brought in one Ad Group - you may want to see additional groups? 

Next steps 
We'll work on bringing in the additional requested fields below. Note that the Insight fields are structured differently (they are spread across separate tables). I'll draft a design for these and then verify with you which fields are required and how we'll model these in Looker. 
 
Fields to add: 
Adsets fields: 
budget_reimaining
lifetime_budget 
Insights field:
action values
conversions
purchase roas
video watched actions
Thanks,
 
Dave 

**Delivery of attribution changes**
Hi team, 
 
We've been making some changes to our attribution model. Specifically:  
Checkout survey comments are now added to our attribution model. As an example, when someone writes 'Google' in the checkout survey box, this is now added to our attribution model and classified as 'Paid Search Non-Brand' Attribution Medium. 
We combined TV related checkout survey comments with the TV checkout survey group (and these are added to our attribution model) - this was an ad-hoc improvement. 
We measured the impact on the number of attributed orders (position based) between January 2020 - August 2020 and the overall impact across mediums is small. The main differences in total number of orders pre and post change are: 
Offline Referral: +3.1%
Paid Social Prospecting: +0.7%
Paid Search Non-Brand: +0.01%
Organic Search: -0.3%
Paid search brand: -0.3%
Direct: -0.6%
Paid Search Shopping: -0.2%
Online referral: -0.3%
TV: +1.9%
The other attribution improvement we are currently working on is allocating checkout answers between paid and organic to fairly attribute between all mediums. 
 
Please let me know if you have any questions or concerns regarding the changes made or its impact. 
 
Thanks,
 
Dave 


## Delivering analysis 
Hi Bhav, 
 
I looked at the average number of days it takes for a customer to make another purchase. The data varies greatly between years and categories; the assumptions/filters used include: 
Excluded orders of the Greeting Cards and Invitations & Occasion Stationery Category One as these would skew the data significantly 
Only looked at orders placed after the 1st of January 2020 to keep the results recent and relevant
Across all categories (excluding Greeting Cards and Invitations & Occasion Stationery), it **takes an average of 39 days for a customer to make another purchase**. The data by category 1 is below (interpretation of the table: Category One is the initial category purchased - it then takes the customer an average of X days to repurchase a product of any category excluding Greeting Cards and Invitations & Occasion Stationery): 

 
Let me know if this makes sense; whether this helps to filter for existing users? 
 
Thanks, 

Dave 

## Project Kickoff email 
Hi all, 
 
A ticket that we're about to prioritize is adding code redemptions as a last touch to our attribution model. There are a few things that need to happen before we can start:  
There needs to be a way to add marketing parameters (e.g. campaign, source, medium) to redemption codes in the Admin section. This would be for both historic codes and any redemption codes going forward
Marketing would then backfill these codes with the parameters
Once this is pipelined into the data warehouse, we can incorporate code redemptions as a last touch to our attribution model
If you agree, I can set up a kickoff call later this week to map out more detailed requirements and actions? 
 
Thanks, 

Dave 

## Solving hard data quality questions 
Hey @Bhavisha Dadhania . I had a look into this - only 5 sessions have the medium 'Paid social prospecting’. These sessions all have an Email campaign referrer AND Facebook UTM parameters. I've seen this behaviour before where sessions start on a nested page (e.g. page = 2 in the URL) with a non-Facebook referrer but with FB or IG UTM parameters (similar to this issue). Do you know what behaviour can result in this structure? 

This Look shows the details of the 5 sessions. With our current attribution logic, these sessions are attributed to Email (following the “utm_medium=email” string in the referrer) rather than Paid Social which is causing the different medium names.

Hey @Bhavisha Dadhania I can see in the URL that you provided: "fbid=6249588409551&page=2&sort=favourite&utm_campaign=%5BUS%5BSOCI%5BSTN_ORG%5BPROS_STANDARD%5BPURCHASE%" So the URL does contain page=2. I don't know why this page 2 would contain UTM parameters though - does it have to do with the campaign that is being run: [US[SOCI[STN_ORG[PROS_STANDARD[PURCHASE]: PAPIER (this campaign applies to all 5 of these session)? 

Hey @Bhavisha Dadhania. I had another look into this to see if it’s a wider problem in our web tracking with implications on attribution. Findings below: - < 0.01% of our sessions start with a nested URL so it’s not something that happens very often. - Of the 26K sessions that do start on a nested URL, 40% have paid social prospecting mediums (main campaigns showing this behavior are: “[UK[SOCI[STN_ORG[PROS_STANDARD[PURCHASE]: PAPIER”, “[US[SOCI[STN_ORG[PROS_STANDARD[PURCHASE]: PAPIER”, “[US[SOCI[STN_STN[PROS_STANDARD[PURCHASE]”) - see this Look with all campaigns showing the behaviour - I pulled the data of these sessions and this behavior started in December 2019, so it’s not something that started only recently - I also confirmed that this structure is what we directly get from our source web tracking data - it’s not something that changes because of how we model the data in the backend. I’m honestly not sure what behavior is causing this but it doesn’t seem to be an issue with how we model the data. Here are a few journeys of users who get Facebook parameters in nested pages (querying our web data so these are a bit slow): - Google > FB (nested) - No referrer > FB (nested) - Email > FB (nested) Do you have more context as to why this might happen based on the above? Perhaps this is a result of how users interact with these specific campaigns? 

Hey @Bhavisha Dadhania Yeah this behaviour is very confusing. The next step would be to involve Joe / Tech to look into why this might happen with their understanding of our web tracking. I think it's important to keep an eye on this and make sure it doesn't become a bigger issue than it is but I don't think the impact is large enough to escalate to Tech at this stage. Let me know if you disagree though!

## Understand which analysis is currently 
I dug into this and the summary of my findings are below. Let me know if this is helpful, and if you'd want to meet to discuss next steps in more detail. . Currently, we do not have data in Looker (available to users) for Onsite Search. . We do capture data about onsite search. The granularity of this data is the term people search on site. If someone searches many terms, we would record each term once per search. We know what term they searched for, who they are (as best as possible, anonymous vs. signed into an account), what page they were on when searching, what page and events they triggered after searching (more difficult to report dynamically though), and the device and browser they were on. . It would be relatively standard for us to stand this up as it's own explore and connect it to our other web data (Device, Browser, Page, User, and Session information). You could get KPI metrics like conversion rate of search terms. It would be much harder for us to develop Onsite Search specific metrics (like, what % of people bounce after searching vs. clicked on something they wanted to find). Or what was a dynamic user journey of customers after they searched for "cat notebook". . What would also help us is to know what you would want to know. What KPIs from onsite search do you care about? Do you have examples of reports you have looked at in the past that have been helpful?

Hi Will - thanks for looking into this. I was thinking the below to start with: Filters: mobile, customer type, market Overview - % Sessions used internal search - Sessions with Search - Total Unique Search - % Search Exits - Time after Search - Search Depth - % Refinement - Total revenue driven by search - Traffic channel segments (to see % of total search driven by each channels) Search terms Search terms details (currently available I believe)

Hey @Leslie Delaplagne Sorry for the delay on this. A lot of these are already possible in Looker using event description 'Searched Products' and the dimension 'Searched Term'. Metrics possible See below the requested metrics and the corresponding measure names and the Look it's referred in (linked below) - Search term - Events Searched Term (Look 1) - % Sessions used internal search - Sessions Searched Rate (Look 2) - Sessions with Search - Sessions Total Searched Sessions (Look 2) - Traffic channel segments - Look 3 - Total Unique Search: Look 4 Look 1 Look 2 Look 3 Look 4 Workarounds / not sure - % Search Exits: we do collect Exit Rates on a page level. However, the Exit rates after Search are captured on the Search Page Type - see this Look. I'm not sure if that helps at all? - Time after Search: we don't currently have this. A very hacky way of doing this would be to take the Session End Time and subtract the Event Start Time of the event 'Searched Products' as in this Look Planned for later this year - Total revenue driven by search: this is part of a larger project planned where we model event-level data back to order level data, which will help answer questions like these. Not currently possible - Search depth. As I understand this, this would be: how many pages do people visit after having used Search? - % refinement: this would be the % of users who search again immediately after searching? Let me know if this helps to get some initial insights? We can then see which of the other metrics that aren't possible / require workarounds are important to get right and we can plan from there. 



## Gathering requirements 
**Asking for specific questions**
I do think it'd be possible to put something together. What would be really helpful is to have a few really targeted questions for us to work off of. An example could be "What web pages do customers visit after they land on /account/orders from an email" or "What are customers that follow this path buying? (sample to full order, the same product, etc.)".  

**Challenging importance** 
I believe Looker is reporting this accurately. From what I can tell, there is no limit to someone singing up to the newsletter, they can do it many times from many locations. That means I don't have a quick way to get a 'unique' count. . How important is this, and will it change decision making? . You could calculate a percentage of the rows, and then multiple the row total (the true unique number) by those percentages. We could create an idea of a 'first location', however that would be a BI ticket we'd have to prioritise, and it's also a very specific, nuanced project that I'd prefer to not have in Looker if it won't change decision making.

**Pushing back on data tests / not knowing the answer**
Dealing with uncertainty 
I couldn't find these web pages in our internal reporting. I might be searching for them the wrong way, but I can't reproduce what is in GA. I will follow up with Joe when he is back next week and see if I can get more information

For the second example, Abandon Cart, I can't honestly say. I'm looking at our UTM data and it seems like Looker is reporting the raw data the right way. Is there anything different about how the UTMs used to be set up? Does Looker match GA for most recent months?

## Lookerpaps delivery 
**LTV model**
New Friday Release:  Lifetime Gross Margin Model
With a focus on 6 month payback.  This model in Looker predicts, for every acquisition, what their six month total gross margin will be based on 62 features.  @anthony @Allison This empowers us to:
- Make faster, data-driven decisions about liftime value - instead of waiting a full six months to measure and learn from strategic changes, we learn right away
- It's forward looking instead of retrospective
- More granular reporting (per customer) instead of aggregated cohorts
- A step forward in understanding liftime value of our customers and implementing predictive models into our reporting
Big thanks to @joe that helped create and improve this.

**Attribution Update:**
We officially have one attribution model again.  This Attribution model now includes checkout survey data to more accurately reflect less-easily tracked channels.  Benefits are:
- Data-driven way to attribute social's impact on attribution which was under reported due to view through and cross device tracking
- No loss of accuracy to campaign performance reporting, since we don't overwrite touch-points that have more accurate tracking (like click IDs)
A structure we can leverage to report offline channels impact on sales in later enhancements.
.
Why does this matter?  Our attribution model is a key lever to drive profitable growth.  Improving our data to empower performance marketing is the best way to improve this lever.  Performance Marketing already adjusted their strategic social budget by 5% because of this work.

**Attribution 4.0 is live**
Our latest enhancement in our attribution model (devaluing direct acquisitions) is live as our single SOT model.  Before this change, Direct was our third largest acquisition channel.  This is not industry standard and illogical, since an acquisition must have learned about Papier from other sources before coming direct to site.  @Allison @Rupert @sophie @Lizi @anthony.
.
So What:  Now, we have a more accurate view on which campaigns are driving acquisitions (previously falling into Direct).  This will help marketing more accurately report performance and better optimise their capital to the initiatives that are driving the most efficient return.

The **Executive Explore** is now live and tested in Looker.
This explore helps the marketing and finance team create reports with blended metrics (e.g. CPA, contribution) without having to perform merged queries and final transformations in spreadsheets. A great use case for this explore is the creation of the weekly trading deck.

New Release: **Keyword to Category Attribution**
We have a new explore, "Google Click Attribution", that empowers the Performance Marketing team to know which specific orders, and more importantly which products, each keyword they bid on every day drives (utilising our attribution model).  So What?  This is will help bring campaign optimisations to a new level of visibility that Performance Marketing has wanted for a while, and help us more efficiently scale our customer acquisition (a continued high priority for Papier into 2021).

**Code redemptions** are now added as a last touch to our attribution model. 
Impact summary
Paid acquisitions aren’t significantly impacted by attributing code redemptions
The channels Email, Referral, and Paid Affiliate show a significant increase in attributed acquisitions
All mediums using code redemptions show an increase in acquisitions. Paid Affiliate, Email, Online Partnerships and Refer A Friend show the largest increase
More details around both approach and impact can be found in these Slides. @Rupert @sophie @Allison @Lizi

^ In hindsight, this isn't great. Before impact: this is done because it's best practice. So what: having this insights allows us to better understand what marketing activity drives customers and help us scale customer acquisitions 

**dbt update**
We reached a milestone in our dbt journey yesterday: we migrated two fundamental transformations from Looker’s PDTs to dbt: webapp_aliases and webapp_pages_aliases. Webapp_pages_aliases is one of our most crucial tables as this is where we define sessions; the logic from this table is used to build other web/attribution tables. 
*Impact*
The benefits of using dbt over Looker’s PDTs are: 
- Faster query run times. The webapp_pages_aliases PDT used to take 40 minutes to build. With dbt, we are only inserting rows that are updated since the last time the model ran; over the last 4 runs, we inserted an average of 2 million rows within 60 seconds (98% decrease in query run time). These improvements will become even more significant as the size and complexity of our data increases and dbt is crucial in us having a future proof and cost effective data infrastructure. 
- Increased control over data scheduling: updating PDTs in Looker results in Looker running a lot of different PDT transformations at once which then overloads the warehouse and causes queries to not run or to be cancelled within Looker. An example of the impact was seen last night where queries were cancelled. Another example is when we aim to update the data in Looker when the PDTs didn’t succeed overnight; it takes multiple hours for Looker to update its tables and be queryable again.  With dbt, we fully control the builds of individual tables, allowing us to add features / fix issues / update data where needed without overwhelming the warehouse and causing causing Looker queries to fail. 
- Over time, we will work on improved data quality testing and data infrastructure documentation, both of which are other key features of dbt. 

We do realise that the dbt migration has caused some disruption in the past to Looker users. Running transformations within dbt is a big change in our data infrastructure and sometimes issues can creep in; however, we have learned a lot in the past few weeks and we aim to limit the impact it has. (edited) 

**Update on data warehouse improvements** 
This week, our main focus has been on finding ways to ensure that Looker consistently updates our data overnight. This translated to identifying performance improvements in our table design that are less constraining on our data warehouse and avoid the data warehouse from running out of disk space when the transformation jobs run. 
Looking at the query plans of our web tables / transformations, we identified that a few of our most taxing joins were inefficient, causing memory to spill to the disk and consequently causing our warehouse to run out of disk space. To improve the performance of the joins, we redistributed and resorted some of our largest web tables following best practices. 
*Impact*
Most importantly, no transformation job has failed overnight in the last two days.
Looking at the query plans, the most constraining joins are now a lot more efficient. 
Our data warehouse is using a smaller percentage of the available storage to run the overnight transformation jobs. 
*Next steps*
Even though we’ve made good progress, we are still utilising a very high percentage of storage to run the overnight jobs. To ensure that Looker can keep updating consistently, we will continue to focus on researching and implementing performance improvements next week.

**Facebook Dynamic Ads Explore**
We just added the Facebook Dynamic Ads Explore to Looker. 
Dynamic ads use our product catalogue to show feed based product specific ads. The Facebook Dynamic Ads Explore differs from our existing Facebook Ads Explore in that Facebook Dynamic Ads only includes dynamic ads at a product-level granularity, whereas Facebook Ads includes all ads (including dynamic ads)  at an ad-level granularity. 
*Impact*
This explore allows PM to report on dynamic ad spend by category which will also 
improve our category CPA reporting. @Rupert @Bhav

^ Can be improved: 'Currently, dynamic ads are categorized into Other even though the targeted product are in Categories. PM is doing this manually now. This change allows reporting within Exec explore by category 1. So what: Facebook accounts to 30% of our Spend - understanding how ads perform across categories is critical to achieve top line acquisition targets. 

**Quick update with high impact**
We now have Stripe Processing Fees since February 8th. 
This adds £11.5K and £14K fees in February and March respectively, and an equal decrease in GM2.  This is a short-term, hardcoded estimation based on logic provided to us by Finance.  Our logic overstates the actual fees by ~10%, but we believe this is acceptable for now since the actuals would be impossible to replicate perfectly (they are dependent on bank fees, card rates, etc) and we plan to replace these estimations with actuals after setting up a new data pipeline with Stripe over the next month. 

## Post mortem Lookerpaps


## Driving change 
Update on importing data from Looker into Google Sheets 
*What happened?*
Since last week, the Lookerfetch function has stopped working because of technical difficulties. Because the issue is with custom functions in Google Sheets, Looker is unable to provide support on this.  
*What’s the solution?*
Looker has built the Google Sheets Looker Action through which we can send or schedule data from Looks into Google Sheets. A benefit of this method is that we can monitor these Actions within Looker and we get full Looker support should anything go wrong.
*How do we use this?*
We set up this doc with instructions on Looker Actions and a suggested approach on how to migrate existing reporting from custom functions to Looker Actions. Alice has started doing the migration for Trading materials and so far it’s working as expected. 
There will be some initial set-up effort but this solution will be more reliable and scalable than other alternatives. Do let me or Alice if there are any questions / concerns. @Rupert @Alice Morris @Gaby @anthony

## Escalation emails
Hi Brian and George,

Sorry to reach out directly, but I need to escalate the urgency of this issue.

The broken Stripe fee reporting is causing mismanagement of our business.  We are over-reporting our profit per order, senior leadership does not have the right data, and as a result, we are not hitting our financial goals.

This has been broken since February.  The "expected" change in reporting was not articulated as part of the contract negotiation and not known to us.  Because of this, our CFO is very frustrated with the result.  I don't believe this issue is being met with the urgency we need.

Can you please escalate this ticket internally?  And help coordinate a faster resolution?  I recommend we set up a call with technical support on Stripe and our side to solve this more quickly.

Cheers,
Will


## Tech tickets
Overview
Now that we show customer's the expected delivery date, it would be great to add this to the reporting. This, in addition to the delivery tracking work in H2, will help us build new Customer SLAs and help improve the customer experience

Problem
Currently, we show customer's when we expect their order to be delivered. However, we don't record this in the database. We'll want to know this data point to report on.
I would think this would fit nicely on fulfilment_shipments. And it will be great to start recording this data now since we have it.

Impact
Improving our operations has a positive impact on Customer NPS. One of our 9 core goals this year is to raise NPS, and having better data and tracking on this will help improve our reporting on printers.
SLA is typically measured by the customer's experience, i.e. did we get their package to them on time (not just leaving the printers). Knowing when the customer can expect the package is half of this meric.




Overview
Tech is changing the way Sellables are created to make it better for everyone. This will result in a new field identifying the state a product is in. We'd love to add this field to Looker reporting.

Problem
Tech are adding an important field for products, we want to make that available to Papier through Looker.
The recommendation is to add the column publishable_state to the Products ETL for all sellables that have this field (books, products, stock items, photobooks, etc.)

Impact
This will help Merchandising and Commerical ensure products are live on site the way they should be. Having the products correctly on site increases sales and conversion rate

## Other
Hi all,
 
Happy friday! Just a reminder that next week the Tech and Product teams will be doing a 'Space to Create' week. The goal is to use some time outside our normal sprint cycle to work on more experimental ideas, with everyone in the team being given complete freedom to work on any project which they think will benefit Papier.
 
We're all really excited to see what we can come up with, the goal is to end up with something that we can ship to customers, whether as an A/B test, new internal functionality, or improvements to existing flows.
 
This will have an impact on other tech/product work during the week, and we won't be working on normal tickets during that time.
 
If you have an urgent request during the week, please let me know directly on Slack and we'll make sure to look at it. For any other requests, please continue to use the Tech Ticket Inbox in Notion as usual.
 
The next two week sprint will start on 19th April, and we'll pick the tickets for that sprint on the Monday morning.
 
If you have any questions, please do let me know!
 
Thanks
 
J
