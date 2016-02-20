# Log Files #

**hleOfxQuotes** writes to a log file name **hleOfxQuotes-log.txt** located in the same directory as the jar file.

You can also get the name of the log file via the output of
```
Help -> About
```

The tool also writes the log entries to standard output, so if manually start **hleOfxQuotes** from a command window, you will also see the running output of the log
```
Window 
  Run -> cmd

java -jar hleOfxQuotes-XXXj.jar

should see log entries here ...
```

To start a cmd window, see also: http://pcsupport.about.com/od/commandlinereference/f/open-command-prompt.htm

The library that **hleOfxQuotes** uses to log is log4j. See: http://logging.apache.org/log4j/1.2/