Some comments on Quote Sources: where we get our quote price. Currently, this tool supports the following quote sources

  1. Yahoo: very good for US stocks, funds ...
  1. Yahoo Options: options prices. You can also this as the fall back quote source for symbols that the main Yahoo quotes source fail to find.
  1. ft.com: very good coverage for UK funds. The one draw back is that you need to download the CSV file yourself.
  1. ~~Google Portfolio: has its quirk. You must have a non-zero transaction. Reason: you cannot get the quote price directly, rather we derive the quote price from currentValue/shares. Can return multiple currency prices (for example: in USD and GBP)~~. **UPDATE**: Google has shutdown the Finance API service. See: http://social.microsoft.com/Forums/en-US/e9831d45-d284-4f9f-81d1-a1628dc6ff96/hleofxquotes-google-finance-api-will-be-shut-down-on-october-20-2012

Most US users use Yahoo. Most UK users use ft.com.

CSV import is sorted of supported via ft.com. If you can get your CSV file into the ft.com format, then you are set. The ft.com format is:
```
Name, Symbol: Exchange, Quote Date & Time, Last Price, Currency for Last Price

Fidelity Moneybuilder Growth ISA Class NAV,FIMGC,Feb 07 2011 00:00 GMT,57.89,GBX
Standard Life UK Smaller Companies Acc Inst Shares,STUSCA,Feb 07 2011 00:00 GMT,341,GBX
```

**CAVEAT**: We are at the mercy of the **free** quote source. We've seen quote source (specifically Yahoo) returning wrong data in the past. Make sure you have good backup so that you can back out of a bad import.

# Yahoo #

Q: I can find ticker XYZ.L and updated price on Yahoo Finance
but your tool cannot download it.

A: Though they can be viewed on the web, the price of those securities are not available for download from Yahoo. If you don't believe me, try this
  * Go to the bottom right of where you see the price quote. Find the section that is labeled
```
Toolbox

    Download Data (delayed)
```
  * Click on the 'Download Data' link, you will see that that data is either blank or has zero values.



# ft.com #

Currently, the following columns are used from ft.com's results.csv file
  * **Name**: Name of security. For example: 'Fidelity Moneybuilder Growth ISA Class NAV'
  * **Symbol: Exchange**: Symbol name and exchange (optional). For example: FIMGC
  * **Quote Date & Time**: date and time of the quote price. For example: 'Feb 07 2011 00:00 GMT'
  * **Last Price**: price. For example: 57.89
  * **Currency for Last Price**: currency for price. For example: GBX

**Question**: Why aren't you using values for other columns like day high, yield ...?

**Answer**: The import process goes through an intermediate interface called OFX importing which has its limitation. OFX does not have interface to import in value of such columns.