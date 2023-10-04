# objdump用法举例

* 输入文件：ELF格式的`libtacker.so`

用objdump读取解析ELF的`libtacker.so`的效果：

## -a：显示存档文件头信息

```bash
➜  arm64-v8a objdump -a libtacker.so

libtacker.so:    file format elf64-littleaarch64
```

## -f：显示全部文件头信息

```bash
➜  arm64-v8a objdump -f libtacker.so

libtacker.so:    file format elf64-littleaarch64
architecture: aarch64
start address: 0x000000000001a5c0
```

## -h：显示节的头信息

```bash
➜  arm64-v8a objdump -h libtacker.so

libtacker.so:    file format elf64-littleaarch64

Sections:
Idx Name                Size     VMA              Type
  0                     00000000 0000000000000000
  1 .note.android.ident 00000098 0000000000000238
  2 .note.gnu.build-id  00000024 00000000000002d0
  3 .dynsym             00000b10 00000000000002f8
  4 .gnu.version        000000ec 0000000000000e08
  5 .gnu.version_r      00000040 0000000000000ef4
  6 .gnu.hash           000001ec 0000000000000f38
  7 .hash               000003b8 0000000000001124
  8 .dynstr             00000c19 00000000000014dc
  9 .rela.dyn           00008850 00000000000020f8
 10 .rela.plt           00000450 000000000000a948
 11 .gcc_except_table   00001960 000000000000ad98 DATA
 12 .rodata             00003434 000000000000c6f8 DATA
 13 .eh_frame_hdr       00001dbc 000000000000fb2c DATA
 14 .eh_frame           00008cd4 00000000000118e8 DATA
 15 .text               000aec60 000000000001a5c0 TEXT
 16 .plt                00000300 00000000000c9220 TEXT
 17 .data.rel.ro        00002eb8 00000000000ca520 DATA
 18 .fini_array         00000010 00000000000cd3d8
 19 .init_array         00000230 00000000000cd3e8
 20 .dynamic            000001d0 00000000000cd618
 21 .got                000000c0 00000000000cd7e8 DATA
 22 .got.plt            00000188 00000000000cd8a8 DATA
 23 .data               000025d8 00000000000cea30 DATA
 24 .bss                00000ad0 00000000000d1010 BSS
 25 .comment            000000c6 0000000000000000
 26 .shstrtab           00000104 0000000000000000
```

## -x：显示全部头信息

```bash
➜  arm64-v8a objdump -x libtacker.so

libtacker.so:    file format elf64-littleaarch64
architecture: aarch64
start address: 0x000000000001a5c0

Program Header:
    PHDR off    0x0000000000000040 vaddr 0x0000000000000040 paddr 0x0000000000000040 align 2**3
         filesz 0x00000000000001f8 memsz 0x00000000000001f8 flags r--
    LOAD off    0x0000000000000000 vaddr 0x0000000000000000 paddr 0x0000000000000000 align 2**12
         filesz 0x00000000000c9520 memsz 0x00000000000c9520 flags r-x
    LOAD off    0x00000000000c9520 vaddr 0x00000000000ca520 paddr 0x00000000000ca520 align 2**12
         filesz 0x0000000000003510 memsz 0x0000000000003510 flags rw-
    LOAD off    0x00000000000cca30 vaddr 0x00000000000cea30 paddr 0x00000000000cea30 align 2**12
         filesz 0x00000000000025d8 memsz 0x00000000000030b0 flags rw-
 DYNAMIC off    0x00000000000cc618 vaddr 0x00000000000cd618 paddr 0x00000000000cd618 align 2**3
         filesz 0x00000000000001d0 memsz 0x00000000000001d0 flags rw-
   RELRO off    0x00000000000c9520 vaddr 0x00000000000ca520 paddr 0x00000000000ca520 align 2**0
         filesz 0x0000000000003510 memsz 0x0000000000003ae0 flags r--
EH_FRAME off    0x000000000000fb2c vaddr 0x000000000000fb2c paddr 0x000000000000fb2c align 2**2
         filesz 0x0000000000001dbc memsz 0x0000000000001dbc flags r--
   STACK off    0x0000000000000000 vaddr 0x0000000000000000 paddr 0x0000000000000000 align 2**64
         filesz 0x0000000000000000 memsz 0x0000000000000000 flags rw-
    NOTE off    0x0000000000000238 vaddr 0x0000000000000238 paddr 0x0000000000000238 align 2**2
         filesz 0x00000000000000bc memsz 0x00000000000000bc flags r--

Dynamic Section:
  NEEDED       liblog.so
  NEEDED       libm.so
  NEEDED       libdl.so
  NEEDED       libc.so
  SONAME       libforce.so
  FLAGS        0x0000000000000008
  FLAGS_1      0x0000000000000001
  RELA         0x00000000000020f8
  RELASZ       0x0000000000008850
  RELAENT      0x0000000000000018
  RELACOUNT    0x0000000000000568
  JMPREL       0x000000000000a948
  PLTRELSZ     0x0000000000000450
  PLTGOT       0x00000000000cd8a8
  PLTREL       0x0000000000000007
  SYMTAB       0x00000000000002f8
  SYMENT       0x0000000000000018
  STRTAB       0x00000000000014dc
  STRSZ        0x0000000000000c19
  GNU_HASH     0x0000000000000f38
  HASH         0x0000000000001124
  INIT_ARRAY   0x00000000000cd3e8
  INIT_ARRAYSZ 0x0000000000000230
  FINI_ARRAY   0x00000000000cd3d8
  FINI_ARRAYSZ 0x0000000000000010
  VERSYM       0x0000000000000e08
  VERNEED      0x0000000000000ef4
  VERNEEDNUM   0x0000000000000002

Version References:
  required from libdl.so:
    0x00050d63 0x00 03 LIBC
  required from libc.so:
    0x00050d63 0x00 02 LIBC

Sections:
Idx Name                Size     VMA              Type
  0                     00000000 0000000000000000
  1 .note.android.ident 00000098 0000000000000238
  2 .note.gnu.build-id  00000024 00000000000002d0
  3 .dynsym             00000b10 00000000000002f8
  4 .gnu.version        000000ec 0000000000000e08
  5 .gnu.version_r      00000040 0000000000000ef4
  6 .gnu.hash           000001ec 0000000000000f38
  7 .hash               000003b8 0000000000001124
  8 .dynstr             00000c19 00000000000014dc
  9 .rela.dyn           00008850 00000000000020f8
 10 .rela.plt           00000450 000000000000a948
 11 .gcc_except_table   00001960 000000000000ad98 DATA
 12 .rodata             00003434 000000000000c6f8 DATA
 13 .eh_frame_hdr       00001dbc 000000000000fb2c DATA
 14 .eh_frame           00008cd4 00000000000118e8 DATA
 15 .text               000aec60 000000000001a5c0 TEXT
 16 .plt                00000300 00000000000c9220 TEXT
 17 .data.rel.ro        00002eb8 00000000000ca520 DATA
 18 .fini_array         00000010 00000000000cd3d8
 19 .init_array         00000230 00000000000cd3e8
 20 .dynamic            000001d0 00000000000cd618
 21 .got                000000c0 00000000000cd7e8 DATA
 22 .got.plt            00000188 00000000000cd8a8 DATA
 23 .data               000025d8 00000000000cea30 DATA
 24 .bss                00000ad0 00000000000d1010 BSS
 25 .comment            000000c6 0000000000000000
 26 .shstrtab           00000104 0000000000000000

SYMBOL TABLE:
```

