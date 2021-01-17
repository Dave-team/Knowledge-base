# Looker

## Links
- Creating Looker Explores Your Users Will Love: https://looker.com/blog/creating-looker-explores-your-users-will-love
- How to teach Looker: https://discourse.looker.com/t/how-to-teach-looker-intro-to-looker-using-the-explore-interface-and-sharing-content/3696
- LookML best practices: https://discourse.looker.com/t/lookml-best-practices/1636
- Considerations when Building Performant Looker Dashboards: https://help.looker.com/hc/en-us/articles/360038233334-Considerations-When-Building-Performant-Looker-Dashboards
- How to design your Looker explores: https://blog.getdbt.com/how-to-design-your-looker-explores/
- LAMS style Guide: https://looker-open-source.github.io/look-at-me-sideways/rules.html#t2

## Best practices
**Performance optimization** 
- Aim to model with many to one joins: starting with the most granular level tends to have the best performance 
- Use datagroups to cache data in dashboards - make sure that dashboards get refreshed early in the morning so people have fresh data when they come in.
- Limit the number of tiles on a dashboard. If needed, there could be an option to link to other dashboards to finish the story
- Limit table calculations and pivots as they are quite heavy. Instead, aim to have filters on the dashboards  
- Limit the number of data points returned. More data point are expensive in memory 
- Use system activity / i__looker to track performance 

