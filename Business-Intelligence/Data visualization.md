# Data visualization 
## Principles
- Always understand what you want to convey in the dashboard. What's its raison d'etre? 
- Don’t make people think 
- Make use of conventions: 
    - People read in Z shapes: left corner is the most important. Think left to right, bottom to top where top right is where you want to head. 
    - Group related content together 
- Eliminate all questions that could be in the heads of your users 
- Use contrast to direct focus. Can be using color, size, position 
- Eliminate clutter: remove anything that doesn’t serve a purpose and generally avoid displaying too much data 
- Minimize any noise 
- Avoid complexity
- Create a story from high level and then more context
- Use consistency. E.g. if a target line is blue in one graph, it should be blue everywhere
- Dashboards need to be actionable. Focus on insights and impact. People need to immediately spot: 'What does this tell me?'. Some tactics: 
    - Compare against target lines 
    - Compare against budgets 
    - Use red and green to indicate good and bad
- When information would add context, don't be afraid of adding this text

### Good graphs
- Title is descriptive title
- Axis titles are descriptive and e.g. include currency 
- Axis values are clear and readable 
- Data values are in the right format
- Data is sorted: e.g. sort bar charts from high to low. Order data tables logically and include the ordering in the title 
- Annotate anything that would raise questions in the graph
- Remove anything that could raise questions - e.g. don't show NULL values 
- Column charts should be sorted such that the largest values are at the bottom
- Hide a legend when the legend is too big - people will just hover over 
- Add a total on top of column charts 

## Good tables
- Only ever show top X - avoid clutter
- Consider conditional formatting to help users find hot spots 
- Think hard about why you're using a table in the first place and whether there could be a better alternative 
- Make sure to order your tables in a logical way 
- Remove color, gridlines, border
- Remove bolded headers 
- Left align text
- Right align numbers
- Align headers with data 
- Resize columns to data 
- Add whitespace
- USe consistent precision in numbers
  