## -d：反汇编可执行指令的内容

### text段反汇编

相关参数：

```bash
       -d
       --disassemble
       --disassemble=symbol
           Display the assembler mnemonics for the machine instructions
           from the input file.  This option only disassembles those
           sections which are expected to contain instructions.  If the
           optional symbol argument is given, then display the assembler
           mnemonics starting at symbol.  If symbol is a function name
           then disassembly will stop at the end of the function,
           otherwise it will stop when the next symbol is encountered.
           If there are no matches for symbol then nothing will be
           displayed.

           Note if the --dwarf=follow-links option is enabled then any
           symbol tables in linked debug info files will be read in and
           used when disassembling.

       -j name
       --section=name
           Display information only for section name.
```

->

```bash
➜  arm64-v8a objdump -d -j .text libtacker.so
...
   c8e54: 60 ca 00 39      strb    w0, [x19, #50]
   c8e58: e8 02 40 39      ldrb    w8, [x23]
   c8e5c: 1f e9 01 71      cmp    w8, #122
   c8e60: 80 01 00 54      b.eq    0xc8e90 <.datadiv_decode2444497212690810360+0x1e4bc>
   c8e64: 44 00 00 14      b    0xc8f74 <.datadiv_decode2444497212690810360+0x1e5a0>
   c8e68: 20 fa ff 90      adrp    x0, 0xc000 <.datadiv_decode2444497212690810360+0x1e1a4>
   c8e6c: 00 ec 3d 91      add    x0, x0, #3963
   c8e70: 46 00 00 14      b    0xc8f88 <.datadiv_decode2444497212690810360+0x1e5b4>
   c8e74: a0 63 00 91      add    x0, x29, #24
   c8e78: e1 03 16 aa      mov    x1, x22
   c8e7c: b5 fa ff 97      bl    0xc7950 <.datadiv_decode2444497212690810360+0x1cf7c>
   c8e80: 60 ca 00 39      strb    w0, [x19, #50]
   c8e84: e8 02 40 39      ldrb    w8, [x23]
   c8e88: 1f e9 01 71      cmp    w8, #122
   c8e8c: 41 07 00 54      b.ne    0xc8f74 <.datadiv_decode2444497212690810360+0x1e5a0>
   c8e90: a0 63 00 91      add    x0, x29, #24
   c8e94: e1 03 16 aa      mov    x1, x22
   c8e98: ae fa ff 97      bl    0xc7950 <.datadiv_decode2444497212690810360+0x1cf7c>
   c8e9c: 38 fa ff f0      adrp    x24, 0xf000 <.datadiv_decode2444497212690810360+0x1e1e4>
   c8ea0: 18 73 25 91      add    x24, x24, #2396
   c8ea4: 39 00 80 52      mov    w25, #1
   c8ea8: 05 00 00 14      b    0xc8ebc <.datadiv_decode2444497212690810360+0x1e4e8>
   c8eac: 9f 24 03 d5      hint    #36
   c8eb0: 79 ce 00 39      strb    w25, [x19, #51]
   c8eb4: 9f 24 03 d5      hint    #36
   c8eb8: f7 06 00 91      add    x23, x23, #1
...
   c9174: 10 7c 40 f9      ldr    x16, [x0, #248]
   c9178: 00 04 40 a9      ldp    x0, x1, [x0]
   c917c: 1f 02 00 91      mov    sp, x16
   c9180: c0 03 5f d6      ret
   c9184: 5f 24 03 d5      hint    #34
   c9188: 00 04 00 a9      stp    x0, x1, [x0]
   c918c: 02 0c 01 a9      stp    x2, x3, [x0, #16]
   c9190: 04 14 02 a9      stp    x4, x5, [x0, #32]
   c9194: 06 1c 03 a9      stp    x6, x7, [x0, #48]
   c9198: 08 24 04 a9      stp    x8, x9, [x0, #64]
   c919c: 0a 2c 05 a9      stp    x10, x11, [x0, #80]
   c91a0: 0c 34 06 a9      stp    x12, x13, [x0, #96]
   c91a4: 0e 3c 07 a9      stp    x14, x15, [x0, #112]
   c91a8: 10 44 08 a9      stp    x16, x17, [x0, #128]
   c91ac: 12 4c 09 a9      stp    x18, x19, [x0, #144]
   c91b0: 14 54 0a a9      stp    x20, x21, [x0, #160]
   c91b4: 16 5c 0b a9      stp    x22, x23, [x0, #176]
   c91b8: 18 64 0c a9      stp    x24, x25, [x0, #192]
   c91bc: 1a 6c 0d a9      stp    x26, x27, [x0, #208]
   c91c0: 1c 74 0e a9      stp    x28, x29, [x0, #224]
   c91c4: 1e 78 00 f9      str    x30, [x0, #240]
   c91c8: e1 03 00 91      mov    x1, sp
   c91cc: 01 7c 00 f9      str    x1, [x0, #248]
   c91d0: 1e 80 00 f9      str    x30, [x0, #256]
   c91d4: 00 04 11 6d      stp    d0, d1, [x0, #272]
   c91d8: 02 0c 12 6d      stp    d2, d3, [x0, #288]
   c91dc: 04 14 13 6d      stp    d4, d5, [x0, #304]
   c91e0: 06 1c 14 6d      stp    d6, d7, [x0, #320]
   c91e4: 08 24 15 6d      stp    d8, d9, [x0, #336]
   c91e8: 0a 2c 16 6d      stp    d10, d11, [x0, #352]
   c91ec: 0c 34 17 6d      stp    d12, d13, [x0, #368]
   c91f0: 0e 3c 18 6d      stp    d14, d15, [x0, #384]
   c91f4: 10 44 19 6d      stp    d16, d17, [x0, #400]
   c91f8: 12 4c 1a 6d      stp    d18, d19, [x0, #416]
   c91fc: 14 54 1b 6d      stp    d20, d21, [x0, #432]
   c9200: 16 5c 1c 6d      stp    d22, d23, [x0, #448]
   c9204: 18 64 1d 6d      stp    d24, d25, [x0, #464]
   c9208: 1a 6c 1e 6d      stp    d26, d27, [x0, #480]
   c920c: 1c 74 1f 6d      stp    d28, d29, [x0, #496]
   c9210: 1e 00 01 fd      str    d30, [x0, #512]
   c9214: 1f 04 01 fd      str    d31, [x0, #520]
   c9218: 00 00 80 d2      mov    x0, #0
   c921c: c0 03 5f d6      ret
```

