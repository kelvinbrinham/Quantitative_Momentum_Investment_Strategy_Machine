# Quantitative_Momentum_Investment_Strategy_Machine
***Work in Progress***

Summary: This tool takes investment inputs and analysis stocks to find the ones with the most high-quality momentum. The code then produces an output order spreadsheet outlining which and how many stocks to purchase.


Scripts:

main.py - Here we import the Momentum_strategy class and use the tool

Momentum_strategy_class.py - Contains the class which performs the analysis and function of the tool AND API KEY

Accessory_scripts/Checking_API_Accepted_Tickers.py - Checks which tickers (stocks) are supported by the IEX API and saves them to a JSON file list_of_tickers_supported.json. This script needn’t be used but I included it for completeness so you can see where list_of_tickers_supported.json came from.



Files:

S&P500_Stocks.csv - Contains the stock tickers in the S&P500 index. I found this online and included it as an example input.

FTSE100_Stocks.csv - Contains the stock tickers in the FTSE100 index. I found this online and included it as an example input.

list_of_tickers_supported.json - Contains the stock tickers which are supported by the IEX API I use.

OUTPUT/Order_sheet_EXAMPLE.xlsx - Example output order sheet that the tool produces.



IMPORTANT:
The API key I use is private. It is stored in a file on my local machine and loaded at the beginning of the Momentum_strategy class in Momentum_strategy_class.py (line 22). THIS MUST BE CHANGED TO ACCEPT YOUR IEX API KEY.


Description of analysis:
The tool analysis two characteristics of stocks. The mean 1-Day momentum (the daily percentage change in stock price) for the year to date (YTD); and, ‘Momentum Hit Ratio (MHR)’. I define MHR as the fraction of days within the YTD in which the share increased in price. This introduces a measure of the quality of momentum. The tool cuts off stocks with an MHR below a user-defined value and then picks the stocks with the highest mean 1-Day momentum. 


Instructions for use (please read Description of analysis first):
Note: All currency is USD

1. Initialise the Momentum_strategy class with the amount you want to invest and the number of shares you wish to buy. E.g. my_strategy = Momentum_strategy(CASH_TO_INVEST, NUMBER_SHARES_TO_BUY)
2. Utilise the Order_Sheet() class function like so:

my_strategy.Order_sheet(MOMENTUM_HIT_RATIO: float, INDEX_FILE: str, TICKER_TAG: str, OUTPUT_FILE_PATH: str, FRACTIONAL_SHARES: bool)

MOMENTUM_HIT_RATIO = The minimum MHR needed for a stock to be ordered
INDEX_FILE = The file path for the .csv file containing the stocks in the desired index
TICKER_TAG = The tag for the ticker column in the INDEX_FILE. E.g. it is ’Symbol’ in the included S&P500_Stocks.csv file and ‘ticker’ in the included FTSE100_Stocks.csv file
OUTPUT_FILE_PATH (default: OUTPUT/Order_sheet.xlsx) = File path for output order spreadsheet
FRACTIONAL_SHARES (default: False) = Set True to allow the order of fractional shares, False otherwise.  


Future:
There are many improvements I can envisage, here are just a few:
- Increase the complexity of analysis with extra metrics
- A portfolio system using OOP which keeps track of stocks purchased and their returns etc. (although there are many apps for this of course)
- Add extra user choice (such as 1-Month momentum etc.)




