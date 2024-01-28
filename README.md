# nosql-challenge

## Background
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## Objectives
This Challenge is divided into three parts:

    1. Create database, form a connection to the database and college in a Jupyter Notebook
    2. Update certain records and fields within the database collection
    3. Exploratory Analysis

### [Database and Collection Creation](Starter_Code/NoSQL_setup_starter.ipynb)

Create, and import the data into, the database. Followed by connecting to the MongoDB a Jupyter Notebook and PyMongo:

- Using the [establishments.json](Starter_Code/Resources/establishments.json) data file provided, use the 'mongoimport' function in a terminal to create a database named 'uk-food' and a collection 'establishments' to import the documents.
    - ``` mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json ```
- In a jupyter notebook, import the required libraries
    - PyMongo
    - Pretty Print (pprint)
- Create an instance of the Mongo Client.
- Confirm that you created the database and loaded the data properly:
    - List the databases you have in MongoDB. Confirm that 'uk_food' is listed.
    - List the collection(s) in the database to ensure that 'establishments' is there.
    - Find and display one document in the establishments collection using 'find_one' and display with 'pprint'.
- Assign the 'establishments' collection to a variable to prepare the collection for use.

------

### [Update Documents and Field Datatypes](Starter_Code/NoSQL_setup_starter.ipynb)

Within the jupyter notebook previously created, develop the code to add a new document, update fields, delete un-required documents and alter specific field's datatypes:

- Add a new document for a recently opened restaraunt using the following data:
    ```
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
    ```

- Find the 'BusinessTypeID' for "Restaurant/Cafe/Canteen" and return only the 'BusinessTypeID' and 'BusinessType' fields.
- Update the new restaurant with the 'BusinessTypeID' you found.
- The magazine is not interested in any establishments in "Dover", so check how many documents contain the "Dover" Local Authority. Then, remove any establishments within the "Dover" Local Authority from the database, and check the number of documents to ensure they were deleted.
- Some of the number values are stored as strings, when they should be stored as numbers.
    - Use 'update_many' to convert 'latitude' and 'longitude' to decimal numbers.
    - Use 'update_many' to convert 'RatingValue' to integer numbers.

------

### [Exploratory Analysis](Starter_Code/NoSQL_analysis_starter.ipynb)

With the database documents prepared, conduct some exploratory analysis on the database to provide some high level insights:

    For each question, provide the following information, unless stated otherwise (visible within the jupyter notebook):
        - Use 'count_documents' to display the number of documents contained in the result.
        - Display the first document in the results using 'pprint'.
        - Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows.

## References

| Reference Name | Description |
|----------------|-------------|
| [UK Food Standards Agency](https://www.food.gov.uk/) | UK food hygiene rating data API. [https://ratings.food.gov.uk/open-data/en-GB](https://ratings.food.gov.uk/open-data/en-GB).<br/> *Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8)*.  |
