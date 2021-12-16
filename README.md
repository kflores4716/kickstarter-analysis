# Kickstarting with Excel

## Overview of Project
Louise’s play Fever has reached its fundraising goal but is still in the Kickstarter phase. She is looking to gather more insight into similar Kickstarter Campaigns to determine what led to their success (or failure). 
### Purpose
The purpose of this project is to analyze multiple Theater Kickstarter Campaigns based on their launch dates and funding goals. This insight will help Louise decide how to position her campaign launch to give herself the highest chance of success. Once launched, she will then have a better idea as to how likely her campaign is to succeed.
## Analysis and Challenges
The two analyses were created in Microsoft Excel using the larger data set contained in the Kickstarter worksheet. The data was filtered down to display Theater campaigns based on two metrics: 
1. Outcomes Based on Launch Date
2. Outcomes Based on Goals
### Analysis of Outcomes Based on Launch Date
To determine the outcomes of these campaigns based on their launch date, I created a `Pivot Table` and accompanying `Line Chart` in a new worksheet. The first column of the table filters the campaigns based on the month of the year that they launched. To create the rows in that column, I used the "Date Created Conversion" field as my Rows filter. I then used the “Parent Category” field as a Filter and refined those categories to only show theater campaigns. Once the table showed the grand total of the campaigns based on the month they launched, I further separated them by using "Outcomes" as the Column filter in my table. This allowed me to split the data into the three possible campaign outcomes:
1. Successful
2. Failed
3. Canceled

See a copy of the table below:

![Theater_Outcomes_vs_Launch_Table](https://user-images.githubusercontent.com/94764735/145914087-528350e4-5eb7-450d-a579-0f3beba80985.png)

Using this `pivot table`, I then created a `line chart` to display the outcomes in a different manner. Graphing the data provides a quicker and easier view of the outcomes of these campaigns based on the months they are launched. Please see below:

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/94764735/145914204-0e0b0dd5-3125-4fe7-8bc8-58562a96e59e.png)

### Analysis of Outcomes Based on Goals
I analyzed campaigns based on funding goals using a different approach than what I used for my launch date analysis. When analyzing the outcomes by launch date, it was easy to filter the data by months as that information was already included in the Kickstarter data set. For this analysis, goal amounts weren’t already separated into specific ranges, so I couldn’t use the `Pivot Table` function to categorize the goal outcomes. Instead, I had to create my own table from scratch so that I could split up the outcomes into different ranges. This way, I could properly determine how campaign goals played a role in the eventual outcomes. 

The first step I took was to create a column splitting up the goals into 12 price ranges (just like the 12 months in the last analysis). I then created 7 more columns to hold the individual counts, total count, and percentages of all three campaign outcomes. To get the count of outcomes, I used the `COUNTIFS` function. Referencing the Kickstarter worksheet, I added `COUNTIFS` criteria to only return outcomes within the specific goal ranges I had just created. Here is an example of a cell with the proper `COUNTIFS` entry:  `=COUNTIFS(Kickstarter!$F$2:$F$4115,"successful",Kickstarter!$D$2:$D$4115,"<1000",Kickstarter!$R$2:$R$4115,"plays")`
Also, see below for an image of the table:

![Outcomes_vs_Goals_Table](https://user-images.githubusercontent.com/94764735/146098575-6610ba0a-bd70-485d-8f29-7641f1c956b0.png)

Once I had the count of these three outcomes, I could total them up and use that data to calculate the percentage of each outcome in the next three columns. Finally, once my table was complete, I used it to create a line chart just like I did with the launch date analysis. See the line chart below:

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/94764735/146098598-7c89d924-b55d-4b9d-b9d0-e8a681a8398b.png)

### Challenges and Difficulties Encountered

#### **Theater Outcomes by Launch Date**

This analysis was the easier of the two that I performed. As I mentioned earlier, we already had the launch dates in our original data set, so I was able to use the `Pivot Table` function to split up the dates by month. One possible challenge here is that your launch dates may be grouped by more than just months (e.g. quarters, years, etc.). To change this, all you need to do is right click one of the date cells and select "Group". From there, you get a list of all the ways to group the data, and you need to make sure that the only group selected is "Months". When you click "okay," your table will then display the data as intended.

Perhaps the biggest challenge was making sure to create the `Pivot Table` properly so that the `Line Chart` I eventually created was easy to interpret. The table itself can be easily interpreted in two ways. Whether the outcomes are listed by column and the dates by row or vice versa, the table makes sense either way. However, when viewing the resulting charts, there is one that is obviously better than the other. See below:

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/94764735/146099497-c1415782-3308-4c78-9ade-110e557bd526.png)

