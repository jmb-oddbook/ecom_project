# CAB Project 3 - ~~Playing with~~ E-commerce

## Description
We, an imaginary team of data analysts (for now just me and my laptop Myc), have been tasked with helping an equally imaginary subsidiary branch of a larger company break into the EU e-commerce market. The hopeful branch company, VS Electronics (VSE), wishes to expand into consumer electronics and have little experience with the e-commerce market.

Our project brief asked us to supply an *overview of the e-commerce business model* and potential competitors in the German and EU markets. We were asked to select a representative sample of competitors in the electronics sector for potential later analysis. Additionally, VSE requires an *alternate method of storing their records*, as the Excel file in which they have stored their web scraped data will become cumbersome in the long run. For this we have designed an *SQLite database*. We will give VSE a *rundown on the data they have supplied* to us and on the basis of that data *suggest several KPIs* that might be of use to them. At the end of the project we have created a *Tableau dashboard* so that VSE can continually monitor their sales performance (providing a data pipeline is set up to keep the data up to date).


## Installation
No installation necessary. Just run the Jupyter notebooks. Please note that the cleaned and concatenated data (csv files) have not been uploaded to GitHub because of their size. You should be able to recreate them easily enough using [the *read_in* Jupyter notebook](read_in.ipynb). There are extensive comments in the notebook.


## Table of Contents
If you want to get into the nitty gritty stuff, please read on. Also do not forget to take a look into the Jupyter notebooks, they contain more comments.

- [Overview of e-commerce model](#mmm)
- [Tidying the tables](#mmmm)
- [Designing the database](#mmmm)
- [Visualising the data with Python](#mmmmmm)
- [Tableau dashboard](#mmmmm)
- [List of deliverables](#mmmmm)


### Overview of e-commerce model

To do: Summarise the overview in the presentation.

For more information please check the presentation files in the folder of the same name.


### Tidying the tables
We have received one Microsoft Excel file containing five worksheets and 554_417 rows per sheet. The rows were added sequentially so that row n on sheet A belongs to row n on sheet B, &c., this makes work much easier. We imported the Excel data to a pandas data frame in a Jupyter notebook, concatenated the sheets, and after cleaning exported the resulting data frame to a SQLite database.

To see the process of our data cleaning and further information on the data, please see the comments in [the Jupyter notebook](read_in.ipynb).

Problems encountered in the data set:
* Products data contains items which are not strictly consumer electronics, i.e. devices for entertainment, communication, and recreation ("black/brown goods"). Also included were telescopes (borderline) and food processors which are white goods and several items that would be considered accessories (selfie stick, camera grip, laptop bag, &c.) or computer components (RAM, flash cards, cooling paste, &c.). 
* One StockCode may be shared by two ASINs. There are 657 instances of this, that makes it *not* a typo. Please ask logistics if the products with those ASINs also share the same shelf space. This would make it difficult to rearrange just one or update the number of products in storage.
* There are 139_315 records in the customer table (linked to the invoice table) where the CustomerID is not known. There needs to be a mark that makes the CustomerID unique even if that customer did not log in. If this is a technical issue, this needs fixing.
* A CustomerID may be linked to more than one country. This should not be. Have pity on your statistics.
* The invoice table needs a proper timestamp field with hours:minutes:seconds. There is one InvoiceNo with both 11 and 12 o'clock, perhaps the order was placed just as the clock turned 12.
* There are products that consist of different items (e.g. keyboard+mouse) and are listed in different product cetegories. Not really a problem per se, but there may be some improvement to be made here.


### Designing the database
One self-imposed restriction was to not add any fields to the tables. It would have been much easier to just add a new field with a unique, sequential ID to the products table and be done with it.

In accordance with good database design we want to divide our data based on subject and reduce the data in the tables to the least common denominator. This reduces redundant data and aids in ensuring the accuracy and integrity of the data as a whole as there is then only one point where a certain value can be changed, it does not appear elsewhere. Each table is required to have a primary and/or foreign key with which to link to other tables.

In SQLite the schema of the database looks like this:
![SQLite schema](/schemas/schema_sqlite.jpg?raw=true)

In MySQL it would look like this. The only difference is in the data types.
![MySQL schema](/schemas/schema_mysql.jpg?raw=true)

The [SQL queries](sql_task_questions.txt) in this project file are not intended for VS Electronics but for internal use only.


### Visualising the data with Python
We reused most of the code from *read_in.ipynb* in a [new Jupyter notebook](ecom_eda.ipynb) but instead of splitting the data into different tables suitable for a database we have combined it into one large data frame.

There are no null strings or values in the new data frame, no duplicates, and strange symbols in the product title have been cleaned up.

As a separator you can specify the comma that Tableau prefers when you connect the csv file with Tableau.

Because of their size these two files have not been uploaded to GitHub.

To do: add some visualisations here with explanations.

[Visualisations notebook](ecom_viz.ipynb)


### Tableau dashboard
[Tableau public link](https://public.tableau.com/app/profile/jessica.baldwin/viz/CAB_ecom_dash_16524324413270/Dashboard2?publish=yes)


### List of deliverables
