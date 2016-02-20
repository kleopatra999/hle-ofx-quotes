**Source Codes**?: http://code.google.com/p/hle-ofx-quotes/wiki/Source_Codes

A java program for generating OFX file that you can use to update quotes in Microsoft Money.

  * **Why**: Microsoft's quote server is no longer working. If you want to see your portfolio values current, you need to update the quote prices.
  * **What does it do**: Generate an OFX file to mimic statement from a fake brokerage.
  * **How do I use it**: You will need [java](http://code.google.com/p/hle-ofx-quotes/wiki/Prerequisite_Java). Then [download](http://code.google.com/p/hle-ofx-quotes/downloads/list) the tool (a `*.jar` file). Double click on the downloaded `*.jar` file to start.

### Features ###
  * Has an UI: easy to get started
  * Support multiple quote sources including
    * **yahoo.com**: default for US users.
    * **ft.com**: which has good coverage for UK fund
    * ~~**Google Portfolio**: has coverage for international funds that cannot be retrieve from Yahoo.~~ **UPDATE**: Google has shutdown the Finance API service. See: http://social.microsoft.com/Forums/en-US/e9831d45-d284-4f9f-81d1-a1628dc6ff96/hleofxquotes-google-finance-api-will-be-shut-down-on-october-20-2012
  * Support bank statement download: https://code.google.com/p/hle-ofx-quotes/wiki/Download_Statements_Tips
  * Can handle large number of quotes (Yahoo): with multiple-thread and re-try.
  * Support **options** (See also: http://biz.yahoo.com/opt/symbol.html)

### First timer ###
  * Please read this page first: http://code.google.com/p/hle-ofx-quotes/wiki/FirstTimerReadMeFirst
  * Then read: http://code.google.com/p/hle-ofx-quotes/wiki/The_first_N_steps
  * **UK users:** please read this document: http://code.google.com/p/hle-ofx-quotes/wiki/UKUsers
  * **version 2005 and earlier:** See notes similar to UK user http://code.google.com/p/hle-ofx-quotes/wiki/UKUsers

### Documentation ###
  * See the Wiki: http://code.google.com/p/hle-ofx-quotes/w/list
  * How to get help: https://code.google.com/p/hle-ofx-quotes/wiki/Help_Me

### Alternative ###
  * Enter the price update by hand
  * PocketSense: http://sites.google.com/site/pocketsense/home/msmoneyfixp1 which can also download statement from banks, brokerages.

![http://sunriise.sourceforge.net/out/hleofxquotes/images/hleofxquotes_001.png](http://sunriise.sourceforge.net/out/hleofxquotes/images/hleofxquotes_001.png)
