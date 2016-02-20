# DRAFT #

This is a DRAFT. Still researching for the right info.

# Introduction #

**Caveat**: I don't use multi-currency. What document here is based various email, discussion with actual multi-currency. If something is not correct, please let us know and we will get this corrected. For now, most of us are hanging out at:
  * http://microsoftmoneyoffline.wordpress.com/2011/01/09/uk-banks-ofx/
  * http://microsoftmoneyoffline.wordpress.com/2010/02/12/java-app-to-update-quotes/
  * http://social.microsoft.com/Forums/en-US/money/threads

MM supports multi-currency:
  * There is a based currency (for example: GBP)
  * And each security can have its own currency (for example: EUR, USD ...)
  * MM will take care of converting between currencies using exchange rates which can be edit manually or via online service (which  is officially off)

# Problem #

Currently we are using imported OFX statement to force quote price update. If you have multi-currency, things are not fully working yet.

Concrete example: let's say your base currency is GBP, and in your generated OFX file, you have two stock
  * STOCK1 in GBP priced at 1 GBP
  * STOCK2 in USD priced at 2 USD
  * And current exchange rate is 1.5
Ater import
  * STOCK1 is OK. MM imported it in with price 1 GBP
  * STOCK2 is NOT OK. MM imported it in with price 3