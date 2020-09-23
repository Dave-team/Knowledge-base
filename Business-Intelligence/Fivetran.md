# Fivetran

## Pricing 
- Initial syncs are free for any new connector 
- Fivetran new pricing model
    - We pay based on Monthly Active Rows synced. The number of distinct primary keys synced via the Fivetran plan calculated on a per-account basis. We only count rows once per Billing Period, even if they sync multiple times.
    - A row becomes active when a new row is added or an existing row is updated (this is determined by looking at primary keys)
    - An active row can be updated without charge for the rest of the month
    - Initial syncs are free
    - This model is based off credits also that are purchased on a yearly basis 
    - Credits are rolled over to the next year
- No API? Consider SFTP which can be pipelined using Fivetran

## Best practices and tips
- Transformations are handy:
  - Allow not having sensitive data in DWH 
  - We can change the Snowflake mapping using transformations


## Technical
- There is currently no support for running one off pipelining jobs. Instead, we’ll need to setup the 24h incremental load and whenever we don’t need the load to happen, we just pause this 
- Fivetran performs an initial historic load and then the rest is incremental based on change logs
- We can hash columns in Fivetran – e.g. helpful when we need to join on email address but don’t want email address in our dwh 
- We can sometimes select exactly which tables and which fields we’d like to pipeline over
- When we change data in e.g. a Google Sheet and we want to sync again, Fivetran will do an upsert on the data already in Snowflake. To start with a clean state, drop the table in the raw schema first instead. If not, you’ll end up cleaning a previous state of a graph you made  

## Relationship management
When working with a vendor, have regular (e.g. monthly catchups). Make sure to track their performance. If and when something looks odd, you’ll have proof and you can ask for refunds when reasonable 

Fivetran monthly catchup: 
- Any performance issues? 
- How is MAR looking? 
- Any plans with new integrations?
- Anything else from either side? 

## When there is no Fivetran connector
- File replication: get the data into an S3 bucket, SFTP server, some Cloud Drive and pipe using Fivetran 
- Get the data into the warehouse directly 
- Cloud functions using APIs

