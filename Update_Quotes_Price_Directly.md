# Introduction #

An alternate method for updating the stock quotes' price. Instead of creating an OFX file and import it into MSMoney, this method modifies the `*.mny` directly. This method opens up possibility to update other quote related values such as percent change, high, low ...

**This feature is EXPERIMENTAL**. Please proceed with caution: test with a copy of your `*.mny` file first.

# Details #

A test version of [Sunriise](https://sourceforge.net/projects/sunriise/) can read new prices from a CSV file and then updates a specified `*.mny` with new prices.

**I've only tested this with Sunset.**

## Download ##

  * http://sunriise.sourceforge.net/out/hleofxquotes/Build_20110628_19/sunriise-Build_20110628_19-app.jar
  * Save to a directory

## Usage ##

  * In a command window
```
java -cp sunriise-Build_20110628_19-app.jar com.le.sunriise.quote.UpdateStockPrices quotes.csv sample.mny
```
    1. quotes.csv: is a CSV file with stock symbol and price
    1. sample.mny: is your `*.mny` file to be modified. **IMPORTANT**: Make sure that this file is currently NOT opened by MSMoney. It is NOT safe to make concurrent modification.
    1. (optional third argument) password for above `*.mny` file

## quotes.csv file ##
Format
```
symbol,name,price,date

MSFT,Microsoft Corpora,25.80,2011/06/28
QQQ,PowerShares QQQ T,56.07,2011/06/28
```

Next version of hleOfxQuotes tool will create this file automatically each time you fetch new prices from quote sources. Here is a test version with that feature: http://sunriise.sourceforge.net/out/hleofxquotes/Build_20110628_19/hleOfxQuotes-Build_20110628_19.jar. Look for file **quotes.csv** in current directory (where you keep hleOfxQuotes-Build\_20110628\_19.jar file)

## Example run ##
```
java -cp sunriise-Build_20110628_19-app.jar com.le.sunriise.quote.UpdateStockPrices quotes.csv sample.mny
0 [main] INFO com.le.sunriise.quote.UpdateStockPrices.main(UpdateStockPrices.java:375) - quotesFile=quotes.csv
11 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.main(UpdateStockPrices.java:376) - inFile=sample.mny
17 [main] INFO  com.le.sunriise.Utils.openDb(Utils.java:108) - > Database.open,dbFile=sample.mny
19 [main] INFO  com.le.sunriise.Utils.openDb(Utils.java:115) - Created db lock file=C:\TEMP\quotes\sample.lrd
157 [main] INFO  com.le.sunriise.Utils.openDb(Utils.java:129) - < Database.open, dbFile=sample.mny
162 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:154) -
163 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:156) - Looking for stockSymbol=MSFT
231 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:162) - Found stockSymbol=MSFT, hsec=114
234 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:183) - Looking for existing row with date=Tue Jun 28 00:00:00 PDT 2011
299 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:188) - Found none
300 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:189) - Will duplicate one
319 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:191) - Last price date Tue Jul 10 00:00:00 PDT 2007
427 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:206) - Just inserted, row={hsp=3077, dt=Tue Jun 28 00:00:00 PDT 2011, hsec=114, src=6, dPrice=29.91, fFractPrice=true, dStrike=null, fFractStrike=false,dOpen=29.7, fFractOpen=true, dHigh=29.99, fFractHigh=true, dLow=29.69, fFractLow=true, dPE=21.5, fFractPE=true, dtExpire=Mon Feb 28 00:00:00 PST 10000, fClosing=false, vol=11900093, hss=null, dChange=0.03999999999999915, fFractChange=true,
dtSerial=Tue Jul 10 08:37:39 PDT 2007, exchgid=-1}
445 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:218) - Old price 29.91
458 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:227) - New price 25.8
460 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:154) -
462 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:156) - Looking for stockSymbol=QQQ
471 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:162) - Found stockSymbol=QQQ, hsec=123
473 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:183) - Looking for existing row with date=Tue Jun 28 00:00:00 PDT 2011
490 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:188) - Found none
493 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:189) - Will duplicate one
507 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:191) - Last price date Fri Feb 15 00:00:00 PST 2008
1471 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:206) - Just inserted, row={hsp=3078, dt=Tue Jun 28 00:00:00 PDT 2011, hsec=123, src=2, dPrice=26.0, fFractPrice=false, dStrike=null, fFractStrike=false, dOpen=null, fFractOpen=false, dHigh=null, fFractHigh=false, dLow=null, fFractLow=false, dPE=null, fFractPE=false, dtExpire=null, fClosing=false, vol=null, hss=null, dChange=null, fFractChange=false, dtSerial=Wed May 02 09:57:58 PDT 2007, exchgid=null}
1476 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:218) - Old price 26.0
1495 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.update(UpdateStockPrices.java:227) - New price 56.07
1499 [main] INFO  com.le.sunriise.viewer.OpenedDb.close(OpenedDb.java:53) - Deleted db lock file=C:\TEMP\quotes\sample.lrd
1502 [main] INFO  com.le.sunriise.quote.UpdateStockPrices.main(UpdateStockPrices.java:384) - < DONE
```