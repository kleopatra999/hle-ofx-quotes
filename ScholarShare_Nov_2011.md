# Introduction #

The ScholarShare College Savings Plan recently transitioned to a new manager, from Fidelity Investments to TIAA-CREF Tuition Financing (under the ScholareShare California 529 College Savings Plan). Unfortunately, TIAA-CREF does not provide downloadable daily price updates. What available is this web page: http://www.scholarshare.com/performance/fundperformance.shtml

# Details #

Starting with build: Build\_20111221\_78 (http://code.google.com/p/hle-ofx-quotes/downloads/detail?name=hleOfxQuotes-Build_20111221_78-app.jar), **hleofxquotes** support a pseudo-quote-source named **Scholarshare** to make it possible to download the Scholarshare daily price update.

  * **hleofxquotes** will read the content of http://www.scholarshare.com/performance/fundperformance.shtml
  * Parse for price info and convert them into a `*`.ofx file


## Usage ##

You use the new **Scholarshare** quote source the same as other quote sources:
  1. Enter symbols
  1. Choose to update price
  1. Import into MsMoney

## Quote source symbol ##

There are no public symbols for the Scholarshare investments, so we will need to come up with a scheme to auto-create the symbols. I will refer to these as the **quote source symbol**. Current scheme
  * Part 1: Take the first letter of portfolio name. For example, for **Active Age-Based Investment Portfolio Option**, we reduce that to AABIPO
  * Part 2: Again first letter of the investment name. For example, for **Age Band 9-10**, we reduce that to AB910
So for above example, the **quote source symbol** is **AABIPOAB910**.

## MsMoney symbol ##

Internally to MsMoney, you should use shorter 4-char symbol, pick something that does not collide with your existing investment symbols. For example, I use SC1, SC2 ...

Then I use the mapper.csv file to map the **quote source symbol** to the **MsMoney source symbol**. (See: http://code.google.com/p/hle-ofx-quotes/wiki/mapperDotCsv)

```
MSMoneySymbol,QuotesSourceSymbol,IsMutualFund,IsOptions,QuotesSourceCurrency
SC1,PABIPOAB58,true
SC2,PABIPOAB910,true
SC3,PABIPOAB1112,true
SC4,PABIPOAB16,true
SC5,AABIPOAB58,true
```

![http://sunriise.sourceforge.net/out/hleofxquotes/images/2011_ScholarShare_1.png](http://sunriise.sourceforge.net/out/hleofxquotes/images/2011_ScholarShare_1.png)

## List of quote source symbols ##
```
AABIPOAB04, Active Age-Based Investment Portfolio Option, Age Band 0-4, 9.83
AABIPOAB58, Active Age-Based Investment Portfolio Option, Age Band 5-8, 9.85
AABIPOAB910, Active Age-Based Investment Portfolio Option, Age Band 9-10, 9.87
AABIPOAB1112, Active Age-Based Investment Portfolio Option, Age Band 11-12, 9.89
AABIPOAB1314, Active Age-Based Investment Portfolio Option, Age Band 13-14, 9.91
AABIPOAB15, Active Age-Based Investment Portfolio Option, Age Band 15, 9.93
AABIPOAB16, Active Age-Based Investment Portfolio Option, Age Band 16, 9.94
AABIPOAB17, Active Age-Based Investment Portfolio Option, Age Band 17, 9.96
AABIPOAB1, Active Age-Based Investment Portfolio Option, Age Band 18+, 9.97
PABIPOAB04, Passive Age-Based Investment Portfolio Option, Age Band 0-4, 9.89
PABIPOAB58, Passive Age-Based Investment Portfolio Option, Age Band 5-8, 9.9
PABIPOAB910, Passive Age-Based Investment Portfolio Option, Age Band 9-10, 9.91
PABIPOAB1112, Passive Age-Based Investment Portfolio Option, Age Band 11-12, 9.92
PABIPOAB1314, Passive Age-Based Investment Portfolio Option, Age Band 13-14, 9.93
PABIPOAB15, Passive Age-Based Investment Portfolio Option, Age Band 15, 9.95
PABIPOAB16, Passive Age-Based Investment Portfolio Option, Age Band 16, 9.96
PABIPOAB17, Passive Age-Based Investment Portfolio Option, Age Band 17, 9.97
PABIPOAB1, Passive Age-Based Investment Portfolio Option, Age Band 18+, 9.98
MFIPADEIP, Multi-Fund Investment Portfolios, Active Diversified Equity Investment Portfolio, 9.79
MFIPAGIP, Multi-Fund Investment Portfolios, Active Growth Investment Portfolio, 9.85
MFIPAMGIP, Multi-Fund Investment Portfolios, Active Moderate Growth Investment Portfolio, 10.01
MFIPACIP, Multi-Fund Investment Portfolios, Active Conservative Investment Portfolio, 10.0
MFIPADFIIP, Multi-Fund Investment Portfolios, Active Diversified Fixed Income Investment Portfolio, 10.0
MFIPAIEIP, Multi-Fund Investment Portfolios, Active International Equity Investment Portfolio, 9.78
MFIPPDEIP, Multi-Fund Investment Portfolios, Passive Diversified Equity Investment Portfolio, 9.87
MFIPPGIP, Multi-Fund Investment Portfolios, Passive Growth Investment Portfolio, 9.9
MFIPPMGIP, Multi-Fund Investment Portfolios, Passive Moderate Growth Investment Portfolio, 9.91
MFIPPCIP, Multi-Fund Investment Portfolios, Passive Conservative Investment Portfolio, 9.99
MFIPPDFIIP, Multi-Fund Investment Portfolios, Passive Diversified Fixed Income Investment Portfolio, 10.02
MFIPIIEIP, Multi-Fund Investment Portfolios, Index International Equity Investment Portfolio, 9.53
SFIPSCIP, Single-Fund Investment Portfolios, Social Choice Investment Portfolio, 9.92
SFIPIBIP, Single-Fund Investment Portfolios, Index Bond Investment Portfolio, 9.99
SFIPIULCEIP, Single-Fund Investment Portfolios, Index U.S. Large Cap Equity Investment Portfolio, 10.05
SFIPIUEIP, Single-Fund Investment Portfolios, Index U.S. Equity Investment Portfolio, 10.01
SFIPPPIIP, Single-Fund Investment Portfolios, Principal Plus Interest Investment Portfolio, 10.02
```