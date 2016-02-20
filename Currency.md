# Introduction #

Current treatment of currency setting.

**Caveat**: I am a US-base user. I don't use non-US and/or multi-currency. So I don't really have actual hand-on experience in this area. I'd love to understand more and I am happy to take input on how to make it better.

# Default Currency #

  * Default: USD
  * Default currency is what written to the `*`.ofx file as
```
<CURDEF>USD</CURDEF>
```
  * You can change that by using menu item
```
Edit -> Quotes -> Currency
```
  * If you need to switch between currencies, for example, you have two quote sources: one in USD and the other in EUR, see the notes [Build\_20110226\_001](Build_20110226_001.md) on how to create a **Quote Profile** (search for string Quote Profile)

# Per Security Currency #

  * Why the need? some quote source provides per security currency (Google), other does not (Yahoo). Also for user using multi-currency, we might have handle translating quoted currency into base currency (not sure).
  * You can provide per security currency via the mapper.csv file (see: [Build\_20110226\_001](Build_20110226_001.md), look for **QuotesSourceCurrency**). See also the wiki [mapperDotCsv](mapperDotCsv.md) page.
  * Currently, the ONLY currency translation is from GBX to GBP. This is more of a work-around/bug fix for user whose default currency is GBP but the quote source is quoting in GBX.
  * There has been some discussion about having a currency exchange table and perform the appropriate conversion as needed. Nothing has been done since it appears the Microsoft automatic quote feed for UK user is still working (main targeted users for this feature).