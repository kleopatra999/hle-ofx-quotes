# Introduction #

I want to try the "Download Statements" feature, what security risks are there? What is my exposure?

  * See also: https://code.google.com/p/hle-ofx-quotes/wiki/Download_Statements_Tips

## Your Money file ##

This tool does not modify your Money file until you **specifically tell it to do so** in both cases:
  1. Quotes download
  1. and Statement download
There are always two steps:
  1. Generate, download the `*`.ofx files
  1. Import the OFX files into Money
You have to specifically click a button to **Import** before the second steps will occur. Nothing change to your MM files until you explicitly say so.

## Source codes ##

This has been raised before. Please see: http://code.google.com/p/hle-ofx-quotes/wiki/Source_Codes.

I trust that you are a grown up and can calculate the risk/reward ratio yourself and make your own decision. You've done that with other
non-source, free software you are currently running on your machine.

So let me give you the following points:
  * Yes there is a risk: source codes are not available so you will not be able to inspect the codes to see if I am doing **bad** things to your stuffs such as secretly transfer your `*`.mny file to some remote server.
  * We have others who are using this tools. Check the count on the download page. The tool has been available almost two years now. As far as I know, no one has complained about privacy issues.
  * I've tried to document what files, registry, URLs this tools will use here: http://code.google.com/p/hle-ofx-quotes/wiki/Files_Registry_URLs
  * I believe I've been a good citizen to the online Microsoft Money community: offer help in area I have expertise on, when I could. A quick search through the newsgroup will show that.

## Username/password exposure ##

  * Username, password are not encrypted. Available in plain-text in fi.properties file.
  * On my TODO list: encrypt username/password in storage.
  * Username, password are in plain text in stored request/response files.
  * On my TODO list: keep OFX request/response in memory only.
  * Personally, I run from a TrueCrypt filesystem (http://www.truecrypt.org/) which mitigates most of the above concern.