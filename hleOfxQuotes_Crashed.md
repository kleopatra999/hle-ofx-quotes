# Introduction #

What to do next if the tool **crashed**


# Details #

The most common cause of the crash is out-of-memory condition which will occur if you have a large number of quote symbols.

What you should do next is to see if increasing memory to the JVM will help:
  * Start a command line window
```
Run -> cmd
```
> See also: http://commandwindows.com/runline.htm
  * Go to the directory where you keep the `*`.jar file
```
cd dir1/dir2
```
  * Start up the tool using additional arguments
```
java -Xms128m -Xmx256m -jar hleOfxQuote*.jar
```
> where hleOfxQuote`*`.jar is the actual name of the jar file.
  * See if you can repeat the crash. If not, then the crash was likely due to out-of-memory condition which we just fixed by allocating more memory.
  * You might want to create a `*`.bat file to start up the tool using above command