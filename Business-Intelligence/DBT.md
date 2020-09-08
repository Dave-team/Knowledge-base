# DBT

## Links
- DBT best practices: https://docs.getdbt.com/docs/guides/best-practices/
- DBT viewpoint: https://docs.getdbt.com/docs/about/viewpoint/
- How we configure Snowflake: https://blog.getdbt.com/how-we-configure-snowflake/
- How we structure our DBT projects: https://discourse.getdbt.com/t/how-we-structure-our-dbt-projects/355


## DBT architecture
### Data Warehouse 
Three databases:
- Raw: this is where all the source tables are. Access is restricted to data loaders. Each source has its own schema: Salesforce, Google Sheets etc. 
- DBT_DEV restricted to DBT developers. This very much functions as a testing environment. Each developer here has a separate schema which is named after their own name. 
- Analytics. This is the prod target. Here we have: 
    - One schema for staging and intermediate models (stg_ and int_)
    - One schema for core data models 
    - Different schemas that represent data marts by functional area 

### DBT models
**Source**
Schemas and tables in a source-conformed structure (i.e. tables and columns in a structure based on what an API returns), loaded by a third party tool. They are the only tables that should directly reference a raw table
With sources, we can add definitions, tests and documentation

**Staging**
The atomic unit of data modeling. Each model bears a one-to-one relationship with the source data table it represents. Staging models have the same granularity as sources, but columns have have been: 
- Fields have been renamed and recast in a consistent way. (use :: to recast to keep things clean and simple)- cast as much as possible as explicit is better than implicit 
- Datatypes, such as timezones, are consistent.
- Light cleansing, such as replacing empty string with NULL values, has occurred.
- If useful, flattening of objects might have occurred.
- There is a primary key that is both unique and not null (and tested).

Each staging directory then has: 
- Different directory by source
- One staging model for each object that is useful for analytics:
    - Named stg_source__object. E.g. stg_salesforce_customers.
    - Generally materialized as a view (unless performance requires it as a table).
- A stg_source.yml file which contains:
    - Source definitions, tests, and documentation
    - Tests and documentation for models in the same directory

**Marts**
Models that represent business processes and entities, abstracted from the data sources that they are based on. Marts are stores of models that describe business entities and processes. They are often grouped by business unit: marketing, finance, product. Models that are shared across an entire business are grouped in a core directory. 

Each marts directory ends up looking like: 
- A core and different marts directories
- fct_ and dim_ models within each directory, e.g. fct_orders, dim_customers
- A directory can include intermediate transformations, these are required to get to a fact or dimension model. They are placed in a nested marts/mart_name/intermediate directory. They are named <
useful_name__transformation_in_past_tense.sql - for example order_payments__joined.sql or customer_orders__grouped.sql
- Models are tested and documented in a dir_name.yml file in the same directory as the models.
- Any extra documentation in a docs block is placed in a dir_name.md file in the same directory.

## DBT principles
- Only staging models should select from source
- Each model needs a primary key 
- Make sure to comment transformation code 
- Always define the data types whilst modelling 
- A new dbt model is not complete without tests and documentation.
- All {{ ref('...') }} statements should be placed in CTEs at the top of the file. (Think of these as import statements.). This makes the code modular with the following benefits: 
    - It clarifies the order in which models need to be run
    - Keeps things DRY: only need to change models once and that change is then reflected in entire project 
    - We run a single model just once, reducing costs in the data warehouse 
    - Everyone uses the same logic for the base models 

## DBT other
- It is more powerful than normal SQL as we write it in the python language (Jinja)
- We can use test severity to either warn about a failure or to let a run fail because of an error 
- Hooks: SQL commands executed at certain times during a run. 
    - Pre hooks to grant the right access to the schemas 
    - Post hooks to grant select or usage on future tables 
- Macros: SQL snippets that are invoked like functions from models. These functions can be re-used between models to keep up with the engineering principles of DRY (Don’t Repeat Yourself). Example of macros: renaming column names that share attributes, changing how DBT handles custom schemas Seeds: loading data from CSV into data warehouse 
- DBT models can be materialized as views, materialized views and tables. For BI tools, make sure to have tables for increased query performance. 
- We can use tags in DBT. Use cases could be to tag frequency of models or models that contain PII 
- Snapshots: Follow the naming convention {source_name}_{source_table_name}_snapshots for your file name
- Seeds: loading CSV files into the DWH using DBT
- DBT debugging: Run the compiled SQL in the data warehouse
- Run fewer models using model selection syntax - this greatly helps when testing models in dev: 
  - Run tests for a single model: dbt test --models opportunity_line_item --target dev
  - Run a single model in DBT: dbt run --models sales_forecast --target dev
  - Run all child relationship models: dbt run --models +Marts.Xero --target dev 
  - Run all models in a schema: 
    - dbt run --models Xero --target dev
    - dbt run --models Staging.Xero.*
  - We can also use the excluded syntax to not run certain models 
- Limit the data being processed while in dev to speed up table creation jobs (and to limit storage in the warehouse): {% if target.name == 'dev' %}
where created_at >= dateadd('day', -3, current_date)
{% endif %}
- We can add a better Continious Integration process to our workflow: https://docs.getdbt.com/docs/dbt-cloud/using-dbt-cloud/cloud-enabling-continuous-integration-with-github/
- Generate docs by enabling the setting on the DBT Cloud job 
- We have the option to add Redshift customizations to improve model performance in DBT 

## DBT set-up



with {{ distinct_source(source=source('gitlab_dotcom', 'gitlab_subscriptions'))}}, 

renamed AS (
    SELECT DISTINCT

      id::INTEGER                    AS gitlab_subscription_id,
      start_date::DATE               AS gitlab_subscription_start_date,
      end_date::DATE                 AS gitlab_subscription_end_date,
      trial_starts_on::DATE          AS gitlab_subscription_trial_starts_on,
      trial_ends_on::DATE            AS gitlab_subscription_trial_ends_on,
      namespace_id::INTEGER          AS namespace_id,
      hosted_plan_id::INTEGER        AS plan_id,
      max_seats_used::INTEGER        AS max_seats_used,
      seats::INTEGER                 AS seats,
      trial::BOOLEAN                 AS is_trial,
      created_at::TIMESTAMP          AS created_at,
      updated_at::TIMESTAMP          AS updated_at,
      valid_from -- Column was added in distinct_source CTE
  
    FROM distinct_source
    WHERE gitlab_subscription_id != 572635 -- This ID has NULL values for many of the important columns.
