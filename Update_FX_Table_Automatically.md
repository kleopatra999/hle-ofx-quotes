# Introduction #

This is an initial effort to make it possible to update the currencies exchange rate table automatically.

**This feature is EXPERIMENTAL**. Please proceed with caution: test with a copy of your `*.mny` file first.


# Details #

Currently, there is no known path to change the currencies exchange rate via OFX file. To update, you will have to do one of the following:

  1. Update manually
  1. Use tool to mimic mouse-keyboard sequences
  1. Use tool to edit `*.mny` file directly

This note documents approach **number 3**.

For now, there are two distinct tasks (we will simplify this at a later date).
  1. Create a **fx.csv** file. This file contains the current rate
  1. Update `*.mny` file using above file **fx.csv**

**So far, I've only tested this on Sunset version.**

## Creating fx.csv file ##
  * You can use **hleOfxQuotes app** to create the **fx.csv** file for you.
  * Get this version of **hleOfxQuotes app**: http://sunriise.sourceforge.net/out/hleofxquotes/Build_20110626_001/hleOfxQuotes-Build_20110626_001.jar
  * Save to a directory.
  * Double-click on **hleOfxQuotes-Build\_20110626\_001.jar** to start. Or from command window
```
java -jar hleOfxQuotes-Build_20110626_001.jar
```
  * In the `Quote Sources -> Yahoo` tab, enter
```
EURUSD=X
```
  * Click on **Update prices** button.
  * In the lower window, click on tab **Exchange Rates**, you should see the current exchange rate for EUR to USD.
  * There should also be a new file named **fx.csv** created in current directory (where you saved the **hleOfxQuotes-Build\_20110626\_001.jar**). The content of **fx.csv** should look something like this:
```
FromCurrency,ToCurrency,Rate, Date

EUR, USD, 1.4128, Sun Jun 26 20:31:46 PDT 2011
```


## Update `*.mny` file ##
  * You can use **sunriise app** to update your `*.mny` file using above generated **fx.csv** file.
  * Get this version of **sunriise app**: http://sunriise.sourceforge.net/out/hleofxquotes/Build_20110626_001/sunriise-0.0.2-SNAPSHOT-jar-with-dependencies.jar
  * Save to same directory as above **hleOfxQuotes app**.
  * Run the following command to update. **Notes**: in the following command, the first argument to java is **-cp** (NOT **-jar**)
```
java -cp sunriise-0.0.2-SNAPSHOT-jar-with-dependencies.jar app.UpdateExchangeRates fx.csv sample.mny
```
  * **UpdateExchangeRates** command takes TWO required arguments
    * File fx.csv
    * File `*.mny` to be updated. **IMPORTANT**: Make sure that this file is currently NOT opened by MSMoney. It is NOT safe to make concurrent modification.
    * (Optional) third-argument is your `*.mny` password
  * Let's say I have file fx.csv and sample.mny in current directory and no password for sample.mny
```
java -cp sunriise-0.0.2-SNAPSHOT-jar-with-dependencies.jar app.UpdateExchangeRates fx.csv sample.mny
0 [main] INFO  com.le.sunriise.currency.UpdateExchangeRates.main(UpdateExchangeRates.java:45) - fxFile=fx.csv
14 [main] INFO  com.le.sunriise.currency.UpdateExchangeRates.main(UpdateExchangeRates.java:46) - inFile=sample.mny
17 [main] INFO  com.le.sunriise.Utils.openDb(Utils.java:108) - > Database.open,dbFile=sample.mny
19 [main] INFO  com.le.sunriise.Utils.openDb(Utils.java:115) - Created db lock file=C:\TEMP\fx\sample.lrd
175 [main] INFO  com.le.sunriise.Utils.openDb(Utils.java:129) - < Database.open, dbFile=sample.mny
242 [main] INFO  com.le.sunriise.currency.UpdateExchangeRates.update(UpdateExchangeRates.java:147) -
243 [main] INFO  com.le.sunriise.currency.UpdateExchangeRates.update(UpdateExchangeRates.java:148) - # YES NEW FX RATE
244 [main] INFO  com.le.sunriise.currency.UpdateExchangeRates.update(UpdateExchangeRates.java:149) -   CURRENT: EUR -> USD, 1.36556, (Euro -> US dollar)
245 [main] INFO  com.le.sunriise.currency.UpdateExchangeRates.update(UpdateExchangeRates.java:150) -   NEW: EUR -> USD, 1.4128
387 [main] INFO  com.le.sunriise.viewer.OpenedDb.close(OpenedDb.java:53) - Deleted db lock file=C:\TEMP\fx\sample.lrd
388 [main] INFO  com.le.sunriise.currency.UpdateExchangeRates.main(UpdateExchangeRates.java:54) - < DONE
```
  * Now use MSMoney to open **sample.mny**. Then choose
