Currencies
A simple option to work with currencies:
•	Have a true_amount that needs to be combined with a currency 
•	A GBP_amount
•	Any other downstream measures would be duplicated: one for each currency 
•	With this, make it mandatory for end users to select a currency when they show true amount - otherwise we’d mix and match e.g. USD and GBP. 
•	When no mandatory filter can be used, the best simple solution is just to show all values in a single currency - e.g. everything in GBP

Currency model (this is required anyway if we don’t use a constant for currency conversions) 
•	Date, source currency, target currency, rate 
•	Each model: price_local, currency, price_usd
•	In DBT, join the currency model to the model you want to use currencies from - make sure to join a date field on a currency date field 

More complex but scalable: 
-	Parameters with liquid and HTML – this would avoid having to duplicate each measure. Instead, the value of the parameter determines what to use and what to display. See Tools document (Looker section) for the specific code. 

Dates
Which dates to use: 
•	Rate at end of period should be used for month end reporting
•	Any financial reporting, metrics should be taken from month end numbers
•	Anything else could be on a current day conversion, or for example when the money actually comes in 

Timezones
-	We either store timestamps in a certain timezone (e.g. UTC) and perform timestamp conversions in the BI tool
-	Or we store timestamps both in local as well UTC and we have a way of identifying each in the tables. 