内容太多了。

看来是把全部的汇编都反编译了。

### reloc段反汇编

相关参数：

```bash
       -d
       --disassemble
       --disassemble=symbol
           Display the assembler mnemonics for the machine instructions
           from the input file.  This option only disassembles those
           sections which are expected to contain instructions.  If the
           optional symbol argument is given, then display the assembler
           mnemonics starting at symbol.  If symbol is a function name
           then disassembly will stop at the end of the function,
           otherwise it will stop when the next symbol is encountered.
           If there are no matches for symbol then nothing will be
           displayed.


           Note if the --dwarf=follow-links option is enabled then any
           symbol tables in linked debug info files will be read in and
           used when disassembling.


       -r
       --reloc
           Print the relocation entries of the file.  If used with -d or
           -D, the relocations are printed interspersed with the
           disassembly.
```

->

```bash
➜  arm64-v8a objdump -d -r libtacker.so > libtacker_objdump_d_r.coffee

libtacker.so:    file format elf64-littleaarch64


Disassembly of section .text:


000000000001a5c0 <.text>:
   1a5c0: 5f 24 03 d5      hint    #34
   1a5c4: 80 05 00 90      adrp    x0, 0xca000 <.text+0x2c4>
   1a5c8: 00 80 14 91      add    x0, x0, #1312
   1a5cc: 1d bb 02 14      b    0xc9240 <__cxa_finalize@plt>
   1a5d0: 5f 24 03 d5      hint    #34
   1a5d4: c0 03 5f d6      ret
   1a5d8: 5f 24 03 d5      hint    #34
   1a5dc: ac a9 02 14      b    0xc4c8c <.datadiv_decode2444497212690810360+0x1a2b8>
   1a5e0: 5f 24 03 d5      hint    #34
   1a5e4: 60 00 00 b4      cbz    x0, 0x1a5f0 <.text+0x30>
   1a5e8: f0 03 00 aa      mov    x16, x0
   1a5ec: 00 02 1f d6      br    x16
   1a5f0: c0 03 5f d6      ret
   1a5f4: 5f 24 03 d5      hint    #34
   1a5f8: 08 00 00 90      adrp    x8, 0x1a000 <.text+0x38>
   1a5fc: 08 81 17 91      add    x8, x8, #1504
   1a600: 82 05 00 90      adrp    x2, 0xca000 <.text+0x300>
   1a604: 42 80 14 91      add    x2, x2, #1312
...
   2e11c: 08 b6 b3 72      movk    w8, #40368, lsl #16
   2e120: 1f 01 17 6b      cmp    w8, w23
   2e124: 60 01 00 54      b.eq    0x2e150 <.datadiv_decode17838636323198310142+0x2820>
   2e128: 1f 01 16 6b      cmp    w8, w22
   2e12c: a1 ff ff 54      b.ne    0x2e120 <.datadiv_decode17838636323198310142+0x27f0>
   2e130: e0 03 14 aa      mov    x0, x20
   2e134: e1 03 13 aa      mov    x1, x19
   2e138: e2 03 15 2a      mov    w2, w21
   2e13c: e3 03 1f 2a      mov    w3, wzr
   2e140: 03 08 00 94      bl    0x3014c <.datadiv_decode8952246851265070369+0x6b4>
   2e144: 28 95 94 52      mov    w8, #42153
   2e148: a8 a2 a4 72      movk    w8, #9493, lsl #16
   2e14c: f5 ff ff 17      b    0x2e120 <.datadiv_decode17838636323198310142+0x27f0>
   2e150: f4 4f 43 a9      ldp    x20, x19, [sp, #48]
   2e154: f6 57 42 a9      ldp    x22, x21, [sp, #32]
   2e158: f7 0b 40 f9      ldr    x23, [sp, #16]
   2e15c: fd 7b c4 a8      ldp    x29, x30, [sp], #64
   2e160: c0 03 5f d6      ret
   2e164: ff 43 01 d1      sub    sp, sp, #80
   2e168: fd 7b 02 a9      stp    x29, x30, [sp, #32]
   2e16c: fd 83 00 91      add    x29, sp, #32
...


000000000002e2bc <.datadiv_decode18328417529454547004>:
   2e2bc: fd 7b ba a9      stp    x29, x30, [sp, #-96]!
   2e2c0: fc 6f 01 a9      stp    x28, x27, [sp, #16]
   2e2c4: fa 67 02 a9      stp    x26, x25, [sp, #32]
   2e2c8: f8 5f 03 a9      stp    x24, x23, [sp, #48]
   2e2cc: f6 57 04 a9      stp    x22, x21, [sp, #64]
   2e2d0: f4 4f 05 a9      stp    x20, x19, [sp, #80]
   2e2d4: 01 05 00 90      adrp    x1, 0xce000 <.datadiv_decode18328417529454547004+0x298>
   2e2d8: d1 0e 80 52      mov    w17, #118
   2e2dc: 21 c0 33 91      add    x1, x1, #3312
   2e2e0: 69 0b 80 52      mov    w9, #91
   2e2e4: 6f 0b 80 12      mov    w15, #-92
   2e2e8: a0 05 80 12      mov    w0, #-46
   2e2ec: d0 0e 80 12      mov    w16, #-119
   2e2f0: cd 02 80 52      mov    w13, #22
   2e2f4: 28 00 40 39      ldrb    w8, [x1]
   2e2f8: 85 0d 80 12      mov    w5, #-109
   2e2fc: 95 0d 80 52      mov    w21, #108
   2e300: 27 0e 80 52      mov    w7, #113
   2e304: 43 0f 80 52      mov    w3, #122
   2e308: 19 0d 80 52      mov    w25, #104
   2e30c: ea 03 28 2a      mvn    w10, w8
   2e310: 0b 01 28 0a      bic    w11, w8, w8
   2e314: 0c 05 1a 12      and    w12, w8, #0xc0
...


   c913c: 06 1c 54 6d      ldp    d6, d7, [x0, #320]
   c9140: 08 24 55 6d      ldp    d8, d9, [x0, #336]
   c9144: 0a 2c 56 6d      ldp    d10, d11, [x0, #352]
   c9148: 0c 34 57 6d      ldp    d12, d13, [x0, #368]
   c914c: 0e 3c 58 6d      ldp    d14, d15, [x0, #384]
   c9150: 10 44 59 6d      ldp    d16, d17, [x0, #400]
   c9154: 12 4c 5a 6d      ldp    d18, d19, [x0, #416]
   c9158: 14 54 5b 6d      ldp    d20, d21, [x0, #432]
   c915c: 16 5c 5c 6d      ldp    d22, d23, [x0, #448]
   c9160: 18 64 5d 6d      ldp    d24, d25, [x0, #464]
   c9164: 1a 6c 5e 6d      ldp    d26, d27, [x0, #480]
   c9168: 1c 74 5f 6d      ldp    d28, d29, [x0, #496]
   c916c: 1e 00 41 fd      ldr    d30, [x0, #512]
   c9170: 1f 04 41 fd      ldr    d31, [x0, #520]
   c9174: 10 7c 40 f9      ldr    x16, [x0, #248]
   c9178: 00 04 40 a9      ldp    x0, x1, [x0]
   c917c: 1f 02 00 91      mov    sp, x16
   c9180: c0 03 5f d6      ret
   c9184: 5f 24 03 d5      hint    #34
   c9188: 00 04 00 a9      stp    x0, x1, [x0]
   c918c: 02 0c 01 a9      stp    x2, x3, [x0, #16]
   c9190: 04 14 02 a9      stp    x4, x5, [x0, #32]
   c9194: 06 1c 03 a9      stp    x6, x7, [x0, #48]
   c9198: 08 24 04 a9      stp    x8, x9, [x0, #64]
   c919c: 0a 2c 05 a9      stp    x10, x11, [x0, #80]
   c91a0: 0c 34 06 a9      stp    x12, x13, [x0, #96]
   c91a4: 0e 3c 07 a9      stp    x14, x15, [x0, #112]
   c91a8: 10 44 08 a9      stp    x16, x17, [x0, #128]
   c91ac: 12 4c 09 a9      stp    x18, x19, [x0, #144]
   c91b0: 14 54 0a a9      stp    x20, x21, [x0, #160]
   c91b4: 16 5c 0b a9      stp    x22, x23, [x0, #176]
   c91b8: 18 64 0c a9      stp    x24, x25, [x0, #192]
   c91bc: 1a 6c 0d a9      stp    x26, x27, [x0, #208]
   c91c0: 1c 74 0e a9      stp    x28, x29, [x0, #224]
   c91c4: 1e 78 00 f9      str    x30, [x0, #240]
   c91c8: e1 03 00 91      mov    x1, sp
   c91cc: 01 7c 00 f9      str    x1, [x0, #248]
   c91d0: 1e 80 00 f9      str    x30, [x0, #256]
   c91d4: 00 04 11 6d      stp    d0, d1, [x0, #272]
   c91d8: 02 0c 12 6d      stp    d2, d3, [x0, #288]
   c91dc: 04 14 13 6d      stp    d4, d5, [x0, #304]
   c91e0: 06 1c 14 6d      stp    d6, d7, [x0, #320]
   c91e4: 08 24 15 6d      stp    d8, d9, [x0, #336]
   c91e8: 0a 2c 16 6d      stp    d10, d11, [x0, #352]
   c91ec: 0c 34 17 6d      stp    d12, d13, [x0, #368]
   c91f0: 0e 3c 18 6d      stp    d14, d15, [x0, #384]
   c91f4: 10 44 19 6d      stp    d16, d17, [x0, #400]
   c91f8: 12 4c 1a 6d      stp    d18, d19, [x0, #416]
   c91fc: 14 54 1b 6d      stp    d20, d21, [x0, #432]
   c9200: 16 5c 1c 6d      stp    d22, d23, [x0, #448]
   c9204: 18 64 1d 6d      stp    d24, d25, [x0, #464]
   c9208: 1a 6c 1e 6d      stp    d26, d27, [x0, #480]
   c920c: 1c 74 1f 6d      stp    d28, d29, [x0, #496]
   c9210: 1e 00 01 fd      str    d30, [x0, #512]
   c9214: 1f 04 01 fd      str    d31, [x0, #520]
   c9218: 00 00 80 d2      mov    x0, #0
   c921c: c0 03 5f d6      ret


Disassembly of section .plt:


00000000000c9220 <.plt>:
   c9220: f0 7b bf a9      stp    x16, x30, [sp, #-16]!
   c9224: 30 00 00 90      adrp    x16, 0xcd000 <.plt+0x14>
   c9228: 11 5e 44 f9      ldr    x17, [x16, #2232]
   c922c: 10 e2 22 91      add    x16, x16, #2232
   c9230: 20 02 1f d6      br    x17
   c9234: 1f 20 03 d5      nop
   c9238: 1f 20 03 d5      nop
   c923c: 1f 20 03 d5      nop


00000000000c9240 <__cxa_finalize@plt>:
   c9240: 30 00 00 90      adrp    x16, 0xcd000 <__cxa_atexit@plt>
   c9244: 11 62 44 f9      ldr    x17, [x16, #2240]
   c9248: 10 02 23 91      add    x16, x16, #2240
   c924c: 20 02 1f d6      br    x17

...

00000000000c9370 <strlen@plt>:
   c9370: 30 00 00 90      adrp    x16, 0xcd000 <realloc@plt>
   c9374: 11 ae 44 f9      ldr    x17, [x16, #2392]
   c9378: 10 62 25 91      add    x16, x16, #2392
   c937c: 20 02 1f d6      br    x17

...

00000000000c9480 <getauxval@plt>:
   c9480: 30 00 00 90      adrp    x16, 0xcd000 <__system_property_get@plt>
   c9484: 11 f2 44 f9      ldr    x17, [x16, #2528]
   c9488: 10 82 27 91      add    x16, x16, #2528
   c948c: 20 02 1f d6      br    x17


00000000000c9490 <__system_property_get@plt>:
   c9490: 30 00 00 90      adrp    x16, 0xcd000 <strncmp@plt>
   c9494: 11 f6 44 f9      ldr    x17, [x16, #2536]
   c9498: 10 a2 27 91      add    x16, x16, #2536
   c949c: 20 02 1f d6      br    x17


00000000000c94a0 <strncmp@plt>:
   c94a0: 30 00 00 90      adrp    x16, 0xcd000 <fprintf@plt>
   c94a4: 11 fa 44 f9      ldr    x17, [x16, #2544]
   c94a8: 10 c2 27 91      add    x16, x16, #2544
   c94ac: 20 02 1f d6      br    x17

...

00000000000c94e0 <pthread_rwlock_unlock@plt>:
   c94e0: 30 00 00 90      adrp    x16, 0xcd000 <dl_iterate_phdr@plt>
   c94e4: 11 0a 45 f9      ldr    x17, [x16, #2576]
   c94e8: 10 42 28 91      add    x16, x16, #2576
   c94ec: 20 02 1f d6      br    x17


00000000000c94f0 <dl_iterate_phdr@plt>:
   c94f0: 30 00 00 90      adrp    x16, 0xcd000 <pthread_rwlock_rdlock@plt>
   c94f4: 11 0e 45 f9      ldr    x17, [x16, #2584]
   c94f8: 10 62 28 91      add    x16, x16, #2584
   c94fc: 20 02 1f d6      br    x17


00000000000c9500 <pthread_rwlock_rdlock@plt>:
   c9500: 30 00 00 90      adrp    x16, 0xcd000 <fwrite@plt>
   c9504: 11 12 45 f9      ldr    x17, [x16, #2592]
   c9508: 10 82 28 91      add    x16, x16, #2592
   c950c: 20 02 1f d6      br    x17


00000000000c9510 <fwrite@plt>:
   c9510: 30 00 00 90      adrp    x16, 0xcd000 <fwrite@plt+0x10>
   c9514: 11 16 45 f9      ldr    x17, [x16, #2600]
   c9518: 10 a2 28 91      add    x16, x16, #2600
   c951c: 20 02 1f d6      br    x17
```

