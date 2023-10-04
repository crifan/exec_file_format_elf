# ELF概览

* `ELF`=`Executable and Linking Format`=`可执行和链接格式`
  * 是什么：一种文件格式file format
    * that defines how an object file is composed and organized
  * 用途：With this information, your kernel and the binary loader know how to load the file, where to look for the code, where to look the initialized data, which shared library that needs to be loaded and so on.
  * 主要历史
    * Linux和安卓通用的[可执行文件格式](https://book.crifan.org/books/executable_file_format/website/)：`ELF`
      * 最早：Linux通用可执行文件格式：`ELF`
      * 后来：Android是基于Linux的，所以也是沿用`ELF`
        * 详见：[Android中的ELF](../android_elf/README.md)

## ELF资料

* ELF资料
  * ELF格式详细定义
    * [Executable and Linkable Format - Wikipedia](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format)
    * [elf(5) — Linux manual pages (courier-mta.org)](http://manpages.courier-mta.org/htmlman5/elf.5.html)
    * [ELF Header (sco.com)](https://www.sco.com/developers/gabi/latest/ch4.eheader.html)
  * 各个section节的含义
    * [Special Sections (oracle.com)](https://docs.oracle.com/en/operating-systems/solaris/oracle-solaris/11.4/linkers-libraries/special-sections.html#GUID-7C59F05C-4F6D-4599-9D85-86982ABDA4F6)
    * [Executable and Linkable Format (ELF) (netmeister.org)](https://stevens.netmeister.org/631/elf.html)
  * elf内部过程
    * [s.eresi-project.org/inc/articles/elf-rtld.txt](http://s.eresi-project.org/inc/articles/elf-rtld.txt)
      * Understanding Linux ELF RTLD internals
