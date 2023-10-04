# rabin2的man手册

```bash
RABIN2(1)                                    BSD General Commands Manual                                    RABIN2(1)

NAME
     RABIN2 — Binary program info extractor

SYNOPSIS
     rabin2 [-AceghHiIsSMzlpRrLxvhqQV] [-a arch] [-b bits] [-B addr] [-C fmt:C:[D]] [-D lang sym|-] [-f subbin]
            [-k query] [-K algo] [-O binop] [-o str] [-m addr] [-@ addr] [-n str] [-X fmt file ...] file

DESCRIPTION
     This program allows you to get information about ELF/PE/MZ and CLASS files in a simple way.

     All those commandline flags are also available under the i command in radare2. Type i? for help.

     -@ addr     Show information (symbol, section, import) of the given address

     -A          List sub-binaries and their associated arch-bits pairs

     -a arch     Set arch (x86, arm, .. accepts underscore for bits x86_32)

     -b bits     Set bits (32, 64, ...)

     -B addr     Override baddr

     -c          List classes

     -cc         List classes in header format

     -C [fmt:C[:D]]
                 Create [elf,mach0,pe] for arm and x86-32/64 tiny binaries where 'C' is an hexpair list of the code
                 bytes and ':D' is an optional concatenation to describe the bytes for the data section.

     -d          Show debug/dwarf information

     -D lang symbolname|-
                 Demangle symbol name (or - to read from stdin) for lang (cxx, swift, java, cxx, ..)

     -e          Show entrypoints for disk and on-memory

     -ee         Show constructor/destructors (extended entrypoints)

     -f subbin   Select sub-binary architecture. Useful for fat-mach0 binaries

     -F binfmt   Force to use that bin plugin (ignore header check)

     -g          Show all possible information

     -G addr     Load address . offset to header

     -h          Show usage help message.

     -H          Show header fields (see ih command in r2)

     -I          Show binary info (iI in r2)

     -i          Show imports (symbols imported from libraries) (ii)

     -j          Output in json

     -k query    Perform SDB query on loaded file

     -K algo     Select a rahash2 checksum algorithm to be performed on sections listing (and maybe others in the
                 future) i.e 'rabin2 -K md5 -S /bin/ls'

     -l          List linked libraries to the binary

     -L          List supported bin plugins

     -M          Show address of 'main' symbol

     -m addr     Show source line reference from a given address

     -N minlen:maxlen
                 Force minimum and maximum number of chars per string (see -z and -zz). if (strlen>minlen && (!maxlen
                 || strlen<=maxlen))

     -n str      Show information (symbol, section, import) at string offset

     -o str      Output file/folder for write operations (out by default)

     -O binop    Perform binary operation on target binary (dump, resize, change sections, ...) see '-O help' for
                 more information

     -p          Disable VA. Show physical addresses

     -P          Show debug/pdb information

     -PP         Download pdb file for binary

     -q          Be quiet, just show fewer data

     -qq         Show less info (no offset/size for -z for ex.)

     -Q          Show load address used by dlopen (non-aslr libs)

     -r          Show output in radare format

     -R          Show realocations

     -s          Show exported symbols

     -S          Show sections

     -u          Unfiltered (no rename duplicated symbols/sections)

     -v          Show version information

     -V          Show binary version information

     -x          Extract all sub binaries from a fat binary (f.ex: fatmach0)

     -X format file ...
                 Package a fat or zip containing all the files passed (fat, zip)

     -z          Show strings inside .data section (like gnu strings does)

     -Z          Guess size of binary program

     -zz         Shows strings from raw bins

     -zzz        Dump raw strings to stdout (for huge files)

ENVIRONMENT
     RABIN2_LANG same as r2 -e bin.lang for rabin2

     RABIN2_DEMANGLE demangle symbols

     RABIN2_MAXSTRBUF same as r2 -e bin.maxstrbuf for rabin2

     RABIN2_DEBASE64 try to decode all strings as base64 if possible

     RABIN2_STRFILTER same as r2 -e bin.strfilter for rabin2

     RABIN2_STRPURGE same as r2 -e bin.strpurge for rabin2

EXAMPLES
     List symbols of a program

       $ rabin2 -s a.out

     Get offset of symbol

       $ rabin2 -n _main a.out

     Get entrypoint

       $ rabin2 -e a.out

     Load symbols and imports from radare2

       $ r2 -n /bin/ls
       [0x00000000]> .!rabin2 -prsi $FILE

SEE ALSO
     rahash2(1), rafind2(1), radare2(1), radiff2(1), rasm2(1), rax2(1), rsc2(1), ragg2(1), rarun2(1),

AUTHORS
     Written by pancake <pancake@nopcode.org>.

                                                     Sep 29, 2016
```
