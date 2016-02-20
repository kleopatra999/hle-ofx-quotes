
```
/*******************************************************************************
 *
 * This library is free software; you can redistribute it and/or
 * modify it under the terms of the GNU Lesser General Public
 * License as published by the Free Software Foundation; either
 * version 2.1 of the License, or (at your option) any later version.
 *
 * This library is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * Lesser General Public License for more details.
 *
 * You should have received a copy of the GNU Lesser General Public
 * License along with this library; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307
 * USA
 *******************************************************************************/
```

## Don't be evil .. and all that ... ##

# Introduction #
This tool was created to help with all the poor souls who have forgotten their `*.mny` password and got no where else to turn. Two modes are supported:
  1. [Dictionary attack](https://en.wikipedia.org/wiki/Dictionary_attack): check password against a set of dictionaries.
  1. [Brute-force attack](https://en.wikipedia.org/wiki/Brute_force_attack): for a given set of alphabets, try all combination.


  * For both modes, you will need a working `*`.mny file and Java installed.
  * For **Dictionary attack**, you will need a good set dictionaries.
![http://sunriise.sourceforge.net/out/sunriise/Build_20120531_128/PasswordCheckerApp_001.jpg](http://sunriise.sourceforge.net/out/sunriise/Build_20120531_128/PasswordCheckerApp_001.jpg)
  * For **Brute-force attack**, you will need sufficiently CPU cycles and times. I will discuss some optimization strategy later on that you can employ to reduce the times requirement.
![http://sunriise.sourceforge.net/out/sunriise/Build_20120616_136/PasswordCheckerApp_002.jpg](http://sunriise.sourceforge.net/out/sunriise/Build_20120616_136/PasswordCheckerApp_002.jpg)


# Usage #
  1. Download a [copy of the JAR file](http://sunriise.sourceforge.net/out/sunriise/Build_20120616_136/sunriise-Build_20120616_136-app.jar) and save it as sunriise-Build\_20120616\_136-app.jar.
  1. To start the tool
```
java -cp sunriise-Build_20120616_136-app.jar app.PasswordCheckerApp
```
  1. Choose which mode to use
  1. Select `*`.mny file
  1. Specify additional parameters that are mode's specific
  1. Click **Start** button to start

Which attack mode should you use? I recommend trying **Dictionary attack** first. Reasons:
  * Faster to run.
  * There are a lot of password list, dictionary already readily available from the Internet.

## Dictionary attack ##
  * Select a word list file/dir.
    * If the word list value is a directory, all sub-directories are traversed.
    * File/dir with prefix 'dot' (.) is ignored. For example:
```
.skipMe
```
    * In each file, each line is used as matching candidate. Line begins with 'hash mark' (#) is skipped. For example
```
# skipMe
```
  * On an old (4 year old) Quad core @2.24Ghz, I get about 140K words per second.
  * On a slight more modern server (~1 year old i7), I get about 240K words per second.
  * See the following link that has references to some of the word list from the Internet that you can use: http://sourceforge.net/projects/sunriise/forums/forum/1386861/topic/4621124/


## Brute-force attack ##
Once you have exhausted all your dictionary, then try the brute-force attack. Caveat: time might not be on your side. To give you some numbers. To search for 8-characters password using a US-keyboard alphabets (for MsMoney, case-insensitive, total 66-chars )
  * given search rate of 140K/second, it will take ~83 years to complete.
  * given search rate of 240K/second, it will take ~49 years to complete.
  * now if you can you reduce the alphabet set of something smaller. For example: upper or lower + digits + 3 special char (!@#), then it will take about ~265 days to complete. Not that great but not insurmountable either.

**Notes**: before you go and start on some large, long-running search, you should convince yourself that this stuff works. Recommend:
  1. Use the sample `*.mny` file.
  1. Add a 5-char password
  1. Use brute-force mode, specify a mask as `*****`
  1. Should find your password in about 1-2 hours.

Knobs that you can can turn to speed up:
  * Number of characters in the alphabets. Smaller is better. For example, search of upper or lowwer + digits will be much faster than all printable characters on US keyboard.
  * Number of characters in the password. Smaller is better. For example, searching for 5-char password will be much faster than 8-char password.
  * If there are known character in the password. For example, if you are pretty sure that your password starts or ends with a bang '!', you can help speed thing up.
  * If you distribute the work-load to multiple servers, then you can speed up the time. For example, one of the number cited above is ~265 days, if you can crowd-source ~265 persons/servers to help you, then it will take just one day to complete.
  * Increase the rate throughput. I cited some number in a range of 140K-240K on a typical home server running pure Java. Adding **native** support that use Windows/Linux provided cryptography libraries (CryptoAPI, openssl ...) will speed things up significantly. If you have an Nvidia graphic card, one can take advantage of the graphic card processing capability. For example, see the following citation: https://dl.acm.org/citation.cfm?id=1719150&dl=ACM&coll=portal (NOT YET IMPLEMENTED)

**Parameters**
  1. **Password length/mask**: You can specify a number or a mask-syntax. Some example:
```
# search for 5-char password
5
# search for 8-char password
8
# search for 5-char password
*****
# search for 5-char password that starts with letter 'a'
a****
# search for 5-char password that ends with '!'
****!
```
  1. **Character set**: by default, the printable us-keyboard characters are used. You can specify a set by listing all characters in the set. For example
```
abcdef123890!@#
```
Notes, that for `*`.mny password, it is case-insensitive, so you should only list either all UPPER or all lower cases.

## Do it yourself distributed attack ##
I mentioned earlier about finding 200 users/servers to help you out. Essentially, you will be implementing a do-it-yourself distributed attack.
  * you will have to manually break the alphabets down to smaller chunk(s). So instead of saying search for 8-char password on alphabets a-z0-9, you will break the job into
```
aa******
...
az******
a1******
...
a9******
```
  * Then hand each of the job to each participants to be calculated. Automate this process is not that hard.

## Known problems/Limitations ##
  * Not resumable. If the tool stops at the middle of a run. You will need to start from scratch again. Supporting resumable is technically doable, juts matter of 'coding it up'. One strategy is to run **smaller job**, see section on **Do it yourself distributed attack**
  * The mask syntax will not work if the known character itself is the star `*`. That can be fixed by using an escape character, technically doable.