```
Tools -> Settings -> Program settings -> Update currencies
```
  * You should see the rate of EUR to USD updated.

## Misc. ##
  * fx.csv generation: only work for Yahoo quote sources
  * If you use Yahoo quote source as your main quote source, you can add the currency pseudo symbol (for example: EURUSD=X) as part of your symbol lists. Only the currencies will go into the fx.csv file and not the generated `*.ofx` file.
  * A sample list of currencies speudo-symbols
```
ALLUSD=X
DZDUSD=X
ARSUSD=X
AWGUSD=X
AUDUSD=X
ATSUSD=X
BSDUSD=X
BHDUSD=X
BDTUSD=X
BBDUSD=X
BEFUSD=X
BZDUSD=X
BMDUSD=X
BTNUSD=X
BOBUSD=X
BAMUSD=X
BWPUSD=X
BRLUSD=X
GBPUSD=X
BNDUSD=X
BGLUSD=X
BIFUSD=X
KHRUSD=X
CADUSD=X
CVEUSD=X
KYDUSD=X
XAFUSD=X
XPFUSD=X
CLPUSD=X
CNYUSD=X
COPUSD=X
KMFUSD=X
CRCUSD=X
HRKUSD=X
CUPUSD=X
CYPUSD=X
CZKUSD=X
DKKUSD=X
DJFUSD=X
DOPUSD=X
NLGUSD=X
XCDUSD=X
ECSUSD=X
EGPUSD=X
AEDUSD=X
EEKUSD=X
ETBUSD=X
EURUSD=X
FJDUSD=X
FIMUSD=X
FRFUSD=X
GMDUSD=X
GELUSD=X
DEMUSD=X
GHCUSD=X
GRDUSD=X
GTQUSD=X
GYDUSD=X
HTGUSD=X
HNLUSD=X
HKDUSD=X
HUFUSD=X
ISKUSD=X
INRUSD=X
IDRUSD=X
IRRUSD=X
IQDUSD=X
IEPUSD=X
ILSUSD=X
ITLUSD=X
JMDUSD=X
JPYUSD=X
JODUSD=X
KZTUSD=X
KESUSD=X
KRWUSD=X
KWDUSD=X
LAKUSD=X
LVLUSD=X
LBPUSD=X
LSLUSD=X
LRDUSD=X
LYDUSD=X
LTLUSD=X
LUFUSD=X
MOPUSD=X
MGFUSD=X
MWKUSD=X
MYRUSD=X
MVRUSD=X
MTLUSD=X
MROUSD=X
MURUSD=X
MXNUSD=X
MDLUSD=X
MNTUSD=X
MADUSD=X
MZMUSD=X
NADUSD=X
NPRUSD=X
TRYUSD=X
NZDUSD=X
NIOUSD=X
NGNUSD=X
NOKUSD=X
OMRUSD=X
PKRUSD=X
PABUSD=X
PGKUSD=X
PYGUSD=X
PENUSD=X
PHPUSD=X
PLZUSD=X
PTEUSD=X
QARUSD=X
RONUSD=X
RUBUSD=X
RWFUSD=X
STDUSD=X
SARUSD=X
CSDUSD=X
SCRUSD=X
SLLUSD=X
SGDUSD=X
SKKUSD=X
SITUSD=X
SBDUSD=X
SOSUSD=X
ZARUSD=X
ESPUSD=X
LKRUSD=X
SRGUSD=X
SZLUSD=X
SEKUSD=X
CHFUSD=X
SYPUSD=X
TWDUSD=X
TZSUSD=X
THBUSD=X
TOPUSD=X
TTDUSD=X
TNDUSD=X
TMMUSD=X
UGXUSD=X
UAHUSD=X
UYUUSD=X
USDALL=X
USDDZD=X
USDARS=X
USDAWG=X
USDAUD=X
USDATS=X
USDBSD=X
USDBHD=X
USDBDT=X
USDBBD=X
USDBEF=X
USDBZD=X
USDBMD=X
USDBTN=X
USDBOB=X
USDBAM=X
USDBWP=X
USDBRL=X
USDGBP=X
USDBND=X
USDBGL=X
USDBIF=X
USDKHR=X
USDCAD=X
USDCVE=X
USDKYD=X
USDXAF=X
USDXPF=X
USDCLP=X
USDCNY=X
USDCOP=X
USDKMF=X
USDCRC=X
USDHRK=X
USDCUP=X
USDCYP=X
USDCZK=X
USDDKK=X
USDDJF=X
USDDOP=X
USDNLG=X
USDXCD=X
USDECS=X
USDEGP=X
USDAED=X
USDEEK=X
USDETB=X
USDEUR=X
USDFJD=X
USDFIM=X
USDFRF=X
USDGMD=X
USDGEL=X
USDDEM=X
USDGHC=X
USDGRD=X
USDGTQ=X
USDGYD=X
USDHTG=X
USDHNL=X
USDHKD=X
USDHUF=X
USDISK=X
USDINR=X
USDIDR=X
USDIRR=X
USDIQD=X
USDIEP=X
USDILS=X
USDITL=X
USDJMD=X
USDJPY=X
USDJOD=X
USDKZT=X
USDKES=X
USDKRW=X
USDKWD=X
USDLAK=X
USDLVL=X
USDLBP=X
USDLSL=X
USDLRD=X
USDLYD=X
USDLTL=X
USDLUF=X
USDMOP=X
USDMGF=X
USDMWK=X
USDMYR=X
USDMVR=X
USDMTL=X
USDMRO=X
USDMUR=X
USDMXN=X
USDMDL=X
USDMNT=X
USDMAD=X
USDMZM=X
USDNAD=X
USDNPR=X
USDTRY=X
USDNZD=X
USDNIO=X
USDNGN=X
USDNOK=X
USDOMR=X
USDPKR=X
USDPAB=X
USDPGK=X
USDPYG=X
USDPEN=X
USDPHP=X
USDPLZ=X
USDPTE=X
USDQAR=X
USDRON=X
USDRUB=X
USDRWF=X
USDSTD=X
USDSAR=X
USDCSD=X
USDSCR=X
USDSLL=X
USDSGD=X
USDSKK=X
USDSIT=X
USDSBD=X
USDSOS=X
USDZAR=X
USDESP=X
USDLKR=X
USDSRG=X
USDSZL=X
USDSEK=X
USDCHF=X
USDSYP=X
USDTWD=X
USDTZS=X
USDTHB=X
USDTOP=X
USDTTD=X
USDTND=X
USDTMM=X
USDUGX=X
USDUAH=X
USDUYU=X
USDUZS=X
USDVUV=X
USDVEB=X
USDVND=X
USDWST=X
USDYER=X
USDZMK=X
USDZWD=X
UZSUSD=X
VUVUSD=X
VEBUSD=X
VNDUSD=X
WSTUSD=X
YERUSD=X
ZMKUSD=X
ZWDUSD=X
```