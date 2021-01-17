## Tools to explore
- Great Expectations: unit testing for data 
- Looker open source tools (https://github.com/ww-tech/lookml-tools)
  - Look At Me Sideways: Looker linter
  - Henry
  - Spectacles
  - Lookmlint: catch style issues, unused views, semicolons in derived table SQL, raw SQL references in joins, and more.
- DBT:
  - Audit helper: https://github.com/fishtown-analytics/dbt-audit-helper
- Prefect
- Dagster
- Datafold
- Datagrip
- Redash
- Metabase
- Singer
- Superset
- Papermill
- Fuzzymatcher
- Cookiecutter
- Snowflake tools:
  - Snowalert
  - Snowflake Inspector
  - Permifrost
- Data visualization: Dash, plotly, bokeh

### Stitch
- Free plan based on row counts 
- Incremental tables need to be backfilled with their data and how to do this is depending on the replication method. This is done by resetting the start date of the table 
- Nested structures are not natively supported in Redshift, meaning that they are represented as new tables in Redshift 
- Initial syncs are free for any new connector

## Visualization tools
- Early stages: 
  - Custom scripts (HTML / PDF)
  - Metabase as open source
- BI tools 
  - Looker for democratizing data - not great for exploration and quick analysis nor funnel analysis 
  - Tableau has good visualization but terrible management and learning curve 
  - Mode is SQL based 
- Product teams 
  - Amplitude – good for funnels and for easy cohorts plotting
- Custom
  - Interactive python using plotly / dash / bokeh 

## Other tools
- Snowpipe is used for streaming data from S3 into Snowflake based on S3 notifications / triggers (e.g. when data is loaded in S3 > load into Snowflake) 

## Tool security 
- Single Sign On (SAML)
- No passwords out in the open (e.g. nothing in Github)
- Only access to certain IP addresses (IP whitelisting)
- Location of data – e.g. US vs EU
- Discoverability of e.g. S3 bucket 
- SSH 
- Only access over VPN 
- Make sure to test the security settings - shouldn’t be able to access tools / data from outside the office and not on VPN
- Get an external security consultant to review the tool stack as well 
- When working with the cloud, put everything behind the company’s firewall that most likely already exists in the cloud provider 
- Access control together with the IT department so it’s scalable: e.g. should automatically update when people leave the business and/or when they change role internally 
- Try to avoid storing any sensitive data. If it’s required, get sign off from legal 
- Think about back-ups and disaster recoveries 
- Run the tool settings by the security consultants 

## Event tracking 
- Google Tag Manager: ok for just Google but need something else for other tools 
- Segment: great way to have the same tags to prod, GA, mixpanel and all it’s integrations 
- Snowplow: for high volume and real time – this is more intense to set up compared to Segment

**Why use Segment / Snowplow **
- Tools like GA and Mixpanel are limited to their front end reporting. Put the data in warehouse and you decide what to report on + you can join data to all other data available. 
- Data cleaning Especially when things change over time, data transformations can ensure the data is still accurate, whereas the front end tools will have a hard time stitching the data together. 
- Joining datasets. In the front end tools you miss the rest of your data. E.g. you don’t track spent in GA / Mixpanel 
- Analytical limitations: having no limit on the views and filters that can be sit by the tools and instead working on the numbers using SQL is a game changer
- Mixpanel and GA require separate tracking on the website and then that’s it. With Segment, you can send the same data to Mixpanel, GA and all other connectors, including a data warehouse. This makes sure that no questions arise to what data is accurate, the data can be used in many different places - e.g. an event leading to an action in a different tool, and there is complete freedom to create your own measures from events (e.g. by loading data into a warehouse and compute new metrics not available in GA / Mixpanel 

**How to set up this tracking**
This is done using JavaScript tags. A tag is simply a snippet of code that sends information to a third party. Once an event occurs, GTM fires a tag and we can then track this is GA. Every event you want to track includes:
- eventCategory – what is the purpose of measuring this event? To see the path towards new registrations? To measure how many leads we drove? eCommerce sales? What are the top interactions someone can have on the website (contact, download, register, login, purchase)
- eventAction – what did the user just do? Click a button? Submit a form? describe the type of content being interacted with. Register = newsletter, account. Purchase = to cart, to wish list, etc.   
0 eventLabel – what form is this? If this is part of an A/B test, what variation?
- eventValue – how much is this action worth? If we have a basic estimate at least we can more easily combine all ‘value’ generated across different conversion types together to see an aggregate of how our traffic is performing.

## Custom pipelining 
- Singer taps 
- Python scripts: pandas or e.g. spark if volumes are higher 
- Transformations can either be done in python directly or you push to Snowflake in JSON format and then transform the data in Snowflake 
- Probably best not to outsource this unless it can be very cheap - we’d only need to take the data and load into Snowflake
- Scheduling
  - managed airflow (Google Cloud composer / Astronomer)
  - For production data, we should be able to directly pipeline from the database used. PII is an use but there will be ways around. Alternatively, engineers can make data available in S3 and we can use Fivetran to extract from S3.  
  - lamba and cloudwatch 
  - Airflow: complex as it needs to run on EC2 
  - Fivetran + Lamdba: complex and 15 minutes limit with Lambda  
  - Cron: not on the cloud
  - Google Cloud Scheduler: possible
  - AWS Glue: possible but probably wouldn’t do the job as nobody mentions it 

## AirFlow
General project notes 
- Using bashoperators to run python script and to run a bash command
- If one of these fail, send an email 
- Don’t run the catch-up, so the scheduler just starts to run from the moment it is initiated

Set-up
- Install airflow using Pip install airflow
- Initialize the Airflow database that stores all Airflow related metadata: airflow initdb. From here, there should be an airflow folder on your local machine. Default arguments for the set up are stored in the airflow.cfg file within the airflow directory 
- Start the Airflow web server using airflow webserver. This allows access to Airflow’s web UI. Access this via http://localhost:8080/admin/
- To actually use Airflow’s scheduling, we need to instantiate the scheduler: airflow scheduler 
- To kill the webserver: pkill -9 -f "airflow scheduler" pkill -9 -f "airflow webserver" pkill -9 -f "gunicorn"
DAGS
  - Airflow is a Workflow Management System that defines tasks and their dependencies as code, executes those tasks on a regular schedule 
  - A dag is a representation of a graph that has a specific order of operation. A DAG consists of operators, which are functions that perform certain tasks. The tasks do the work we want performed
  - The dag file should sit in dags within airflow directory. Save the related Python file to run in the same directory
  - A DAG file consists of: 
    - default arguments
    - a specific DAG description, which includes a specific schedule interval. 
    - The actual tasks that need be executed  
  - Test a DAG file using airflow dag_name task_name 2017-03-18T18:00:00.0. In this case, my_test_dag is the actual dag id and the operator task is what the task within the DAG is called:: airflow test twitter_dag twitter_run 2018-08-07T20:04:00.0
  - Actual run a specific task: airflow run twitter Twitter 2019-08-07
  - Backfill allows us to run a DAG (or sections of it) for a specified date range.  Backfill: airflow backfill twitter -s 2019-08-07 -e 2019-08-09. 
Email set-up
- SMTP settings are added to the airflow.cfg file
- Imported Emailoperator and added a second task to actually send the email. The DAG order of operations are specified underneath the file 
- The email is only sent when all prior tasks have failed, so it only runs when t1: the Twitter bash job has failed in entirety. This is set using Airflow trigger rules  
- The email addresses need to be a list. 

Airflow principles
- The scheduler runs jobs at the end of the schedule_interval. So a daily task on 20150101 will run on 20150101 23:59
- Every time the scheduler trigger has been hit (or when a run is initiated), Airflow creates a DAG run. 
- When Airflow scheduler start to schedule DAG runs, it starts from the very earliest point, so if I say start today at interval of one hour, Airflow will run a catchup process first by running the number of occurrences that airflow should have been run, but hasn’t. This means in my instance that I can schedule Airflow once a day with a certain start date and airflow will do the catch up each time I start the scheduler. We can set this to false using catchup = False (use the documentation). 
- Campaign / Acquisition Tracking. Every campaign needs to be tagged with unique parameters that allow your analytics tool to identify it. This can e.g. be in a URL: everything after the question mark is data used to track marketing campaigns. 

