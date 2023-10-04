# rabin2用法举例

## `-I`：binary info

```bash
➜  arm64-v8a rabin2 -I libtacker.so
arch     arm
baddr    0x0
binsz    848338
bintype  elf
bits     64
canary   true
class    ELF64
compiler Linker: LLD 14.0.1 clang version 14.0.0
crypto   false
endian   little
havecode true
laddr    0x0
lang     c
linenum  false
lsyms    false
machine  ARM aarch64
nx       true
os       android
pic      true
relocs   false
relro    full
rpath    NONE
sanitize false
static   false
stripped true
subsys   android
va       true
```

## `-i`：imports

```bash
➜  arm64-v8a rabin2 -i libtacker.so
[Imports]
nth vaddr      bind   type lib name
―――――――――――――――――――――――――――――――――――
1   0x000c9240 GLOBAL FUNC     __cxa_finalize
2   0x000c9250 GLOBAL FUNC     __cxa_atexit
3   0x000c9260 GLOBAL FUNC     __android_log_print
4   0x000c9270 GLOBAL FUNC     __stack_chk_fail
5   0x000c9280 GLOBAL FUNC     memset
6   0x000c9290 GLOBAL FUNC     strncpy
7   0x000c92a0 GLOBAL FUNC     strncat
8   0x000c92b0 GLOBAL FUNC     pthread_self
9   0x000c92c0 GLOBAL FUNC     malloc
10  0x000c92d0 GLOBAL FUNC     free
11  0x000c92e0 GLOBAL FUNC     posix_memalign
12  ---------- GLOBAL OBJ      __sF
13  0x000c92f0 GLOBAL FUNC     vfprintf
14  0x000c9300 GLOBAL FUNC     fputc
15  0x000c9310 GLOBAL FUNC     vasprintf
16  0x000c9320 GLOBAL FUNC     android_set_abort_message
17  0x000c9330 GLOBAL FUNC     openlog
18  0x000c9340 GLOBAL FUNC     syslog
19  0x000c9350 GLOBAL FUNC     closelog
20  0x000c9360 GLOBAL FUNC     abort
21  0x000c9370 GLOBAL FUNC     strlen
22  0x000c9380 GLOBAL FUNC     realloc
23  0x000c9390 GLOBAL FUNC     memmove
24  0x000c93a0 GLOBAL FUNC     __memmove_chk
25  0x000c93b0 GLOBAL FUNC     __strlen_chk
26  0x000c93c0 GLOBAL FUNC     memchr
27  0x000c93d0 GLOBAL FUNC     __vsnprintf_chk
28  0x000c93e0 GLOBAL FUNC     memcpy
29  0x000c93f0 GLOBAL FUNC     pthread_mutex_lock
30  0x000c9400 GLOBAL FUNC     pthread_mutex_unlock
31  0x000c9410 GLOBAL FUNC     calloc
32  0x000c9420 GLOBAL FUNC     strcmp
33  0x000c9430 GLOBAL FUNC     pthread_getspecific
34  0x000c9440 GLOBAL FUNC     pthread_once
35  0x000c9450 GLOBAL FUNC     pthread_setspecific
36  0x000c9460 GLOBAL FUNC     pthread_key_delete
37  0x000c9470 GLOBAL FUNC     pthread_key_create
38  0x000c9480 GLOBAL FUNC     getauxval
39  0x000c9490 GLOBAL FUNC     __system_property_get
40  0x000c94a0 GLOBAL FUNC     strncmp
41  0x000c94b0 GLOBAL FUNC     fprintf
42  0x000c94c0 GLOBAL FUNC     fflush
43  0x000c94d0 GLOBAL FUNC     pthread_rwlock_wrlock
44  0x000c94e0 GLOBAL FUNC     pthread_rwlock_unlock
45  0x000c94f0 GLOBAL FUNC     dl_iterate_phdr
46  0x000c9500 GLOBAL FUNC     pthread_rwlock_rdlock
47  0x000c9510 GLOBAL FUNC     fwrite
```

## `-E`：exports

```bash
➜  arm64-v8a rabin2 -E libtacker.so
[Exports]
nth paddr      vaddr      bind   type size  lib name                                demangled
―――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――
48  0x00044ce8 0x00044ce8 GLOBAL FUNC 6608      .datadiv_decode16117807209816376729
49  0x00078a04 0x00078a04 GLOBAL FUNC 2696      .datadiv_decode9901940071257331957
50  0x000a8a58 0x000a8a58 GLOBAL FUNC 3892      .datadiv_decode14716202181486223822
...
70  0x0008e650 0x0008e650 GLOBAL FUNC 3772      .datadiv_decode13214095259256631718
71  0x000381fc 0x000381fc GLOBAL FUNC 3696      .datadiv_decode3631146530348700705
72  0x0006f220 0x0006f220 GLOBAL FUNC 3892      .datadiv_decode8050698040297613930
73  0x000a8884 0x000a8884 GLOBAL FUNC 4         .datadiv_decode11706101414295225912
74  0x000aa438 0x000aa438 GLOBAL FUNC 1436      JNI_OnLoad
75  0x00026d98 0x00026d98 GLOBAL FUNC 18656     .datadiv_decode12335027288954124723
76  0x00033a2c 0x00033a2c GLOBAL FUNC 11972     .datadiv_decode18261546535841772752
77  0x0003c8dc 0x0003c8dc GLOBAL FUNC 8072      .datadiv_decode5616837089396308971
...
115 0x0005c790 0x0005c790 GLOBAL FUNC 4         .datadiv_decode1552205700074701063
116 0x0005ed50 0x0005ed50 GLOBAL FUNC 6304      .datadiv_decode15147620753704794795
117 0x000a5e74 0x000a5e74 GLOBAL FUNC 4         .datadiv_decode5454406552017557296
```

## `-l`：linked libraries

```bash
➜  arm64-v8a rabin2 -l libtacker.so
[Linked libraries]
liblog.so
libm.so
libdl.so
libc.so

4 libraries
```

## `-z`：strings (from data section)

