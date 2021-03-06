GenericMakefile
===============

A generic makefile for use with small/medium C and C++ projects. Allows for
easy project setup without the need to create tedious build rules or
dependency lists.

#Features:
* Automatically finds and compiles all source files within the source directory.
* Automatically generates dependecies as files are compiled, ensuring that files are correctly recompiled when dependecies have updated.
* Includes configurations for normal (release) build and debug build suitable for GDB debugging.
* Times the compilation of each file and the entire build.
* Generates version numbers based on git tags (see below), which are passed the compiler as preprocessor macros.
* By default, builds in a "quiet" mode that only lists the actions being performed. By passing V=true to make, you can compile in verbose mode to see the full compiler commands being issued.

##Versioning:
Tags should be made in the format "vMAJOR.MINOR.PATCH[-description]", where MAJOR, MINOR and PATCH are numeric. The following macros will be generated and passed to the preprocessor:
* VERSION_MAJOR (int) - The major version number from the most recent tag.
* VERSION_MINOR (int) - The minor version number from the most recent tag.
* VERSION_PATCH (int) - The patch version number from the most recent tag.
* VERSION_REVISION (int) - The number of commits since the most recent tag.
* VERSION_HASH (string) - The SHA of the current commit. Includes the "-dirty" suffix if there are uncommited changes.

#Limitations:
* Assumes GNU make.
* Doesn't really support multiple types of source files in the same project.
* No easy way to exclude files from the build. You can either change the
  extension of files to be excluded, or use preprocessor flags for
  conditional compilation.

#Thanks to:
* My friend Jay and people on Stack Overflow for help with regex to parse the version info.
* The residents of /r/programming for suggesting numerous tweaks and improvements.
