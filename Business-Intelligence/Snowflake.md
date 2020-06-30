# Snowflake
## Best practices
- Snowflake operates with different warehouse sizes (t shirt sizes). Create different warehouses for different purposes. This helps with security settings (i.e. access to data) as well as monitoring spending in the warehouse. In general, every different function should have a different warehouse
    - EL DWH is often on for a long time and should possibly be on a smaller data warehouse. Speed is not very important
    - Analytics should be fast so this should possibly sit in a bigger data warehouse.  
- Make sure to give each user of Snowflake the right access
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
-	Snowflake has resource monitors that specify the resources used by warehouse – it is possibly to get this data in a Looker dashboard  
