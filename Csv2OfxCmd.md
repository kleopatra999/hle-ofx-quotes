# Introduction #

A command-line tool to convert `*`.csv (list of transactions) into a `*`.ofx file that can be imported by MsMoney.

## Installation ##
  * Download: http://sunriise.sourceforge.net/out/hleofxquotes/Build_20111026_28/csv2ofx.zip
  * Unzip to get folder **csv2ofx**

## Usage ##
  * Tool need 3 arguments:
    1. Input file: CSV file (see example: http://sunriise.sourceforge.net/out/hleofxquotes/Build_20111017_98/sample1.csv)
    1. Output file: OFX file (see example: http://sunriise.sourceforge.net/out/hleofxquotes/Build_20111017_98/sample1.ofx)
    1. Mapper file: `*.props` file (see example: http://sunriise.sourceforge.net/out/hleofxquotes/Build_20111017_98/csv2ofx.props)
  * See the sample **csv2ofx.bat** file
  * Command-line:
```
java -cp hleOfxQuotes-Build_20111026_28-app.jar app.Csv2OfxCmd sample1.csv sample1.ofx csv2ofx.props
```
    * That will run java using the code in file **hleOfxQuotes-Build\_20111026\_28-app.jar**
    * Run tool **app.Csv2OfxCmd** with three given arguments
      1. Input: sample1.csv
```
Date,Transaction Type,Check Number,Description,Amount
02/03/2011,POS,,WAL-MART SUPER CENTER 02-02-11 **** BB&T CHECK CARD PURCHASE-PIN,($8.02)
02/04/2011,POS,,SALLY BEAUTY 02-02 **** BB&T CHECK CARD PURCHASE,($7.53)
02/07/2011,POS,,WAL-MART SUPER CENTER 02-05-11 **** BB&T CHECK CARD PURCHASE-PIN,($47.81)
02/07/2011,POS,,WILCO 02-05 **** BB&T CHECK CARD PURCHASE,($19.50)
02/08/2011,Deposit,,TRANSFER FROM SAVINGS ************* 02-08-11 BB&T ONLINE TRANSFER,$100.00
02/08/2011,Debit,,ONLINE PMT AT&T CKF*********POS BB&T ONLINE BILL PAYMENT,($18.67)
02/08/2011,Debit,,ONLINE PMT TIME WARNER CKF*********POS BB&T ONLINE BILL PAYMENT,($16.13) 
02/08/2011,,,***LEDGERBAL***,$1000.00
```
      1. Output: sample1.ofx
```
OFXHEADER:100
DATA:OFXSGML
VERSION:102
SECURITY:NONE
ENCODING:USASCII
CHARSET:1252
COMPRESSION:NONE
OLDFILEUID:NONE
NEWFILEUID:NONE

<OFX>
    <SIGNONMSGSRSV1>
        <SONRS>
            <STATUS>
                <CODE>0
                <SEVERITY>INFO
            </STATUS>
            <DTSERVER>20111017204606
            <LANGUAGE>ENG
            <FI>
                <ORG>HAN
                <FID>6805
            </FI>
        </SONRS>
    </SIGNONMSGSRSV1>
    <BANKMSGSRSV1>
        <STMTTRNRS>
            <TRNUID>0
            <STATUS>
                <CODE>0
                <SEVERITY>INFO
            </STATUS>
            <STMTRS>
                <CURDEF>USD
                <BANKACCTFROM>
                    <BANKID>123456789
                    <ACCTID>987654321
                    <ACCTTYPE>CHECKING
                </BANKACCTFROM>
                <BANKTRANLIST>
                    <DTSTART>20110203080000
                    <DTEND>20110208080000
                    <STMTTRN>
                        <TRNTYPE>DEBIT
                        <DTPOSTED>20110203080000
                        <TRNAMT>-8.02
                        <FITID>06c03d85153e1f20008f3d1be77a863c
                        <NAME>WAL-MART SUPER CENTER 02-02-11 **** BB&amp;T CHECK CARD PURCHASE-PIN
                    </STMTTRN>
                    <STMTTRN>
                        <TRNTYPE>DEBIT
                        <DTPOSTED>20110204080000
                        <TRNAMT>-7.53
                        <FITID>706bf4a80e553e3817a97fc8e74aa572
                        <NAME>SALLY BEAUTY 02-02 **** BB&amp;T CHECK CARD PURCHASE
                    </STMTTRN>
                    <STMTTRN>
                        <TRNTYPE>DEBIT
                        <DTPOSTED>20110207080000
                        <TRNAMT>-47.81
                        <FITID>984d8cffc17f10f6fcfd352e02498d38
                        <NAME>WAL-MART SUPER CENTER 02-05-11 **** BB&amp;T CHECK CARD PURCHASE-PIN
                    </STMTTRN>
                    <STMTTRN>
                        <TRNTYPE>DEBIT
                        <DTPOSTED>20110207080000
                        <TRNAMT>-19.5
                        <FITID>0b882ac2055f7013b58bde9e7a0682cd
                        <NAME>WILCO 02-05 **** BB&amp;T CHECK CARD PURCHASE
                    </STMTTRN>
                    <STMTTRN>
                        <TRNTYPE>CREDIT
                        <DTPOSTED>20110208080000
                        <TRNAMT>100
                        <FITID>f8d26e7730926267571b0724e6de5752
                        <NAME>TRANSFER FROM SAVINGS ************* 02-08-11 BB&amp;T ONLINE TRANSFER
                    </STMTTRN>
                    <STMTTRN>
                        <TRNTYPE>DEBIT
                        <DTPOSTED>20110208080000
                        <TRNAMT>-18.67
                        <FITID>ad818191718f71c40df0f727ac98cb85
                        <NAME>ONLINE PMT AT&amp;T CKF*********POS BB&amp;T ONLINE BILL PAYMENT
                    </STMTTRN>
                    <STMTTRN>
                        <TRNTYPE>DEBIT
                        <DTPOSTED>20110208080000
                        <TRNAMT>-16.13
                        <FITID>16b1a324b0c5cba26aa5aa196f525f54
                        <NAME>ONLINE PMT TIME WARNER CKF*********POS BB&amp;T ONLINE BILL PAYMENT
                    </STMTTRN>
                </BANKTRANLIST>
                <LEDGERBAL>
                    <BALAMT>1000
                    <DTASOF>20110208080000
                </LEDGERBAL>
            </STMTRS>
        </STMTTRNRS>
    </BANKMSGSRSV1>
</OFX>
```
      1. Mapper: csv2ofx.props
```
# how to map CSV columns to OFX values
# OFX = CSV
#column.TRNTYPE=Transaction Type
column.DTPOSTED=Date
#column.DTUSER=Date
column.TRNAMT=Amount
#column.FITID=FITID
column.NAME=Description
column.MEMO=Check Number

# FI info (financial institution). You can look it up from http://www.ofxhome.com/.
# If not sure, just enter some "reasonable" values.
# I think MsMoney uses this value to try to match to the right account.
ORG=HAN
FID=6805

# Account info
# Default currency
CURDEF=USD
BANKID=123456789
ACCTID=987654321

#CHECKING Checking
#SAVINGS Savings
#MONEYMRKT Money Market
#CREDITLINE Line of credit
ACCTTYPE=CHECKING
```
  * Take a quick look of the the generated file to make sure that it looks good.
  * Double-click on **sample1.ofx** to import into MsMoney
  * Example of the account after imported
<img src='http://sunriise.sourceforge.net/out/hleofxquotes/Build_20111017_98/Csv2OfxCmd.png'></li></ul>

<h3>First time consideration ###
  * Make sure your `*.csv` file has one entry that looks like this
```
02/08/2011,,,***LEDGERBAL***,$1000.00
```
  * The above line is needed so that the tool can generate a REQUIRED tag for account balance. Minimum requirements:
    * Date (column.DTPOSTED): date for the balance
    * Amount (column.TRNAMT): account balance at above date
    * Description (column.NAME): must have value `***LEDGERBAL***` (prefix and suffix with 3 `*`)
  * Make sure your **mapper** (`*.props`) file has appropriate values for
```
# FI info (financial institution). You can look it up from http://www.ofxhome.com/.
# If not sure, just enter some "reasonable" values.
# I think MsMoney uses this value to try to match to the right account.
ORG=HAN
FID=6805

# Account info
# Default currency
CURDEF=USD
BANKID=123456789
ACCTID=987654321

#CHECKING Checking
#SAVINGS Savings
#MONEYMRKT Money Market
#CREDITLINE Line of credit
ACCTTYPE=CHECKING
```
## Map file ##
Reason for the map file
  * Need a way to map `*.csv` column into `*.ofx` tag
    * Minimum column map
```
column.DTPOSTED=Date
column.TRNAMT=Amount
column.NAME=Description
```
  * The tool will auto-calculate
    * column.TRNTYPE: DEBIT (for negative amount), CREDIT (for positive amount). You can override this auto-calculate by setting **column.TRNTYPE** to a column in your `*.csv` file. See section on list of valid OFX TRNTYPE.
    * column.FITID: a unique id to identify this transaction.
  * There are some additional data such as account number, balance ... that needs to be specified.
    * ORG: your bank (check http://www.ofxhome.com/)
    * FID: your bank id (check http://www.ofxhome.com/)
    * CURDEF: default currency
    * BANKID: your bank routing number
    * ACCTID: account id
    * ACCTTYPE: account type (see list of valid ACCTTYPE)

### Valid OFX TRNTYPE ###
List of valid OFX TRNTYPE
```
    CREDIT Generic credit
    DEBIT Generic debit
    INT Interest earned or paid
    Note: Depends on signage of amount
    DIV Dividend
    FEE FI fee
    SRVCHG Service charge
    DEP Deposit
    ATM ATM debit or credit
    Note: Depends on signage of amount
    POS
    Point of sale debit or credit
    Note: Depends on signage of amount
    XFER Transfer
    CHECK Check
    PAYMENT Electronic payment
    CASH Cash withdrawal
    DIRECTDEP Direct deposit
    DIRECTDEBIT Merchant initiated debit
    REPEATPMT Repeating payment/standing order
    OTHER Other
```

### Valid OFX ACCTTYPE ###
```
CHECKING Checking
SAVINGS Savings
MONEYMRKT Money Market
CREDITLINE Line of credit
```
## See also ##
  * http://code.google.com/p/hle-ofx-quotes/issues/detail?id=37
  * http://social.microsoft.com/Forums/en-US/money/thread/1e01e5a8-3c06-4265-931d-9601af50db56/
  * http://social.microsoft.com/Forums/en-US/money/thread/2aab47da-fe95-45ca-8338-1f63af5ecdc6