## -s：显示每个节的内容

```bash
➜  arm64-v8a objdump -s libtacker.so > libtacker_objdump_s.coffee
...
libtacker.so:    file format elf64-littleaarch64
Contents of section .note.android.ident:
 0238 08000000 84000000 01000000 416e6472  ............Andr
 0248 6f696400 15000000 72323400 00000000  oid.....r24.....
 0258 00000000 00000000 00000000 00000000  ................
 0268 00000000 00000000 00000000 00000000  ................
 0278 00000000 00000000 00000000 00000000  ................
 0288 00000000 00000000 38323135 38383800  ........8215888.
 0298 00000000 00000000 00000000 00000000  ................
 02a8 00000000 00000000 00000000 00000000  ................
 02b8 00000000 00000000 00000000 00000000  ................
 02c8 00000000 00000000                    ........
Contents of section .note.gnu.build-id:
 02d0 04000000 14000000 03000000 474e5500  ............GNU.
 02e0 3a269496 ef440c78 5356664f 89464681  :&...D.xSVfO.FF.
 02f0 5d3c61ad                             ]<a.
Contents of section .dynsym:
 02f8 00000000 00000000 00000000 00000000  ................
 0308 00000000 00000000 01000000 12000000  ................
 0318 00000000 00000000 00000000 00000000  ................
 0328 10000000 12000000 00000000 00000000  ................
 0338 00000000 00000000 1d000000 12000000  ................
 0348 00000000 00000000 00000000 00000000  ................
。。。
 d0f70 5a565416 5f564b5a 5c165849 49165550  ZVT._VKZ\.XII.UP
 d0f80 5b167758 4d504f5c 715c5549 5c4b3900  [.wXMPO\q\UI\K9.
 d0f90 a9cde0ef e5f3eee8 e5aee0f1 f1aec0f1  ................
 d0fa0 f1ede8e2 e0f5e8ee efbaa8d7 81000000  ................
 d0fb0 10000000 00000000 08000000 00000000  ................
 d0fc0 00000000 00000000 00000000 00000000  ................
 d0fd0 00000000 00000000 00000000 00000000  ................
 d0fe0 00000000 00000000 00000000 00000000  ................
 d0ff0 00000000 00000000 00000000 00000000  ................
 d1000 00000000 00000000                    ........
Contents of section .bss:
<skipping contents of bss section at [d1010, d1ae0)>
Contents of section .comment:
 0000 4c696e6b 65723a20 4c4c4420 31342e30  Linker: LLD 14.0
 0010 2e310063 6c616e67 20766572 73696f6e  .1.clang version
 0020 2031342e 302e3000 416e6472 6f696420   14.0.0.Android 
 0030 28383037 35313738 2c206261 73656420  (8075178, based 
 0040 6f6e2072 34333731 31326229 20636c61  on r437112b) cla
 0050 6e672076 65727369 6f6e2031 342e302e  ng version 14.0.
 0060 31202868 74747073 3a2f2f61 6e64726f  1 (https://andro
 0070 69642e67 6f6f676c 65736f75 7263652e  id.googlesource.
 0080 636f6d2f 746f6f6c 63686169 6e2f6c6c  com/toolchain/ll
 0090 766d2d70 726f6a65 63742038 36373133  vm-project 86713
 00a0 34386238 31623935 66633630 33353035  48b81b95fc603505
 00b0 64666338 38316234 35313033 62656531  dfc881b45103bee1
 00c0 37333129 0000                        731)..
Contents of section .shstrtab:
 0000 002e696e 69745f61 72726179 002e6669  ..init_array..fi
 0010 6e695f61 72726179 002e7465 7874002e  ni_array..text..
 0020 676f7400 2e636f6d 6d656e74 002e6e6f  got..comment..no
 0030 74652e61 6e64726f 69642e69 64656e74  te.android.ident
 0040 002e676f 742e706c 74002e72 656c612e  ..got.plt..rela.
 0050 706c7400 2e627373 002e6479 6e737472  plt..bss..dynstr
 0060 002e6568 5f667261 6d655f68 6472002e  ..eh_frame_hdr..
 0070 676e752e 76657273 696f6e5f 72002e64  gnu.version_r..d
 0080 6174612e 72656c2e 726f002e 72656c61  ata.rel.ro..rela
 0090 2e64796e 002e676e 752e7665 7273696f  .dyn..gnu.versio
 00a0 6e002e64 796e7379 6d002e67 6e752e68  n..dynsym..gnu.h
 00b0 61736800 2e65685f 6672616d 65002e67  ash..eh_frame..g
 00c0 63635f65 78636570 745f7461 626c6500  cc_except_table.
 00d0 2e6e6f74 652e676e 752e6275 696c642d  .note.gnu.build-
 00e0 6964002e 64796e61 6d696300 2e736873  id..dynamic..shs
 00f0 74727461 62002e72 6f646174 61002e64  trtab..rodata..d
 0100 61746100                             ata.
```

