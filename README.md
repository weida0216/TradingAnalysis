# Hollywood Stock Exchange Trading Analysis

Hollywood Stock Exchange (HSX) is the world's leading entertainment stock market. At HSX.com, 
visitors buy and sell virtual shares of celebrities and movies with a currency called the Hollywood Dollar®. 
My team and I were tasked to trade on HSX for a course of 2 months and evaluate our trading performance as part of an assignment in class. 

## Specifications
Your manager would like you to develop a single, interactive, dashboard to assess your performance 
as individual traders on the HSX, as well as monitor the overall investment portfolio. 
You should include relevant information about securities held (currently or previously), positions, the 
current market value and cost basis of those positions, trades made, realised and unrealised gains and 
losses, historical prices of securities, etc. 
To correctly calculate gains/losses, cost basis, and market value, you will need to develop two Python 
programs that each output relevant data to include in the data source for your dashboard. 

## Cost Basis Calculation

For positions that were opened with a single trade, the unit cost base PC is simply the original price 
when bought or shorted. For more complex sequences of trades however, we need to calculate a 
proper moving weighted average with each transaction. 
Each time we make an additional trade against the same position, we need to recalculate the cost 
basis C, weighted average unit cost PC, as well as the full cost FC and weighted average unit full cost 
PFC (the last two include commissions). 
If we extend a position (buy or short an additional quantity over what we’ve already bought or 
shorted) then we need to add to the cost basis and full cost, then recalculate both the weighted 
average unit cost PC and unit full cost PFC. 
If we partly close out a position by Covering or Selling Q securities, then we need to reduce the cost 
basis by Q * Pc. Since we have not incurred additional costs, we need not recalculate PC. We also 
realise a gain or loss at this point, calculated as the proceeds from the Sell or Cover minus Q * PFC. 
If we fully close out a position, all gains or losses are fully realised (same calculation). 
If we later reopen the position, we restart all cost calculations the same as if it were the first trade for 
that security. 

To correctly determine the cost base and any realised gains/losses, I wrote a 
Python program that correctly recalculates for each historical trade in sequence, outputting a 
ten-column CSV file with the last set of values, current as per the last recorded trade, for every 
security traded by every trader on your team. 

The script can be located here: https://github.com/weida0216/TradingAnalysis/blob/main/WebScraping.ipynb
## Market Value and unrealised gains and losses

To calculate the market value of open positions, we use the following formulae: 
Long positions: Q * PM 
Short positions: Q * (2PC – PM) 
Where Q is the current quantity of securities held, and PM is the latest price for the security. 
The unrealised gain or loss for an open position, is the current market value of that position less the 
full cost of any remaining securities held. Note that these calculations require cost basis information, 
as well as latest prices from the HSX web site. 

## Web Scraping for latest price of securities

I wrote a second Python program that scrapes the latest prices from the HSX 
website for each security with a remaining open position (or all active securities), outputting a 
two-column CSV file with security symbol and current price for each security. 

The script can be located here: 
https://github.com/weida0216/TradingAnalysis/blob/main/WebScraping.ipynb

