# Gcov

## Introduction

Profiling tools help you analyze your code's performance. Using a profiler such as gcov or gprof, you can find out some basic performance statistics, such as:

* How often each line of code executes.
* What lines of code are actually executed.
* How much computing time each section of code uses.

Gcov is a source code coverage analysis and statement-by-statement profiling tool. Gcov generates exact counts of the number of times each statement in a program is executed and annotates source code to add instrumentation. Gcov comes as a standard utility with the GNU Compiler Collection (GCC) suite. It uses two files for profiling:

  * **gcno file**: Option ```-ftest-coverage``` will generate a gcno file when binary is **compiled**. It contains information to reconstruct the basic block graphs and assign source line numbers to blocks.
  * **gcda file**: Option ```-fprofile-arcs``` will generate a gcda file when each object file is **executed**.

gcov will use these files, and the source code to generate a gcov file with the execution info.

## Installation

You already has it:
```
sudo dnf group install 'Development Tools'
```

Additional, to use front-end lcov:
```
sudo dnf install lcov.noarch nodejs-lcov-parse.noarch
```

## Source to test

* cov.c:

```
#include <stdio.h>

int
main (void)
{
  int i;

  for (i = 1; i < 10; i++)
    {
      if (i % 3 == 0)
        printf ("%d is divisible by 3\n", i);
      if (i % 11 == 0)
        printf ("%d is divisible by 11\n", i);
    }

  return 0;
}
```

* Makefile:

```
COMPILER = gcc
SOURCE = cov.c
C_FLAGS = -Wall -fprofile-arcs -ftest-coverage

all:
	${COMPILER} ${C_FLAGS} ${SOURCE}

clean:
	rm -f *.gcov *.out *.gcda *.gcno *.info
	rm -fr out/

# Run before analysis
run:
	./a.out

# Analysis, generate file .gcov
analysis:
	gcov ${SOURCE}
	lcov -t "result" -o coverage.info -c -d .
	genhtml coverage.info --output-directory out

# Launch results
launch:
	firefox out/index.html
```

If you ```make```, ```make run``` and ```make analysis```, a gcov file will be generated containing:

```
gcov cov.c
File 'cov.c'
Lines executed:85.71% of 7
Creating 'cov.c.gcov'
```

and will generate a gcov file containing:

```
-:    0:Source:cov.c
-:    0:Graph:cov.gcno
-:    0:Data:cov.gcda
-:    0:Runs:1
-:    0:Programs:1
-:    1:#include <stdio.h>
-:    2:
-:    3:int
1:    4:main (void)
-:    5:{
-:    6:  int i;
-:    7:
10:    8:  for (i = 1; i < 10; i++)
-:    9:    {
9:   10:      if (i % 3 == 0)
3:   11:        printf ("%d is divisible by 3\n", i);
9:   12:      if (i % 11 == 0)
#####:   13:        printf ("%d is divisible by 11\n", i);
-:   14:    }
-:   15:
1:   16:  return 0;
-:   17:}
```

Use ```make launch``` to see the results in Firefox.

## Command line options

### gcov

* -h (--help): Display help.
* -v (--version): Display the gcov version number.
* -a (--all-blocks): Write individual execution counts for every basic block. Normally gcov outputs execution counts only for the main blocks of a line. With this option you can determine if blocks within a single line are not being executed.
* -b (--branch-probabilities): Write branch frequencies to the output file, and write branch summary info to the standard output. This option allows you to see how often each branch in your program was taken. Unconditional branches will not be shown, unless the -u option is given.
* -c (--branch-counts): Write branch frequencies as the number of branches taken, rather than the percentage of branches taken.
* -n (--no-output): Do not create the gcov output file.
* -l (--long-file-names): Create long file names for included source files. For example, if the header file x.h contains code, and was included in the file a.c, then running gcov on the file a.c will produce an output file called a.c##x.h.gcov instead of x.h.gcov. This can be useful if x.h is included in multiple source files and you want to see the individual contributions. If you use the ''-p' option, both the including and included file names will be complete path names.
* -p (--preserve-paths): Preserve complete path information in the names of generated .gcov files. Without this option, just the filename component is used. With this option, all directories are used, with '/' characters translated to '#' characters, . directory components removed and unremoveable .. components renamed to '^'. This is useful if sourcefiles are in several different directories.
* -r (--relative-only): Only output information about source files with a relative pathname (after source prefix elision). Absolute paths are usually system header files and coverage of any inline functions therein is normally uninteresting.
* -f (--function-summaries): Output summaries for each function in addition to the file level summary.
* -o directory|file (--object-directory directory or --object-file file): Specify either the directory containing the gcov data files, or the object path name. The .gcno, and .gcda data files are searched for using this option. If a directory is specified, the data files are in that directory and named after the input file name, without its extension. If a file is specified here, the data files are named after that file, without its extension.
* -s directory (--source-prefix directory): A prefix for source file names to remove when generating the output coverage files. This option is useful when building in a separate directory, and the pathname to the source directory is not wanted when determining the output file names. Note that this prefix detection is applied before determining whether the source file is absolute.
* -u (--unconditional-branches): When branch probabilities are given, include those of unconditional branches. Unconditional branches are normally not interesting.
* -d (--display-progress): Display the progress on the standard output.

