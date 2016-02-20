# Introduction #

Here is a list of registry, files, URLS this tools access


## Registry ##

This tool uses the Java's Preferences class to store user-specific information (such as last used quote list, various settings like 'Randomized Shared Count' ...). On Windows, the Preferences implementation uses Window's registry
```
HKCU\Software\JavaSoft\Prefs\le\com\tools\moneyutils\ofx\quotes
```

## Files ##
  * Read mapper.cvs
  * Read directory bookmarks/ for entries to populate Yahoo's popup menu.
  * Write hleOfxQuote-log.txt (log file)
  * Write generated OFX to temp directory. On Vista, I see
```
C:\Users\HUNGLE~1\AppData\Local\Temp\quotes8452759604132664180.ofx
```
> These files will be deleted on exit.
  * Read/Write files under directory **fi/** if exist. These files are used for the 'Download Statements' feature.

## URLs ##
  * Yahoo: download.finance.yahoo.com
  * Yahoo API (for looking up options): query.yahooapis.com and finance.yahoo.com
  * Google Portfolio: finance.google.com
  * If you are using "Download Statements", any URl you specified in your **fi.properties** file.