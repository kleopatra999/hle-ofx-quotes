# DRAFT #

# Introduction #

A primer on how to read the generated OFX file.

# Format #

It is an XML file so if you have a tool that can display the XML content as the "tree" it will help seeing things more clearer especially if the file is large.

## Security List ##

First look for tag `<INVPOSLIST>`. This is


INVPOSLIST
Tag `<SECID>` has the ticker name. This value should match up
with what you specify in Microsoft Money for your security.
```
              <SECID>
                <UNIQUEID>AAPL</UNIQUEID>
                <UNIQUEIDTYPE>TICKER</UNIQUEIDTYPE>
              </SECID>
```

## Price ##

Tag `<UNITPRICE>` has the current price

```
              <UNITPRICE>355.49</UNITPRICE>

```