## -t：显示符号表

```bash
➜  arm64-v8a objdump -t libtacker.so

libtacker.so:    file format elf64-littleaarch64

SYMBOL TABLE:
```

## -T：显示动态符号表

```bash
➜  arm64-v8a objdump -T libtacker.so


libtacker.so:    file format elf64-littleaarch64


DYNAMIC SYMBOL TABLE:
0000000000000000      DF *UND*    0000000000000000 (LIBC)       __cxa_finalize
0000000000000000      DF *UND*    0000000000000000 (LIBC)       __cxa_atexit
0000000000000000      DF *UND*    0000000000000000              __android_log_print
0000000000000000      DF *UND*    0000000000000000 (LIBC)       __stack_chk_fail
0000000000000000      DF *UND*    0000000000000000 (LIBC)       memset
0000000000000000      DF *UND*    0000000000000000 (LIBC)       strncpy
0000000000000000      DF *UND*    0000000000000000 (LIBC)       strncat
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_self
0000000000000000      DF *UND*    0000000000000000 (LIBC)       malloc
0000000000000000      DF *UND*    0000000000000000 (LIBC)       free
0000000000000000      DF *UND*    0000000000000000 (LIBC)       posix_memalign
0000000000000000      DO *UND*    0000000000000000 (LIBC)       __sF
0000000000000000      DF *UND*    0000000000000000 (LIBC)       vfprintf
0000000000000000      DF *UND*    0000000000000000 (LIBC)       fputc
0000000000000000      DF *UND*    0000000000000000 (LIBC)       vasprintf
0000000000000000      DF *UND*    0000000000000000 (LIBC)       android_set_abort_message
0000000000000000      DF *UND*    0000000000000000 (LIBC)       openlog
0000000000000000      DF *UND*    0000000000000000 (LIBC)       syslog
0000000000000000      DF *UND*    0000000000000000 (LIBC)       closelog
0000000000000000      DF *UND*    0000000000000000 (LIBC)       abort
0000000000000000      DF *UND*    0000000000000000 (LIBC)       strlen
0000000000000000      DF *UND*    0000000000000000 (LIBC)       realloc
0000000000000000      DF *UND*    0000000000000000 (LIBC)       memmove
0000000000000000      DF *UND*    0000000000000000 (LIBC)       __memmove_chk
0000000000000000      DF *UND*    0000000000000000 (LIBC)       __strlen_chk
0000000000000000      DF *UND*    0000000000000000 (LIBC)       memchr
0000000000000000      DF *UND*    0000000000000000 (LIBC)       __vsnprintf_chk
0000000000000000      DF *UND*    0000000000000000 (LIBC)       memcpy
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_mutex_lock
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_mutex_unlock
0000000000000000      DF *UND*    0000000000000000 (LIBC)       calloc
0000000000000000      DF *UND*    0000000000000000 (LIBC)       strcmp
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_getspecific
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_once
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_setspecific
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_key_delete
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_key_create
0000000000000000      DF *UND*    0000000000000000 (LIBC)       getauxval
0000000000000000      DF *UND*    0000000000000000 (LIBC)       __system_property_get
0000000000000000      DF *UND*    0000000000000000 (LIBC)       strncmp
0000000000000000      DF *UND*    0000000000000000 (LIBC)       fprintf
0000000000000000      DF *UND*    0000000000000000 (LIBC)       fflush
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_rwlock_wrlock
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_rwlock_unlock
0000000000000000      DF *UND*    0000000000000000 (LIBC)       dl_iterate_phdr
0000000000000000      DF *UND*    0000000000000000 (LIBC)       pthread_rwlock_rdlock
0000000000000000      DF *UND*    0000000000000000 (LIBC)       fwrite
0000000000044ce8 g    DF .text    00000000000019d0              .datadiv_decode16117807209816376729
0000000000078a04 g    DF .text    0000000000000a88              .datadiv_decode9901940071257331957
00000000000a8a58 g    DF .text    0000000000000f34              .datadiv_decode14716202181486223822
0000000000076128 g    DF .text    0000000000000870              .datadiv_decode4891596974783633952
...
00000000000a8884 g    DF .text    0000000000000004              .datadiv_decode11706101414295225912
00000000000aa438 g    DF .text    000000000000059c              JNI_OnLoad
0000000000026d98 g    DF .text    00000000000048e0              .datadiv_decode12335027288954124723
...
000000000005c790 g    DF .text    0000000000000004              .datadiv_decode1552205700074701063
000000000005ed50 g    DF .text    00000000000018a0              .datadiv_decode15147620753704794795
00000000000a5e74 g    DF .text    0000000000000004              .datadiv_decode5454406552017557296
```

