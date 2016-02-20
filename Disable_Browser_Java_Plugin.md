# Introduction #

I am trying to give some info on the on-going security concern about Java. In particular the zero-day exploit (http://www.theregister.co.uk/2013/01/10/java_0day/).

# Details #

On Jan 10, 2013, CERT issued a bulletin on a new Java's security hole called zero-day exploit. CERT advises everyone to disable Java in all browser.

'hleofxquotes' uses Java. But **NOT** via the browser's plugin. What is the difference:

  * When you run java with a tool such as 'hleofxquotes', you start the JVM with a known set of classes namely the ones from the 'hleofxquotes`*`.jar' file.
  * When Java is being invoked via the browser's java plugin, your browser accesses and downloads files from remote servers and can be tricked into download and execute classes that you don't know.

You will need Java to run 'hleofxquotes'. My recommendation is to keep your Java installation installed as-is but **DISABLE** the browser's **Java plugin**.


For more info about the exploit, see CERT bulletin http://www.kb.cert.org/vuls/id/625617


# Is my browser's Java plugin enable? #

To check to see if your browser's Java plugin enable, use this page: https://www.java.com/en/download/testjava.jsp

  * Java is enable (**NOT** good)

![https://hle-ofx-quotes.googlecode.com/issues/attachment?aid=630002001&name=image002.png&token=uorBRnP040zMN51UEq1Vq0b_k_c%3A1357946899277&abc=def.png](https://hle-ofx-quotes.googlecode.com/issues/attachment?aid=630002001&name=image002.png&token=uorBRnP040zMN51UEq1Vq0b_k_c%3A1357946899277&abc=def.png)

  * Java is disable (good)

![https://hle-ofx-quotes.googlecode.com/issues/attachment?aid=630002000&name=image001.png&token=sAPMNj_xR6eExDEHn1A-_3FJ-C4%3A1357946696248&abc=def.png](https://hle-ofx-quotes.googlecode.com/issues/attachment?aid=630002000&name=image001.png&token=sAPMNj_xR6eExDEHn1A-_3FJ-C4%3A1357946696248&abc=def.png)

# To disable Java in browser #

See this link:  https://krebsonsecurity.com/how-to-unplug-java-from-the-browser/