### lcov

* -t: Sets a test name.
* -o: Specify the output file.
* -c: Capture the coverage data.
* -d: Specify the directory where the data files needs to be searched.

## Full explanation

Text extracted from ```gcov-io.h```. File format for coverage information, part of the GCC.

Coverage information is held in two files.  A notes file, which is
generated by the compiler, and a data file, which is generated by
the program under test.  Both files use a similar structure.  We do
not attempt to make these files backwards compatible with previous
versions, as you only need coverage information when developing a
program.  We do hold version information, so that mismatches can be
detected, and we use a format that allows tools to skip information
they do not understand or are not interested in.
Numbers are recorded in the 32 bit unsigned binary form of the
endianness of the machine generating the file. 64 bit numbers are
stored as two 32 bit numbers, the low part first.  Strings are
padded with 1 to 4 NUL bytes, to bring the length up to a multiple
of 4. The number of 4 bytes is stored, followed by the padded
string. Zero length and NULL strings are simply stored as a length
of zero (they have no trailing NUL or padding).

* int32:  ```byte3 byte2 byte1 byte0 | byte0 byte1 byte2 byte3```
* int64:  ```int32:low int32:high```
* string: ```int32:0 | int32:length char* char:0 padding```
* padding: ```| char:0 | char:0 char:0 | char:0 char:0 char:0```
* item: ```int32 | int64 | string```

The basic format of the files is:

* file : ```int32:magic int32:version int32:stamp record*```

The magic ident is different for the notes and the data files.  The
magic ident is used to determine the endianness of the file, when
reading.  The version is the same for both files and is derived
from gcc's version number. The stamp value is used to synchronize
note and data files and to synchronize merging within a data
file. It need not be an absolute time stamp, merely a ticker that
increments fast enough and cycles slow enough to distinguish
different compile/run/compile cycles.
Although the ident and version are formally 32 bit numbers, they
are derived from 4 character ASCII strings.  The version number
consists of a two character major version number
(first digit starts from 'A' letter to not to clash with the older
numbering scheme), the single character minor version number,
and a single character indicating the status of the release.
That will be 'e' experimental, 'p' prerelease and 'r' for release.
Because, by good fortune, these are in alphabetical order, string
collating can be used to compare version strings.  Be aware that
the 'e' designation will (naturally) be unstable and might be
incompatible with itself.  For gcc 17.0 experimental, it would be
'B70e' (0x42373065).  As we currently do not release more than 5 minor
releases, the single character should be always fine.  Major number
is currently changed roughly every year, which gives us space
for next 250 years (maximum allowed number would be 259.9).

A record has a tag, length and variable amount of data.

*	record: ```header data```
* header: ```int32:tag int32:length```
* data: ```item*```

Records are not nested, but there is a record hierarchy.  Tag
numbers reflect this hierarchy.  Tags are unique across note and
data files.  Some record types have a varying amount of data.  The
LENGTH is the number of 4bytes that follow and is usually used to
determine how much data.  The tag value is split into 4 8-bit
fields, one for each of four possible levels.  The most significant
is allocated first.  Unused levels are zero.  Active levels are
odd-valued, so that the LSB of the level is one.  A sub-level
incorporates the values of its superlevels.  This formatting allows
you to determine the tag hierarchy, without understanding the tags
themselves, and is similar to the standard section numbering used
in technical documents.  Level values ```[1..3f]``` are used for common
tags, values ```[41..9f]``` for the notes file and ```[a1..ff]``` for the data
file.

The notes file contains the following records:

*	note: ```unit function-graph*```
* unit: ```header int32:checksum string:source```
* function-graph: ```announce_function basic_blocks {arcs | lines}*```
* announce_function: ```header int32:ident int32:lineno_checksum int32:cfg_checksum```
* string: ```name string:source int32:lineno```
* basic_block: ```header int32:flags*```
* arcs: ```header int32:block_no arc*```
* arc:  ```int32:dest_block int32:flags```
* lines: ```header int32:block_no line* int32:0 string:NULL```
* line:  ```int32:line_no | int32:0 string:filename```

