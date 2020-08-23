### Stitch
- Free plan based on row counts 
- Incremental tables need to be backfilled with their data and how to do this is depending on the replication method. This is done by resetting the start date of the table 
- Nested structures are not natively supported in Redshift, meaning that they are represented as new tables in Redshift 
- Initial syncs are free for any new connector

### Fivetran
- Initial syncs are free for any new connector 
- Fivetran new pricing model
    - We pay based on Monthly Active Rows synced. The number of distinct primary keys synced via the Fivetran plan calculated on a per-account basis. We only count rows once per Billing Period, even if they sync multiple times.
    - A row becomes active when a new row is added or an existing row is updated (this is determined by looking at primary keys)
    - An active row can be updated without charge for the rest of the month
    - Initial syncs are free
    - This model is based off credits also that are purchased on a yearly basis 
    - Credits are rolled over to the next year
- No API? Consider SFTP which can be pipelined using Fivetran

When working with a vendor, have regular (e.g. monthly catchups). Make sure to track their performance. If and when something looks odd, you’ll have proof and you can ask for refunds when reasonable 

Fivetran monthly catchup: 
- Any performance issues? 
- How is MAR looking? 
- Any plans with new integrations?
- Anything else from either side? 

