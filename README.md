# Crowdfunding Analysis in Microsoft Excel
Crowdfunding platforms like Kickstarter and Indiegogo have been growing in success and popularity since the late 2000s. From independent content creators to famous celebrities, more and more people are using crowdfunding to launch new products and generate buzz, but not every project has found success.

To receive funding, projects must meet or exceed an initial goal, so many organizations dedicate considerable resources looking through old projects in an attempt to discover “the trick” to finding success.

<img width="1619" alt="image" src="https://github.com/user-attachments/assets/56acfb14-6481-41e4-9853-f673ad548bee" />

## What Was Done:
- Used conditional formatting to fill each cell in the `outcome` column with a different color, depending on whether the associated campaign was successful, failed, canceled, or is currently live.

  - Created new column `Percent Funded` that uses a formula to find how much money a campaign made relative to its initial funding goal.

- Used conditional formatting to fill each cell in the `Percent Funded` column according to a three-color scale. Scale begins at 0 with a dark shade of red, transitioning to green at 100 and blue at 200.

  - Created new column `Average Donation` that uses a formula to find how much each project backer paid on average.

  - Created two new columns, `Parent Category` and `Sub-Category`, that use formulas to split the `Category and Sub-Category` column into two new, separate columns.

  - Created a new worksheet <i>Category Statistics</i> with a pivot table that analyzes the initial <i>Crowdfunding</i> worksheet to count how many campaigns were successful, failed, canceled, or currently live per category.
    - Within <i>Category Statistics</i> worksheet, created a stacked-column pivot chart that can be filtered by country based on the pivot table.

- Created a new worksheet <i>Sub-category Statistics</i> with a pivot table that analyzes the initial <i>Crowdfunding</i> worksheet to count how many campaigns were successful, failed, or canceled, or are currently live per sub-category.
  - Within <i>Sub-category Statistics</i> worksheet, created a stacked-column pivot chart that can be filtered by country and parent category based on the pivot table.

- The dates in the `deadline` and `launched_at` columns use Unix timestamps. Fortunately for us, [this formula](https://www.extendoffice.com/documents/excel/2473-excel-timestamp-to-date.html) can be used to convert these timestamps to a normal date.
  - Created a new column `Date Created Conversion` that uses [this formula](https://www.extendoffice.com/documents/excel/2473-excel-timestamp-to-date.html) to convert the data contained in `launched_at` into Excel's date format.
  - Create a new column named `Date Ended Conversion` that uses [this formula](https://www.extendoffice.com/documents/excel/2473-excel-timestamp-to-date.html) to convert the data contained in `deadline` into Excel's date format.
 
## Outcomes Based On Launch Date
- Created new worksheet <i>Outcome Based on Launch Date</i> with a pivot table that has a column of `outcome`, rows of `Date Created Conversion`, values based on the count of `outcome`, and filters based on `parent category` and `Years`.
- Created a pivot chart line graph that visualizes this new table.

### Results ###
Given the provided data, what are three conclusions that we can draw about crowdfunding campaigns?
1. There are generally more successful crowdfunding campaigns than canceled crowdfunding campaigns.
2. Parent Category of Theater has both the highest number of canceled campaigns as well as the highest number of successful campaigns.
3. Journalism is the least popular crowdfunded campaign with a total of 4 successful campaigns.


What are some limitations of this dataset?
-	This dataset only has data from 7 countries.
-	This dataset only includes 9 parent category crowdfunding campaigns.

What are some other possible tables and/or graphs that we could create, and what additional value would they provide?
- Comparing the average donation per backer in successful vs failed campaigns would be helpful. It could help indicate whether a new live campaign was on track to succeed or not given the cumulative average of donations being received per backer at that point in the campaign.


## Crowdfunding Goal Analysis
- Create a new sheet with 8 columns:
  - `Goal`
  - `Number Successful`
  - `Number Failed`
  - `Number Canceled`
  - `Total Projects`
  - `Percentage Successful`
  - `Percentage Failed`
  - `Percentage Canceled`
- In the `Goal` column, create 12 rows with the following headers:
  - Less than 1000
  - 1000 to 4999
  - 5000 to 9999
  - 10000 to 14999
  - 15000 to 19999
  - 20000 to 24999
  - 20000 to 24999
  - 25000 to 29999
  - 30000 to 34999
  - 35000 to 39999
  - 40000 to 44000
  - 45000 to 49999
  - Greater than or equal to 50000
 
  - ![image](https://github.com/user-attachments/assets/12e875f8-3523-4413-b6dd-be71f1cf5d41)

- Using the `COUNTIFS()` formula, counted how many successful, failed, and canceled projects were created with goals within the ranges listed above. Populated the `Number Successful`, `Number Failed`, and `Number Canceled` columns with these data points.

- Added up each of the values in the `Number Successful`, `Number Failed`, and `Number Canceled` columns to populate the `Total Projects` column. Then, using a mathematical formula, find the percentage of projects that were successful, failed, or canceled per goal range.

- Created a line chart that graphs the relationship between a goal amount and its chances of success, failure, or cancellation.

## Statistical Analysis
Most people would use the number of campaign backers to assess the success of a crowdfunding campaign. Creating a summary statistics table is one of the most efficient ways that data scientists can characterize quantitative metrics, such as the number of campaign backers.

For gaining an in-depth understanding of campaign backers, evaluated the number of backers of successful and unsuccessful campaigns by creating my own summary statistics table.

- Created a new worksheet <i>Summary Statistics</i>, creating one column for the number of backers of successful campaigns and one column for unsuccessful campaigns.

![image](https://github.com/user-attachments/assets/16035930-5860-43c1-bced-25ad405be186)

- Used Excel to evaluate the following values for both successful and unsuccessful campaigns:

  - The mean number of backers

  - The median number of backers

  - The minimum number of backers

  - The maximum number of backers

  - The variance of the number of backers

  - The standard deviation of the number of backers

<img width="870" alt="image" src="https://github.com/user-attachments/assets/1158c1d7-3aca-4d48-aa31-90b0616a82af" />

- Question: Does the mean or the median better summarizes the data?
  - Answer: The Mean summarizes the data more meaningfully due to the fact that there are outliers in successful campaigns whose number of backers significantly skew the mean to the right.
- Question: Use your data to determine if there is more variability with successful or unsuccessful campaigns. Does this make sense? Why or why not?
  - Answer: There is more variability in succesful campaigns because the standard deviation in the number of backers is greater than that for unsuccessful campaigns.
