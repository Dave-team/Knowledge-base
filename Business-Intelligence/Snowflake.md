# Snowflake

## Links
- top 10 cool things I like about Snowflake: https://www.snowflake.com/blog/top-10-cool-things-i-like-about-snowflake/
- 
## Principles
- Separate storage from compute reducing costs. Compute is billed per second that a warehouse is on. Different warehouses have different associated costs 
- Built in optimizers - no tuning required 

## Improvements over other warehouses 
- Great SQL functionality
- Native JSON support, unlike Redshift and Bigquery is not quite as good either 
- Great partners with Fivetran, DBT, Looker
- Exciting new features coming up – e.g. visualizing data directly within Snowflake 
- No bad reviews; people move away from Redshift 
- No performance tuning required, unlike Redshift 



## Best practices
- Snowflake operates with different warehouse sizes (t shirt sizes). Create different warehouses for different purposes. This helps with security settings (i.e. access to data) as well as monitoring spending in the warehouse. In general, every different function should have a different warehouse
    - EL DWH is often on for a long time and should possibly be on a smaller data warehouse. Speed is not very important
    - Analytics should be fast so this should possibly sit in a bigger data warehouse.  
    - In addition to different warehouse sizes, multi-cluster customers (enterprise) could also work with different clusters. This would allow handling concurrency: extra compute when there is a large load on the dwh (e.g. 9 am in the morning). This avoids queuing and the extra compute would automatically cool off when no longer required 
- Make sure to give each user of Snowflake the right access to the different warehouses
    - Fivetran needs create access on RAW only
    - Looker needs grants on ANALYTICS
    - DBT needs access on DBT Dev and Analytics
- Make sure to set the right policies – e.g. only whitelisting certain IP addresses to the warehouse
- Limit the max spend in resource monitors 
- The roles determine what you’re able to do in Snowflake – make sure to perform actions with the right role 
    - Accountadmin to set users and settings – nothing else
    - Security admin only when certain settings require it 
    - Sysadmin in all other cases 
- Set the suspend / resume settings up correctly as you don’t want a warehouse (especially a large one) to be ‘on’ for too long. The minimum amount for a warehouse to be on is 5 minutes. So each time you start a new warehouse, it runs for 5 mins minimum. Also: setting this to the lower amounts of time would result in a loss of caching, whilst the warehouse is still on, it will cache the previous result 
- Different users have different roles depending on their function to manage access control 
- Snowflake has resource monitors that specify the resources used by warehouse – it is possibly to get this data in a Looker dashboard  
- Run a Snowflake POC to get an understanding of usage, speed and associated costs 

## Other
- The Snowflake history section is quite powerful, it shows caching stats, performance stats and it shows the query profile showing how the query is being run. Using history, we can retrieve query results without costs up to 24 hours after the query was run
- Pipeline data into Snowflake
  - Put files into staging and copy (Snowflake’s copy command) from staging into the actual warehouse. This is very much done for batch processing
  - Snowpipe is another option but this focuses primarily on auto ingesting data into the data warehouse
  - We could also pipeline data from SDK 