The BASIC_BLOCK record holds per-bb flags.  The number of blocks
can be inferred from its data length.  There is one ARCS record per
basic block.  The number of arcs from a bb is implicit from the
data length.  It enumerates the destination bb and per-arc flags.
There is one LINES record per basic block, it enumerates the source
lines which belong to that basic block.  Source file names are
introduced by a line number of 0, following lines are from the new
source file.  The initial source file for the function is NULL, but
the current source file should be remembered from one LINES record
to the next.  The end of a block is indicated by an empty filename
- this does not reset the current source file.  Note there is no
ordering of the ARCS and LINES records: they may be in any order,
interleaved in any manner.  The current filename follows the order
the LINES records are stored in the file, *not* the ordering of the
blocks they are for.

The data file contains the following records:

* data: ```{unit summary:object summary:program* function-data*}*```
* unit: ```header int32:checksum```
* function-data:	```announce_function present counts```
* announce_function: ```header int32:ident int32:lineno_checksum int32:cfg_checksum```
* present: ```header int32:present```
* counts: ```header int64:count*```
* summary: ```int32:checksum {count-summary}GCOV_COUNTERS_SUMMABLE```
* count-summary: ```int32:num int32:runs int64:sum int64:max int64:sum_max histogram```
* histogram: ```{int32:bitvector}8 histogram-buckets*```
* histogram-buckets: ```int32:num int64:min int64:sum```

The ANNOUNCE_FUNCTION record is the same as that in the note file,
but without the source location.  The COUNTS gives the
counter values for instrumented features.  The about the whole
program.  The checksum is used for whole program summaries, and
disambiguates different programs which include the same
instrumented object file.  There may be several program summaries,
each with a unique checksum.  The object summary's checksum is
zero.  Note that the data file might contain information from
several runs concatenated, or the data might be merged.
This file is included by both the compiler, gcov tools and the
runtime support library libgcov. IN_LIBGCOV and IN_GCOV are used to
distinguish which case is which.  If IN_LIBGCOV is nonzero,
libgcov is being built. If IN_GCOV is nonzero, the gcov tools are
being built. Otherwise the compiler is being built. IN_GCOV may be
positive or negative. If positive, we are compiling a tool that
requires additional functions (see the code for knowledge of what
those functions are).

## Gcov on embedded systems

All of above is real good stuff buf in embedded systems this approach sometimes is not possible because,
for example, we don't have filesystem to write output files to, etc. In this kind of scenaries two approach
are posible but both of them MUST provide its own gcov recollection functions in order to be success with
its task:

* GDB: You can use gdb over a jtag connection and dump info from board memory to a host compuler file.
* UART: you can use the uart to send raw data and have a program in host computer getting it.

### References

* [Gcov on an embedded system](http://sysrun.haifa.il.ibm.com/hrl/greps2007/papers/gcov-on-an-embedded-system.pdf)
* [Use gcov and lcov](https://qiaomuf.wordpress.com/2011/05/26/use-gcov-and-lcov-to-know-your-test-coverage)
* [Coverage](http://www.bullseye.com/coverage.html)
* [Gcov is amazing yet undocumented](http://allsoftwaresucks.blogspot.com.es/2015/05/gcov-is-amazing-yet-undocumented.html)
* [Astarasikov patches](https://github.com/astarasikov/lk/commit/2a4af09a894194dfaff3e05f6fd505241d54d074)
* [Embedded apps code coverage](https://www.pathpartnertech.com/embedded-applications-code-coverage/)
* [Tiny-coverage (GDB approach)](https://github.com/aitorvs/tiny-coverage)
* [Sparc gcov (UART approach in leon2 processors)](https://github.com/aitorvs/sparc-gcov)
* [Code coverage embedded target](http://simply-embedded.blogspot.com.es/2014/07/code-coverage-embedded-target.html)
* [Libgcov embedded](https://github.com/reeteshranjan/libgcov-embedded)


## Bibliography

* [Wikipedia gcov](https://en.wikipedia.org/wiki/Gcov)
* [Wikipedia code coverage](https://en.wikipedia.org/wiki/Code_Coverage)
* [Generating statistics with gcov and lcov](https://codeflu.blog/2014/12/26/using-gcov-and-lcov-to-generate-beautiful-c-code-coverage-statistics/)
* [Gcov file data](https://gcc.gnu.org/onlinedocs/gcc-4.1.0/gcc/Gcov-Data-Files.html)
* [Gcovr python user guide](http://gcovr.com/guide.html)
