# CAB Project 3 - Playing with E-commerce

We, an imaginary team of data analysts (for now just me and my laptop Myc), have been tasked with helping an equally imaginary subsidiary branch of a larger company break into the EU e-commerce market. The hopeful branch company, VS Electronics, wishes to expand into consumer electronics and have little experience with the e-commerce market.

Our project brief asked us to supply an overview of the e-commerce business model and potential competitors in the German and EU markets. We were asked to select a representative sample of competitors in the electronics sector for potential later analysis. Additionally, VSE requires an alternate method of storing their records, as the Excel file they have currently been using will become cumbersome in the long run. We will give VSE a rundown on the data they have supplied to us and on the basis of that data suggest several KPIs that might be of use to them.

We are waiting for a response from the VSE team for clarification of the following point(s):
* You wish to *"[...] focus on selling 'Laptops', 'Monitors', 'Headphones', 'Processors', etc."* and yet in the data we received there are also items which are not strictly consumer electronics. Consumer electronics usually include devices for entertainment, communication, and recreation ("black/brown goods") opposed to devices for housekeeping ("white goods). In the data set we received are also for example telescopes, which with their computer components could be considered black goods but are more often placed with optic equipment. Also in the set are food processors which are white goods and several items that would be considered accessories (selfie stick, camera grip, laptop bag, &c.) or computer components (RAM, flash cards, cooling paste, &c.). Is this something you wish to keep offering?

## Part 1 -- Tidying the tables
We have received one Microsoft Excel file containing five worksheets and 554417 rows per sheet. The rows were added sequentially so that row n on sheet A belongs to row n on sheet B, &c., this makes work much easier. We imported the Excel data to a pandas data frame in a Jupyter notebook and after cleaning exported the resulting data frame to a SQLite database. 

To see the process of our data cleaning and further information on the data, please see the comments in [the Jupyter notebook](read_in.ipynb).

Problems encountered in the data set:



## Part 2 -- Designing the database
loremipsum
[insert schema image here]

## Part 3 -- Feed the database and do some SQL queries

## Part 4 -- Back to Python and Jupyter
Do some exploratory data anaylsis with the sales database.

## Part 5 -- Visualisations
Pretty graphs.

## Part 6 -- Presentation

[Tableau public link](https://public.tableau.com/app/profile/jessica.baldwin/viz/CAB_ecom_dash_16524324413270/Dashboard2?publish=yes)
