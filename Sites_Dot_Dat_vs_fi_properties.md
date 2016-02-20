# Introduction #

For those currently using PocketSense and want to try out the "Statement Download" feature in hleOfxQuotes, I am documenting equivalent concepts or settings that you are already familiar with from the sites.dat file.

You should also see the **Quick Start** section at http://code.google.com/p/hle-ofx-quotes/wiki/Download_Statements_Tips

## Site vs fi dir ##

At top-level,
  * PocketSense stores site information (URL, fi org, fi id ...) in file sites.dat in a list of `<site>....</site>` block.
  * hleOfxQuote stores the same information in a directory structure
```
  fi -- FI_001 -- fi.properties
     -- FI_002 -- fi.properties
     -- FI_003 -- fi.properties
```

## Key value pair ##

| **PocketSense** | **hleOfxQuotes** | **Comments** |
|:----------------|:-----------------|:-------------|
| SiteName        | fi.name          | Name of the Financial Institution (FI) |
| AcctType        | requestType      | CCSTMT=creditCard, INVSTMT=investment, BASTMT=bank |
| fiorg           | fi.org           | FI Org       |
| fid             | fi.id            | FI Id. Some FI has id. Others don't. When in doubt, keep this value empty |
| url             | fi.url           | FI Url. In hleOfxQuotes, if you comment it out. That FI will be skipped during download phase. |
| bankid          | account.1.bankId | Only meaningful if requestType is bank. Often is the bank's routing number|
| brokerid        | fi.brokerId      | FI Broker Id. Some FI don't have Broker ID. When in doubt, keep this value empty |
| appid           | TODO             | Client app id to be present to server |
| appver          | TODO             | Client app  ver to be present to server |
| mininterval     | startDate        | In hleOfxQuotes, you can specify absolute date '20110101' or offset '-30'|
| timeOffset      |  TODO            | Add (-subtract) number of hours to statement DTASOF field(s).  Default = zero. |

## Account information ##

  * In PocketSense, account information is stored in file **ofx\_config.cfg**. For example
```
S''
p0
.I00
.(lp0
(lp1
S'VANGUARD'
p2
aS'12345678'
p3
aS''
p4
aS'hle-vanguard'
p5
aS'12345678'
p6
aa.
```
  * In hleOfxQuotes, account information is kept in the fi's fi.properties file
```
# List of accounts that you have with this FI
# Number of accounts
accounts=1
# Account ID #1
account.1.id=123456789

# Another example. This FI has two accounts. Note the usage of 'account.N.key' as the key name.
# Number of accounts
#accounts=2
# Account ID #1
#account.1.bankId=123456
#account.1.id=987654321
#account.1.type=CHECKING
#account.2.bankId=123456
#account.2.id=987654321
#account.2.type=SAVINGS
```