## -r：显示静态重定位入口

```bash
➜  arm64-v8a objdump -r libtacker.so

libtacker.so:    file format elf64-littleaarch64
```

## -R：显示动态重定位入口

```bash
➜  arm64-v8a objdump -R libtacker.so
...


00000000000cd858 R_AARCH64_RELATIVE       *ABS*+0xcc650
00000000000cd860 R_AARCH64_RELATIVE       *ABS*+0xf3b9
00000000000cd868 R_AARCH64_RELATIVE       *ABS*+0xcc668
00000000000cd870 R_AARCH64_RELATIVE       *ABS*+0xf3b0
00000000000cd878 R_AARCH64_RELATIVE       *ABS*+0xcc680
00000000000cd880 R_AARCH64_RELATIVE       *ABS*+0xcc698
00000000000cd888 R_AARCH64_RELATIVE       *ABS*+0xcd1a8
00000000000cd890 R_AARCH64_RELATIVE       *ABS*+0xcd1d0
00000000000cd898 R_AARCH64_RELATIVE       *ABS*+0xcd2a0
00000000000cd8a0 R_AARCH64_RELATIVE       *ABS*+0xcd2c8
00000000000cece8 R_AARCH64_RELATIVE       *ABS*+0xc206c
00000000000d0fd0 R_AARCH64_RELATIVE       *ABS*+0xacb9c
00000000000d0fd8 R_AARCH64_RELATIVE       *ABS*+0xaccbc
00000000000d0fe0 R_AARCH64_RELATIVE       *ABS*+0xd4a7
00000000000d0fe8 R_AARCH64_RELATIVE       *ABS*+0xd12a1
00000000000d0ff0 R_AARCH64_RELATIVE       *ABS*+0xd12e0
00000000000d0ff8 R_AARCH64_RELATIVE       *ABS*+0xd12e0
00000000000d1000 R_AARCH64_RELATIVE       *ABS*+0xd1ae0
00000000000cd828 R_AARCH64_GLOB_DAT       __sF
00000000000cd460 R_AARCH64_ABS64          .datadiv_decode16117807209816376729
00000000000cd500 R_AARCH64_ABS64          .datadiv_decode9901940071257331957
00000000000cd5f8 R_AARCH64_ABS64          .datadiv_decode14716202181486223822
00000000000cd4e8 R_AARCH64_ABS64          .datadiv_decode4891596974783633952
00000000000cd570 R_AARCH64_ABS64          .datadiv_decode9339716730803528690
00000000000cd488 R_AARCH64_ABS64          .datadiv_decode13183548145838600894
00000000000cd490 R_AARCH64_ABS64          .datadiv_decode3525000441545555282
00000000000cd4a0 R_AARCH64_ABS64          .datadiv_decode8298916886736451040
00000000000cd4e0 R_AARCH64_ABS64          .datadiv_decode6610309240369344955
00000000000cd5b8 R_AARCH64_ABS64          .datadiv_decode5742785139195766122
00000000000cd410 R_AARCH64_ABS64          .datadiv_decode12946686905750037712
00000000000cd4c0 R_AARCH64_ABS64          .datadiv_decode12620377358555187834
00000000000cd520 R_AARCH64_ABS64          .datadiv_decode15294134973280561020
00000000000cd578 R_AARCH64_ABS64          .datadiv_decode123525175395121774
00000000000cd598 R_AARCH64_ABS64          .datadiv_decode17486258817593906496
00000000000cd470 R_AARCH64_ABS64          .datadiv_decode15789135661111847785
00000000000cd508 R_AARCH64_ABS64          .datadiv_decode9708024290202508361
00000000000cd550 R_AARCH64_ABS64          .datadiv_decode12389017544255092540
00000000000cd5a8 R_AARCH64_ABS64          .datadiv_decode8646520184225136992
00000000000cd528 R_AARCH64_ABS64          .datadiv_decode5555087159661513939
00000000000cd538 R_AARCH64_ABS64          .datadiv_decode18018071361702630102
00000000000cd548 R_AARCH64_ABS64          .datadiv_decode11327300974587163078
00000000000cd568 R_AARCH64_ABS64          .datadiv_decode13214095259256631718
00000000000cd428 R_AARCH64_ABS64          .datadiv_decode3631146530348700705
00000000000cd4d0 R_AARCH64_ABS64          .datadiv_decode8050698040297613930
00000000000cd5f0 R_AARCH64_ABS64          .datadiv_decode11706101414295225912
00000000000cd3e8 R_AARCH64_ABS64          .datadiv_decode12335027288954124723
00000000000cd418 R_AARCH64_ABS64          .datadiv_decode18261546535841772752
00000000000cd450 R_AARCH64_ABS64          .datadiv_decode5616837089396308971
00000000000cd4f8 R_AARCH64_ABS64          .datadiv_decode13827763977763901235
00000000000cd458 R_AARCH64_ABS64          .datadiv_decode14151120317447827231
00000000000cd480 R_AARCH64_ABS64          .datadiv_decode11770512853690929982
00000000000cd5c0 R_AARCH64_ABS64          .datadiv_decode14401673864441325462
00000000000cd400 R_AARCH64_ABS64          .datadiv_decode8952246851265070369
00000000000cd478 R_AARCH64_ABS64          .datadiv_decode5074647643595886391
00000000000cd4a8 R_AARCH64_ABS64          .datadiv_decode11553230420239584337
00000000000cd4d8 R_AARCH64_ABS64          .datadiv_decode11784788714666544642
00000000000cd4f0 R_AARCH64_ABS64          .datadiv_decode15357274442415173716
00000000000cd510 R_AARCH64_ABS64          .datadiv_decode16313801769778548889
00000000000cd580 R_AARCH64_ABS64          .datadiv_decode18380577887196024106
00000000000cd3f8 R_AARCH64_ABS64          .datadiv_decode18328417529454547004
00000000000cd518 R_AARCH64_ABS64          .datadiv_decode12121706469311219939
00000000000cd540 R_AARCH64_ABS64          .datadiv_decode4193671268968804409
00000000000cd5c8 R_AARCH64_ABS64          .datadiv_decode6405721680354649260
00000000000cd5e8 R_AARCH64_ABS64          .datadiv_decode8316381480288167535
00000000000cd468 R_AARCH64_ABS64          .datadiv_decode12672127785521407892
00000000000cd530 R_AARCH64_ABS64          .datadiv_decode1095597082262436137
00000000000cd558 R_AARCH64_ABS64          .datadiv_decode11689284992262612148
00000000000cd588 R_AARCH64_ABS64          .datadiv_decode17940233878698364930
00000000000cd448 R_AARCH64_ABS64          .datadiv_decode1771790552069125206
00000000000cd4c8 R_AARCH64_ABS64          .datadiv_decode12950792008805936966
00000000000cd560 R_AARCH64_ABS64          .datadiv_decode6931257938975476985
00000000000cd5a0 R_AARCH64_ABS64          .datadiv_decode15620942718649555403
00000000000cd600 R_AARCH64_ABS64          .datadiv_decode8758840755024801160
00000000000cd408 R_AARCH64_ABS64          .datadiv_decode8010288038339893607
00000000000cd4b8 R_AARCH64_ABS64          .datadiv_decode2175705720332001599
00000000000cd590 R_AARCH64_ABS64          .datadiv_decode256915654516018196
00000000000cd5b0 R_AARCH64_ABS64          .datadiv_decode16710377636940783008
00000000000cd5d0 R_AARCH64_ABS64          .datadiv_decode1639262728706781308
00000000000cd5e0 R_AARCH64_ABS64          .datadiv_decode5533236249192328355
00000000000cd608 R_AARCH64_ABS64          .datadiv_decode2444497212690810360
00000000000cd420 R_AARCH64_ABS64          .datadiv_decode15481956303235929690
00000000000cd438 R_AARCH64_ABS64          .datadiv_decode17677705362567080649
00000000000cd440 R_AARCH64_ABS64          .datadiv_decode7614718738418908679
00000000000cd3f0 R_AARCH64_ABS64          .datadiv_decode17838636323198310142
00000000000cd430 R_AARCH64_ABS64          .datadiv_decode17330405497468958994
00000000000cd498 R_AARCH64_ABS64          .datadiv_decode1552205700074701063
00000000000cd4b0 R_AARCH64_ABS64          .datadiv_decode15147620753704794795
00000000000cd5d8 R_AARCH64_ABS64          .datadiv_decode5454406552017557296
00000000000cd8c0 R_AARCH64_JUMP_SLOT      __cxa_finalize
00000000000cd8c8 R_AARCH64_JUMP_SLOT      __cxa_atexit
00000000000cd8d0 R_AARCH64_JUMP_SLOT      __android_log_print
00000000000cd8d8 R_AARCH64_JUMP_SLOT      __stack_chk_fail
00000000000cd8e0 R_AARCH64_JUMP_SLOT      memset
00000000000cd8e8 R_AARCH64_JUMP_SLOT      strncpy
00000000000cd8f0 R_AARCH64_JUMP_SLOT      strncat
00000000000cd8f8 R_AARCH64_JUMP_SLOT      pthread_self
00000000000cd900 R_AARCH64_JUMP_SLOT      malloc
00000000000cd908 R_AARCH64_JUMP_SLOT      free
00000000000cd910 R_AARCH64_JUMP_SLOT      posix_memalign
00000000000cd918 R_AARCH64_JUMP_SLOT      vfprintf
00000000000cd920 R_AARCH64_JUMP_SLOT      fputc
00000000000cd928 R_AARCH64_JUMP_SLOT      vasprintf
00000000000cd930 R_AARCH64_JUMP_SLOT      android_set_abort_message
00000000000cd938 R_AARCH64_JUMP_SLOT      openlog
00000000000cd940 R_AARCH64_JUMP_SLOT      syslog
00000000000cd948 R_AARCH64_JUMP_SLOT      closelog
00000000000cd950 R_AARCH64_JUMP_SLOT      abort
00000000000cd958 R_AARCH64_JUMP_SLOT      strlen
00000000000cd960 R_AARCH64_JUMP_SLOT      realloc
00000000000cd968 R_AARCH64_JUMP_SLOT      memmove
00000000000cd970 R_AARCH64_JUMP_SLOT      __memmove_chk
00000000000cd978 R_AARCH64_JUMP_SLOT      __strlen_chk
00000000000cd980 R_AARCH64_JUMP_SLOT      memchr
00000000000cd988 R_AARCH64_JUMP_SLOT      __vsnprintf_chk
00000000000cd990 R_AARCH64_JUMP_SLOT      memcpy
00000000000cd998 R_AARCH64_JUMP_SLOT      pthread_mutex_lock
00000000000cd9a0 R_AARCH64_JUMP_SLOT      pthread_mutex_unlock
00000000000cd9a8 R_AARCH64_JUMP_SLOT      calloc
00000000000cd9b0 R_AARCH64_JUMP_SLOT      strcmp
00000000000cd9b8 R_AARCH64_JUMP_SLOT      pthread_getspecific
00000000000cd9c0 R_AARCH64_JUMP_SLOT      pthread_once
00000000000cd9c8 R_AARCH64_JUMP_SLOT      pthread_setspecific
00000000000cd9d0 R_AARCH64_JUMP_SLOT      pthread_key_delete
00000000000cd9d8 R_AARCH64_JUMP_SLOT      pthread_key_create
00000000000cd9e0 R_AARCH64_JUMP_SLOT      getauxval
00000000000cd9e8 R_AARCH64_JUMP_SLOT      __system_property_get
00000000000cd9f0 R_AARCH64_JUMP_SLOT      strncmp
00000000000cd9f8 R_AARCH64_JUMP_SLOT      fprintf
00000000000cda00 R_AARCH64_JUMP_SLOT      fflush
00000000000cda08 R_AARCH64_JUMP_SLOT      pthread_rwlock_wrlock
00000000000cda10 R_AARCH64_JUMP_SLOT      pthread_rwlock_unlock
00000000000cda18 R_AARCH64_JUMP_SLOT      dl_iterate_phdr
00000000000cda20 R_AARCH64_JUMP_SLOT      pthread_rwlock_rdlock
00000000000cda28 R_AARCH64_JUMP_SLOT      fwrite
```
