# CAB Project 3 - Playing with E-commerce

We, an imaginary team of data analysts (for now just me and my laptop Myc), have been tasked with helping an equally imaginary subsidiary branch of a larger company break into the EU e-commerce market. The hopeful branch company, VS Electronics, wishes to expand into consumer electronics and have little experience with the e-commerce market.

Our project brief asked us to supply an overview of the e-commerce business model and potential competitors in the German and EU markets. We were asked to select a representative sample of competitors in the electronics sector for potential later analysis. Additionally, VSE requires an alternate method of storing their records, as the Excel file they have currently been using will become cumbersome in the long run. We will give VSE a rundown on the data they have supplied to us and on the basis of that data suggest several KPIs that might be of use to them.

We are waiting for a response from the VSE team for clarification of the following point(s):
* You wish to *"[...] focus on selling 'Laptops', 'Monitors', 'Headphones', 'Processors', etc."* and yet in the data we received there are also items which are not strictly consumer electronics. Consumer electronics usually include devices for entertainment, communication, and recreation ("black/brown goods") opposed to devices for housekeeping ("white goods). In the data set we received are also for example telescopes, which with their computer components could be considered black goods but are more often placed with optic equipment. Also in the set are food processors which are white goods and several items that would be considered accessories (selfie stick, camera grip, laptop bag, &c.) or computer components (RAM, flash cards, cooling paste, &c.). Is this something you wish to keep offering?

## Part 1 -- Tidying the tables
We have received one Microsoft Excel file containing five worksheets and 554417 rows per sheet. The rows were added sequentially so that row n on sheet A belongs to row n on sheet B, &c., this makes work much easier. We imported the Excel data to a pandas data frame in a Jupyter notebook and after cleaning exported the resulting data frame to a SQLite database. 

To see the process of our data cleaning and further information on the data, please see the comments in [the Jupyter notebook](read_in.ipynb).

Problems encountered in the data set:
* One StockCode may be shared by two ASINs. There are 657 instances of this, that makes it *not* a typo. Please ask logistics if the products with those ASINs also share the same shelf space. This makes it difficult to rearrange just one or update the number of products in the stores.
* There are 139315 records in the customer table (linked to the invoice table) where the CustomerID is not known. There needs to be a mark that makes the CustomerID unique even if that customer did not log in. If this is a technical issue, this needs fixing.
* A CustomerID may be linked to more than one country. This should not be. Have pity on your statistics.
* The invoice table needs a proper timestamp field with hours:minutes:seconds. There is one InvoiceNo with both 11 and 12 o'clock.
* There are products that cosist of different items and are listed in different product cetegories. Not really a problem per se, but there may be some improvement to be made here.

## Part 2 -- Designing the database
One self-imposed restriction was to not add any fields to the tables. It would have been much easier to just add a new field with a unique, sequential ID to the products table and be done with it.

In accordance with good database design we want to divide our data based on subject and reduce the data in the tables to the least common denomiator. This reduces redundant data and aids in ensuring the accuracy and integrity of the data as a whole as there is then only one point where a certain value can be changed, it does not appear elsewhere. Each table is required to have a primary and/or foreign key with which to link to other tables.

In SQLite the schema of the database looks like this:
![SQLite schema](/schemas/schema_sqlite.jpg?raw=true)

In MySQL it would look like this. The only difference is in the data types.
![MySQL schema](/schemas/schema_mysql.jpg?raw=true)

## Part 3 -- Feed the database and do some SQL queries
We already fed the database in the Jupyter notebook [read_in.ipynb](read_in.ipynb). The [SQL queries](sql_task_questions.txt) are not intended for VS Electronics but for internal use only.

## Part 4 -- Back to Python and Jupyter
We have reused most of the code from *read_in.ipynb* but instead of splitting the data into different tables we have combined it into one large data frame.<br />
There are no null strings or values in the new data frame, no duplicates, and strange symbols in the product title have been cleaned up.

This large data frame has been exported twice. One for use in Tableau and one for further analysis with pandas. Tableau does not like decimal separators as a period and requires them to be a comma.<br />
Because of their size these two files have not been uploaded to GitHub.

## Part 5 -- Visualisations
Pretty graphs.

## Part 6 -- Presentation

[Tableau public link](https://public.tableau.com/app/profile/jessica.baldwin/viz/CAB_ecom_dash_16524324413270/Dashboard2?publish=yes)
