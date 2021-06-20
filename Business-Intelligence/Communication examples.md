# Communication templates

## Gathering requirements and project management 
**Asking for specific questions**
I do think it'd be possible to put something together. What would be really helpful is to have a few really targeted questions for us to work off of. An example could be "What web pages do customers visit after they land on /account/orders from an email" or "What are customers that follow this path buying? (sample to full order, the same product, etc.)".  

**Challenging importance** 
I believe Looker is reporting this accurately. From what I can tell, there is no limit to someone singing up to the newsletter, they can do it many times from many locations. That means I don't have a quick way to get a 'unique' count. . How important is this, and will it change decision making? . You could calculate a percentage of the rows, and then multiple the row total (the true unique number) by those percentages. We could create an idea of a 'first location', however that would be a BI ticket we'd have to prioritise, and it's also a very specific, nuanced project that I'd prefer to not have in Looker if it won't change decision making.

Hey @Mathilde Dechansiaud, thanks for bumping this. We did kick off work, but the finance model is looking to be more cohort based, which I don't think will help answer this question. I actually thing we should just use the LTV actuals for LTV reporting on this. Do you have a particular deadline for when you would like this to be answered by? Also, how high of a priority is it, is it more of a nice to have or is there a key decision it would influence?

**Pushing back on data tests / not knowing the answer**
Dealing with uncertainty 
I couldn't find these web pages in our internal reporting. I might be searching for them the wrong way, but I can't reproduce what is in GA. I will follow up with Joe when he is back next week and see if I can get more information

For the second example, Abandon Cart, I can't honestly say. I'm looking at our UTM data and it seems like Looker is reporting the raw data the right way. Is there anything different about how the UTMs used to be set up? Does Looker match GA for most recent months?

**Pushing back for others to do analysis**
Hey @Mathilde Dechansiaud. Thanks for this. 
The % credit Look looks good to me.

To confirm the next steps:

Contribution comparison
This is the Look with First Order Contribution by channel. As discussed, it is worth thinking about how to split this data over time and category given the implications on CPA. It should be easy to change this to all orders rather than first orders using filters.
I think PM already report on first order contribution in the In Week reporting which is worth using as a reference. 

Mention Me customers flag
We should be able to create this flag soon. We will assume that any customer that got issued refer a friend credit is a Mention Me Customer who received credit.

Customer analysis
I’d recommend speaking to Louise and/or Faye to understand what is possible in Looker and how to approach the analysis. Happy to support/validate any reports coming out of this exercise.

@Rupert Griffiths  @Will (Danger) Huntoon let me know if you agree with the next steps above. 

**Clarifying next steps from meeting**
Hey @Nikita Kursov. Following up with what I believe the outcome of yesterday’s meeting. Sessions A point to check is how Kameleoon reports on sessions related to the experiment. I believe you mentioned that filtering on Homepage page types only in Looker brings the data a lot more in line - could this be the cause of the discrepancies? In addition, Will provided this Custom Filter. @Will (Danger) Huntoon can you confirm what the intended behaviour of this is? From my understanding, this filter would only exclude sessions in which all events happened at the same time as the session start time (e.g. this session gets excluded). Conversions If a user converted during a session, that gets counted as a conversion in Looker - regardless of whether that was pre or post being part of the experiment. This will be different from Kameleoon where the conversion only counts after being part of the experiment (I assume?). We could do a scoping exercise on our end to see if it’s possible to more dynamically count conversions in experiments but the scope of that is likely a roadmap project given the complexity. Let me know if the above makes sense of if I've missed anything. 


## Project management 
**Getting context pre kick-off**
Hey Gaby - before kicking off the Upsell project I want to make sure I have the right context and can set the right expectations with everyone involved. What would be really helpful is if you could share an existing Upsell report you use and indicate what you would want to report on, but currently can’t? That way, I can dive a bit deeper in the upsell data structures and get a feel for what should be discussed during the scoping call. 
Happy to discuss over a call if that’s easier!


**Attribution kick-off email**
Hi all, 
 
A ticket that we're about to prioritize is adding code redemptions as a last touch to our attribution model. There are a few things that need to happen before we can start:  
There needs to be a way to add marketing parameters (e.g. campaign, source, medium) to redemption codes in the Admin section. This would be for both historic codes and any redemption codes going forward
Marketing would then backfill these codes with the parameters
Once this is pipelined into the data warehouse, we can incorporate code redemptions as a last touch to our attribution model
If you agree, I can set up a kickoff call later this week to map out more detailed requirements and actions? 
 
Thanks, 

Dave 

**Onboarding kick-off email**
Hi all,
 
As Papier’s headcount is growing quickly over the next few months, we want to ensure new Paps experience a seamless Looker onboarding process.
To facilitate this, we’re reviewing our current Looker onboarding process and as part of that, we want to speak to recent joiners and understand what went well and what can be improved in our onboarding.
 
