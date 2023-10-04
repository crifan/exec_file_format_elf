# ELF术语和概念

## ELF相关术语

* ELF相关术语
  * Table表
    * GOT=Global Offset Table
    * SHT=Section Header Table
    * PLT=Procedure Linkage Table
    * PHT=Program Header Table
      * the kernel knows which section goes to which segment
  * 文件格式
    * COFF=Common object file format
    * 其他文件格式
      * Mach-O=Mach object file format
      * PE=Portable executable
  * BSS=Block Started by Symbol
    * The uninitialized data segment containing statically-allocated variables
  * DWARF
    * A standardized debugging data format
  * PC=Program counter
    * On x86, this is the same as IP (Instruction Pointer) register
  * section
    * SHF=Section header Flag
    * shstrtab = section header string table
  * 地址
    * RVA=Relative virtual address
    * VMA=Virtual Memory Area/Address
  * 加载
    * PIC=Position independent code
    * PIE=Position independent executable
    * REL=RELA=Relocation
  * TLS=Thread-Local Storage
    * DTV=Dynamic thread vector
    * access models
      * GD=Global Dynamic
        * dynamic TLS
      * IE=Initial Executable
        * static TLS with assigned offsets
      * LD=Local Dynamic
        * dynamic TLS of local symbols
      * LE=Local Executable
        * static TLS

## ELF相关概念

* ELF相关概念
  * section
    * 不同的section
      * .text=代码段
      * .data=数据段：全局变量
      * .bss：未初始化的数据值
        * 【整理】ELF相关：.bss节
  * segment ~= VMA
    * Linux内核内部的概念
    * contains virtually contiguous page frame