```bash
➜  arm64-v8a rabin2 -z libtacker.so
[Strings]
nth paddr      vaddr      len size section type    string
―――――――――――――――――――――――――――――――――――――――――――――――――――――――――
0   0x0000c6f9 0x0000c6f9 26  27   .rodata ascii   covariant return thunk to
1   0x0000c719 0x0000c719 10  11   .rodata ascii   operator^=
2   0x0000c724 0x0000c724 10  11   .rodata ascii   operator<=
3   0x0000c72f 0x0000c72f 24  25   .rodata ascii   unknown pointer encoding
4   0x0000c748 0x0000c748 47  48   .rodata ascii   unsupported restore location for float register
5   0x0000c782 0x0000c782 9   10   .rodata ascii   decltype(
6   0x0000c78f 0x0000c78f 8   9    .rodata ascii   typeid (
7   0x0000c798 0x0000c798 5   6    .rodata ascii   {...}
8   0x0000c79e 0x0000c79e 11  12   .rodata ascii   operator>>=
9   0x0000c7aa 0x0000c7aa 11  12   .rodata ascii   operator<=>
10  0x0000c7b6 0x0000c7b6 4   5    .rodata ascii   long
11  0x0000c7bb 0x0000c7bb 8   9    .rodata ascii   char32_t
12  0x0000c7c4 0x0000c7c4 64  65   .rodata ascii   libunwind: malformed DW_CFA_register DWARF unwind, reg2 too big\n
13  0x0000c805 0x0000c805 68  69   .rodata ascii   libunwind: malformed DW_CFA_val_offset_sf DWARF unwind, reg too big\n
14  0x0000c84e 0x0000c84e 5   6    .rodata ascii   throw
15  0x0000c854 0x0000c854 7   8    .rodata ascii   wchar_t
16  0x0000c85c 0x0000c85c 7   8    .rodata ascii   'lambda
17  0x0000c864 0x0000c864 9   10   .rodata ascii   operator~
18  0x0000c86e 0x0000c86e 11  12   .rodata ascii   operator""
19  0x0000c87a 0x0000c87a 17  18   .rodata ascii   std::basic_string
20  0x0000c88c 0x0000c88c 14  15   .rodata ascii   decltype(auto)
21  0x0000c89b 0x0000c89b 32  33   .rodata ascii   Deleted virtual function called!
22  0x0000c8bc 0x0000c8bc 14  15   .rodata ascii   std::exception
23  0x0000c8cb 0x0000c8cb 40  41   .rodata ascii   terminating with %s exception of type %s
24  0x0000c8f4 0x0000c8f4 10  11   .rodata ascii   const_cast
25  0x0000c902 0x0000c902 17  18   .rodata ascii   unsigned __int128
26  0x0000c914 0x0000c914 15  16   .rodata ascii   operator delete
27  0x0000c924 0x0000c924 10  11   .rodata ascii   operator>=
28  0x0000c92f 0x0000c92f 13  14   .rodata ascii   unwind_phase2
29  0x0000c93d 0x0000c93d 26  27   .rodata ascii   unsupported arm64 register
30  0x0000c958 0x0000c958 62  63   .rodata ascii   libunwind: malformed DW_CFA_def_cfa DWARF unwind, reg too big\n
31  0x0000c997 0x0000c997 10  11   .rodata ascii   getSLEB128
32  0x0000c9a2 0x0000c9a2 16  17   .rodata ascii   getSavedRegister
33  0x0000c9bb 0x0000c9bb 18  19   .rodata ascii   typeinfo name for
34  0x0000c9ce 0x0000c9ce 12  13   .rodata ascii   operator new
35  0x0000c9db 0x0000c9db 5   6    .rodata ascii   ) ? (
36  0x0000c9e1 0x0000c9e1 12  13   .rodata ascii    [enable_if:
37  0x0000c9ee 0x0000c9ee 14  15   .rodata ascii   std::nullptr_t
38  0x0000c9fd 0x0000c9fd 11  12   .rodata ascii   objc_object
39  0x0000ca09 0x0000ca09 14  15   .rodata ascii   std::bad_alloc
40  0x0000ca18 0x0000ca18 15  16   .rodata ascii   std::bad_typeid
41  0x0000ca28 0x0000ca28 11  12   .rodata ascii   getEncodedP
42  0x0000ca3e 0x0000ca3e 13  14   .rodata ascii   typeinfo for
43  0x0000ca4c 0x0000ca4c 24  25   .rodata ascii   reference temporary for
44  0x0000ca65 0x0000ca65 13  14   .rodata ascii   unsigned char
45  0x0000ca75 0x0000ca75 10  11   .rodata ascii   operator&=
46  0x0000ca80 0x0000ca80 10  11   .rodata ascii   operator*=
47  0x0000ca8b 0x0000ca8b 70  71   .rodata ascii   std::basic_string<char, std::char_traits<char>, std::allocator<char> >
48  0x0000cad2 0x0000cad2 21  22   .rodata ascii   getSavedFloatRegister
49  0x0000caf6 0x0000caf6 17  18   .rodata ascii   operator delete[]
50  0x0000cb10 0x0000cb10 11  12   .rodata ascii   std::string
51  0x0000cb23 0x0000cb23 4   5    .rodata ascii   auto
52  0x0000cb2a 0x0000cb2a 14  15   .rodata ascii   unsigned short
53  0x0000cb39 0x0000cb39 5   6    .rodata ascii   false
54  0x0000cb3f 0x0000cb3f 4   5    .rodata ascii   %LaL
55  0x0000cb44 0x0000cb44 9   10   .rodata ascii   operator/
56  0x0000cb4e 0x0000cb4e 9   10   .rodata ascii   operator|
57  0x0000cb5c 0x0000cb5c 10  11   .rodata ascii   exynos9810
58  0x0000cb67 0x0000cb67 77  78   .rodata ascii   libunwind: malformed DW_CFA_val_offset DWARF unwind, reg (%lu) out of range\n\n
59  0x0000cbb9 0x0000cbb9 19  20   .rodata ascii   FDE has zero length
60  0x0000cbcd 0x0000cbcd 19  20   .rodata ascii   FDE is really a CIE
61  0x0000cbe5 0x0000cbe5 6   7    .rodata ascii   delete
62  0x0000cbec 0x0000cbec 9   10   .rodata ascii   operator&
63  0x0000cbf6 0x0000cbf6 9   10   .rodata ascii   operator%
64  0x0000cc00 0x0000cc00 10  11   .rodata ascii   operator>>
65  0x0000cc0b 0x0000cc0b 5   6    .rodata ascii   ) : (
66  0x0000cc11 0x0000cc11 5   6    .rodata ascii   [abi:
67  0x0000cc1b 0x0000cc1b 65  66   .rodata ascii   libunwind: malformed DW_CFA_same_value DWARF unwind, reg too big\n
68  0x0000cc5d 0x0000cc5d 47  48   .rodata ascii   DW_EH_PE_aligned pointer encoding not supported
69  0x0000cc8d 0x0000cc8d 28  29   .rodata ascii   truncated sleb128 expression
70  0x0000ccad 0x0000ccad 39  40   .rodata ascii   terminate_handler unexpectedly returned
71  0x0000ccd7 0x0000ccd7 11  12   .rodata ascii   signed char
72  0x0000cce6 0x0000cce6 10  11   .rodata ascii   sizeof...(
73  0x0000ccf1 0x0000ccf1 13  14   .rodata ascii   basic_ostream
74  0x0000ccff 0x0000ccff 12  13   .rodata ascii   std::ostream
75  0x0000cd0c 0x0000cd0c 13  14   .rodata ascii   std::iostream
76  0x0000cd1a 0x0000cd1a 9   10   .rodata ascii   long long
77  0x0000cd24 0x0000cd24 9   10   .rodata ascii   noexcept(
78  0x0000cd2e 0x0000cd2e 41  42   .rodata ascii   unsupported restore location for register
79  0x0000cd6a 0x0000cd6a 14  15   .rodata ascii   operator new[]
80  0x0000cd79 0x0000cd79 9   10   .rodata ascii   operator!
81  0x0000cd83 0x0000cd83 49  50   .rodata ascii   std::basic_ostream<char, std::char_traits<char> >
82  0x0000cdb5 0x0000cdb5 10  11   .rodata ascii   __float128
83  0x0000cdc0 0x0000cdc0 8   9    .rodata ascii   char16_t
84  0x0000cdc9 0x0000cdc9 98  99   .rodata ascii   during phase1 personality function said it would stop here, but now in phase2 it did not stop here
85  0x0000ce2c 0x0000ce2c 83  84   .rodata ascii   libunwind: malformed DW_CFA_GNU_negative_offset_extended DWARF unwind, reg too big\n
86  0x0000ce96 0x0000ce96 9   10   .rodata ascii   typename
87  0x0000cea4 0x0000cea4 10  11   .rodata ascii   operator()
88  0x0000ceaf 0x0000ceaf 9   10   .rodata ascii   operator>
89  0x0000ceb9 0x0000ceb9 10  11   .rodata ascii   operator[]
90  0x0000cec4 0x0000cec4 10  11   .rodata ascii   operator->
91  0x0000cecf 0x0000cecf 13  14   .rodata ascii   unsigned long
92  0x0000cee1 0x0000cee1 13  14   .rodata ascii   std::bad_cast
93  0x0000ceef 0x0000ceef 11  12   .rodata ascii   setRegister
94  0x0000cefb 0x0000cefb 70  71   .rodata ascii   libunwind: malformed DW_CFA_offset_extended DWARF unwind, reg too big\n
95  0x0000cf45 0x0000cf45 11  12   .rodata ascii   > typename
96  0x0000cf51 0x0000cf51 21  22   .rodata ascii   (anonymous namespace)
97  0x0000cf67 0x0000cf67 10  11   .rodata ascii   operator==
98  0x0000cf72 0x0000cf72 8   9    .rodata ascii    complex
99  0x0000cf7b 0x0000cf7b 25  26   .rodata ascii   CIE version is not 1 or 3
100 0x0000cf9d 0x0000cf9d 11  12   .rodata ascii   vtable for
101 0x0000cfa9 0x0000cfa9 8   9    .rodata ascii   VTT for
102 0x0000cfb2 0x0000cfb2 9   10   .rodata ascii   alignof (
103 0x0000cfbe 0x0000cfbe 10  11   .rodata ascii   noexcept (
104 0x0000cfc9 0x0000cfc9 4   5    .rodata ascii   char
105 0x0000cfd0 0x0000cfd0 9   10   .rodata ascii   operator<
106 0x0000cfda 0x0000cfda 11  12   .rodata ascii   operator->*
107 0x0000cfe6 0x0000cfe6 12  13   .rodata ascii   unsigned int
108 0x0000cff3 0x0000cff3 47  48   .rodata ascii   DW_EH_PE_funcrel pointer encoding not supported
109 0x0000d023 0x0000d023 45  46   .rodata ascii   libunwind: Unsupported .eh_frame_hdr version\n
110 0x0000d055 0x0000d055 9   10   .rodata ascii   libc++abi
111 0x0000d05f 0x0000d05f 12  13   .rodata ascii   dynamic_cast
112 0x0000d074 0x0000d074 5   6    .rodata ascii   short
113 0x0000d07a 0x0000d07a 5   6    .rodata ascii    ...
114 0x0000d080 0x0000d080 6   7    .rodata ascii   string
115 0x0000d087 0x0000d087 7   8    .rodata ascii   ostream
116 0x0000d08f 0x0000d08f 11  12   .rodata ascii   long double
117 0x0000d0a2 0x0000d0a2 10  11   .rodata ascii   unexpected
118 0x0000d0ad 0x0000d0ad 19  20   .rodata ascii   guard variable for
119 0x0000d0c4 0x0000d0c4 4   5    .rodata ascii   true
120 0x0000d0c9 0x0000d0c9 9   10   .rodata ascii   operator?
121 0x0000d0d3 0x0000d0d3 20  21   .rodata ascii   bad_array_new_length
122 0x0000d0e8 0x0000d0e8 19  20   .rodata ascii   libunwind: %s - %s\n
123 0x0000d103 0x0000d103 17  18   .rodata ascii   virtual thunk to
124 0x0000d123 0x0000d123 9   10   .rodata ascii   operator*
125 0x0000d12d 0x0000d12d 10  11   .rodata ascii   operator||
126 0x0000d138 0x0000d138 7   8    .rodata ascii   istream
127 0x0000d144 0x0000d144 7   8    .rodata ascii   char8_t
128 0x0000d14c 0x0000d14c 30  31   .rodata ascii   DW_OP_deref_size with bad size
129 0x0000d16b 0x0000d16b 40  41   .rodata ascii   Unknown DWARF encoding for search table.
130 0x0000d19c 0x0000d19c 40  41   .rodata ascii   unexpected_handler unexpectedly returned
131 0x0000d1c5 0x0000d1c5 24  25   .rodata ascii   construction vtable for
132 0x0000d1e3 0x0000d1e3 8   9    .rodata ascii   __int128
133 0x0000d1ec 0x0000d1ec 9   10   .rodata ascii   template<
134 0x0000d1f6 0x0000d1f6 10  11   .rodata ascii   operator<<
135 0x0000d201 0x0000d201 9   10   .rodata ascii   operator+
136 0x0000d20b 0x0000d20b 10  11   .rodata ascii   operator+=
137 0x0000d216 0x0000d216 10  11   .rodata ascii   operator++
138 0x0000d221 0x0000d221 14  15   .rodata ascii   string literal
139 0x0000d230 0x0000d230 18  19   .rodata ascii   unsigned long long
140 0x0000d243 0x0000d243 10  11   .rodata ascii    imaginary
141 0x0000d24e 0x0000d24e 65  66   .rodata ascii   libunwind: malformed DW_CFA_expression DWARF unwind, reg too big\n
142 0x0000d2a6 0x0000d2a6 9   10   .rodata ascii   operator=
143 0x0000d2b0 0x0000d2b0 10  11   .rodata ascii   operator/=
144 0x0000d2bb 0x0000d2bb 4   5    .rodata ascii   bool
145 0x0000d2c0 0x0000d2c0 18  19   .rodata ascii   evaluateExpression
146 0x0000d2de 0x0000d2de 9   10   .rodata ascii   operator^
147 0x0000d2e8 0x0000d2e8 9   10   .rodata ascii    restrict
148 0x0000d2f2 0x0000d2f2 9   10   .rodata ascii   decimal64
149 0x0000d2fc 0x0000d2fc 64  65   .rodata ascii   libunwind: malformed DW_CFA_undefined DWARF unwind, reg too big\n
150 0x0000d34c 0x0000d34c 44  45   .rodata ascii   terminating with %s exception of type %s: %s
151 0x0000d379 0x0000d379 21  22   .rodata ascii   non-virtual thunk to
152 0x0000d396 0x0000d396 49  50   .rodata ascii   std::basic_istream<char, std::char_traits<char> >
153 0x0000d3c8 0x0000d3c8 8   9    .rodata ascii   iostream
154 0x0000d3d1 0x0000d3d1 13  14   .rodata ascii   pixel vector[
155 0x0000d3df 0x0000d3df 5   6    .rodata ascii   union
156 0x0000d3e5 0x0000d3e5 29  30   .rodata ascii   _Unwind_Resume() can't return
157 0x0000d403 0x0000d403 63  64   .rodata ascii   libunwind: malformed DW_CFA_register DWARF unwind, reg too big\n
158 0x0000d446 0x0000d446 4   5    .rodata ascii   yptn
159 0x0000d44b 0x0000d44b 10  11   .rodata ascii   operator%=
160 0x0000d456 0x0000d456 6   7    .rodata ascii    const
161 0x0000d45d 0x0000d45d 27  28   .rodata ascii   DW_OP_fbreg not implemented
162 0x0000d481 0x0000d481 37  38   .rodata ascii   terminating with %s foreign exception
163 0x0000d4a7 0x0000d4a7 8   9    .rodata ascii   uncaught
164 0x0000d4b3 0x0000d4b3 10  11   .rodata ascii   operator--
165 0x0000d4be 0x0000d4be 10  11   .rodata ascii   operator|=
166 0x0000d4c9 0x0000d4c9 50  51   .rodata ascii   std::basic_iostream<char, std::char_traits<char> >
167 0x0000d4fc 0x0000d4fc 14  15   .rodata ascii   _Unwind_Resume
168 0x0000d50b 0x0000d50b 65  66   .rodata ascii   libunwind: malformed DW_CFA_def_cfa_sf DWARF unwind, reg too big\n
169 0x0000d55d 0x0000d55d 15  16   .rodata ascii   'block-literal'
170 0x0000d56d 0x0000d56d 9   10   .rodata ascii   operator-
171 0x0000d577 0x0000d577 13  14   .rodata ascii   basic_istream
172 0x0000d585 0x0000d585 12  13   .rodata ascii   std::istream
173 0x0000d592 0x0000d592 6   7    .rodata ascii   double
174 0x0000d59c 0x0000d59c 33  34   .rodata ascii   invocation function for block in
175 0x0000d5be 0x0000d5be 11  12   .rodata ascii   static_cast
176 0x0000d5ca 0x0000d5ca 11  12   .rodata ascii   sizeof... (
177 0x0000d5dc 0x0000d5dc 10  11   .rodata ascii   operator-=
178 0x0000d5e7 0x0000d5e7 73  74   .rodata ascii   libunwind: malformed DW_CFA_offset_extended_sf DWARF unwind, reg too big\n
179 0x0000d631 0x0000d631 10  11   .rodata ascii   getULEB128
180 0x0000d63c 0x0000d63c 28  29   .rodata ascii   malformed uleb128 expression
181 0x0000d659 0x0000d659 28  29   .rodata ascii   DWARF opcode not implemented
182 0x0000d683 0x0000d683 7   8    .rodata ascii   nullptr
183 0x0000d68b 0x0000d68b 11  12   .rodata ascii   operator<<=
184 0x0000d697 0x0000d697 11  12   .rodata ascii   ::operator
185 0x0000d6a3 0x0000d6a3 4   5    .rodata ascii   enum
186 0x0000d6a8 0x0000d6a8 69  70   .rodata ascii   libunwind: malformed DW_CFA_val_expression DWARF unwind, reg too big\n
187 0x0000d6fb 0x0000d6fb 11  12   .rodata ascii   terminating
188 0x0000d70b 0x0000d70b 16  17   .rodata ascii   reinterpret_cast
189 0x0000d721 0x0000d721 47  48   .rodata ascii   DW_EH_PE_textrel pointer encoding not supported
190 0x0000d751 0x0000d751 28  29   .rodata ascii   truncated uleb128 expression
191 0x0000d773 0x0000d773 9   10   .rodata ascii   operator
192 0x0000d77d 0x0000d77d 6   7    .rodata ascii   throw
193 0x0000d784 0x0000d784 12  13   .rodata ascii   basic_string
194 0x0000d791 0x0000d791 4   5    .rodata ascii   void
195 0x0000d796 0x0000d796 5   6    .rodata ascii   float
196 0x0000d79c 0x0000d79c 10  11   .rodata ascii   decimal128
197 0x0000d7a7 0x0000d7a7 7   8    .rodata ascii   ro.arch
198 0x0000d7af 0x0000d7af 71  72   .rodata ascii   libunwind: malformed DW_CFA_restore_extended DWARF unwind, reg too big\n
199 0x0000d7f7 0x0000d7f7 17  18   .rodata ascii   getTableEntrySize
200 0x0000d81f 0x0000d81f 10  11   .rodata ascii   operator&&
201 0x0000d82a 0x0000d82a 9   10   .rodata ascii   decimal32
202 0x0000d834 0x0000d834 18  19   .rodata ascii   CIE ID is not zero
203 0x0000d84f 0x0000d84f 33  34   .rodata ascii   thread-local wrapper routine for
204 0x0000d871 0x0000d871 40  41   .rodata ascii   thread-local initialization routine for
205 0x0000d89a 0x0000d89a 8   9    .rodata ascii   sizeof (
206 0x0000d8a3 0x0000d8a3 10  11   .rodata ascii   operator!=
207 0x0000d8ae 0x0000d8ae 9   10   .rodata ascii   __uuidof(
208 0x0000d8b8 0x0000d8b8 14  15   .rodata ascii   std::allocator
209 0x0000d8c7 0x0000d8c7 9   10   .rodata ascii   allocator
210 0x0000d8d1 0x0000d8d1 6   7    .rodata ascii   struct
211 0x0000d8d8 0x0000d8d8 71  72   .rodata ascii   libunwind: malformed DW_CFA_def_cfa_register DWARF unwind, reg too big\n
212 0x0000d920 0x0000d920 52  53   .rodata ascii   Can't binary search on variable length encoded data.
213 0x0000d95d 0x0000d95d 49  50   .rodata ascii   terminate_handler unexpectedly threw an exception
214 0x0000d992 0x0000d992 9   10   .rodata ascii   operator,
215 0x0000d99c 0x0000d99c 9   10   .rodata ascii   decimal16
216 0x0000d9a6 0x0000d9a6 8   9    .rodata ascii   noexcept
217 0x0000d9af 0x0000d9af 11  12   .rodata ascii   getRegister
218 0x0000d9bb 0x0000d9bb 51  52   .rodata ascii   DW_EH_PE_datarel is invalid with a datarelBase of 0
219 0x0000d9f9 0x0000d9f9 16  17   .rodata ascii   unknown register
220 0x0000da0c 0x0000da0c 14  15   .rodata ascii   basic_iostream
221 0x0000da1b 0x0000da1b 5   6    .rodata ascii   std::
222 0x0000da21 0x0000da21 9   10   .rodata ascii    volatile
223 0x0000da2b 0x0000da2b 6   7    .rodata ascii   throw(
224 0x0000da32 0x0000da32 29  30   .rodata ascii   Pure virtual function called!
225 0x0000da50 0x0000da50 18  19   .rodata ascii   std::bad_exception
226 0x0000da63 0x0000da63 27  28   .rodata ascii   DW_OP_piece not implemented
227 0x0000df91 0x0000df91 5   6    .rodata ascii   \t\t\t\t\t
228 0x0000df97 0x0000df97 25  26   .rodata ascii   \t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t
229 0x0000dfb1 0x0000dfb1 5   6    .rodata ascii   \t\t\t\t\t
230 0x0000dfc2 0x0000dfc2 4   5    .rodata ascii   Ocv}
231 0x0000e135 0x0000e135 14  15   .rodata ascii   \t7\t\t\t\t\t\t\t\t\t\t\t\t
232 0x0000e150 0x0000e150 32  65   .rodata utf16le PPPPPPPPPPPPPPPPPPPPPPPPPPPP~PP\
233 0x0000e194 0x0000e194 17  35   .rodata utf16le ddddddddddddddddd
234 0x0000e1c0 0x0000e1c0 9   19   .rodata utf16le ddddddddd
235 0x0000e27a 0x0000e27a 49  50   .rodata ascii    (N12_GLOBAL__N_116itanium_demangle11SpecialNameE
236 0x0000e2ac 0x0000e2ac 39  40   .rodata ascii   N12_GLOBAL__N_116itanium_demangle4NodeE
237 0x0000e2d4 0x0000e2d4 57  58   .rodata ascii   N12_GLOBAL__N_116itanium_demangle21CtorVtableSpecialNameE
238 0x0000e30e 0x0000e30e 43  44   .rodata ascii   N12_GLOBAL__N_116itanium_demangle8NameTypeE
239 0x0000e33a 0x0000e33a 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10NestedNameE
240 0x0000e369 0x0000e369 60  61   .rodata ascii   N12_GLOBAL__N_116itanium_demangle24ForwardTemplateReferenceE
241 0x0000e3a6 0x0000e3a6 50  51   .rodata ascii   N12_GLOBAL__N_116itanium_demangle14IntegerLiteralE
242 0x0000e3d9 0x0000e3d9 43  44   .rodata ascii   N12_GLOBAL__N_116itanium_demangle8BoolExprE
243 0x0000e405 0x0000e405 55  56   .rodata ascii   N12_GLOBAL__N_116itanium_demangle16FloatLiteralImplIfEE
244 0x0000e43d 0x0000e43d 55  56   .rodata ascii   N12_GLOBAL__N_116itanium_demangle16FloatLiteralImplIdEE
245 0x0000e475 0x0000e475 55  56   .rodata ascii   N12_GLOBAL__N_116itanium_demangle16FloatLiteralImplIeEE
246 0x0000e4ad 0x0000e4ad 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13StringLiteralE
247 0x0000e4df 0x0000e4df 51  52   .rodata ascii   N12_GLOBAL__N_116itanium_demangle15UnnamedTypeNameE
248 0x0000e513 0x0000e513 62  63   .rodata ascii   N12_GLOBAL__N_116itanium_demangle26SyntheticTemplateParamNameE
249 0x0000e552 0x0000e552 57  58   .rodata ascii   N12_GLOBAL__N_116itanium_demangle21TypeTemplateParamDeclE
250 0x0000e58c 0x0000e58c 60  61   .rodata ascii   N12_GLOBAL__N_116itanium_demangle24NonTypeTemplateParamDeclE
251 0x0000e5c9 0x0000e5c9 61  62   .rodata ascii   N12_GLOBAL__N_116itanium_demangle25TemplateTemplateParamDeclE
252 0x0000e607 0x0000e607 57  58   .rodata ascii   N12_GLOBAL__N_116itanium_demangle21TemplateParamPackDeclE
253 0x0000e641 0x0000e641 51  52   .rodata ascii   N12_GLOBAL__N_116itanium_demangle15ClosureTypeNameE
254 0x0000e675 0x0000e675 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10LambdaExprE
255 0x0000e6a4 0x0000e6a4 51  52   .rodata ascii   N12_GLOBAL__N_116itanium_demangle15IntegerCastExprE
256 0x0000e6d8 0x0000e6d8 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13FunctionParamE
257 0x0000e70a 0x0000e70a 43  44   .rodata ascii   N12_GLOBAL__N_116itanium_demangle8FoldExprE
258 0x0000e736 0x0000e736 58  59   .rodata ascii   N12_GLOBAL__N_116itanium_demangle22ParameterPackExpansionE
259 0x0000e771 0x0000e771 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10BinaryExprE
260 0x0000e7a0 0x0000e7a0 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10PrefixExprE
261 0x0000e7cf 0x0000e7cf 43  44   .rodata ascii   N12_GLOBAL__N_116itanium_demangle8CastExprE
262 0x0000e7fb 0x0000e7fb 43  44   .rodata ascii   N12_GLOBAL__N_116itanium_demangle8CallExprE
263 0x0000e827 0x0000e827 50  51   .rodata ascii   N12_GLOBAL__N_116itanium_demangle14ConversionExprE
264 0x0000e85a 0x0000e85a 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10DeleteExprE
265 0x0000e889 0x0000e889 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13QualifiedNameE
266 0x0000e8bb 0x0000e8bb 43  44   .rodata ascii   N12_GLOBAL__N_116itanium_demangle8DtorNameE
267 0x0000e8e7 0x0000e8e7 58  59   .rodata ascii   N12_GLOBAL__N_116itanium_demangle22ConversionOperatorTypeE
268 0x0000e922 0x0000e922 51  52   .rodata ascii   N12_GLOBAL__N_116itanium_demangle15LiteralOperatorE
269 0x0000e956 0x0000e956 55  56   .rodata ascii   N12_GLOBAL__N_116itanium_demangle19GlobalQualifiedNameE
270 0x0000e98e 0x0000e98e 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10MemberExprE
271 0x0000e9bd 0x0000e9bd 54  55   .rodata ascii   N12_GLOBAL__N_116itanium_demangle18ArraySubscriptExprE
272 0x0000e9f4 0x0000e9f4 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10BracedExprE
273 0x0000ea23 0x0000ea23 51  52   .rodata ascii   N12_GLOBAL__N_116itanium_demangle15BracedRangeExprE
274 0x0000ea57 0x0000ea57 48  49   .rodata ascii   N12_GLOBAL__N_116itanium_demangle12InitListExprE
275 0x0000ea88 0x0000ea88 47  48   .rodata ascii   N12_GLOBAL__N_116itanium_demangle11PostfixExprE
276 0x0000eab8 0x0000eab8 42  43   .rodata ascii   N12_GLOBAL__N_116itanium_demangle7NewExprE
277 0x0000eae3 0x0000eae3 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13EnclosingExprE
278 0x0000eb15 0x0000eb15 51  52   .rodata ascii   N12_GLOBAL__N_116itanium_demangle15ConditionalExprE
279 0x0000eb49 0x0000eb49 55  56   .rodata ascii   N12_GLOBAL__N_116itanium_demangle19SizeofParamPackExprE
280 0x0000eb81 0x0000eb81 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13NodeArrayNodeE
281 0x0000ebb3 0x0000ebb3 44  45   .rodata ascii   N12_GLOBAL__N_116itanium_demangle9ThrowExprE
282 0x0000ebe0 0x0000ebe0 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10UUIDOfExprE
283 0x0000ec0f 0x0000ec0f 63  64   .rodata ascii   N12_GLOBAL__N_116itanium_demangle27ExpandedSpecialSubstitutionE
284 0x0000ec4f 0x0000ec4f 48  49   .rodata ascii   N12_GLOBAL__N_116itanium_demangle12CtorDtorNameE
285 0x0000ec80 0x0000ec80 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10AbiTagAttrE
286 0x0000ecaf 0x0000ecaf 57  58   .rodata ascii   N12_GLOBAL__N_116itanium_demangle21StructuredBindingNameE
287 0x0000ece9 0x0000ece9 44  45   .rodata ascii   N12_GLOBAL__N_116itanium_demangle9LocalNameE
288 0x0000ed16 0x0000ed16 55  56   .rodata ascii   N12_GLOBAL__N_116itanium_demangle19SpecialSubstitutionE
289 0x0000ed4e 0x0000ed4e 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13ParameterPackE
290 0x0000ed80 0x0000ed80 48  49   .rodata ascii   N12_GLOBAL__N_116itanium_demangle12TemplateArgsE
291 0x0000edb1 0x0000edb1 56  57   .rodata ascii   N12_GLOBAL__N_116itanium_demangle20NameWithTemplateArgsE
292 0x0000edea 0x0000edea 52  53   .rodata ascii   N12_GLOBAL__N_116itanium_demangle16StdQualifiedNameE
293 0x0000ee1f 0x0000ee1f 56  57   .rodata ascii   N12_GLOBAL__N_116itanium_demangle20TemplateArgumentPackE
294 0x0000ee58 0x0000ee58 48  49   .rodata ascii   N12_GLOBAL__N_116itanium_demangle12EnableIfAttrE
295 0x0000ee89 0x0000ee89 52  53   .rodata ascii   N12_GLOBAL__N_116itanium_demangle16FunctionEncodingE
296 0x0000eebe 0x0000eebe 44  45   .rodata ascii   N12_GLOBAL__N_116itanium_demangle9DotSuffixE
297 0x0000eeeb 0x0000eeeb 48  49   .rodata ascii   N12_GLOBAL__N_116itanium_demangle12NoexceptSpecE
298 0x0000ef1c 0x0000ef1c 56  57   .rodata ascii   N12_GLOBAL__N_116itanium_demangle20DynamicExceptionSpecE
299 0x0000ef55 0x0000ef55 48  49   .rodata ascii   N12_GLOBAL__N_116itanium_demangle12FunctionTypeE
300 0x0000ef86 0x0000ef86 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13ObjCProtoNameE
301 0x0000efb8 0x0000efb8 53  54   .rodata ascii   N12_GLOBAL__N_116itanium_demangle17VendorExtQualTypeE
302 0x0000efee 0x0000efee 43  44   .rodata ascii   N12_GLOBAL__N_116itanium_demangle8QualTypeE
303 0x0000f01a 0x0000f01a 51  52   .rodata ascii   N12_GLOBAL__N_116itanium_demangle15PixelVectorTypeE
304 0x0000f04e 0x0000f04e 46  47   .rodata ascii   N12_GLOBAL__N_116itanium_demangle10VectorTypeE
305 0x0000f07d 0x0000f07d 44  45   .rodata ascii   N12_GLOBAL__N_116itanium_demangle9ArrayTypeE
306 0x0000f0aa 0x0000f0aa 55  56   .rodata ascii   N12_GLOBAL__N_116itanium_demangle19PointerToMemberTypeE
307 0x0000f0e2 0x0000f0e2 58  59   .rodata ascii   N12_GLOBAL__N_116itanium_demangle22ElaboratedTypeSpefTypeE
308 0x0000f11d 0x0000f11d 47  48   .rodata ascii   N12_GLOBAL__N_116itanium_demangle11PointerTypeE
309 0x0000f14d 0x0000f14d 49  50   .rodata ascii   N12_GLOBAL__N_116itanium_demangle13ReferenceTypeE
310 0x0000f17f 0x0000f17f 56  57   .rodata ascii   N12_GLOBAL__N_116itanium_demangle20PostfixQualifiedTypeE
311 0x0000f21d 0x0000f21d 5   6    .rodata ascii   KKKK6
312 0x0000f290 0x0000f290 32  33   .rodata ascii   N10__cxxabiv116__shim_type_infoE
313 0x0000f2b1 0x0000f2b1 33  34   .rodata ascii   N10__cxxabiv117__class_type_infoE
314 0x0000f2d3 0x0000f2d3 33  34   .rodata ascii   N10__cxxabiv117__pbase_type_infoE
315 0x0000f2f5 0x0000f2f5 35  36   .rodata ascii   N10__cxxabiv119__pointer_type_infoE
316 0x0000f319 0x0000f319 36  37   .rodata ascii   N10__cxxabiv120__function_type_infoE
317 0x0000f33e 0x0000f33e 45  46   .rodata ascii   N10__cxxabiv129__pointer_to_member_type_infoE
318 0x0000f388 0x0000f388 39  40   .rodata ascii   N10__cxxabiv123__fundamental_type_infoE
319 0x0000f3c0 0x0000f3c0 4   5    .rodata ascii   PKDn
320 0x0000f453 0x0000f453 4   5    .rodata ascii   PKDh
321 0x0000f483 0x0000f483 4   5    .rodata ascii   PKDu
322 0x0000f48f 0x0000f48f 4   5    .rodata ascii   PKDs
323 0x0000f49b 0x0000f49b 4   5    .rodata ascii   PKDi
324 0x0000f4a0 0x0000f4a0 33  34   .rodata ascii   N10__cxxabiv117__array_type_infoE
325 0x0000f4c2 0x0000f4c2 32  33   .rodata ascii   N10__cxxabiv116__enum_type_infoE
326 0x0000f4e3 0x0000f4e3 36  37   .rodata ascii   N10__cxxabiv120__si_class_type_infoE
327 0x0000f508 0x0000f508 37  38   .rodata ascii   N10__cxxabiv121__vmi_class_type_infoE
328 0x0000f52e 0x0000f52e 12  13   .rodata ascii   St9exception
329 0x0000f53b 0x0000f53b 17  18   .rodata ascii   St13bad_exception
330 0x0000f54d 0x0000f54d 12  13   .rodata ascii   St9bad_alloc
331 0x0000f55a 0x0000f55a 24  25   .rodata ascii   St20bad_array_new_length
332 0x0000f573 0x0000f573 12  13   .rodata ascii   St9type_info
333 0x0000f580 0x0000f580 11  12   .rodata ascii   St8bad_cast
334 0x0000f58c 0x0000f58c 14  15   .rodata ascii   St10bad_typeid
335 0x0000f610 0x0000f610 30  124  .rodata utf32le DPpppppppppppppppppppppppppppp
336 0x0000f6a4 0x0000f6a4 4   20   .rodata utf32le P|`l
337 0x0000f6da 0x0000f6da 6   14   .rodata utf16le \e,7L`|
338 0x0000f76a 0x0000f76a 5   6    .rodata ascii   +\n:IE
339 0x0000f808 0x0000f808 32  66   .rodata utf16le &&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
0   0x000cca31 0x000cea31 4   5    .data   ascii   STSN
1   0x000cca40 0x000cea40 17  18   .data   ascii   G1ARyk_p}ooUroh}r
...
70  0x000cd304 0x000cf304 4   5    .data   ascii   hi\t@
71  0x000cd30e 0x000cf30e 14  16   .data   utf8    ǡ#Gaj}j$gjel$X blocks=Latin Extended-B,Basic Latin
72  0x000cd31e 0x000cf31e 20  21   .data   ascii   ybel0B"Gaj}j$gjel$Be
73  0x000cd333 0x000cf333 6   7    .data   ascii   nlny0\v
74  0x000cd340 0x000cf340 10  11   .data   ascii   ?=,\b9;39?=
75  0x000cd34b 0x000cf34b 4   5    .data   ascii   6>7X
...
195 0x000ce8b0 0x000d08b0 11  12   .data   ascii   2V{t~hus~5t
196 0x000ce8bc 0x000d08bc 97  98   .data   ascii   n5Ohs!AVp{l{5v{t}5Inhst}!Vp{l{5v{t}5Inhst}!AVp{l{5v{t}5Inhst}!Vp{l{5v{t}5Inhst}!3V{t~hus~5~{n{x{i
197 0x000ce91e 0x000d091e 8   9    .data   ascii   5Yohiuh!
...
225 0x000cef2e 0x000d0f2e 31  32   .data   ascii   P-]ahl~h-nlaa-dcdy%$-bc-`ldc-ye
226 0x000cef4e 0x000d0f4e 5   6    .data   ascii   hli#\r
227 0x000cef58 0x000d0f58 19  20   .data   ascii   ALVUID\%l|mzzq@lwjk
228 0x000cef74 0x000d0f74 5   6    .data   ascii   _VKZ\
229 0x000cef82 0x000d0f82 13  14   .data   ascii   wXMPO\q\UI\K9
```

## `-s`：symbols

```bash
➜  arm64-v8a rabin2 -s libtacker.so
[Symbols]
nth paddr      vaddr      bind   type size  lib name                                demangled
―――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――
48  0x00044ce8 0x00044ce8 GLOBAL FUNC 6608      .datadiv_decode16117807209816376729
49  0x00078a04 0x00078a04 GLOBAL FUNC 2696      .datadiv_decode9901940071257331957
...
73  0x000a8884 0x000a8884 GLOBAL FUNC 4         .datadiv_decode11706101414295225912
74  0x000aa438 0x000aa438 GLOBAL FUNC 1436      JNI_OnLoad
75  0x00026d98 0x00026d98 GLOBAL FUNC 18656     .datadiv_decode12335027288954124723
...
117 0x000a5e74 0x000a5e74 GLOBAL FUNC 4         .datadiv_decode5454406552017557296
1   0x000c9240 0x000c9240 GLOBAL FUNC 16        imp.__cxa_finalize
2   0x000c9250 0x000c9250 GLOBAL FUNC 16        imp.__cxa_atexit
3   0x000c9260 0x000c9260 GLOBAL FUNC 16        imp.__android_log_print
4   0x000c9270 0x000c9270 GLOBAL FUNC 16        imp.__stack_chk_fail
5   0x000c9280 0x000c9280 GLOBAL FUNC 16        imp.memset
6   0x000c9290 0x000c9290 GLOBAL FUNC 16        imp.strncpy
7   0x000c92a0 0x000c92a0 GLOBAL FUNC 16        imp.strncat
8   0x000c92b0 0x000c92b0 GLOBAL FUNC 16        imp.pthread_self
9   0x000c92c0 0x000c92c0 GLOBAL FUNC 16        imp.malloc
10  0x000c92d0 0x000c92d0 GLOBAL FUNC 16        imp.free
11  0x000c92e0 0x000c92e0 GLOBAL FUNC 16        imp.posix_memalign
12  ---------- ---------- GLOBAL OBJ  16        imp.__sF
13  0x000c92f0 0x000c92f0 GLOBAL FUNC 16        imp.vfprintf
14  0x000c9300 0x000c9300 GLOBAL FUNC 16        imp.fputc
15  0x000c9310 0x000c9310 GLOBAL FUNC 16        imp.vasprintf
16  0x000c9320 0x000c9320 GLOBAL FUNC 16        imp.android_set_abort_message
17  0x000c9330 0x000c9330 GLOBAL FUNC 16        imp.openlog
18  0x000c9340 0x000c9340 GLOBAL FUNC 16        imp.syslog
19  0x000c9350 0x000c9350 GLOBAL FUNC 16        imp.closelog
20  0x000c9360 0x000c9360 GLOBAL FUNC 16        imp.abort
21  0x000c9370 0x000c9370 GLOBAL FUNC 16        imp.strlen
22  0x000c9380 0x000c9380 GLOBAL FUNC 16        imp.realloc
23  0x000c9390 0x000c9390 GLOBAL FUNC 16        imp.memmove
24  0x000c93a0 0x000c93a0 GLOBAL FUNC 16        imp.__memmove_chk
25  0x000c93b0 0x000c93b0 GLOBAL FUNC 16        imp.__strlen_chk
26  0x000c93c0 0x000c93c0 GLOBAL FUNC 16        imp.memchr
27  0x000c93d0 0x000c93d0 GLOBAL FUNC 16        imp.__vsnprintf_chk
28  0x000c93e0 0x000c93e0 GLOBAL FUNC 16        imp.memcpy
29  0x000c93f0 0x000c93f0 GLOBAL FUNC 16        imp.pthread_mutex_lock
30  0x000c9400 0x000c9400 GLOBAL FUNC 16        imp.pthread_mutex_unlock
31  0x000c9410 0x000c9410 GLOBAL FUNC 16        imp.calloc
32  0x000c9420 0x000c9420 GLOBAL FUNC 16        imp.strcmp
33  0x000c9430 0x000c9430 GLOBAL FUNC 16        imp.pthread_getspecific
34  0x000c9440 0x000c9440 GLOBAL FUNC 16        imp.pthread_once
35  0x000c9450 0x000c9450 GLOBAL FUNC 16        imp.pthread_setspecific
36  0x000c9460 0x000c9460 GLOBAL FUNC 16        imp.pthread_key_delete
37  0x000c9470 0x000c9470 GLOBAL FUNC 16        imp.pthread_key_create
38  0x000c9480 0x000c9480 GLOBAL FUNC 16        imp.getauxval
39  0x000c9490 0x000c9490 GLOBAL FUNC 16        imp.__system_property_get
40  0x000c94a0 0x000c94a0 GLOBAL FUNC 16        imp.strncmp
41  0x000c94b0 0x000c94b0 GLOBAL FUNC 16        imp.fprintf
42  0x000c94c0 0x000c94c0 GLOBAL FUNC 16        imp.fflush
43  0x000c94d0 0x000c94d0 GLOBAL FUNC 16        imp.pthread_rwlock_wrlock
44  0x000c94e0 0x000c94e0 GLOBAL FUNC 16        imp.pthread_rwlock_unlock
45  0x000c94f0 0x000c94f0 GLOBAL FUNC 16        imp.dl_iterate_phdr
46  0x000c9500 0x000c9500 GLOBAL FUNC 16        imp.pthread_rwlock_rdlock
47  0x000c9510 0x000c9510 GLOBAL FUNC 16        imp.fwrite
```

## `-S`：sections

```bash
➜  arm64-v8a rabin2 -S libtacker.so
[Sections]