![Good table](https://user-images.githubusercontent.com/28791247/93847904-30af8e80-fca0-11ea-98de-ea051fe5904d.png)


### Good dashboards
- Good dashboards are interactiove: 
    - Filters to segment data
    - Ability to drill down to look into the details
    - Helpful tooltips to understand the data better when hovering over a graph  
- Designed with the use case in mind (test this!): 
    - Check the sizing of the dashboard on multiple devices
    - In a dashboard will be used in meetings, spotting good / bad should be possible from afar
- Good looking
- Include the company’s color palette 
- Use of clear headers
- Single value visualizations go at the top of the dashboard
- Make use of placeholders when there is some WIP
- Where relevant, notes can be added in text boxes. In general, text is your friend: use it to label, introduce, explain, reinforce, highlight, recommend, and tell a story. If there is a conclusion your want your audience to reach, state it in words. 
- Headers and graphs are well sized
- Consider adding a tile that outlines what the user is looking at 
- Only show the critical few metrics to portray the story. 6 metrics by dashboard is a good starting point. All elements need to serve a purpose and any other clutter should be eliminated   
- Data is logically laid out and well alligned 
- Leverage white space
- Similar timeframe across all visualizations 
- Use color as an intentional decision; only to highlight important pieces

## Chart decisions
- Bar charts to compare numbers/categories. Bar charts should always start at zero baseline. When going to negatives, consider using a light grey colour for the whole area below 0. With a horizontal bar chart, consider a thin line after every e.g. 5 bars. 
- Stacked bars for categorical comparisons and the share of their subcomponents 
- Line charts to depict trends over time. Most commonly used to plot continuous data. With a line chart, include a zero baseline whenever possible. Use direct labelling when possible to enhance readability and understanding. When there are negative values, make the zero grid line on the x axis heavier than the other grid lines. 
- Scatter plots to easily see outliers and spot the relationship between two things. In a scatter plot, the independent variable (control variable) is displayed on the x-axis. This parameter gets systematically incremented. The dependent variable is displayed on the y axis. This value depends on the value of the independent variable. Sometimes, there is no dependent variable. In that case, it doesn’t matter what gets plotted where. 
- Maps to depict data geographically
- Pie charts to show relative proportions or percentages of data. If there are 6+ areas within a pie chart, use a bar or line graph instead
- Bubble chart: bubbles should be used as a way to accentuate data on scatter plots or maps – the bubble sizes give information about the data
- Histogram – when you want to see how data are distributed across different groups
- Heat maps – a table with visual cues, often color. It removes the user from thinking too much and they directly get directed to what they should be focused on. It reduces mental processing. Make sure to always include a legend that helps interpret the data. This is helpful e.g. for contribution analysis. 
- Highlight table – essentially, this is a heatmap with actual data in a table
- Box plot: show distribution of data.
- Simple text when you have one or two numbers to share 
- Table for when the data isn’t many, but more and therefore needs more organization than simple text. Note that a table is often used when someone is looking for a particular value by itself in a specific row. It’s also helpful when there’s multiple units of measure to show. Don’t show a table in a presentation as it is very distracting from the point you’re trying to make – people will try to see the trends. 
- Waterfall chart is often use to show and specific in and decreases – e.g. sales, returns, late charges, and shipping costs in a month to get to the net added amount in a month 
- Area graph – where the size of an area in a graph represents the size of the variable. Not recommended as people do a bad job attributing the space. Perhaps only use it to show great differences in order of magnitude 
- Plus-Minus charts to show variances: this is a baseline and then plus or minus values on each side, either absolute or percentages 
- Integrated variance analysis to show absolute values, as well as the variances. 
- Contribution analysis: access the contribution of all parts to the whole value. Use waterfall charts to show contributions 

![Visualizations](https://user-images.githubusercontent.com/28791247/93848010-73716680-fca0-11ea-8a21-92081453c6ce.png)

**Visualizations not to use:**
- Pie charts: the human eye isn’t good at ascribing quantitative value to two dimensional space, making them hard for people to read. If two pieces are close, you can’t tell which is better. If ywo pieces are far off, you still can’t tell by how much. Use a bar/column chart instead
- Don’t use donut charts: we can’t compare arc lengths either
- Never use 3D 
- Try not to use secondary axis. Instead, use the techniques as outlined in the image 



### Action oriented dashboard
![Action oriented dashboard](https://user-images.githubusercontent.com/28791247/93705326-34aea580-fb14-11ea-9427-403731477a56.png)

Explanation
- Include a title
- Include the responsible people from the business side, as well as the analysis side. 
- Indicate the health of the metric with the dot at the top of the dashboard (red, yellow, green) 
- First quadrant: show trend of metric (will be glossed over)
- Second quadrant shows key trends and insights. Here, you add value by interpreting the trends and by supplying context. This will be main focus of the executive 
- Third quadrant is where the analyst needs to get out of his or her silo and talk to people and understand what is already being done. The goal is to identify root cause for trends in the metric and to recommend solid action. It’s a great opportunity to become smart about the business. In this quadrant, you recommend the next step or action. 
- The fourth quadrant is really a kick in the butt to most executives and outlines the problems the company has or will see from the badly performing metric. It answers: ‘As a result of this trend, what was the impact on the company and its customers?’

### Data storytelling examples 
![Storytelling 1](https://user-images.githubusercontent.com/28791247/93705518-0cc04180-fb16-11ea-8208-25a4df80e92e.png)


![Storytelling 2](https://user-images.githubusercontent.com/28791247/93705521-16e24000-fb16-11ea-91db-7c74075f49d7.png)

![Storytelling 3](https://user-images.githubusercontent.com/28791247/93705528-219cd500-fb16-11ea-94a1-4ca679990654.png)

![Storytelling 4](https://user-images.githubusercontent.com/28791247/93705535-2b263d00-fb16-11ea-9f20-ad08400205bf.png)

![Storytelling 5](https://user-images.githubusercontent.com/28791247/93705539-35e0d200-fb16-11ea-9c7f-59198f3eb5e7.png)

![Storytelling 6](https://user-images.githubusercontent.com/28791247/93705543-4002d080-fb16-11ea-9543-237345952aae.png)

![Storytelling 7](https://user-images.githubusercontent.com/28791247/93705553-498c3880-fb16-11ea-8aed-c19bb6f8b8ab.png)

### Other visualizations 
![Secondary axis](https://user-images.githubusercontent.com/28791247/93705681-172f0b00-fb17-11ea-8d4e-0308812a840e.png)

![Dashboard](https://user-images.githubusercontent.com/28791247/93705716-58bfb600-fb17-11ea-9930-949ba3a0639c.png)

![MRR](https://user-images.githubusercontent.com/28791247/93705738-80af1980-fb17-11ea-9c4c-e2b5d0c17f04.png)

![Cohort](https://user-images.githubusercontent.com/28791247/93705748-93c1e980-fb17-11ea-9caf-49cf8b2162cd.png)