![Theater_Outcomes_vs_Launch_Incorrect_Chart](https://user-images.githubusercontent.com/94764735/146099514-4010e080-181d-4c12-b625-3ebaa982623a.png)

As you can see, the chart on top is much easier to read than that on the bottom. Thus, listing the outcomes as columns and dates as rows is what I used in my final product.

#### **Outcomes Based on Goals**

This analysis was more involved, and as a result there was more room for error. Using the `COUNTIFS` function can be tricky because you are referencing multiple categories of data that each have their respective criteria to meet. If the categories and their criteria aren’t typed using the proper spelling and punctuation, the data in the table will not display the figures you are intending to. This can be especially annoying because you won't get an error message, so if you aren't careful you can create a whole table and not even realize that the data is wrong. As a matter of fact, this happened to me the first time I created my goals table.

When I first created my data table, I did not type all criteria in my `COUNTIFS` function properly. I was using the “>=” connotation for the lower bound goal range criteria, listing the exact lower bound number from column one. However, for the upper bound goal range, I was using “<=" but typed the lower bound goal from the proceeding range. For example, for the second range I used 1000 and 5000 as the bounds rather than 1000 and 4999. In my mind, I thought I would save some typing and just use "<" along with the next lower bound. If I typed it correctly, this would have worked just fine. This is actually how I created my table in the end, but as I said I used "<=" and not "<". My error meant that my goal counts were including some of the goals from the next range, so the resulting data in my table was throwing off my whole analysis.

At first, I didn’t realize my mistake because the data table didn’t return any errors and appeared to be correct. However, when I created my chart I had a feeling that something was off. I added up my "Total Projects" column to make sure I was including all projects, and thats when I realized that I had definitely made a mistake. So, I took another look at my `COUNTIFS` functions and pretty quickly was able to locate that mistake and correct it. 

I did actually make one other error, although I believe it actually may have helped me fix my last mistake. When I created my `Line Chart`, I first chose a chart type labeled "100% Stacked Line." I figured since I was graphing percentages, this might be a good chart type to use. When the chart populated, I immediately noticed that the "Percentage Failed" line was not showing at all. I also noticed that my "Percntage Canceled" line was up at 100% when the table clearly had all "Percentage Canceled" at 0%. As I just mentioned, this incorrect chart made me go back and look at my data, which then led to the discovery of my `COUNTIFS` errors. So, perhaps chosing the wrong chart type actually helped me out a little in the end. Anyways, after fixing my data table, I then changed my chart type to the basic "Line" option and everything was finally showing as intended.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

1. Theater campaigns have the highest chance of success when launched in the middle of the year. The two months with the highest success rates are May and June, so that might be a good time frame to aim for.
2. You should avoid launching a theater campaign in December. Only 37 of the 75 campaigns in December were successful. This is the only month where the success rate is below 50%.

- What can you conclude about the Outcomes based on Goals?

1. Most of these play campaigns have a funding goal of less than $10,000, and the majority of those campaigns are successful. As the funding goals increase, the percentage of successful campaigns begins to decrease. So, if you want your campaign to succeed, it is in your best interest to start with a funding goal that’s on the small side.

- What are some limitations of this dataset?

    - These campaigns span across several countries who have their own currencies. If we were to consider exchange rates, many of the funding goal and funding pledged amounts         would be different than what the table lists. In addition, those different countries may have different preferences as a whole. So, some of these campaigns might succeed         just because the country they're in likes all theater, and some might fail just because their country is more critical of new shows or perhaps just doesn't like theater in       general.

    - The data doesn’t show us what is being done to attract backers and funding. The number of backers and amount of funding can impact the eventual success (or failure) of the       campaign.

    - We aren’t given any information on how these campaigns are being marketed to the public. Marketing almost always has an impact on the success of a new product (or in this       case, theater campaign).

- What are some other possible tables and/or graphs that we could create?

    - We could create a table and graph comparing the amount of pledged funding to the campaign outcomes to see if that pledged amount impacts the success of a campaign.

    - We could also create a table and graph comparing the number of backers to the campaign outcomes, again to see if it impacts a campaign’s success.

    - If the number of backers and pledged amount do correlate with the success of a campaign, we could go even further to see what might impact those two factors. We could          compare each of them (with tables and graphs) to the funding goals and determine if those funding goals affect their outcomes. With this new data, we could have a deeper        understanding as to why a campaign’s funding goal impacted its outcome.

    - Additionally, we could draw a comparison between funding goals and launch dates as well, since we already have tables and graphs showing how they impact a campaign’s            outcome. It would take some time, but we could make 12 copies of the COUNTIFS table we created for funding goals. Then, in each table we could add another criteria to            further separate the data by months. Finally, once we have the new tables, we could create graphs for each one. With our new data, could determine what time of year a            campaign should launch based on its funding goal.
