# Introduction #

If you have different symbol lists that you want to quickly switch between them, you can
use a **bookmarks** directory to store those lists. They will then be available in a popup menu in the symbol panel.

# Details #

  * Stop hleOfxQuotes tool.
  * Create a directory named **bookmarks** in current directory (where you keep the `*.jar` file).
  * In **bookmarks** directory, add files. For example, add
    * USD.txt
```
AAPL
```
    * HKD.txt
```
3988.HK
```
  * Start hleOfxQuotes tool
  * In the **Symbols** panel, click right-mouse to bring up popup menu, you should see a menu
```
Bookmarks -> USD.txt
Bookmarks -> HKD.txt
```
  * Select one will populate the symbol list with content of that file.