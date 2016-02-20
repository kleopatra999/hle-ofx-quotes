**Q:** What version should I download?

**A:** Download from: http://code.google.com/p/hle-ofx-quotes/downloads/list. Download the build that is labelled **DOWNLOAD ME**.

---

**Q:** What Microsoft Money version does this tool support?

**A:** I use MS Money Sunset US. So
  * Best support: MS Money Sunset US
  * Limited support: 2005 UK (See http://code.google.com/p/hle-ofx-quotes/wiki/UKUsers)
  * Microsoft Money that supports OFX version 2.00 and above. I am not quite sure which version of Microsoft Money starts to support OFX 2.00

---

**Q:** Cannot start. Nothing happens where I double click on the jar file.

**A:** Try to run the tool in a command window.
  1. Start the command window (see also: http://pcsupport.about.com/od/commandlinereference/f/open-command-prompt.htm)
  1. Go to the directory (folder) where you keep your hleofxquotes**.jar file
```
cd …some\directory
```
  1. At the prompt type
```
java -jar nameOfJarFile.jar
```
  1. Is there any error in the window?
  1. There should be a log file in same folder/directory (see: https://code.google.com/p/hle-ofx-quotes/wiki/Log_Files)

---**Q:**Generated OFX file imported OK (no error) but price is not updated**

**A:** If you are using MS Money 2005, please make sure to enable option **Incrementally Increased Share Count**. See the following page for explanation: http://code.google.com/p/hle-ofx-quotes/wiki/UKUsers

---

**Q:** I think I need to use a **mapper.csv** file but I don't know where to start.

**A:** Please see page: http://code.google.com/p/hle-ofx-quotes/wiki/mapperDotCsv

---

**Q:** Your tool uses Java, I was told to disable Java due to security risk.

**A:** Short-answer, hleofxquotes uses Java but not as a browser plugin (that is where the security risk is). See also: http://code.google.com/p/hle-ofx-quotes/wiki/Disable_Browser_Java_Plugin

---

**Q:** I picked the wrong account when first prompted. How to can I re-do to create a **Dummy** account?

**A:** See: http://microsoftmoneyoffline.wordpress.com/fixing-ofx-financial-institution-file-association/

---

**Q:** Google Portfolio no longer work.

**A:** Google has shutdown the Finance API service.
See: http://social.microsoft.com/Forums/en-US/e9831d45-d284-4f9f-81d1-a1628dc6ff96/hleofxquotes-google-finance-api-will-be-shut-down-on-october-20-2012

---

**Q:** Google Finance has a mean to export to OFX. Why can't I use that?

**A:** The generated OFX file is not completed. The price is always zero
```
<UNITPRICE>0
```

---

**Q:** Select to import OFX, bring up MondayDance

**A:** You will need to decide which programs (MoneyDance or MM) to handle when you double-click the `*`.ofx file.
  * If you want to let MoneyDance to handle when you double-click the `*`.ofx file. Then in hleofxquots, select to save the generated `*`.ofx file. Then in MM, use Import to import the generated `*`.ofx
  * If you wan to re-set the `*`.ofx association, see http://money.mvps.org/faq/article/178.aspx