# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
Coded in Python 3.9.19 <br>
LLMs was utilised for review of syntax and preview of data, noted in areas used. 

Complete the assignment as follows:

1. Explore API structure and generate Pandas dataframe from [CityBikes](https://citybik.es/) for bike stations in Redding, California. The city was chosen for due to the 

2. Connect to Foursquare and Yelp APIs to retrieve restaurants, bars, and points of interest (POI) from each bike station found in Part 1. Compare the quality of information provided by Foursquare and Yelp under the criteria of number of POIs, ratings, and other factors to be decided

3. Combine the data from Part 1 and Part 2 into a new dataframe and visualize data. Create an SQLite database to store and validate the data. 

4. Demonstrate a relationship and derive insights between the number of bikes and the characteristics of POI in Vancouver with a regression model from Python's `statsmodels` module 


## Process
### Generating DataFrame from CityBikes API
Started with understanding the CityBikes API to pull the stations for Redding, which involved parsing through the networks to find the proper endpoint, and then parsing through the stations json to create a dataframe.

### (your step 2)

### (your step 2)

### (your step 2)

### (your step 2)


## Results
(fill in what you found about the comparative quality of API coverage in your chosen area and the results of your model.)

## Challenges 
(discuss challenges you faced in the project)
* CityBikes API documentation is really limited. Figured out that we need to call href to figure out what url to call to get desired information.
* API documentation in Yelp missing information required. The Authorization key in header needs the text "Bearer " in front of the key.
* Limited API Calls from Yelp


## Future Goals
(what would you do if you had more time?)
