# Introduction #

This page tries to list the OS environment variables that affect WAF behaviour.  For instance, in a unix system, with a bourne shell, the variable CXX can be used to select a particular compiler, like this:
```
CXX=/usr/bin/g++-3.3 waf configure
```


# Details #

## Variables that always have effect ##

NOCOLOR
> When set, color is disabled in WAF output; see also TERM.

TERM
> If the value of TERM is 'dumb', color is disabled in WAF output; see also NOCOLOR.

COMSPEC
> Only used in the win32 platform; controls the command interpreter that is used to run commands

WAFDIR
> Selects WAF modules installation directory.

WAFCACHE
> Directory to use for project configuration caching generated by WAF

WAFLOCK
> Name of the lock file (named '.lock-wscript' by default)

## Variables that affect waf configure ##

These variables only have effect when running 'waf configure', and are completely ignored in 'waf build' or 'waf'.

CFLAGS
> Selects compilation options for when the C compiler is used, e.g. "-Wall".

CXXFLAGS
> Selects compilation options for when the C++ compiler is used, e.g. "-Wall".

CPPFLAGS
> Selects C preprocessor options, e.g. "-DFOO=bar"

LINKFLAGS
> Extra linker options, e.g. "-L/usr/local -lsome-library"

CC
> The C compiler that will be used instead of the platform default.  Example CC=/usr/bin/gcc-2.95

CXX
> The C++ compiler that will be used instead of the platform default.  Example CXX=/usr/bin/g++-2.95

PREFIX
> The default installation prefix to be used, if no --prefix option is given.

## Variables that affect waf build ##
These variables only have effect when running 'waf build'.

JOBS
> The amount of parallel jobs when building targets, if no --jobs option is given.

## Variables that affect waf install ##
These variables only have effect when running 'waf install'.

DESTDIR
> Used in "waf install", sets the base installation directory, i.e. a path that is used as prefix to all installation paths.  This is typically in packaging to ensure that files are installed to a temporary folder during packaging even though they would normally go to a different directory under normal installation. Example:
```
$ DESTDIR=/tmp waf install
Compilation finished successfully 
* installing build/default/foo.pyc as /tmp/usr/local/lib/python2.5/site-packages/foo.pyc
* installing foo.py as /tmp/usr/local/lib/python2.5/site-packages/foo.py
* installing build/default/foo.pyo as /tmp/usr/local/lib/python2.5/site-packages/foo.pyo
* installing build/default/spam.so as /tmp/usr/local/lib/python2.5/site-packages/spam.so
* installing build/default/test as /tmp/usr/local/bin/test
Installation finished successfully 
```