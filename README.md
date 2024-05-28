# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
Coded in Python 3.9.19 <br>

Complete the assignment as follows:

1. Explore API structure and generate Pandas dataframe from [CityBikes](https://citybik.es/) for bike stations in Redding, California. This city was chosen as the more remote location also allows will reduce the impact of the limited API calls and will allow for comparison of the quality of information returned from Foursquare and Yelp for a more remote location.

2. Connect to Foursquare and Yelp APIs to retrieve restaurants, bars, and landmarks from each bike station found in Part 1. Compare the quality of information provided by Foursquare and Yelp under the criteria of number of POIs, number of returned arguments, and value of arguments returned.

3. Combine the data from Part 1 and Part 2 into a new dataframe and visualize data. Create an SQLite database to store and validate the data. 

4. Build a regression model to show a relationship between the number of bikes and the characteristics of POIs in Redding with a regression model from Python's `statsmodels` module 


## Process
### Generating DataFrame of Bike Stations in Redding, CA with CityBikes API
Started with understanding the CityBikes API to pull the stations for Redding, which involved parsing through the networks to find the proper endpoint, and then parsing through the stations json to create a dataframe.

### Generating DataFrames of locations within 1km of each station with Foursqaure and Yelp APIs
First familiarizing with Foursqaure and Yelp API and pulling locations near each station from each source. After that, parsing and organizing the data into useful dataframes and comparing the result from both. 
<img src='https://i.imgur.com/Qw1AG5j.png'>


### Combining data from the different sources and performing EDA
Combinging the CityBikes data to the venues data, performing EDA by looking at some correlation matrices and some linear regression scatter plots of data. 
<img src='https://i.imgur.com/SYIQNUH.png'>

<img src='https://i.imgur.com/uao706h.png'>

### Created a SQLite database 
Created and SQLite databases from the data gathered from each API. Ran queries to create an combined data frame of bike stations and venues from both Foursquare and Yelp


### Building a regression model 
Set up a backward regression model using numerical data from the combined data frame of venues from Both APIs. 




## Results
A couple notable difference between the Foursquare and Yelp API:
* The Yelp API provide a much larger number of locations for each station, but the number of unique locations were nearly identical from Foursquare to Yelp. 
* Foursquare provides a couple extra elements not directly given by Yelp such as popularity and number of photos
* However, Yelp showed to have much more reviews than Foursquare, suggesting that many more people visit and contribute to Yelp. 

 <img src='https://i.imgur.com/6oHXQfm.png'>

<br>

### Regresstion model

Combining the data from the two APIs, a statistically significant model was found, showing a relationship between the distance and number of venues in a location to the number of bike slots available at each bike station:

 `11.9609-0.0897(venues)-0.0073(distanceIdistancenMeters)=(bikeSlots)`
 
 Where venues is number of POIs in area, distance is the distance in meters of the POIs to the bike station, and bikeSlots being the total bike capacity of a given bike station.

 <img src='https://i.imgur.com/84otJLd.png'>


## Challenges 
* CityBikes API documentation is really limited. Figured out that we need to call href endpoints to figure out what url to call to get desired information.
* API documentation in Yelp was missing some information. The Authorization key for the header parameters actually needs the text "Bearer " in front of the key, which is not shown in examples nor the emulator provided in documentation.
* Even with a lower population city like Redding, the limited API Calls and returned venues from Yelp were reached in multiple occasions, resulting in partially complete data. 
* Yelp does not return the highest level of category grouping, only the subgroup and alias. This made it difficult to parse through the different categories when querying for multiple overarching categories at once. The solution implemented was to seperate the api calls by category. This also helped minimize the impact of the call limits with multiple for each station. 
* Yelp API returned venues and locations that had a distance larger than the radius set and reason why is unclear, those locations were removed.


## Future Goals
* Return and specify fields to be called in citybikes instead of calling all and then reorganizing columns
* Get all venues and locations from yelp for each location instead of just the limited 50. Possibly by using multiple calls and different sorting. 
* Complete analysis of a city with more bike stations to have more data points for statstical analysis. 
* Organise and create a better shema for the SQLite database
* Rerun analysis for a city with more bike stations

## Additional Notes
Certain functions and blocks of code were adapted from material provided in Lighthouse Labs Data Science course material