nth paddr          size vaddr         vsize perm type        name
―――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――
0   0x00000000      0x0 0x00000000      0x0 ---- NULL
1   0x00000238     0x98 0x00000238     0x98 -r-- NOTE        .note.android.ident
2   0x000002d0     0x24 0x000002d0     0x24 -r-- NOTE        .note.gnu.build-id
3   0x000002f8    0xb10 0x000002f8    0xb10 -r-- DYNSYM      .dynsym
4   0x00000e08     0xec 0x00000e08     0xec -r-- GNU_VERSYM  .gnu.version
5   0x00000ef4     0x40 0x00000ef4     0x40 -r-- GNU_VERNEED .gnu.version_r
6   0x00000f38    0x1ec 0x00000f38    0x1ec -r-- GNU_HASH    .gnu.hash
7   0x00001124    0x3b8 0x00001124    0x3b8 -r-- HASH        .hash
8   0x000014dc    0xc19 0x000014dc    0xc19 -r-- STRTAB      .dynstr
9   0x000020f8   0x8850 0x000020f8   0x8850 -r-- RELA        .rela.dyn
10  0x0000a948    0x450 0x0000a948    0x450 -r-- RELA        .rela.plt
11  0x0000ad98   0x1960 0x0000ad98   0x1960 -r-- PROGBITS    .gcc_except_table
12  0x0000c6f8   0x3434 0x0000c6f8   0x3434 -r-- PROGBITS    .rodata
13  0x0000fb2c   0x1dbc 0x0000fb2c   0x1dbc -r-- PROGBITS    .eh_frame_hdr
14  0x000118e8   0x8cd4 0x000118e8   0x8cd4 -r-- PROGBITS    .eh_frame
15  0x0001a5c0  0xaec60 0x0001a5c0  0xaec60 -r-x PROGBITS    .text
16  0x000c9220    0x300 0x000c9220    0x300 -r-x PROGBITS    .plt
17  0x000c9520   0x2eb8 0x000ca520   0x2eb8 -rw- PROGBITS    .data.rel.ro
18  0x000cc3d8     0x10 0x000cd3d8     0x10 -rw- FINI_ARRAY  .fini_array
19  0x000cc3e8    0x230 0x000cd3e8    0x230 -rw- INIT_ARRAY  .init_array
20  0x000cc618    0x1d0 0x000cd618    0x1d0 -rw- DYNAMIC     .dynamic
21  0x000cc7e8     0xc0 0x000cd7e8     0xc0 -rw- PROGBITS    .got
22  0x000cc8a8    0x188 0x000cd8a8    0x188 -rw- PROGBITS    .got.plt
23  0x000cca30   0x25d8 0x000cea30   0x25d8 -rw- PROGBITS    .data
24  0x000cf008      0x0 0x000d1010    0xad0 -rw- NOBITS      .bss
25  0x000cf008     0xc6 0x00000000     0xc6 ---- PROGBITS    .comment
26  0x000cf0ce    0x104 0x00000000    0x104 ---- STRTAB      .shstrtab
```

## `-SS`：segments

```bash
➜  arm64-v8a rabin2 -SS libtacker.so
[Segments]

nth paddr          size vaddr         vsize perm type name
――――――――――――――――――――――――――――――――――――――――――――――――――――――――――
0   0x00000040    0x1f8 0x00000040    0x1f8 -r-- MAP  PHDR
1   0x00000000  0xc9520 0x00000000  0xc9520 -r-x MAP  LOAD0
2   0x000c9520   0x3510 0x000ca520   0x3510 -rw- MAP  LOAD1
3   0x000cca30   0x25d8 0x000cea30   0x30b0 -rw- MAP  LOAD2
4   0x000cc618    0x1d0 0x000cd618    0x1d0 -rw- MAP  DYNAMIC
5   0x000c9520   0x3510 0x000ca520   0x3ae0 -r-- MAP  GNU_RELRO
6   0x0000fb2c   0x1dbc 0x0000fb2c   0x1dbc -r-- MAP  GNU_EH_FRAME
7   0x00000000      0x0 0x00000000      0x0 -rw- MAP  GNU_STACK
8   0x00000238     0xbc 0x00000238     0xbc -r-- MAP  NOTE
9   0x00000000     0x40 0x00000000     0x40 -rw- MAP  ehdr
```

