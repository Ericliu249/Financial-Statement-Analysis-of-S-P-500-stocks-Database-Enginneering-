# Financial Statement Analysis of S&P 500 stocks

- Author: Yang Liu, Jiawei Xue<br>
- E-mail: eric.liu.249@gmail.com<br>
          yliu249@stevens.edu
<br><br>
## Introduction<br>

Financial statement analysis is the process of analyzing a company's financial statements for decision-making purposes and to seek the undervalued stocks for investments. Financial statements record financial data, which must be evaluated through financial statement analysis to become more useful to investors, shareholders, managers, and other interested parties.

In this project, we attempted to use Mysql and financial statement analysis to achieve two goals.

First, we aimed to implement the value investing method, known as Warren Buffett's and Benjamin Graham's investment methodology, to find out which stocks to invest in. Value investing is an investment strategy where stocks are selected and traded for less than their intrinsic values. Using this investment strategy, we could find the opportunity to profit because most of the speculators on the market overreact to good and bad news, resulting in stock price movements that do not correspond with a company's long-term fundamentals. 

Second, we utilized the DuPont analysis to analyze a company’s ability to increase its return on equity. In other words, this model breaks down the return on equity ratio to explain how companies can increase their return for investors. The Dupont analysis looks at three main components of the ROE ratio: profit margin, total asset turnover, and financial leverage. Based on these three performance measures the model concludes that a company can raise its ROE by maintaining a high profit margin, increasing asset turnover, or leveraging assets more effectively.

## Data Sources<br>

We retrieved our datasets from Kaggle-New York Stock Exchange, a competition on the most famous data science community. 

The datasets in this Kaggle competition consisted three following files: 

*1.Securities.csv*: general information of each company information from EDGAR SEC databases, such as stock symbol, company name, industry, address, the first date that a company became a listedd company and the CIK number of each company (A Central Index Key or CIK number is a number given to an individual or company by the United States Securities and Exchange Commission. The number is used to identify the filings of a company, person, or entity in several online databases, including EDGAR). 

*2.Financial statements.csv*: Public companies’ financial statements' data from Nasdaq Financials. 

Financial statements is a formal record of the financial activities and position of a business, person, or other entity,it reports on a company's assets, liabilities, and owners equity at a given point in time, a company's income, expenses, and profits over a period of time, the changes in equity of the company during the stated period, and a company's cash flow activities, particularly its operating, investing and financing activities. 

*3.Prices.csv*: Historical stock data from Yahoo Finance, contains the information of stock symbol, transaction date, open price, close price, lowest price, highest price and the trasaction volume in one day.

## Data Model

We built the entity-relationship diagram (ER model for short) as our data model. An ER diagram describes how entities relate to each other. 

**Design reasoning**: 

(a)By drawing ER diagrams to visualize database design ideas, we had a chance to identify the mistakes and design flaws, and to make corrections before executing the changes in the database. 

(b)Considering that there may be some ambiguities or unnecessary processes if the users or other developers do not understand the database very well, we decided to present our data schema in a graphical form, which offers the users and developers a easier and more efficient way to manipulate and communicate. 

(c)By visualizing a database schema with an ERD, we have a full picture of the entire database schema. We can easily locate entities, view their attributes and to identify the relationships they have with others. These allows us to analyze an existing database and to reveal database problem easier. 

**Design method**: 

Our methodology when designing the ER diagram is to connect all the data we needed together and to implement this in the simplest way. The main table in the ERD is the securities table because it has unique values in the column of ticker_symbol and each row could be joined to other tables which also contain the column of ticker_symbol. The primary key in the securities table is ticker_symbol. 

For the tables of financial_statements and prices, as they do not have unique values in any column, we chose to use composite keys as their primary keys. The composite primary key of financial_statements is ticker_symbol and period_ending. The values of this combination in each row is unique. Similarly, the composite primary key of prices are symbol and date. The financial_statements uses ticker_symbol as its foreign key while prices uses symbol as its foreign key so that they can both refer to ticker_symbol, the primary key of securities. 

In summary, both the relationships between securities and financial_statements and between securities and prices are one to many relationships. 
