# Netflix_Content_Report
Taking a dataset of all titles on Netflix and evaluating its data

For this project, I downloaded the initial dataset from Kaggle

Source : https://www.kaggle.com/shivamb/netflix-shows

Creating new file and Uploading the Dataset :

    -> Open Power BI Desktop and create a new file, named Netflix.pbix
    -> Get Data from file netflix_titles.csv downloaded from source 
    -> Click Transform Data to open Power Query Editor    

Cleaning the Dataset : 

  -> The dataset has 7787 rows and 12 columns:
        ) show_id: unique id of each show
        ) type: The category of a show, can be either a Movie or a TV Show
        ) title: Name of the show
        ) director: Name of the director(s) of the show
        ) cast: Name of actors and other cast of the show
        ) country: Name of countries the show is available to watch on Netflix (First country is the Origin place of Show)
        ) date_added: Date when the show was added on Netflix
        ) release_year: Release year of the show
        ) rating: Show rating on netflix
        ) duration: Time duration of the show
        ) listed_in: Genre of the show
        ) description: Some text describing the show    
    -> In View Ribbon, check Column Quality and Column Distribution.
    -> Since column "director" and "cast" has varying values with multiple missig values, remove those columns.
    -> Columns "rating" and "date_added" have very few missing values, so we remove the rows with missing values in those columns. (Or alternatively, fill those columns with actual values if you want to use entire dataset) 
    -> Fill "country" column's missing values with either the mode of column or "Unspecified"
    -> Even though "description" column has no missing value you can choose to either retain it but hide it in report view or delete the column to improve efficiency of database 
    -> Using Extract and Text before Delimiter, extract value in country column before ","(comma) and delete the original column, keeping new column as "Country". 
    -> Similarily, extract data from before "," in column "listed_in" as "Genre". 
    -> Using Conditional Column, make a column called "Category" for sorting show's target audience via "rating" coumn values
    -> Using Column from Examples, extract "Year Added" from "date_added" 
    -> Using extract in succession, extract No. of Seasons and Length of Movies in Numeric format as "Duration"
    -> Extract text after delimiter "s" from "show_id" as "Show ID" and change its type to Whole Number
    -> Now that data is cleaned, we have following columns :
        ) Show ID
        ) Type
        ) Title
        ) Year Added
        ) Date Added (Not Required)
        ) Release Year
        ) Category
        ) Rating (Not Required)
        ) Duration 
        ) Country
        ) Genre
    
Creating Final Report :

    -> Rename first page as "Content Overview"
    -> Add new Slicer on page and add Category in its field
    -> Edit Font Size to your preference (Slicer Header - 20, Items - 14)
    -> Add Pie Chart to Report with Legend to Type and Values to Title
    -> Add Line Chart with Types as Legend, Count of Titles as Values and Year Added as Axis
    -> Create new page and name it "Movies"
    -> Add Slicer with Year Added as field
    -> Add a Question Field just below the Slicer.
    -> Add a line chart with Count of Titles as values and Duration as Axis, labelled "Distribution of Title by Runtime"
    -> Finally, add a bar chart with Genre as axis and Count of Title as Values
    -> Duplicate "Movies" page and rename it to "TV Shows"
    -> Change Line Chart to depict no. of Seasons and sync slicers on both pages
    -> Create new page and name it as "World Distribution"
    -> Add Map on page, add Country to Location, Type to Legend and Count of Title to Size

Finally, Publish the Report on powerbi.com for your organization
