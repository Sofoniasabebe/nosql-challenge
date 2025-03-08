# nosql-challenge

# Eat Safe, Love

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating.
The task in this challenge is to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## Part 1: Database and Jupyter Notebook Set Up

In this part, the following tasks were completed:

1. I imported the data provided in the establishments.json file from the Terminal. I named the database uk_food and the collection establishments. I copied the text I used to import the data from the Terminal to a markdown cell in the setup notebook.
2. Within your notebook, I imported the libraries needed: PyMongo and Pretty Print. 
3. Created an instance of the Mongo Client.
4. Confirmed that I created the database and loaded the data properly:
* Listed the databases I have in MongoDB. Confirmed that uk_food is listed.
* Listed the collection(s) in the database to ensure that establishments is there.
* Located and displayed one document in the establishments collection using find_one and display with pprint.
5. Assigned the establishments collection to a variable to prepare the collection for use.

## Part 2: Update the Database

The following changes were made to the establishments collection:
1. Added the information of a new restaurant named "Penang Flavours" to the database. 
2. Retrieved the BusinessTypeID for "Restaurant/Cafe/Canteen" and returned only the BusinessTypeID and BusinessType fields.
3. Updated the new restaurant with the BusinessTypeID retrieved.
4. The magazine is not interested in any establishments in Dover, so I checked how many documents contain the Dover Local Authority. Then, I removed any establishments within the Dover Local Authority from the database, and checked the number of documents to ensure they were deleted.
5. Some of the number values are stored as strings, when they should be stored as numbers.
* Used update_many to convert latitude and longitude to decimal numbers.
* Used update_many to convert RatingValue to integer numbers. 

## Part 3: Exploratory Analysis

Eat Safe, Love had specific questions they wanted answers to, which would help them find the locations they wish to visit and avoid.
I ecplored the database as follows and found answers that can be provided to the magazine editors. 

1. I identified which establishments have a hygiene score equal to 20.
2. I identified which establishments in London have a RatingValue greater than or equal to 4; I used $regex as part of my search. 
3. The top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant I added, "Penang Flavours" were identified. 
4. Then, I discovered how many establishments in each Local Authority area have a hygiene score of 0. I then sorted the results from highest to lowest, and printed out the top ten local authority areas. I used the aggregation method to answer this.

**References**

*UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).*
