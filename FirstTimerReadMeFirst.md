# Introduction #

If you are first-timer, please read me first to see what works, what does not.

There is no documented way to externally update the quote price in Microsoft Money. This tool exploits a particular path that has shown to work in Microsoft Money Sunset US. Seems to work with other version too but there is no way to know for sure until you try it yourself.

The tool mimics a statement from brokerage using zero share count. This means you need a **Dummy** account in MM to stores the imported information. MM will prompt if you want to create one the first time you import the generated OFX.

The flow goes something like this:
  * Tool: Hey, MM here is a statement from your brokerage named Dummy
  * MM: check and says ... I know nothing about Dummy. Do you want me to create an account for it? You say yes.
  * MM: imports the statement which has a list of securities with updated price and zero shares. Something like
```
AAPL,345.00, 0.00
GOOG, 600.00, 0.00
```
  * MM: will update the holding values in other account that has AAPL and GOOG.

# Backup Plan #

Before you do anything, make sure you have backup or know how to roll back (http://code.google.com/p/hle-ofx-quotes/wiki/Rolling_Back)

# Prerequisites #

Your will need a recent version of **Java: 1.6 and later** is best. To check your Java version
```
# Start cmd window
Run -> cmd 
# Then run
java -version

# You want to see something that looks like this
C:\Documents and Settings\Administrator>java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Client VM (build 19.1-b02, mixed mode, sharing)
```

# Limitation #

  * For import statement, MM appear to update its quote price only **ONCE** a day. So if you import one in the morning, subsequent update will not change the price.
  * The sweet spot for this tool is: **US users using Microsoft Money Sunset**. I will try to support other version and environment BUT you need to be the kind who is willing to roll up your sleeve to pitch in: providing sample output, describe how things work in your environment ...

# Where thing could go wrong #
  * You are using the tool for the first time and not getting the dialog to create a 'Dummy' account. You should turn OFF the auto-click feature, then try to import again
```
Tools -> Import dialog auto-click -> uncheck the check mark
```
  * Tool cannot find the price for a particular symbol. For UK, I recommend using the ft.com quote source. For other international user, try Google Portfolio.
  * Price in MM does not update. See above on notes on price is update only **ONCE** a day.
  * MM indicates that the import statement has error. Look for a tool called OFXAnalyzer which can check the syntax. See where to get additional help below.

# See also #
  * http://code.google.com/p/hle-ofx-quotes/wiki/The_first_N_steps

# Where to get help #
  * http://microsoftmoneyoffline.wordpress.com/2010/02/12/java-app-to-update-quotes/
  * http://social.microsoft.com/Forums/en-US/money/threads