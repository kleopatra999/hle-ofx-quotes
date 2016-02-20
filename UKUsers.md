It appears that MS2005UK still getting quote price updated. So you might NOT want to try any of this yet!. Check with the following resources for the latest news on that front:
  * http://social.microsoft.com/Forums/en-US/money/threads
  * http://microsoftmoneyoffline.wordpress.com/2010/02/12/java-app-to-update-quotes/

# Introduction #

Updating quote prices for UK users is sort of working with some rough spots. I am documenting here the current state as I know it.

# Known working path #

  * Use the ft.com quote source to get UK stocks and fund price.
  * Use the latest test build (http://code.google.com/p/hle-ofx-quotes/downloads/list) which has support for **Incrementally Increased Share Count**
  * Make sure you set the **Incrementally Increased Share Count**
```
Edit -> Quotes -> Incrementally Increased Share Count -> set to true
```
  * Use the mapper.csv file to map the ft.com symbol into the matching symbol in Microsoft Money.
> If you have managed funds, make sure you use mapper.csv file to give the tool a hint that a particular security is a managed fund. For example:
```
MSMoneySymbol,QuotesSourceSymbol,IsMutualFund,IsOptions
FIMYI,FIMYI,TRUE,FALSE
```
> See: https://code.google.com/p/hle-ofx-quotes/wiki/mapperDotCsv
  * Enable `"Force <INVTRANLIST>"` so that the MM will show the correct statement date
```
Edit -> Force <INVTRANLIST> (set to true)
```
  * Each time you import, you will be prompt to adjust the share count (add or remove), go ahead and let Microsoft Money does it. A reminder: for imported statement, MM will only update the share price **ONCE** a day.

## Why ft.com? ##

  * Best coverage for UK funds. Yahoo does not come close.
  * Alternative is Google Portfolio if you don't want to manually download the CSV file.
  * **Please don't use Yahoo**: Yahoo does NOT return security currency and I will assume the price is in USD which will likely to be wrong. Stay with ft.com. It is your best bet.
  * **If you must use Yahoo**, make sure you use the 'QuotesSourceCurrency' column in mapper.csv file to specify the correct incoming currency.

### Why 'Incrementally Increased Share Count' ###

  * In US Sunset version, when we import in a zero share count. MM will happy update the price **BUT** for MM05UK, Microsoft Money seems to ignore zero share count, we need to force a actual transaction before MM will pick up the price data. 'Incrementally Increased Share Count' ensure that each time you import a statement, MM will have to adjust: by adding new share in a transaction thus updating the price. Share count will be increase by 0.001 increment and will wrap around at 0.999. This share count only affect the **Dummy** account.

### Why mapper.csv file? ###

  * For a give security (stock, fund ..) chances are symbol that ft.com provides is **NOT** the same as that in Microsoft Money so you need a way to say:
    * When dealing with ft.com, use this symbolA
    * When dealing with MM, this this symbolB
  * If you have managed funds, the tool needs to be told that a particular symbol is a managed fund or those prices are not going to get updated.

### Why `"Force <INVTRANLIST>"` ###

  * MMM05 appears to depend on the date fields in tag `<INVTRANLIST>` for the statement date. If you don't use this work-around, the statement will show up in MM05 as having a date of 1970.