I’ll be scheduling 30 minutes with each of you over the next few days to talk through your Looker experience. Feel free to suggest a different time if the suggested time doesn’t work.
 
Thanks,
 
Dave

**Royalties kick-off email**
Hi all,

A high priority Q2 project for Finance is the revision of the Royalties calculation. We want to kick this off early in the quarter as it’ll likely involve Tech development work that needs to be scoped out. I've added context below and booked in 30 minutes next week to discuss this in more detail. 

Let me know if this time doesn’t work and if there are any questions or concerns beforehand. 

Dave

Problem
Tech supplies us with a Royalty value that is calculated as Designer Royalty Fee % x Product Revenue (as far as we know).
There are two challenges with this calculation:
- Product Revenue is a sales tax inclusive amount, whereas royalties should be calculated on sales tax exclusive product revenue.
- The Product Revenue includes the price of envelopes - these aren’t design elements and ultimately shouldn’t be part of the royalty fee.

Finance currently builds ad-hoc custom reports (using a custom sales-exclusive Royalty Basis Price from Looker and assumptions around envelopes revenue) to create a more accurate royalty payment report. The main problem is that these values differ from what the Commercial team sends our Design partners more regularly (using the Items.Royalty field). As a result, partners lose confidence in the royalties data we provide them.
 
Impact
Providing accurate royalties data to our Design partners is key to maintaining the relationships and continuing to offer product ranges that can achieve our growth goals.
 
Open questions to discuss
- With the difficulty around tax reporting, it is probably easier for the final Royalty calculation to sit within Looker. In order to get there, we want to discuss a few points:
- What currently makes up the items.royalty_basis_price field? 
- What options do we have to subtract envelopes revenue (and potentially other upsell revenue?) from the items.royalty_basis_price (if not subtracted already)? As far as I can tell, envelopes are tracked as separate SKUs, but not as individual products (unlike our Pens for example) - as a result, we currently don't seem to track envelopes' product revenue. 
- Can the Royalties % be added to the ETL? We wouldn't want to hardcode this in the logic as it can change and already is different across partners. 

Let me know if there are any questions or concerns regarding this. 
 
Thanks,
 
Dave

**Royalties follow-up**
Hi all, 
 
Thanks for your time earlier today - below is a recap of what we agreed and follow-up actions. 
 
What I believe we agreed:
The final royalties calculation will reside within Looker given the complexity around our Sales Tax.
Pending on the results of the actions below, we can consider a phased roll-out of the royalties calculation: 
Phase 1: Looker calculation using the tax-exclusive items.royalty_basis_price (with optional assumptions around the cost of envelopes). We'd still need the designer royalty charges from Tech in order to calculate this accurately. 
Phase 2 (pending on technical feasibility and impact): adding additional logic that requires structural changes in our reporting (e.g. bundles, more accurate envelope reporting).

Follow-up actions: 
Joe - can you confirm which field contains the royalties fee by designer (I can't easily find it and it might not be ETL'ed)? As discussed, this field can change over time so it would be best to capture the fee at point of sale - how difficult is it to add this to the ETL? 
Emma - Tech belief that the items.royalty_basis_price excludes non-designer elements such as colored envelopes - does this align with your calculations and comparisons?
Emma - can you confirm whether we want to exclude the costs of free envelopes from the royalty basis price? If so, we can pick up on what logic we should build into Looker to account for this. 
Emma - the biggest challenge in getting the royalties completely accurate is around the bundles. It doesn't sound like this would be a straightforward fix given our current data structures. How important is this to get right?

Let me know if you agree and if I'm missing anything! 

Dave 

**Onboarding follow-up**
Hi all,

I wanted to follow up with key insights and next steps following the onboarding review.
 
First of all, a massive thank you for sharing your onboarding experience and ideas for improvement. Your feedback has given us lots of inspiration; below are the key onboarding challenges you shared and our next steps.
 
Key onboarding challenges  
It’s not easy to find existing reports. As a new joiner, these existing reports help to understand the business and its key metrics. In addition, existing reports will speed up the time to insights, as most reporting use cases already exist somewhere.
Current Looker docs don’t cater to all learning styles. Some prefer visual aids/screen share, others learn by exploring from existing reports.
It’s challenging to build initial reports and insights - specific hurdles that arise:
Which Explore/fields/filters should be used?
How can we be confident the data answers the question accurately?
Next steps
There are a lot of follow-up actions from the onboarding review.
 
In the short term, we will revise the BI introduction meeting with the new joiner and focus more on introducing Looker and available training resources. We’ll also create concise Looker onboarding docs, covering the business’s key metrics, an overview of our Explores, a glossary of key Looker terms, and an introduction to filters in Looker.
 
