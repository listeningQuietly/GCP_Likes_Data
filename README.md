GCP_Likes_Data

Last week I mentioned considering down stream customers might like to make pretty graphs.
Well Google Cloud Platform (GCP) likes data and can make pretty visuals that can be easily shared.
So what happens if we take our new csvs (Silly and Original) and upload them in gsheets?
We find out the CSVs only have 2 attributes: Keys and Values, which is not great for visuals because Values has multiple data points inside it.
After splitting the non-atomic Values and replacing all the parenthesis with nothing, we have successfully ETL'ed our data to the GCP.
The entire process takes less than 2 minutes, but I imagine doing it the first time would require a little meandering and would take an additional 10 minutes of learning where the buttons are.

Anyway, we can now make Pivot tables and Graphs with our data!
Which is great until you try testing the relationships and realize the Category variable (the one added by the processing) won't update.
That is because there is no relationship between Attributes 1, 2,and 3 and Category.
That only existed while processing the raw data, which is really unfortunate because that means our pivot tables and graphs will all be inaccurate if we manipulate any of the data points, even accidentally.
I recommend testing this yourself by taking a copy of the gSheet I provided below and altering the data in the highlighted cells.
Testing letters seems to throw an error sometimes, which is weird given these were both processed via IF logic but pretty graphs can be twitchy.

This is far from optimal. If we update the data, the category and infographics should also update.
But that means we will have to create in gSheets a similar process to what our process was before ETL'ing the outputs.
And if we're going to do that, we might as well process the raw data in gSheets too and save ourselves pre-processing and ETL'ing work.
And with that third tab (Raw_3Attributes), may I present to you a spreadsheet version of,"How else can I mimic that optimized SQL process?"

You can see in column E I am using IF and =1 logic and there is no output if all conditionals are false, so the pivot table and charts won't represent the (FALSE) row.
This is nice and easy and pretty and quick to put together, but if you have experience with MS Excel, you probably realized the pivot table and graph update as soon as the data updates.
That means this is updating the products every time a cell is updated, which makes it processing-expensive - all of column E and the infographics are rerunning each cell update.
We don't see how bad this could get because these example data sets are small and we only have 3 attributes to categorize.

This final detail brings me back to the one con of the optimized SQL process: 'The syntax is tedious to expand.'
"What would it look like if our data set is 126 times as big AND we are sorting by 10 attributes?"

In the fourth tab, you'll see it results in more than 1000 Categories to logically path through (1024 to be exact).
Coding the structure took days due to human error, which was unavoidable because even AI tools refused to produce >1000 lines of code.
I can't say I blame them. It is tedious.
Enjoy the slower updates.
