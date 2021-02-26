# Python
## Python use cases
Python vs Excel: 
- Can work with large datasets
- Offers more scalable solutions
- The code and analysis is reproducible 
- Faster and more flexible for any stats work 

Analytics
- Working with large datasets (e.g. instead of vlookups)
- EDA on dataset
- Statistical analysis (hypothesis tests)
- Visualizations 
- Combining datasets from multiple sources 
- Regular expressions

Data science 

ETL 
- Retrieving data from API
- Transforming the data using pandas or e.g. Pyspark
- Loading the data into DWH from a dataframe

Automation 
- Organize files on machine, like copying specific files (pyperclip module), compressing, renaming files in bulk, moving files, deleting files 
- Web scraping. First, download a HTML page and then use Beautifulsoup to actually scrape the HTML of the page 
- Work with Excel files using openpyxl modules. Things to do: update cell values, copy cell values, working with complicated formulas - rather than learning the Excel formula we just use Python to recreate the formula but then pythonic
- Work with CSV and JSON files. For CSV files, I would always use Pandas to manipulate the dataset. When working with datasets in Python, make sure to always first backup the dataset itself so you avoid messing with the dataset by accident. Working with JSON is done using the loads and dumps functions. JSON is often used to work with APIs 
- Schedule tasks and launch programs. Use e.g. cron or Windows scheduler  
- Send emails on a schedule, via a SMTP server. You can send reminders to people from a spreadsheet. There is a service called Twilio that can be used to send text messages using python - use this e.g. to send yourself reminders. Other example: send automated emails with data returned by a SQL query 
- GUI automation. We can replicate what we do with the mouse and keyboard using GUI automation. The module for this is pyautogui. The mouse movements/clicks/scrolls are based on coordinates on the screen, which are based on the resolution. You can click on a point, you can drag items, you can click on e.g. grey buttons by first automating making a screenshot of the screen and then python knows intuitively where to click. You can fill in forms e.g. from a spreadsheet source. E.g. write a script that nudges your mouse every couple of minutes 

## Style guide 
- Beautiful is better than ugly.
- Explicit is better than implicit.
- Simple is better than complex.
- Flat is better than nested.
- Sparse is better than dense.
- Readability counts.
- Use spaces, not tabs