In the short-to-medium term, we will introduce BI Office Hours. These are recurring opportunities to book 15-30 minutes with the BI team during which we can cover e.g. training, scoping of a data use case or validation of a report. In addition, we will set up centralized, validated Looker KPI dashboards with key Looks per team.
 
In the longer term, we are planning to introduce a centralized space with key reporting use cases and corresponding reports, a BI newsletter, training videos, and an improved FAQ.
 
We will also be sharing a recommended onboarding strategy to all Paps following the learnings soon.
 
 
As we start to roll out these changes I'll be in touch with some of you to align on the onboarding process and to get a feeling for the effectiveness of the new initiatives. In the meantime, feel free to reach out with any questions or suggestions you may have.
 
Thanks, 

**Following up on open questions**
Hi all, 
 
There were two open questions from this week's session around attributing checkout answers to organic and paid:
What is the 6 month average ratio between paid and organic session conversions across search and social mediums?
Social: 36% of converted sessions are coming from an organic social medium
Search: 28% of converted sessions are coming from an organic search medium
How many sessions were converted by the different Search mediums in the last 6 months? This should inform whether we'd want to split current orders allocated to the 'Paid Search Non-Brand' medium between 'Paid Search Shopping' and 'Paid Search Brand' mediums as well.
See the table below for the distribution of converted sessions in the last 6 months
 
Let me know if this answers the open questions; whether you'd be happy for us to push the current proposed changes (following the slides) to live and whether we should add a ticket as a next step to further split the allocation of paid search orders. 
 
Thanks, 

Dave 


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

**Customer Explore update**
The revamped Customer Explore is live
Why we’ve done this
There is an increased focus on retention and repeat behaviour analysis across the business. To facilitate this need, we want users to be able to easily create accurate reporting in the Customers Explore. The previous Customers Explore didn’t allow for this as it was not user-friendly, confusing and often caused inaccurate data. 
What’s changed
We’ve removed the ‘First Item’, ‘First Order’, First Product’, ‘Most Recent Order’, ‘Reviews’, and ‘SKUs’ views from the Explore. We have taken the most relevant fields from these views and modelled them directly in the Customer view.
We’ve updated relevant, recently used existing reports
We’ve done this by pointing fields we’ve deleted to the updated fields. This means that existing, saved Looks using the Customer should be updated and working as per usual. Please reach out if this is not the case. 
We recommend changing existing Customer Explore reports
The new Customer Explore makes it easier to report on Acquisition Product Category and Acquisition Date, two very common use cases of the Customers Explore. We recommend using the designated fields for this, rather than recreating this logic using multiple filters as that sets us up for inaccurate, inconsistent data. Please reach out if you have questions around updating existing Looks. 
Answers to FAQs:
Why is {field} missing? 
We have kept the Customer Explore as simple as possible at this stage, only including fields we know are used and relevant based on past Looker usage data. As we increase the complexity of our Customer analysis, we will likely want to add additional fields. We believe we’ve modelled the code in ways that should be this fairly straightforward to do. 
How do I use the Customer Explore
We have created this short Slide deck outlining how to use some of the most common fields / use cases in the Customer Explore. 
Next steps
In making these changes, we have centralised logic in our code, making it more scalable and reducing the chance of inconsistencies. We will now prioritise changing the references in our code such that everything points to single sources of truth. 
Please reach out directly if you have questions, see anything that doesn’t look right or need help transitioning existing reports!


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

**Roadmap follow-up 1**
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

**Roadmap follow-up 2**

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

**Quarterly roadmap revision 1**
Hey Neil and Nikita, 

Can you confirm this looks good on your end?
 
I updated our BI Q4 roadmap to reflect our conversation last week.  
 
I deprioritised App and Product Performance reporting due to strategic priorities, kept the user journey reporting, and added Bytedance and Web KPI reporting.  
 
SEO and on-site search reporting are Q1 2021 top priorities.
 
Cheers!
Will

**Quarterly roadmap revision 2**
Fwd: BI / Finance Quarterly Review
Hi Tony, 

Since you're on holiday, I thought it was easier to send your quarterly review by email.  I'm happy to catch up in person on this if you want to discuss anything in more detail.
 
BI was able to complete everything we had on the Finance roadmap for Q3, including the Checkout.com reporting ahead of schedule.  
 
For Q4, the additional priorities from team Finance are Papier KPIs, Kickoff Inventory and Finance ERP (this will carry into 2021), finalise Emma's tax metrics, and help Alice transition trading over to the Exec explore.
 
For Q1 2021, we'll work on incorporating freight and import duty.  
 
Let me know how this looks and if there's anything I missed,
Will

**Quarterly roadmap revision 3**
Hey Gaby, 
 
We’re doing our Q2 review and I just wanted to confirm Commercial’s priorities. We have both Upsell reporting and support of the tagging process on our list. Can you confirm if these are still priority projects to kick off in Q2 (with Upsell presumably being a higher priority of the two?) In addition, we’re still planning on having the BI Exec to work on Digital Foil Reporting when they join.
 
