# Introduction #

Some recommendation on how to prepare so that you can roll back to a known state: getting back to where you know things were working.


# Details #

One good thing about MM is that almost everything are self-contained in a single `*`.mny file. For example: if you have two files
  * sample.mny
  * Copy of sample.mny
And you start up 'Copy of sample.mny' and really mess it up, you can throw away 'Copy of sample.mny'. Make another 'Copy of sample.mny' from 'sample.mny' and be back to your starting point.

So my recommendation when trying out this tool, do you testing on a **COPY** of you real `*`.mny file.

There are two ways to start Microsoft Money
  1. Select the "Money Plus" in the Windows menu
  1. OR double-click on the `*`.mny file itself

Choice #1 will always start the last `*`.mny file that you opened. Keep that in mind. Personally, I always use #2, to ensure that I am opening the `*`.mny file that I want.