**Looker modeling**
- The initial table in the explore should contain measures and it should be the most granular table. For any subsequent joined tables we lose trust (unless there's a 1:1 relationship). 
    - Fields can become duplicated is there's a many to one relationship
    - Fanouts happen when there is a one to many relationship as we increase the number of rows within the Looker model. Avoid fanouts by starting with the most granular data table. Looker solves for these with symmetric aggregates: sum distinct and count distinct on tables avoiding the risk of duplicates if they are entered into the data model. The problem would still be seeing duplicate dimensions if explored seperately  
- Always have a primary key in your view
- Only use {TABLE} once – from there you always want to reference that field. Reason: keeping things DRY 
- Add relevant drill downs in the models 
- Use value format names to ensure data shows up in the right format

**Looker organization / design**
- Each explore should describe a separate process. In terms of development, you can either start bigger and once you understand use cases go smaller, or you start small and go bigger once people ask for it. In general, avoid people feeling overwhelmed. Start small and let people request data as and when they need it
- Make sure to group explores / models that relate together. So Activities, Opportunities and Pipeline History are all under Salesforce 
- Restrict user thinking – create measures with filters
- Limit the number of fields in the field picker: group measures / dimension together when they strongly relate to each other. E.g. use a group label Address and then within that is Town, Country, Post code etc. 
- Add descriptions to fields and explores to clarify what fields mean to end users. 
- Add labels to views and explores to avoid confusion for end users 
- Hide non relevant fields 
- Spaces are named after business function: e.g. Marketing 
- Dashboards are named as business function - specific. E.g. Marketing - Channel Overview
- The explore pane should by by business function and then more granular - this is depending on the natural groupings and expectations of the business users  
- Get fields into Looker and then describe and hide them. You can always unhide later 
- Use big headings in LookML that help scanning the file: ###MEASURES### 
- Dimension and measure group labels to specify order order/product dimensions and revenue/order measures
- Have a logical ordering in LookML:
  - Primary keys 
  - Dimensions - grouped by function
  - Measures - grouped by function/type 
- Dimension / Measure order: 
  - hidden
  - group_label
  - label
  - description
  - type
  - sql

## Looker Debugging
- Run the generated SQL in Snowflake 
- Use content validator to check whether something is broken
- If something is broken, replace the names. If multiple changes happened, change e.g. first the model and then the view
- To check whether a LookML field is broken, break LookML on purpose:
    - Slightly change the name of the field
    - Run content validator and see what breaks

## Looker uses 
- Embedding Looker looks / dashboards into different applications
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
- Use iLooker to track how users use Looker and to delete non relevant content 
- Remember that we can literally name / alias anything: dimension,measure,view,explore and we can so differently between different explores (e.g. a view can be called differently between different explores). Similarly, we can give two views the same name and they will be consolidated in the Looker explore 

## Looker common gotchas
- Remember that Looker is case sensitive – e.g. strings should be single quotes, as per Snowflake SQL. However, case sensitivty can be turned off  
- When doing Snowflake calculations, make sure to include the nullif statement to avoid that the calculation breaks 

## Looker checklist 
- Regularly check the content validator. Make it a habit to check the content validator any time you have made significant changes to the LookML. Simple things like name changes can really mess things up
- Look at Looker Labs and Looker Labs to see what else can be done 
- Be constantly up to date with Looker's release notes
- Live in Looker 

## LookML
- LookML is SQL but it adds version control, it’s extensible (i.e. you can enrich with HTML) and modular. Rather than having to rewrite complicated SQL scripts, you define things once for the entire company  
- Liquid is a templating language used to create dynamic content. E.g. to have links to external tools from within Looker. We used it combined with HTML to calculate USD or GBP depending on parameter values. This uses the if, elseif construct and it included the rendered value to show formatted data 
- Parameter: they create a filter-only field users can use to provide input to a liquid parameter tag. It can be used to filter, but it cannot be added to the result set. Often used to create interactive query results, labels, URLs combined with liquid. Other use cases of parameters can include how users would like to aggregate a certain measure: sum, count, average – this is then all included in the liquid of the measure to select the right aggregation. Also to select how users want to show a date without including all options in the field picker. Parameters can be used to as filters that can make measures dynamic. E.g. we use a parameter to select how we want to show our amount metrics. We then a liquid variable with the parameter in a measure to actually make it dynamic. We also use some HTML to change how we visualize the rendered values     
- HTML parameter: specify HTML contained by a field. Did we use this for the custom tooltip?  
- Constants: an unchanging value provided that can be used throughout the project - e.g. a hardcoded currency that you don't need to repeat
- Sets: list that defines a group of fields that are used together 
- Looker drill fields
  - Can be set on dimension, measure or view. 
  - At the view level, it applies to all measures, unless a measure has unique drill fields applied to it 
  - Drill fields can take sets (of fields) or individual fields 
  - There are options to have visual drills. There are also options to have include e.g. custom filters, drill into different dashboards, different explores, etc. 
  - Important notes:
      - Drill fields can only be applied to fields that are also in the same model. E.g. pipeline history can’t take fields from the opportunities field 
      - We cannot drill into table calculations at the moment - that’s why attended to S1 is not showing up as a drill field. Also SDR ramping performance 
- View labels can be the same as different views to ensure they are listed under one view header 
- Images are brought in via a URL combined with some HTML 
- A good rule of thumb could be to only persist tables when they are referenced by other views or when they require the performance of a materialized table 

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

## Looker and Github 
Looker has local branches. Deleting remote still shows up in local Looker. Anyone who interacted with the branch (i.e. checkout by switching to the branch in Looker) will also have the branch locally.  
To delete local, developers need to clean up their own branches in Looker. 

    By default, we work on our own dev branch in Looker. This personal dev branch is read only to all other Looker users. 
Because dev branch is read only, we’d want to collaborate on different branches that are newly created for each project and based off master. This means that other Looker users can switch to the branch and review changes as well (e.g. compare your newly created branch against prod) 

## Looker onboarding
- Welcome
- Looker is out BI tool
- X is your superuser who will support you throughout your journey and can answer any questions 
- We have a Slack ‘Lookerpaps’
- There are 3 relevant intro docs to using Looker: Looker intro, Looker worksheet and worksheet answers

Looker training: 
- Kickoff: intro of me, and overview of what we’re going to do and get an understanding of how users want to use the data  
- Introduction: what is Looker and how is it helpful? 
- Looker demo: tour of what we have built so far in Looker  
- Essentials of Looker - dimension, measures, filters, pivots 
- Practical exercises for users to try. One can be guided by me and then they try themselves. Make sure they save it in own dashboard
- Explanations of different Looker use cases and how this relates to what the users wanted to get out of the session  
- Table calculations, scheduling
- Building dashboards 

## Looker tips
Option + click a field and it takes you the place in LookML 
Command - J to navigate to files 
Command + click and then drag to have multiple cursors at once
Fold LookML by adding the code between curly brackets

## Open source tools
- Lookmlint: catch style issues, unused views, semicolons in derived table SQL, raw SQL references in joins, and more.
- LAMS (Look at Me Sideways): official LookML styler and linter
- Finding unused content: Henry
- Find/prevent broken LookML <> dwh references: Spectacles 
- WW tech: https://github.com/ww-tech/lookml-tools

## Other
- Self service is supported - people should build their own things 
- However, make sure there still are SSOT dashbaords that are maintained by the data team and heavily socialized. Also consider putting these on Looker's homepage 

## Looker technical
- Looker: create a calculated field that only applies to a single field: pivot_where(${opportunities.pipeline_attribution}="Marketing", ${plan_sal.total_SALs}*1.0). We can then show that calculation as a line in an otherwise stacked column chart.  Similarly: pivot_where(${opportunities.opportunity_funnel_stage} = "SAO", ${opportunities.number_of_opportunities}) / ${opportunities.number_of_opportunities:row_total}
- We can turn off ‘plot null values’ to only show relevant data 
- Looker filters: show dates until today needs to be done using two filters 
- Hide null values from a Look viz but not plotting null values. Note that for now, this is only available for line graphs
- Looker value format in graphs that show GBP: [$£-en-GB]#,##0
- Moving average: mean(offset_list(pivot_where(${opportunities.opportunity_funnel_stage} = "SAO",${opportunities.number_of_opportunities}), -2,3))
- When LookML errors occur but we still want to commit: Shift click on the arrow next to validate again - here we can actually commit the code 
- We can create usage and metadata reports with i__looker: https://tessian.eu.looker.com/explore/i__looker/history?qid=qrQxWuqEwUSOG7DqJW33iu
- Grant Looker access to Redshift table: 
  - GRANT USAGE ON SCHEMA facebook TO looker;
  - GRANT SELECT ON ALL TABLES IN SCHEMA facebook TO looker;



**Parameters and liquid for displaying currencies:**

```
  parameter: select_region {
    description: "Advanced use only - used to seperate USD and GBP conversions"
    type: unquoted
    default_value: "none"
    allowed_value: {
      value: "all"
      label: "All"
    }
    allowed_value: {
      value: "namer"
      label: "NAMER"
    }
    allowed_value: {
      value: "emea"
      label: "EMAE"
    }
  }

  dimension: amount_usd_only {
    hidden: yes
    type: number
    sql: CASE WHEN ${currency} = 'USD' THEN ${amount_salesforce} ELSE 0 END ;;
    value_format_name: usd
  }

  dimension: amount_gbp_only {
    hidden: yes
    type: number
    sql: CASE WHEN ${currency} = 'GBP' THEN ${amount_salesforce} ELSE 0 END ;;
    value_format_name: gbp
  }

  dimension: amount_gbp_converted {
    hidden: yes
    type: number
    sql: CASE WHEN ${currency} = 'USD' THEN ${amount_salesforce} / 1.25  ELSE ${amount_salesforce} END ;;
    value_format_name: gbp
  }

  measure: total_amount_dynamic {
    description: "Advanced use only - used to seperate USD and GBP conversions"
    type: sum
    value_format_name: decimal_0
    sql:
    {% if select_region._parameter_value == 'namer' %} ${amount_usd_only}
    {% elsif select_region._parameter_value == 'emea' %} ${amount_gbp_only}
    {% else %} ${amount_gbp_converted}
    {% endif %}
    ;;
    html:
      {% if select_region._parameter_value == 'namer' %}
            ${{ rendered_value }}
          {% else %}
            £{{ rendered_value }}
          {% endif %}
      ;;
  }
  ```


**Extensive calculation in Looker.**
```
 index(${historic_sales_forecast.value}, max(offset_list(if(is_null(${historic_sales_forecast.value}), null, row()), -1 * row() + 1, row())))
```

- Get the row number for each non-null row using the row() function
- Use offset_list to get a list of all of those row numbers from the first row to the current row
- Take the max of that list of values, which will be the row number of the last non-null row
- Use the index function to get the value of the field for that row number

**Links in Looker**
```
dimension: merchant_name {
    group_label: "Monzo Transactions"
    label: "Merchant Name"
    type: string
    sql: ${TABLE}.merchant_name ;;
    link: {label:"Merchant Website"
           url:"https://{{ fluentd_monzo.merchant_metadata_website._value }}"
           icon_url: "https://www.google.com/s2/favicons?domain=google.com"
          }
    link: {label:"Merchant Twitter Profile"
           url:"https://twitter.com/{{ fluentd_monzo.merchant_metadata_twitter_id._value }}"
           icon_url: "
https://www.google.com/s2/favicons?domain=twitter.com"
      }


link: {label:"View in Google Maps"
       url: "https://www.google.com/maps/search/?api=1&query={{ fluentd_monzo.merchant_address_latitude._value }},{{ fluentd_monzo.merchant_address_longitude._value }}&query_place_id={{ fluentd_monzo.merchant_metadata_google_places_id._value }}"
       icon_url: "https://www.google.com/s2/favicons?domain=maps.google.com"}
link: {label:"View in Foursquare"
       url: "{{ fluentd_monzo.merchant_metadata_foursquare_website._value }}"
       icon_url: "https://www.google.com/s2/favicons?domain=foursquare.com"
    }

dimension: opportunity_name {
    type: string
    sql: $.dealname ;;
    link: {
      label: "View Deal in Hubspot"
      url: "https://app.hubspot.com/contacts/4402794/deal/{  }/"
      icon_url: "http://app.hubspot.com/favicon.ico"
    }
}
```
