![image](https://github.com/10H-K/Crowdfunding_ETL/assets/152667250/e9b17252-3114-42e8-8e5d-1b825df2b61f)


# Building ETL Pipeline Using Python & Pandas

## Overview ##

The objective of this project is to build an extract, transform, and load (ETL) pipeline using Python, Pandas, and Python dictionary methods to extract and transform data. After the data is transformed, four CSV files will be created. The CSV file data will then be used to create an entity relationship diagram (ERD) and table schema. Finally, the CSV file data will be uploaded into a Postgres database.

## Process ##

A) Extract The crowdfunding.xlsx Data:
  1. Importation of dependencies (Pandas and NumPy)
  2. Read the data in the excel file 'crowdfunding.xlsx' into a Pandas DataFrame
  3. Get a brief summary of the crowdfunding_info_df DataFrame

B) Create The Category And Subcategory DataFrames:
  1. Get the crowdfunding_info_df columns
  2. Assign the category and subcategory values to separate category and subcategory columns
  3. Get the unique categories and subcategories in separate lists, print both lists
  4. Get the number of distinct values in the categories and subcategories lists
  5. Create numpy arrays from 1-9 for the categories and 1-24 for the subcategories
  6. Use a list comprehension to add "cat" to each category_id
  7. Use a list comprehension to add "subcat" to each subcategory_id
  8. Create a category DataFrame with the category_id array as the category_id and categories list as the category name
  9. Create a subcategory DataFrame with the subcategory_id array as the subcategory_id and subcategories list as the subcategory name
  10. Display category DataFrame and subcategory DataFrame
  11. Export category DataFrame and subcategory DataFrame as CSV files

C) Create Campaign DataFrame:
  1. Create a copy of the crowdfunding_info_df DataFrame named campaign_df
  2. Rename the blurb, launched_at, and deadline columns
  3. Convert the goal and pledged columns to a `float` data type
  4. Check the datatypes
  5. Format the launched_date and end_date columns to DateTime format
  6. Merge the campaign_df with the category_df on the "category" column and the subcategory_df on the "subcategory" column
  7. Drop unwanted columns
  8. Export the DataFrame as a CSV file

D) Extract The contacts.xlsx Data
  1. Read the data into a Pandas DataFrame, using the header=3 parameter when reading in the data

E) Create The Contacts DataFrame, Using Pandas
  1. Iterate through the contact_info_df and convert each row to a dictionary
     - Iterate through each dictionary (row) and get the values for each row using list comprehension
     - Append the list of values for each row to a list
  4. Print out the list of values for each row
  5. Create a contact_info DataFrame and add each list of values, i.e., each row to the 'contact_id', 'name', 'email' columns
  6. Check the datatypes
  7. Create a "first"name" and "last_name" column with the first and last names from the "name" column
  8. Drop the contact_name column
  9. Reorder the columns
  10. Check the datatypes one more time before exporting as CSV file
  11. Export the DataFrame as a CSV file

---

# Create The Crowdfunding Database

## Overview ##

Inspect the four CSV files created above, and then sketch an entity relationship diagram (ERD) of the tables by using QuickDBD.

<img width="1384" alt="Crowdfunding_ETL_ERD" src="https://github.com/10H-K/Crowdfunding_ETL/assets/152930492/2e41a12b-7061-43d5-acd2-cad887288ccd">

## Process ##

A) Create The Crowdfunding Database:
  1. Use the information from the ERD to create a table schema for each CSV file
  2. Save the database schema as a Postgres file named crowdfunding_db_schema.sql
  3. Create a new Postgres database, named crowdfunding_db
  4. Using the database schema, create the tables in the correct order to handle the foreign keys
  5. Verify the table creation by running a SELECT statement for each table
  6. Import each CSV file into its corresponding SQL table
  7. Verify that each table has the correct data by running a SELECT statement for each

