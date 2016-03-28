# exerb-mingw

Build standalone executables using Ruby.

This repository containsthe conversion of original [exerb](http://exerb.sourceforge.jp/index.en.html) code
into pure-C one that works better against MinGW compilers.

## Usage
+ Navigate to a ruby file and execute the `mkexy` command
  `mkexy source.rb`
+ Edit the newly generated file "source.exy" to check the file bindings. You can also change the options under the "general" section.
+ Execute `exerb --verbose source.exy`. It will generate the file "source.exe".

## Ruby gems bindings
If you load rubygems and relative files and have problems with the generated executable not finding the relative files,
add the following lines to your source file **before** the `require`:

```
# Avoids errors when requiring relative files and working dir is different 
$LOAD_PATH.unshift(File.dirname(__FILE__)) unless defined? Exerb
# In execution adds current path to allow loading relative files
$LOAD_PATH << '.' if defined? $Exerb || defined? Exerb
```