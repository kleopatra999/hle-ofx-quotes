# Introduction #

Tips and tricks for downloading statements

  * See also: https://code.google.com/p/hle-ofx-quotes/wiki/Download_Statements_Security_Risks

# OFX info #

Source for OFX info: url, brokers ID, ...
  * Look up your OFX settings: http://microsoftmoneyoffline.wordpress.com/look-up-your-ofx-settings/
  * More OFX download settings: http://microsoftmoneyoffline.wordpress.com/2010/10/06/cal-learners-review-fidelity-401k-citi-card-and-vanguard-account-info/
  * OFX home: http://www.ofxhome.com/

## **fi** directory ##
**Financial Institution** data are stored directory **fi**.
  * Each sub directory represents an FI
  * The directory name is used as the FI's name if `fi.name` is not specified
  * To tell to the tool to ignore a directory, name it with '-' (minus, or dash) in front. For example, **-ignoreMe**.
  * To tell the tool to skip a FI during download, just comment out the `fi.url` line. For example
```
#fi.url=https://olbp.bankofthewest.com/ofx0002/ofx_isapi.dll
```

# Quick start #
> I've created a sample directory that you can use as a starting point.

## Populate the fi/ directory ##
  1. Download file fi.zip from http://code.google.com/p/hle-ofx-quotes/downloads/detail?name=fi.zip
  1. Save fi.zip to same directory as your hleOfxQuotes`*`.jar file
  1. Unzip to get directory fi/
  1. Start hleOfxQuotes
  1. Will work best if you have an account from one of the following institutions
```
ae - American Express (credit card)
bankOfTheWest - Bank of the West (checking account)
capitalOneBank - Capital One (checking account)
fidelity - Fidelity (investment)
fidelityNetbenefits - Fidelity (401k)
vanguard - Vanguard (investment)
```
  1. Otherwise, create a new directory under fi/. Copy a fi.property file from existing directory to your new directory. If hleOfxQuotes is running, in **Statements** tab, click on **Refresh** to update the FI list.

## Configure an FI (Financial Institution) ##
> For each fi, you will need to configure the following
  * Which URL to use?
  * Which login/password to use?
  * Which account(s)?

## Example ##
  1. First, let's configure the URL.
  1. Select **American Express** in the top-panel list
  1. In bottom panel, in **Properties** tab, find
```
#fi.url=https://online.americanexpress.com/myca/ofxdl/desktop/desktopDownload.do?request_type=nl_ofxdownload
```
  1. uncomment that line out
```
fi.url=https://online.americanexpress.com/myca/ofxdl/desktop/desktopDownload.do?request_type=nl_ofxdownload
```
  1. type control-s or popup-menu and choose "Save". From here on, I will refer this action as "Save changes"
  1. Click on "Download". That will attempt to download statement for the currently-selected FI. In this case: American Express.
  1. At this point, you should get an error. You can click on the "Download Error" tab to see more details.
  1. Next, let's configure login/password.
  1. Find lines
```
user.id=id123456
user.password=password654321
```
  1. Change them to your login and password for American Express. Save changes.
  1. Now click on "Download".
  1. You should now have a success status. This means we are able to connect and login. But if you look at the response in tab "OFX Response", you should see error because we have not configured the account information.
  1. To configure the account information. Go back to tab "Properties". Look for lines:
```
# List of accounts that you have with this FI
# Number of accounts
accounts=1
# Account ID #1
account.1.id=123456789
```
  1. Change those values to match your information. Save changes.
  1. Now click on "Download". Examine response in table "OFX Response"
  1. If you have multiple accounts from the same FI, change value of
```
accounts=2
```
  1. Then add the second account using syntax
```
account.2.id=123456789
```

# FI specific info #
> Information that is specific per FI.

## American Express ##
  * Known working OFX values:
```
fi.name=American Express

# Financial Institution (FI) info
# http://www.ofxhome.com/
# FI Id
fi.id=3101
# FI Org
fi.org=AMEX
# FI Url
fi.url=https://online.americanexpress.com/myca/ofxdl/desktop/desktopDownload.do?request_type=nl_ofxdownload
# FI Broker Id
#fi.brokerId=

# ofx version
# 1 or 2
ofx.version=2

# Request type
requestType=creditCard
```

## Bank of the West ##
  * Saving account data seems to be "intermingle" into checking account data.
  * Known working OFX values:
```
fi.name=Bank of the West
# Financial Institution (FI) info
# http://www.ofxhome.com/
# FI Id
fi.id=5809
# FI Org
fi.org=BancWest Corp
# FI Url
#fi.url=https://olbp.bankofthewest.com/ofx0002/ofx_isapi.dll
# FI Broker Id
#fi.brokerId=

# ofx version
# 1 or 2
ofx.version=1

# Request type
requestType=bank
```

## Capital One Bank ##
  * Known working OFX values:
```
fi.name=Capital One Bank
# Financial Institution (FI) info
# http://www.ofxhome.com/
# FI Id
fi.id=1001
# FI Org
fi.org=Hibernia
# FI Url
fi.url=https://onlinebanking.capitalone.com/ofx/process.ofx
# FI Broker Id
#fi.brokerId=

# ofx version
# 1 or 2
ofx.version=1

# Request type
requestType=bank
```

## Fidelity ##
  * Known working OFX values:
```
fi.name=Fidelity
# Financial Institution (FI) info
# http://www.ofxhome.com/
# FI Id
fi.id=7776
# FI Org
fi.org=fidelity.com
# FI Url
fi.url=https://ofx.fidelity.com/ftgw/OFX/clients/download
# FI Broker Id
fi.brokerId=fidelity.com

# ofx version
# 1 or 2
ofx.version=2

# Request type
# investment (INVSTMTTRNRQ): Investment Statement Download
requestType=investment
```

## Fidelity Netbenefits ##
  * Known working OFX values:
```
fi.name=Fidelity Netbenefits
# Financial Institution (FI) info
# http://www.ofxhome.com/
# FI Id
fi.id=8288
# FI Org
fi.org=nbofx.fidelity.com
# FI Url
fi.url=https://nbofx.fidelity.com/netbenefits/ofx/download
# FI Broker Id
fi.brokerId=nbofx.fidelity.com

# ofx version
# 1 or 2
ofx.version=2

# Request type
# investment (INVSTMTTRNRQ): Investment Statement Download
requestType=investment
```

## ING DIRECT ##
  * You need to request access for using **personal financial management tool**. Go to the 'My Info' section of ING Direct and enable Personal Finance Access Code.  You then use this code instead of your web password.
  * Response has problem. The response from ING has a missing required field `<DTEND>` in `<BANKTRANLIST>`. I think PocketSense has a fix for that.
  * Known working OFX values:
```
fi.name=ING DIRECT
# Financial Institution (FI) info
# http://www.ofxhome.com/
# FI Id
fi.id=031176110
# FI Org
fi.org=ING DIRECT
# FI Url
#fi.url=https://ofx.ingdirect.com/OFX/ofx.html
# FI Broker Id
fi.brokerId=nbofx.fidelity.com

# ofx version
# 1 or 2
ofx.version=1

# Request type
requestType=bank
```

## Vanguard ##
  * Make sure to use **ofx.version=2**. If you use **ofx.version=1** and you have no transaction during the download period (default: last 30 days), the imported OFX file will cause MM to crash. From what I see in the v1 response, the OFX does not include the `<SECLIST>`.
  * Known working OFX values:
```
fi.name=Vanguard

# Financial Institution (FI) info
# http://www.ofxhome.com/
# FI Id
#fi.id=
# FI Org
fi.org=Vanguard
# FI Url
fi.url=https://vesnc.vanguard.com/us/OfxDirectConnectServlet
# FI Broker Id
fi.brokerId=vanguard.com

# ofx version
# 1 or 2
ofx.version=2

# Request type
# investment (INVSTMTTRNRQ): Investment Statement Download
requestType=investment
```