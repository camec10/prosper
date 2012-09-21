Prosper Repository
===
---

The purpose of this repository is to 
* consolidate my notes for future reference
* create an online backup
* document the process used to perform the analysis
* share code with the public


Possible Questions to Investigate
---
* What is the probability of default?
* What are the anticipated loan repayment amounts for each scheduled loan repayment date?
* What is the anticipated loss amount?
* What is the anticipated loss amount for which there's only a 95% chance of surpassing?
* What is the ultimate loss amount expressed as a ratio of the original loan amount?
* What is the anticipated number of months until default?
* What is the risk premium earned over the life of the loan?
* What is the anticipated term structure of interest rates?
* Which loans are anticipated to be 
	* profitable?
	* unprofitable?
	* paid off early?
	* sold in the Prosper secondary market?
	* fraudulent?

Possible Statistical Questions to Investigate
---
What is the probability distribution of the ...
* internal rate of return (IRR) of the loan
* net present value of loan amount
* default probability
* ultimate loss amount
* ultimate loss amount as a percent of original loan amount
* time until default
* term structure of interest rates


Note, these will typically be summarized by using a single number like the following:
* expected value 
* median or 50th percentile (the value in the distribution for which 50% of future observations will be less than)
* 95th percentile (the value in the distribution for which 95% of future observations will be less than)


Process Summary
---
* transfer data from prosper to local computer
* importing XML data into database
* prepare data
	* join (aka flatten or denormalize)
	* clean
	* create derived attributes
* summarize the data 
	* list data elements
	* create distributions (list of values and frequency of occurrence)
* build models
	* use regression analysis to predict continuous outcomes
	* use classification analysis to predict categorical  outcomes
	* use survival analysis to predict time until event outcomes
* evaluate model performance
* recalibrate models
	* create feedback-loop to train models


Data Sources
---
Main
* Prosper (e.g. loan amount, interest rate, term)
	http://www.prosper.com/tools/
	http://www.prosper.com/tools/DataExport.aspx
	http://www.prosper.com/Downloads/Services/Documentation/ProsperDataExport_Specification.pdf
	https://services.prosper.com/AuthDownload.aspx?file=daily

Supplemental
* Federal Reserve (e.g. money supply, default rates)
	* http://research.stlouisfed.org/fred2/
	* http://research.stlouisfed.org/fred2/sources
	* http://www.federalreserve.gov/econresdata/statisticsdata.htm
	* http://www.federalreserve.gov/releases/h15/data.htm
	* http://www.federalreserve.gov/datadownload/
* Bureau of Labor and Statistics (BLS) (e.g. unemployment, inflation)
	* http://www.bls.gov/
* Capital Markets
	* asset prices for equity, debt, real estate, etc
* Google Results
	* public records
	* Facebook
 
Future Data Enhancements:
* find additional public data sources

Models
---
Process Models
* discrete process
* collective risk
* individual risk

Statistical Models
* regression analysis
* classification analysis
* time until event analysis
* time series analysis

Unstructured Data Models
* association analysis
* text mining analysis

Future Modeling Enhancements:
* apply additional statistical models to the data


Optimization
---
Apply parallel processing for the following tasks:
* loading data
* building models
* applying models (i.e. scoring)
* querying data
* monitoring processes

Future Optimization Enhancements:
* develop faster methods to process the data

Documentation
---
* audio/video
* flow charts
* pivot tables and charts
* word documents
* spread sheets
* considerations:
	* online vs. offline
	* dynamic vs. static

Miscellaneous Notes
===
---
## Data Considerations:
* What are the data quality issues?
	* missing data
	* invalid data
	* inconsistent data
	* survivorship bias
	* left truncation bias
	* right censoring bias
* How is data entered into the Prosper database?
* How is data removed from the Prosper database?
* How is data updated in the Prosper database?
* What are the levels or hierarchies of the data?
* How is data aggregated?
* Which data elements have been made available?
* Which data elements need to be derived?
* Which attributes are constant through time (e.g. gender) and which change (e.g. balance)?


## Computing Considerations:
* notification (text messages and emails)
	* process status
	* error and exceptions
* validation and unit testing
	* data 
	* functions 
	* processes
* optimization
	* alter data types to minimize hard drive I/O
	* index tables
	* consider normalized vs. denormalied data issues
* documentation
	* package together misc code and utilities


References
===
---
Prior Research:
* http://www.prosper.com/welcome/marketplace.aspx
* https://www.lendingclub.com/info/statistics.action
* http://courses.media.mit.edu/2008fall/mas622j/Projects/CharlieCocoErnestoMatt/data/
* http://www.dataspora.com/2011/12/prosper-loan-data-part-2-social-network-analysis-what-is-the-value-of-a-friend/
* http://www.dataspora.com/category/r/
* http://courses.media.mit.edu/2008fall/mas622j/Projects/CharlieCocoErnestoMatt/#contents
* https://docs.google.com/viewer?a=v&q=cache:zdjpBmG2hrYJ:galitshmueli.com/system/files/ProsperREPORT.pdf+prosper+data+mining&hl=en&gl=us&pid=bl&srcid=ADGEESjbg2JgwM8O_G1O7DKhqgqb-gMEJXGV5jKrUqE3zBEMI9pWhwpT3fX1tHIb2qzMzr1vix0xQ7WuhKG_l-IZPIcChd0mA5Yi3gJcMug5CJYZv9Lx83uOYpxkZ1Jy0QWbV2Lknp3S&sig=AHIEtbTHx6IN5kMgN6WdnwfNUdLmKpgIjA


Import XML File into a Database:
* http://www.microsoft.com/en-us/download/details.aspx?id=11811
* http://www.red-gate.com/products/sql-development/sql-toolbelt/entrypage/xsd-0409
* http://xsd2db.sourceforge.net/
* http://www.rateladder.com/2008/02/22/convert-prosper-xml-to-csv/
* http://stackoverflow.com/questions/2628327/how-to-build-a-database-from-an-xsd-schema-and-import-xml-data
* http://stackoverflow.com/questions/5003835/best-way-to-import-xml-data-into-sql-server-express-2005
* http://support.microsoft.com/kb/316005
* http://www.sqlteam.com/forums/topic.asp?TOPIC_ID=97679
* http://stackoverflow.com/questions/467176/generating-sql-server-db-from-xsd
* http://msdn.microsoft.com/en-us/library/ms345117(v=sql.90).aspx
* http://www.rateladder.com/2007/01/02/import-prospercom-listing-loan-group-member-data-into-microsoft-sql-server-2000/




Software
---
Relational Database Software:
* SQL Server Express with Advanced Services
	* (contains the database engine, express tools, reporting services, and full text search)
	* http://www.microsoft.com/sqlserver/en/us/editions/2012-editions/express.aspx
	* http://www.microsoft.com/en-us/download/details.aspx?id=29062

* MySQL
	* http://www.mysql.com/downloads/mysql/

Statistical Computing Software:
* R
	* http://www.r-project.org/

General Purpose Programming Languages:
* Python
	* http://www.python.org/




Online Publishing Technologies to Investigate:
* .pdf files built in R
* .html files built in R
* Python notebooks
* SQL Server Reporting Services
* Pentaho
* WordPress


Misc Links:
* http://www.fedstats.gov/
* http://www.usa.gov/Topics/Reference-Shelf/Data.shtml
* http://www.economy.com/freelunch/
* http://data-mining.meetup.com/cities/us/tx/prosper/








































