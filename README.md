# Common-Causes-of-Death-
Analyze common causes of death internationally and develop conclusions. 

# Geographical Anaylsis
Using the information from Google's coordinate spreadsheet (countries.csv), we created a new data frame "country_totals" to group the data by country and sum up the 30 year data from our existing "cause_aid_pop_df" dataframe. We iterated through the values in the "Country/Territory" column of country_totals dataframe and checked if the country name exists in the "name" column of the google spreadsheet. If there is a match, it will retrieve the latitude and longitude columns from the Google spreadsheet and add it to the "country_totals" dataframe. The final results are exported to "results.csv" in the resources folder.
Now that every country in our dataframe has coordinate data, we implemented two hvplots to map the total malaria deaths and total aid given per country over the 30 year span. The scaling was adjusted so that each point was legible on the map. The stats are also viewable when you hover over each point.