Thanks, 

Dave 

**Quarterly roadmap revision 4**
Hi Tony, 
 
I wanted to send the quarterly review by email to update on Finance's Q1 projects and clarify priorities for Q2. I'm happy to catch up in person on this if you want to discuss anything in more detail.
 
In Q1, we finalized work on Digital Services Tax and Budget metrics in the Executive Explore. The LTV model V1 is currently in progress and was expected to roll into Q2. 
 
For Q2, the priorities on my list are GM logic revision and royalties calculation - can you confirm these are still priorities for Q2? 
In addition, we're planning on having the BI Executive take on Stripe reporting improvements (Q1 planned), standardization of Looker to match business logic, and depreciating Checkout.com. We can reprioritize the Invoice review support project in H2 (Q1 planned but more of a nice-to-have). 
 
Let me know if you agree and if there's anything I missed? 
 
Thanks, 
 
Dave 

Hi Tony,

I wanted to provide an update on our roadmap progress, outlined in the 'BI Internal Tracker' tab of the attached BI Roadmap Tracker. We project to complete ≈60% of our prioritised Q2 projects this quarter. These are split between high-priority projects currently in progress (light blue), and high-priority projects not started but expected to be completed this quarter (darker blue).

Can you let me know if you agree with the prioritised projects planned? Once we're on the same page, I will update the relevant stakeholders. 
We intend on doing our H2 planning in the beginning of July per usual. The aim is to be conservative in what we’re signing up for as:
A large chunk of time will be dedicated to getting Eve up to speed
We’ll still have Q2 projects to complete
We need to have the flexibility to support new joiners’ onboarding and their data requests. From initial conversations, we expect requests from Leslie’s team, Product, and Retention / Insights
Not being able to keep up with demand of the business and missing the roadmap isn't sustainable and it isn't the quality we strive for in BI. In addition to new hires joining this year, Will is doing a post mortem on the first half of the year to see if there are any lessons and signals we can use to better plan for the future. 

Let me know if you have any questions, or if it helps to run through this in person.

Thanks,

Dave 



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


**Quarterly roadmap revision to Tony**
Hi Tony, 
 
We've revisited the BI roadmap for Q2. Key points: 
Re-assigned projects in the 'BI Internal Tracker' - projects assigned to Dave are the highest priority and projects assigned to BI Executive will be great wins when they join - these are all less high priority for the business.
We have lots on in Q2. We believe what's planned for is achievable as the larger projects (Upsell, Royalties, GM) will roll into H2, and the other projects are scoped to be quicker wins. Anything we don't finish will be re-assessed and rolled over to H2 pending on speed and hiring. 
Let me know if you have any questions, feedback, or if it helps to run through this in person before circulating more widely. 
 
Thanks, 

Dave 

**Quarterly update to the business**
Hi all, 
 
I wanted to circulate our revised BI 2021 roadmap. This is updated to align with changing business priorities/initiatives and it's restructured to accommodate the lack of BI resources in Q2. 
 
We believe that projects allocated to Dave in the BI Internal Tracker are the highest priority; the new BI Executive has accepted the role (start date TBC) so we hope to pick up on those projects soon. 
 
Feel free to distribute this more wildly to anyone that may be interested.

Dave 

Hi all, 
 
I wanted to provide an update on our Q2 roadmap. We project to complete ≈60% of our prioritized Q2 projects this quarter. These are split between high-priority projects currently in progress (light blue), and high-priority projects not started but expected to be completed this quarter (darker blue).
 
Not being able to keep up with the demand of the business and missing the roadmap isn't the quality we strive for in BI. Realistically, we'll be constrained on resources for a while longer as Eve will join us at the end of July as a BI Executive and will need time to ramp up. 
 
In the meantime, we will continue to work on the highest impact projects only. We will do our H2 planning at the beginning of July, where we will plan projects for the rest of the year and reprioritize unfinished Q1/Q2 projects. 
 
Please let me know if any of our priorities should be switched around or if there are any questions. 
 
Thanks, 

Dave 




**Prioritization question Slack**
Hey Tony. We’re planning Q2 and the two big projects for Finance are Royalties calculation and the GM logic revision. Given how cross-functional these are (especially with Tech) it probably makes most sense to start with one of these. In your mind, which is higher priority and when would be good to kick that off?


## Announcement messages
**Modeling issue in Looker**
Hi all,

The inaccurate Conversant Spend was caused by a data modeling fault in Looker. I will push the code fixes live EOD today to avoid Looker disruption. More context below.

What happened
A code change was made in March that reintroduced legacy Conversant code to Looker. This resulted in all Conversant metrics duplicating (including all historic Conversant data).
The code change was introduced as part of a complex project involving many dependencies - it’s hard to replicate exactly what happened, but it’s a reminder that our current code review process isn’t watertight and needs improving.

