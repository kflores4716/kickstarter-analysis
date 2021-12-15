# Kickstarting with Excel

## Overview of Project
Louise’s play Fever has reached its fundraising goal but is still in the Kickstarter phase. She is looking to gather more insight into similar Kickstarter Campaigns to determine what led to their success (or failure). 
### Purpose
The purpose of this project is to analyze multiple Theater Kickstarter Campaigns based on their launch dates and funding goals. This insight will help her decide how to position her campaign launch to give herself the highest chance of success. Once launched, she will then have a better idea as to how likely her campaign is to succeed.
## Analysis and Challenges
The two analyses were created in Microsoft Excel using a larger data set containing several categories of Kickstarter Campaign information. The data was filtered down to display Theater campaigns based on two metrics: 
1. Outcomes Based on Launch Date
2. Outcomes Based on Goals
### Analysis of Outcomes Based on Launch Date
To determine the outcomes of these campaigns based on their launch date, I created a Pivot Table and accompanying Line Chart in a new Excel sheet. The first column of the table filters the campaigns based on the month of the year that they launched. I then referenced the “Parent Category” column from the larger data set and filtered those categories to only show theater campaigns. Once the table showed the grand total of the campaigns based on the month they launched, I further separated them to show the three possible campaign outcomes:
1. Successful
2. Failed
3. Canceled

See a copy of the table below:

![Theater_Outcomes_vs_Launch_Table](https://user-images.githubusercontent.com/94764735/145914087-528350e4-5eb7-450d-a579-0f3beba80985.png)

Using this pivot table, I then created a line chart to display the outcomes in a different manner. Graphing the data can allow for a quicker and easier visualization of the outcomes of these campaigns based on the months they are launched. Please see below:

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/94764735/145914204-0e0b0dd5-3125-4fe7-8bc8-58562a96e59e.png)

### Analysis of Outcomes Based on Goals
I analyzed these campaigns based on funding goals using a different approach than what I used for my launch date analysis. When analyzing the outcomes by launch date, it was easy to filter the data by months as that information was already included in the original Kickstarter data set. The goal amounts weren’t already separated into specific ranges, so I couldn’t use the Pivot Table function to categorize the goal outcomes. I had to create my own table from scratch. 

The first step I took was to create a column splitting up the goals into 12 price ranges (just like the 12 months in the last analysis). I then created 7 more columns to hold the individual counts, total count, and percentage of each campaign outcome (successful, failed, and canceled). To get the count of outcomes, I used the `COUNTIFS` function. I referenced the Kickstarter sheet and added the necessary criteria that would return the outcomes based on the specific ranges from column one. Here is an example of a cell with the proper `COUNTIFS` entry:  `=COUNTIFS(Kickstarter!$F$2:$F$4115,"successful",Kickstarter!$D$2:$D$4115,"<1000",Kickstarter!$R$2:$R$4115,"plays")`
Also, see below for table image:

![Outcomes_vs_Goals_Table](https://user-images.githubusercontent.com/94764735/146098575-6610ba0a-bd70-485d-8f29-7641f1c956b0.png)

Once I had the count of these outcomes, I could total them up and use that data to calculate the percentage of each outcome in the next three columns. Finally, after all data was gathered, I used the table to create another Line Chart to better visualize the percentage of each outcome based on the price ranges. See the line chart below:

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/94764735/146098598-7c89d924-b55d-4b9d-b9d0-e8a681a8398b.png)

### Challenges and Difficulties Encountered
Analyzing the Campaign outcomes based on launch date was the easier of the two analyses. As I mentioned earlier, we already had the launch dates in our original data set, so it was easy to use the Pivot Table function to split up the dates by month. The biggest challenge was making sure to create the Pivot Table properly so that the Line Chart I eventually created was easy to interpret. The Table itself can be easily interpreted in two ways. Whether the outcomes are listed by column and dates by row or vice versa, the Table makes sense either way. However, when viewing the resulting line charts, there is one that is obviously better than the other. See below:

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/94764735/146099497-c1415782-3308-4c78-9ade-110e557bd526.png)

![Theater_Outcomes_vs_Launch_Incorrect_Chart](https://user-images.githubusercontent.com/94764735/146099514-4010e080-181d-4c12-b625-3ebaa982623a.png)

As you can see, the chart on the left is much easier to read than that on the right. Thus, the table listing the outcomes as columns and dates as rows is what was used as the final product.
