# Introduction #

This tool can use a helper file called **mapper.csv** to let you map a symbol that MM knows to a symbol that your quote source knows.

  * **Problem**: let's say you have stock that MM knows as **BBT**, your quote source (where you get price) knows the same stock as **BBT:NYQ**. Obviously there is mis-match that someone will have to resolve. That is where mapper.csv comes in to play. Using mapper.csv, you can tell the tool:
    * When talking to the quote source, use **BBT:NYQ**
    * When talking to MM, use **BBT**. Literally, this means when generating the OFX file.
  * Some Quote Source also does NOT provide the information that identify if a symbol is of type mutual funds or managed funds. This tool needs that information to generate correct OFX output. If you are using ft.com or Google Portfolio, you MUST create a mapper.cvs file with filled in column **IsMutualFund** or your fund will not be updated correctly.

Sample file: http://hle-ofx-quotes.googlecode.com/files/mapper.csv

### If it does not appear to work, one quick check ###

Make sure the mapper.csv file is the 'current working directory'. You can find the 'current working directory' by looking at the output of menu item
```
Help -> About

 ... look for the value of 

Directory:
```

The other thing that is not intuitive (some might even call it a bug). The mapper.csv only get loaded when you fetch the price update. So do a price update once to the "Prices" tab populated, now check the "Mapper" tab to see if your mapper.csv file is loaded.

## Usage ##

  * Create a file name **mapper.csv** in the same directory where you keep the `*`.jar file. You can also use menu
```
Help -> About
```
> to get the name of the directory.
  * Create file mapper.csv. You can use Excel, if you want. Just make sure that you save it as CSV file.
  * Format of mapper.csv
```
MSMoneySymbol,QuotesSourceSymbol,IsMutualFund,IsOptions
BBT,BBT:NYQ,FALSE,FALSE
AAPLOPT1,AAPL110219C00220000,FALSE,TRUE
```
  * You can also give hints to the tool about the type of the security: mutual fund? options? by using the appropriate column
    * IsMutualFund: set TRUE if this security is a mutual fund
    * IsOptions: set TRUE if this security is an options

Sanity check: check the content of the "Mapper" tab, it should have the content of your mapper.csv file. If not, the tool did not read the file.