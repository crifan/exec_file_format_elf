# objdump的语法help

```bash
➜  ~ objdump --help
OVERVIEW: llvm object file dumper

USAGE: objdump [options] <input object files>

OPTIONS:
  --adjust-vma=offset     Increase the displayed address by the specified offset
  --all-headers           Display all available header information, relocation entries and the symbol table
  --arch-name=<value>     Target arch to disassemble for, see --version for available targets
  --archive-headers       Display archive header information
  -a                      Alias for --archive-headers
  -C                      Alias for --demangle
  --debug-vars-indent=<value>
                          Distance to indent the source-level variable display, relative to the start of the disassembly
  --debug-vars=<value>    Print the locations (in registers or memory) of source-level variables alongside disassembly. Supported formats: ascii, unicode (default)
  --demangle              Demangle symbol names
  --disassemble-all       Disassemble all sections found in the input files
  --disassemble-symbols=<value>
                          List of symbols to disassemble. Accept demangled names when --demangle is specified, otherwise accept mangled names
  --disassemble-zeroes    Do not skip blocks of zeroes when disassembling
  --disassembler-options=options
                          Pass target specific disassembler options
  --disassemble           Disassemble all executable sections found in the input files
  --dwarf=<value>         Dump the specified DWARF debug sections. The only supported value is 'frames'
  --dynamic-reloc         Display the dynamic relocation entries in the file
  --dynamic-syms          Display the contents of the dynamic symbol table
  -D                      Alias for --disassemble-all
  -d                      Alias for --disassemble
  --fault-map-section     Display the content of the fault map section
  --file-headers          Display the contents of the overall file header
  --full-contents         Display the content of each section
  -f                      Alias for --file-headers
  --headers               Alias for --section-headers
  --help                  Display available options (--help-hidden for more)
  -h                      Alias for --section-headers
  -j <value>              Alias for --section
  --line-numbers          When disassembling, display source line numbers. Implies --disassemble
  -l                      Alias for --line-numbers
  --macho                 Use MachO specific object file parser
  --mattr=a1,+a2,-a3,...  Target specific attributes (--mattr=help for details)
  --mcpu=cpu-name         Target a specific cpu type (--mcpu=help for details)
  -M <value>              Alias for --disassembler-options=
  -m                      Alias for --macho
  --no-leading-addr       When disassembling, do not print leading addresses
  --no-print-imm-hex      Do not use hex format for immediate values (default)
  --no-show-raw-insn      When disassembling instructions, do not print the instruction bytes.
  --prefix-strip=prefix   Strip out initial directories from absolute paths. No effect without --prefix
  --prefix=prefix         Add prefix to absolute paths
  --print-imm-hex         Use hex format for immediate values
  --private-headers       Display format specific file headers
  -p                      Alias for --private-headers
  --raw-clang-ast         Dump the raw binary contents of the clang AST section
  --reloc                 Display the relocation entries in the file
  -R                      Alias for --dynamic-reloc
  -r                      Alias for --reloc
  --section-headers       Display summaries of the headers for each section.
  --section=<value>       Operate on the specified sections only. With --macho dump segment,section
  --show-lma              Display LMA column when dumping ELF section headers
  --source                When disassembling, display source interleaved with the disassembly. Implies --disassemble
  --start-address=address Set the start address for disassembling, printing relocations and printing symbols
  --stop-address=address  Set the stop address for disassembling, printing relocations and printing symbols
  --symbol-description    Add symbol description for disassembly. This option is for XCOFF files only.
  --symbolize-operands    Symbolize instruction operands when disassembling
  --syms                  Display the symbol table
  -S                      Alias for --source
  -s                      Alias for --full-contents
  --triple=<value>        Target triple to disassemble for, see --version for available targets
  -T                      Alias for --dynamic-syms
  -t                      Alias for --syms
  --unwind-info           Display unwind information
  -u                      Alias for --unwind-info
  --version               Display the version of this program
  -v                      Alias for --version
  --wide                  Ignored for compatibility with GNU objdump
  --x86-asm-syntax=att    Emit AT&T-style disassembly
  --x86-asm-syntax=intel  Emit Intel-style disassembly
  -x                      Alias for --all-headers
  -z                      Alias for --disassemble-zeroes

llvm-objdump MachO Specific Options:
  --arch=<value>         architecture(s) from a Mach-O file to dump
  --archive-member-offsets
                         Print the offset to each archive member for Mach-O archives (requires --macho and --archive-headers)
  --bind                 Display mach-o binding info
  --data-in-code         Print the data in code table for Mach-O objects (requires --macho)
  --dis-symname <value>  disassemble just this symbol's instructions (requires --macho)
  --dsym=<value>         Use .dSYM file for debug info
  --dyld_info            Print bind and rebase information used by dyld to resolve external references in a final linked binary (requires --macho)
  --dylib-id             Print the shared library's id for the dylib Mach-O file (requires --macho)
  --dylibs-used          Print the shared libraries used for linked Mach-O files (requires --macho)
  --exports-trie         Display mach-o exported symbols
  --full-leading-addr    Print full leading address
  --function-starts      Print the function starts table for Mach-O objects (requires --macho)
  -g                     Print line information from debug info if available
  --indirect-symbols     Print indirect symbol table for Mach-O objects (requires --macho)
  --info-plist           Print the info plist section as strings for Mach-O objects (requires --macho)
  --lazy-bind            Display mach-o lazy binding info
  --link-opt-hints       Print the linker optimization hints for Mach-O objects (requires --macho)
  --no-leading-headers   Print no leading headers
  --no-symbolic-operands do not symbolic operands when disassembling (requires --macho)
  --non-verbose          Print the info for Mach-O objects in non-verbose or numeric form (requires --macho)
  --objc-meta-data       Print the Objective-C runtime meta data for Mach-O files (requires --macho)
  --private-header       Display only the first format specific file header
  --rebase               Display mach-o rebasing info
  --rpaths               Print the runtime search paths for the Mach-O file (requires --macho)
  --universal-headers    Print Mach-O universal headers (requires --macho)
  --weak-bind            Display mach-o weak binding info

Pass @FILE as argument to read options from FILE.
```
