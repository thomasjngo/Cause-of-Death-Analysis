# Cause of Death Analysis (1990-2019)
Analyzes the common causes of death internationally from 1990 to 2019.

## Project by Grant G., Justin B., Karuna K., Harleen K., Thomas N., and Joseph C.

# Data Interception / Initial Dive
We imported the Causes of Death CSV data set and initiated data cleaning and preparation tasks, including renaming columns, filtering columns, and changing data types. Next, we merged the following three data sets: the U.S. Foreign Aid data set, the Population data set, and the Geographic data set. After merging each data set, we used the same data-cleaning process to create different data frames to answer our questions.

# Top 5 and bottom 5 Causes of Death Analysis
Using the data from the merged data set of cause_aid_pop_df we performed a sum() fucntion acroos the columns that were causes of death from 1990-2019. This created a new df that had the total amount of deaths caused by each specific disease. We then sorted them by using the sort_values function which gave us the a list fo the causes of deathn from the most deadly to the least deadly. To just take the top 5 and bottom 5 we filtered the df to only give the first 5 and the last 5. These two new dfs were then plotted as a pie chart and a bar graph to visualize the top and bottom 5 casues of death from the period of 1990-2019.

# Normalizing the Data to Show Death per Capita 
We wanted to normalize the data based on population so that wecould compare them not just soley on raw numbers. To do this a causes_pop_df was created by merging the population to the causes of death csv. To get this desired df we had to iterate through the causes_pop_df and divide each death count of each year in each country by the countrys specific population then add that calculated value to a new columns of the df. Once this was completed the new df was filtered to only include per capita data and the population of each country during the specified year. Once this new df was created a fucntion was also created so that a specific country code could be plugged in and the fucntion would return a df that had the top 5 causes of death in that country over the 30 year period(1990-2019). A similar function was also created that would return the bottom 5 causes of death for a specifc country code over the 30 year period. This fucntion made it very easy to create different visualition based on death per capita for a specific country.

# Checking whether foreign aid receiving affects causes of death
Here we are creating dataframes for High aid receving contries and Low aid receving contries with top and bottom death causes. First,we started with top causes of death in high and low aid receving countries,so that, 'Current Amount of Aid Given by US ($USD)' column in the main dataframe 'cause_aid_pop_df' is sorted in the descending order and found the highest aid receving countries. Created a dataframe using the top aid receving countries and top causes of death as 'filter_top_df'. Filtered this data frame with years. Lastly performed  grouped by 'Year' function on this dataframe with mean as the aggregation function and got the average top cusess of  death in high aid receving countries over year dataframe as 'top_aid_df'.The same logic applied in finding the average death in low aid receving countries over year by sorting the 'Current Amount of Aid Given by US ($USD)' colomn in acsending order and got the dataframe as 'bottom_aid_df'. Visualized both 'top_aid_df' and 'bottom_aid_df' using line plot. The above steps are repeated for creating average least causes of death in high and low aid receving countries over yers by using the bottom_causes. The main conclusions are as follows: 1-High Aid Receiving Countries: the data suggests that US aid efforts had a non-trivial, positive impact on causes of death arising from public health-related factors  (respiratory infections and diarrheal disorders). 2-Low Aid Receiving Countries: the data suggests that the reduction/elimination of US aid had a tremendous impact from 2000 - 2019.

# Finding percentage of deaths in high and low income countries.
First find the percentage of death of deaths in different countries over year as 'Cause_aid_pct_df'. Grouped the dataframe by 'Country Income Category' column and named the dataframe as 'income_death_pct_df'. Performed transpose function on the 'income_death_pct_df' dataframe to get the income catogory as columns. We then plotted two bar graphs,one with y axis as 'High Income Country' for finding "Percetage death in High income countries" and the other with y axis as 'Low Income Country' for finding "Percetage death in Low income countries". The main conclusions from the visualization are: 1-  Cardiovascular diseases and neoplasms are a worldwide problem. 2- Deaths that can be attributable in large part to public health conditions (diarrheal, respiratory) are twice as high in low income countries than they are in high income countries.

# Taking an In Depth Look at Two Specific High, and Low Income Nations, and Thier Top Causes of Death 
With the data grouped as we would like for examining a single countries top and bottom causes of death via our defined bottom_death_of_country and top_death_of_country function, We looked at the trend in the top and bottom causes of death in two high income nations(USA, Japan), and two low income nations (Afghanistan, Nigeria) across the 30 years of entries. In the high income nations, the top two deaths Cardio vascular disease and Neoplasm deaths were the same, but differently correlated in the two nations, suggesting different cultural precursors. In Japan, the lowest deaths were dominated by exposure to forces of nature, with a spike in years correlated to extreme life off loss weather events. In America, bottoms deaths have maintained at a low level(spikes in conflict and terrorism deaths/exposure to forces of nature - 911, 2001 / Hurrican Katrina, 2005), and are dominated by drug use deaths, with an exponential increase in amount over the 30 years. Low income nations saw differences in top causes of death. In Afghanistan, the top deaths saw a deacrease in prevelance over the years, and were dominated by neoplasms and diarrheal deaths. These causes of death had a weak corrleation suggesting they have different starting causes, but suggest a basis of innedequate personal heath resources for these to be occuring at the frequency they are. In Nigeria, the top deaths were caused by lower respiratory infection and neonatal disorder deaths. These deaths were strongly correlated to eachother, suggesting an influence of the availible surrounding resources to combat major heath issues in that country and other third world countries like viral infections (malaria) (adaquate prenatal treatment). Both of the countries bottom causes of death were dominated by conflict and terrorism, which saw spikes in the years these nations experienced war. 

# Geographical Anaylsis
Using the information from Google's coordinate spreadsheet (countries.csv), we created a new data frame "country_totals" to group the data by country and sum up the 30 year data from our existing "cause_aid_pop_df" dataframe. We iterated through the values in the "Country/Territory" column of country_totals dataframe and checked if the country name exists in the "name" column of the google spreadsheet. If there is a match, it will retrieve the latitude and longitude columns from the Google spreadsheet and add it to the "country_totals" dataframe. The final results are exported to "results.csv" in the resources folder.

With the corresponding coordinate data, we implemented two hvplots to map the total malaria deaths and total aid given per country over the 30 year span. The scaling was adjusted so that each point was legible on the map. The stats are also viewable when you hover over each point.
