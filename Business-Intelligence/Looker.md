# Looker
## Best practices
**Performance optimization** 
- Aim to model with many to one joins: starting with the most granular level tends to have the best performance 
- Use datagroups to cache data in dashboards - make sure that dashboards get refreshed early in the morning so people have fresh data when they come in.
- Limit the number of tiles on a dashboard
- Limit table calculations and pivots as they are quite heavy 
- Limit the number of data points returned 

**Looker modelling**
- The initial table in the explore should contain measures and it should be the most granular table. For any subsequent joined tables we lose trust (unless there's a 1:1 relationship). 
    - Fields can become duplicated is there's a many to one relationship
    - Fanouts happen when there is a one to many relationship as we increase the number of rows within the Looker model. Avoid fanouts by starting with the most granular data table
- Always have a primary key in your view
- Only use {TABLE} once – from there you always want to reference that field. Reason: keeping things DRY 
- Add relevant drill downs in the models 
- Use value format names to ensure data shows up in the right format

**Looker organization / design**
- Each explore should describe seperate process. 
- Make sure to group explores / models that relate together. So Activities, Opportunities and Pipeline History are all under Salesforce 
- Restrict user thinking – create measures with filters
- Limit the number of fields in the field picker: group measures / dimension together when they strongly relate to each other. E.g. use a group label Address and then within that is Town, Country, Post code etc. 
- Add descriptions to fields and explores to clarify what fields mean to end users. 
- Hide non relevant fields 
- Spaces are named after business function: e.g. Marketing 
- Dashboards are named as business function - specific. E.g. Marketing - Channel Overview
- The explore pane should by by business function and then more granular - this is depending on the natural groupings and expectations of the business users  


## Looker Debugging
- Run the generated SQL in Snowflake 
- Use content validator to check whether something is broken
- If something is broken, replace the names. If multiple changes happened, change e.g. first the model and then the view
- To check whether a LookML field is broken, break LookML on purpose:
    - Slightly change the name of the field
    - Run content validator and see what breaks

## Looker uses 
- Embedding 
- Alerts e.g. when customer is about to churn
- Easily share data via Slack 
- Scheduled dashboards
- Boards for teams to create curated dashboards and looks 
- We can add links to different tools from Looker. E.g. each opportunity links to its own opportunities page in Salesforce

## Looker tactics 
- We can use Looker tiering to bin numbers
- Use dimension groups for dates only when having the groups are actually relevant
- We can rename everything: each field and each explore can be renamed 
- People keep booleans in the DWH: TRUE / FALSE. This is converted to yes/No in Looker. Also: You can also easily cast a boolean to an integer and take the average. All of that seems like an acceptable amount of work in order to keep the legibility of true/false as the values
- User attributes to create custom experiences for each Looker user. E.g. a dashboard with automatically set filters depending on user. E.g. each manager sees dashboard with only their team mates. Can also be used to switch between dev and prod connection details. 
- We can change Looker dashboards and pages using HTML. E.g. adding custom HTML / CSS headers in dashboard, adding links to a WIKI on each employee’s Looker homepage 

## Looker common gotchas
-	Remember that Looker is case sensitive – e.g. strings should be single quotes, as per Snowflake SQL 
-	When doing Snowflake calculations, make sure to include the nullif statement to avoid that the calculation breaks 

## Looker checklist 
- Regularly check the content validator. Make it a habit to check the content validator any time you have made significant changes to the LookML. Simple things like name changes can really mess things up
- Look at Looker Labs and Looker Labs to see what else can be done 
- Be constantly up to date with Looker's release notes
- Live in Looker 

## LookML
- LookML is SQL but it adds version control, it’s extensible (i.e. you can enrich with HTML) and modular. Rather than having to rewrite complicated SQL scripts, you define things once for the entire company  
- Liquid is a templating language used to create dynamic content. E.g. to have links to external tools from within Looker. We used it combined with HTML to calculate USD or GBP depending on parameter values. This uses the if, elseif construct and it included the rendered value to show formatted data 
- Parameter: they create a filter-only field users can use to provide input to a liquid parameter tag. It can be used to filter, but it cannot be added to the result set. Often used to create interactive query results, labels, URLs combined with liquid. Other use cases of parameters can include how users would like to aggregate a certain measure: sum, count, average – this is then all included in the liquid of the measure to select the right aggregation. Also to select how users want to show a date without including all options in the field picker    
- HTML parameter: specify HTML contained by a field. Did we use this for the custom tooltip?  
- Constants: an unchanging value provided that can be used throughout the project 
- Sets: list that defines a group of fields that are used together 
Looker drill fields
- Can be set on dimension, measure or view. 
- At the view level, it applies to all measures, unless a measure has unique drill fields applied to it 
- Drill fields can take sets (of fields) or individual fields 
- There are options to have visual drills. There are also options to have include e.g. custom filters, drill into different dashboards, different explores, etc. 
- Important notes:
    - Drill fields can only be applied to fields that are also in the same model. E.g. pipeline history can’t take fields from the opportunities field 
    - We cannot drill into table calculations at the moment - that’s why attended to S1 is not showing up as a drill field. Also SDR ramping performance 

## Glossary 
- LookML: language to describe LookML models in database
- Looker project: Collection of LookML models – highest level hierarchy
- Model: connection to a single database and where explores are defined with their joined views, as well as some model settings. It’s also used to separate access control  
- Explore: starting point for querying data. It is the FROM clause of a query. The other joined views are defined in the model file 
- View: similar to a database table. This is where dimensions, measures and field sets are defined in LookML 
- PDT (Persistent Derived Table) – basically a table transformation that can be scheduled 
- Dimension: columns in a table, or a computed value based on other fields (e.g. case whens, bins, concats). They usually provide context and are used to filter/group. 
- Measure: aggregations like sums, count or calculations defined in LookML. Measures compute values across multiple rows. 

## Looker homepages
- Change settings to recently viewed rather than 2 static folders 
- We can change the landing page per individual Looker user 
- Consider having boards as homepages 
- When users mark a homepage as favourite this will be shown on the homepage. This is probably very critical to get right and it should be part of onboarding 
- We should also consider Looker markdown pages

## Looker access control
High level:
- Content Access: view/manage folders 
- Data access: control what data user is allowed to view. Managed via model sets
- Feature access: control types of actions that a user is allowed to do. Managed via permission sets 

The aim is to set user level access by SAML integration, which means it is managed by Okta. To enable this, we need to think about the organizational hierarchy as people in the same group would get the same access. E,g, there is a difference between Sales Leadership, Division Leaders and other Managers The groups that are created in Looker are coming from SAML and so are the users that belong to each group. Users only belong to a group on when:
- They are set as a Looker User in Octa 
- They are part of a SAML group that is enabled in Octa


In the SAML settings within Looker, we specify the Role that belongs to each Group. A role has a certain permission and model set:
- Permission set: what can the user do in Looker? E.g. create dashboards, schedule Looks, Explore data, view LookML 
- Model set: What models does the user have access to? 

To give users the functionality of seeing dashboards with sensitive data if they are shared one, but not being able to explore the data, we need to create a new role. This role has Xero data as a model set, but the permission in see dashboard, not explore. Then we add this role to a group that also needs to be able to see dashboards with sensitive data. 

In the folder access within Looker, the idea is to:
- Provide everyone with view access on the shared folders
- Give specific access to individual sub folders when there is any data that shouldn’t be visible to everybody within the organization
- At least at the start, Admins should be the one with the Edit and Manage permissions 
- Folder access needs to be managed on a folder by folder basis and by default, they inherit the parent folder’s permission
- Dashboards in personal folders shouldn’t be visible to others 

Final tip: check what others users can and can’t see by sudo’ing them