How will we avoid similar issues going forward?
dbt data quality checks will allow us to spot issues like these before making changes to the code. This is still a WIP but remains a high priority.
Improving our processes around managing and reviewing complex code changes. I’ll pick up the specifics around this with Will once he’s back.
Apologies for the inconvenience this has caused - I’m aware this had had a large impact and a lot of time went into the investigation. 

Let me know if there are any questions/concerns,

Dave



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

**Lookerfetch update**
Update on importing data from Looker into Google Sheets 
*What happened?*
Since last week, the Lookerfetch function has stopped working because of technical difficulties. Because the issue is with custom functions in Google Sheets, Looker is unable to provide support on this.  
*What’s the solution?*
Looker has built the Google Sheets Looker Action through which we can send or schedule data from Looks into Google Sheets. A benefit of this method is that we can monitor these Actions within Looker and we get full Looker support should anything go wrong.
*How do we use this?*
We set up this doc with instructions on Looker Actions and a suggested approach on how to migrate existing reporting from custom functions to Looker Actions. Alice has started doing the migration for Trading materials and so far it’s working as expected. 
There will be some initial set-up effort but this solution will be more reliable and scalable than other alternatives. Do let me or Alice if there are any questions / concerns. @Rupert @Alice Morris @Gaby @anthony


**Mistakes our end**
Hi all,

The inaccurate Conversant Spend was caused by a data modeling fault in Looker. I will push the code fixes live EOD today to avoid Looker disruption. More context below.

What happened
A code change was made in March that reintroduced legacy Conversant code to Looker. This resulted in all Conversant metrics duplicating (including all historic Conversant data).
The code change was introduced as part of a complex project involving many dependencies - it’s hard to replicate exactly what happened, but it’s a reminder that our current code review process isn’t watertight and needs improving.

How will we avoid similar issues going forward?
dbt data quality checks will allow us to spot issues like these before making changes to the code. This is still a WIP but remains a high priority.
Improving our processes around managing and reviewing complex code changes. I’ll pick up the specifics around this with Will once he’s back.
Apologies for the inconvenience this has caused - I’m aware this had had a large impact and a lot of time went into the investigation. 

Let me know if there are any questions/concerns,

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
 
Approach
We allocate orders with the 'Search Engine' or 'Social Media' checkout survey group as their source **based on the ratio of organic vs paid converted sessions by day**. As an example, say that 20% of all converted sessions on 01/09/2020 came from an organic search medium. Then we allocate 20% of orders with the 'Search Engine' checkout survey group to the 'Organic Search' medium and 80% of the orders to the 'Paid Search Non-Brand' medium. We used the same approach to allocate between the mediums 'Organic Social Brand' and 'Organic Social Other'.
 
Impact summary
Allocating Checkout Survey answers between Organic and Paid reduces paid acquisitions by 3%
Organic Social is now the 6th largest channel; 75% driven by the “Organic Social Other” medium
Paid Social Prospecting and Paid Search Non-Brand are the largest mediums negatively impacted by the changes
More details around both approach and impact can be found in these Slides.
 
Please let me know if there are any questions or concerns before we push this live. Because of the slightly technical approach and the impact, I am more than happy to clarify any questions or concerns in more detail during a call. 
 
Thanks, 

Dave 

**Changes to Executive Explore sign-off over Slack 1**
Hey Tony - re the May campaign. We recommend keeping the Executive Explore as is. Manually excluding the Spend probably defeats the purpose of the Exec Explore being a source of truth for all Spend and adding a filter for Brand Spend would be a complex exercise with our current Exec Explore logic. 
Impact on Trading 
The Brand related Spend will be categorised in the ‘Other’ category 1. Because the campaigns target Stationery & Accessories products, we expect to see a drop in CPA for Stationery & Accessories Category 1 (as the Spend isn’t categorised into Stationery & Accessories Category 1). 
The Campaign Performance explore can be used for more context around the Brand Spend - PM will be able to pull this data by filtering on ‘Brand’ Campaign Category 2. 
Let me know if you agree with this approach and I’ll share it more widely in an email.

