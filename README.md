# nosql-challenge
The instructions for the challenge were as follows:
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

My Part 1 consisted of database and Jupyter Notebook set up I used the NoSQL_setup_starter.ipynb provided by my bootcamp for this section of the challenge.First, I imported the data provided in the establishments.json file from my Terminal. I named the database uk_food and the collection establishments. I copied the text I used to import the data from my Terminal to a markdown cell in my notebook. Within the notebook, I import the libraries I needed: PyMongo and Pretty Print (pprint). I then created an instance of the Mongo Client and confirmed that I created the database and loaded the data properly and completed the following:

        *Listed the databases I had in MongoDB and confirmed that uk_food is listed.
        *Listed the collection(s) in the database to ensure that establishments is there.
        *Found and displayed one document in the establishments collection using find_one and display with pprint.
        *Assigned the establishments collection to a variable to prepare the collection for use.

In Part 2, I updated the database. I used the NoSQL_setup_starter.ipynb for this section of the challenge.The instructions given detaled that the magazine editors had some requested modifications for the database before I could perform any queries or analysis for them. I was asked to make the following changes to the establishments collection:
            *An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database:
                    {
                        "BusinessName":"Penang Flavours",
                        "BusinessType":"Restaurant/Cafe/Canteen",
                        "BusinessTypeID":"",
                        "AddressLine1":"Penang Flavours",
                        "AddressLine2":"146A Plumstead Rd",
                        "AddressLine3":"London",
                        "AddressLine4":"",
                        "PostCode":"SE18 7DY",
                        "Phone":"",
                        "LocalAuthorityCode":"511",
                        "LocalAuthorityName":"Greenwich",
                        "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
                        "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
                        "scores":{
                            "Hygiene":"",
                            "Structural":"",
                            "ConfidenceInManagement":""
                        },
                        "SchemeType":"FHRS",
                        "geocode":{
                            "longitude":"0.08384000",
                            "latitude":"51.49014200"
                        },
                        "RightToReply":"",
                        "Distance":4623.9723280747176,
                        "NewRatingPending":True
                    }
        *Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields.

        *Update the new restaurant with the BusinessTypeID you found.

        *The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.

        *Some of the number values are stored as strings, when they should be stored as numbers.
            * I used update_many to convert latitude and longitude to decimal numbers.
            *I used update_many to convert RatingValue to integer numbers.


Part 3 holds the Exploratory Analysis portion of the project. In this scenario, Eat Safe, Love had specific questions they wanted me to answer, which would help them find the locations they wish to visit and avoid. I used NoSQL_analysis_starter.ipynb for this section of the challenge.I was also mindful of the following while exploring the dataset:

        *RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
                Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
        *The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.
