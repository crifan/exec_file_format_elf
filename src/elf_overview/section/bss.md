# .bss

Uninitialized global data ("Block Started by Symbol").

Depending on the compilers, uninitialized global variables could be stored in a nameness section called COMMON (named after Fortran 77's "common blocks".) To wit, consider the following code:

```c
    int globalVar;
    static int globalStaticVar;
    void dummy() {
       static int localStaticVar;
    }
```

Compile with gcc -c, then on x86_64, the resulting object file has the following structure:

```bash
    $ objdump -t foo.o

    SYMBOL TABLE:
     ....
    0000000000000000 l     O .bss   0000000000000004 globalStaticVar
    0000000000000004 l     O .bss   0000000000000004 localStaticVar.1619
     ....
    0000000000000004       O *COM*  0000000000000004 globalVar
```

so only the file-scope and local-scope global variables are in the .bss section.
If one wants globalVar to reside in the .bss section, use the -fno-common compiler command-line option. Using -fno-common is encouraged, as the following example shows:

```bash
    $ cat foo.c
    int globalVar;
    $ cat bar.c
    double globalVar;
    int main(){}
    $ gcc foo.c bar.c
```

Not only there is no error message about redefinition of the same symbol in both source files (notice we did not use the extern keyword here), there is no complaint about their different data types and sizes either. However, if one uses -fno-common, the compiler will complain:

```bash
    /tmp/ccM71JR7.o:(.bss+0x0): multiple definition of `globalVar'
    /tmp/ccIbS5MO.o:(.bss+0x0): first defined here
    ld: Warning: size of symbol `globalVar' changed from 8 in /tmp/ccIbS5MO.o to 4 in /tmp/ccM71JR7.o
```