**Changes to Executive Explore sign-off over Slack 2**
Hey both, 
Tony confirmed that we want to exclude the Brand campaign Spend from the Executive Explore. I think a good way of doing this is by creating a new Campaign Group 2 called ‘Brand Awareness’ (open to other suggestions)
Currently, these campaigns would be categorised into ‘Brand’ campaign group 2. The issue with ‘Brand’ campaign group 2 is that this also includes e.g. Google spend on brand related keywords. By creating the new Campaign Group 2, we can easily filter out the relevant campaigns from the Executive Explore whilst still having the ability to report on them individually in e.g. Campaign Performance. 
I double checked with Bhav and confirmed that the below naming conventions capture all relevant Brand campaigns - including those we ran in 2019 (which we’ll also exclude from the Executive Explore):
YouTube -campaign name contains “Brand Video” 
Facebook - campaign name contains “[SOCI[BRAND”
Let me know if you think this is a sensible approach and if you any questions/concerns around it? 

**Dynamic Ads changes approval**

Hi all, 
 
I've been working on changing how Spend (and Clicks) is categorized in the Executive Explore. This change will increase Spend by category and negatively impact blended metrics, such as CPA, in the Executive Explore. Even though I believe this is expected, I want to check if there any implications/concerns around this. See below for more details. 
 
Change in the logic 
In the current Executive Explore, all campaigns are categorized into Category 1's based on their Campaign Name. However, this doesn't accurately represent how Facebook metrics should be categorized. The updated Executive Explore will follow the logic:  
Non-Facebook channels are categorized into Category 1's based on their Campaign Name 
For Facebook: 
If a Facebook ad is 'Dynamic', then Category 1 equals the Product Category 1
If a Facebook ad isn't 'Dynamic' then the ad is categorized into Category 1's based on the Ad Name 
This logic is similar to PM's In Week reporting; I worked with Bhav and Grace to compare the data and In Week matches the Executive Explore. 
 
Impact 
In February 2021, 'Other' Spend decreased by 67% because of this Spend now moving into categories. This has a knock-on effect on blended metrics such as CPA - see the table below for the CPA impact between new and old Executive Explore. Note that global metrics (i.e. not split by Categories) remain flat. 
 
Let me know if there are any concerns and/or questions around this. 
 
Thanks, 

Dave



**Repeat definitions**




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

## Solving hard data quality questions 
**Notion ticket example**
Hey @Bhavisha Dadhania . I had a look into this - only 5 sessions have the medium 'Paid social prospecting’. These sessions all have an Email campaign referrer AND Facebook UTM parameters. I've seen this behaviour before where sessions start on a nested page (e.g. page = 2 in the URL) with a non-Facebook referrer but with FB or IG UTM parameters (similar to this issue). Do you know what behaviour can result in this structure? 

This Look shows the details of the 5 sessions. With our current attribution logic, these sessions are attributed to Email (following the “utm_medium=email” string in the referrer) rather than Paid Social which is causing the different medium names.

Hey @Bhavisha Dadhania I can see in the URL that you provided: "fbid=6249588409551&page=2&sort=favourite&utm_campaign=%5BUS%5BSOCI%5BSTN_ORG%5BPROS_STANDARD%5BPURCHASE%" So the URL does contain page=2. I don't know why this page 2 would contain UTM parameters though - does it have to do with the campaign that is being run: [US[SOCI[STN_ORG[PROS_STANDARD[PURCHASE]: PAPIER (this campaign applies to all 5 of these session)? 

Hey @Bhavisha Dadhania. I had another look into this to see if it’s a wider problem in our web tracking with implications on attribution. Findings below: - < 0.01% of our sessions start with a nested URL so it’s not something that happens very often. - Of the 26K sessions that do start on a nested URL, 40% have paid social prospecting mediums (main campaigns showing this behavior are: “[UK[SOCI[STN_ORG[PROS_STANDARD[PURCHASE]: PAPIER”, “[US[SOCI[STN_ORG[PROS_STANDARD[PURCHASE]: PAPIER”, “[US[SOCI[STN_STN[PROS_STANDARD[PURCHASE]”) - see this Look with all campaigns showing the behaviour - I pulled the data of these sessions and this behavior started in December 2019, so it’s not something that started only recently - I also confirmed that this structure is what we directly get from our source web tracking data - it’s not something that changes because of how we model the data in the backend. I’m honestly not sure what behavior is causing this but it doesn’t seem to be an issue with how we model the data. Here are a few journeys of users who get Facebook parameters in nested pages (querying our web data so these are a bit slow): - Google > FB (nested) - No referrer > FB (nested) - Email > FB (nested) Do you have more context as to why this might happen based on the above? Perhaps this is a result of how users interact with these specific campaigns? 

Hey @Bhavisha Dadhania Yeah this behaviour is very confusing. The next step would be to involve Joe / Tech to look into why this might happen with their understanding of our web tracking. I think it's important to keep an eye on this and make sure it doesn't become a bigger issue than it is but I don't think the impact is large enough to escalate to Tech at this stage. Let me know if you disagree though!

## Escalation emails
Hi Brian and George,

Sorry to reach out directly, but I need to escalate the urgency of this issue.

The broken Stripe fee reporting is causing mismanagement of our business.  We are over-reporting our profit per order, senior leadership does not have the right data, and as a result, we are not hitting our financial goals.

This has been broken since February.  The "expected" change in reporting was not articulated as part of the contract negotiation and not known to us.  Because of this, our CFO is very frustrated with the result.  I don't believe this issue is being met with the urgency we need.

Can you please escalate this ticket internally?  And help coordinate a faster resolution?  I recommend we set up a call with technical support on Stripe and our side to solve this more quickly.

Cheers,
Will

## Tech tickets
**Example 1**
Overview
Now that we show customer's the expected delivery date, it would be great to add this to the reporting. This, in addition to the delivery tracking work in H2, will help us build new Customer SLAs and help improve the customer experience

Problem
Currently, we show customer's when we expect their order to be delivered. However, we don't record this in the database. We'll want to know this data point to report on.
I would think this would fit nicely on fulfilment_shipments. And it will be great to start recording this data now since we have it.

Impact
Improving our operations has a positive impact on Customer NPS. One of our 9 core goals this year is to raise NPS, and having better data and tracking on this will help improve our reporting on printers.
SLA is typically measured by the customer's experience, i.e. did we get their package to them on time (not just leaving the printers). Knowing when the customer can expect the package is half of this meric.

**Example 2**
Overview
Tech is changing the way Sellables are created to make it better for everyone. This will result in a new field identifying the state a product is in. We'd love to add this field to Looker reporting.

Problem
Tech are adding an important field for products, we want to make that available to Papier through Looker.
The recommendation is to add the column publishable_state to the Products ETL for all sellables that have this field (books, products, stock items, photobooks, etc.)

Impact
This will help Merchandising and Commerical ensure products are live on site the way they should be. Having the products correctly on site increases sales and conversion rate

**Example 3**
Overview
In Admin, Product Visibility includes the ‘Merchandised’ option. This is currently not part of the ETL and we’d love to have this field in our Looker reporting.
Problem
We want a way to report on products that are actually showing up on the front-end of the website. By adding the ’primary_variant’ field to the Products ETL, we can add this back as a dimension in Looker and enable this reporting functionality.
Impact
Growing our category revenues continues to be a big focus in 2021. Accurate reporting on merchandised products allows the Trading team to optimise for this growth.

## Onboarding 
**Slack superhero**
Quick question: I see that Dafne is joining on Monday - do you think she’ll want/need a Looker account? If so, we can create her an account and send her all the relevant intro material in advance

**Onboarding and access email**
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

**Sharing onboarding recommendations**
Hi all, 
 
Below is the summary of the Looker onboarding review we've done in Q2. This is especially relevant to recent new joiners as well (soon to be) managers whose teams use Looker. 
 
Objective: Papier is growing fast and we want to ensure that new joiners can self-serve their analytics needs within Looker quickly and easily. 
 
Approach: We have spoken to recent new joiners as well as 'Looker Superheroes' to understand current onboarding processes and challenges, resulting in the recommendations below.
 
Recommended onboarding process
Looker Docs 
The Looker Docs continue to be the best place to start to learn about Looker - we've added new and improved existing docs to better accommodate common challenges faced by new joiners. Our new Start here - Looker onboarding doc is a comprehensive overview of all our Looker onboarding docs.
 
Looker Superhero support
Functional knowledge and expertise remain key to getting new joiners up to speed. We recommend Superheroes to: 
Provide an intro to existing KPIs, reports, dashboards, and relevant Explores in Looker
Act as the first line of support for any questions and data validation
BI intro call 
We recommend new joiners set up a 30 minutes call with the BI team to get a higher-level intro to BI at Papier, ways of working, and to discuss any questions.
 
Future planned onboarding improvements
The recommendation above is essentially how we've been onboarding users for a while and we know that it comes with challenges, including 1) it doesn't account for different learning styles, 2) it's not easy for new joiners to see which reports are available already, 3) it's difficult to transition from the docs to insights, 4) there isn't much support to transition into Looker experts. Below are the main initiatives planned to accommodate these challenges; we will adapt our priorities and approach as we learn about what works and what doesn't.  
Data Office Hours (Q3): 15-30 minute slots with the BI team to provide training, scope a data use case, or validate a report
Centralized Looker KPI dashboards (Q3/Q4): dashboards with key reports by team which are validated and maintained by BI
Looker FAQ (TBD): a central space with well-documented answers to frequent questions
BI newsletter (TBD)
Looker training videos (TBD)
For a more comprehensive overview of our onboarding review and next steps, please refer to Looker onboarding doc. 
 
Please reach out directly if you have any questions, would like more info, or need help with Looker/data in general. 
 
Thanks, 
 
Dave


## Other
**Clarifying team priorities**
Hi all,

Happy friday! Just a reminder that next week the Tech and Product teams will be doing a 'Space to Create' week. The goal is to use some time outside our normal sprint cycle to work on more experimental ideas, with everyone in the team being given complete freedom to work on any project which they think will benefit Papier.
 
We're all really excited to see what we can come up with, the goal is to end up with something that we can ship to customers, whether as an A/B test, new internal functionality, or improvements to existing flows.
 
This will have an impact on other tech/product work during the week, and we won't be working on normal tickets during that time.
 
If you have an urgent request during the week, please let me know directly on Slack and we'll make sure to look at it. For any other requests, please continue to use the Tech Ticket Inbox in Notion as usual.
 
The next two week sprint will start on 19th April, and we'll pick the tickets for that sprint on the Monday morning.
 
If you have any questions, please do let me know!
 
Thanks
 
J

**Executive data quality updates**
Hi both, 
 
Thanks for flagging this. I can see that this is caused by MentionMe campaigns that went live in the last 3 days and that we haven't yet modelled in Looker. I'll follow up with Mathilde and update in Lookerpaps when the fix is live. 
Also FYI - we are going to implement more rigorous data quality tests this quarter that should help us proactively spot issues like these. 
 
Dave

**Understand which analysis is currently available**
Notion flow example

I dug into this and the summary of my findings are below. Let me know if this is helpful, and if you'd want to meet to discuss next steps in more detail. . Currently, we do not have data in Looker (available to users) for Onsite Search. . We do capture data about onsite search. The granularity of this data is the term people search on site. If someone searches many terms, we would record each term once per search. We know what term they searched for, who they are (as best as possible, anonymous vs. signed into an account), what page they were on when searching, what page and events they triggered after searching (more difficult to report dynamically though), and the device and browser they were on. . It would be relatively standard for us to stand this up as it's own explore and connect it to our other web data (Device, Browser, Page, User, and Session information). You could get KPI metrics like conversion rate of search terms. It would be much harder for us to develop Onsite Search specific metrics (like, what % of people bounce after searching vs. clicked on something they wanted to find). Or what was a dynamic user journey of customers after they searched for "cat notebook". . What would also help us is to know what you would want to know. What KPIs from onsite search do you care about? Do you have examples of reports you have looked at in the past that have been helpful?

Hi Will - thanks for looking into this. I was thinking the below to start with: Filters: mobile, customer type, market Overview - % Sessions used internal search - Sessions with Search - Total Unique Search - % Search Exits - Time after Search - Search Depth - % Refinement - Total revenue driven by search - Traffic channel segments (to see % of total search driven by each channels) Search terms Search terms details (currently available I believe)

Hey @Leslie Delaplagne Sorry for the delay on this. A lot of these are already possible in Looker using event description 'Searched Products' and the dimension 'Searched Term'. Metrics possible See below the requested metrics and the corresponding measure names and the Look it's referred in (linked below) - Search term - Events Searched Term (Look 1) - % Sessions used internal search - Sessions Searched Rate (Look 2) - Sessions with Search - Sessions Total Searched Sessions (Look 2) - Traffic channel segments - Look 3 - Total Unique Search: Look 4 Look 1 Look 2 Look 3 Look 4 Workarounds / not sure - % Search Exits: we do collect Exit Rates on a page level. However, the Exit rates after Search are captured on the Search Page Type - see this Look. I'm not sure if that helps at all? - Time after Search: we don't currently have this. A very hacky way of doing this would be to take the Session End Time and subtract the Event Start Time of the event 'Searched Products' as in this Look Planned for later this year - Total revenue driven by search: this is part of a larger project planned where we model event-level data back to order level data, which will help answer questions like these. Not currently possible - Search depth. As I understand this, this would be: how many pages do people visit after having used Search? - % refinement: this would be the % of users who search again immediately after searching? Let me know if this helps to get some initial insights? We can then see which of the other metrics that aren't possible / require workarounds are important to get right and we can plan from there. 


## BI monthly invitation announcements 
**BI monthly calendar invite**
Hi All, 
This is a placeholder for the next BImonthly LOOKin where Alice will be presenting how she uses Looker as an FP&A Manager. 
During this session, you’ll learn about the Executive Explore and how it is used to report on the business’s core KPIs. In addition, you’ll learn how to send/schedule data from Looker and how to import data automatically into Google Sheets using Looker Actions. 
I highly recommend joining if you are interested in learning more about FP&A, Looker, or data at Papier in general.
Feel free to reach out to BI in advance if you have any questions!
Dave


**BI monthly invitation email**
Hi Nikita, 

We are planning towards our next Looker BImontly session in February and wonder whether you would be up for presenting how you use Looker? These are a few use cases that would be great to cover (in addition to anything else you may want to present):

- KPI Reporting dashboard including the period comparisons and the annotations
- Experiments mega boards and how this plays a role in the A/B testing framework/process
- Conversion funnel report 

Let me know if you have any questions around this; if you could let me know soon, that would be ideal as we can start booking in a timeslot. 

Thanks, 

Dave 

**BI monthly calendar description**
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
