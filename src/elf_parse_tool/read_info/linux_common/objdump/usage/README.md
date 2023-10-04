# objdump用法

概述：

* 单个参数
  * `-a`=`--archive-headers`：显示存档文件头信息
    * 说明
      * 看一个`.a`静态库文件中包含了哪些目标文件
    * 语法
      ```bash
      objdump -a elfFile
      ```
  * `-f`=`--file-headers`：显示全部文件头信息
    * 语法
      ```bash
      objdump -f elfFile
      ```
  * `-h`=`--headers`=`--section-headers`：显示节的头信息
    * 对比
      * == `readelf -S`
    * 语法
      ```bash
      objdump -h elfFile
      ```
  * `-s`=`--full-contents`：显示每个节的内容
    * 语法
      ```bash
      objdump -s elfFile
      ```
  * `-t`=`--syms`：显示符号表
    * 语法
      ```bash
      objdump -t elfFile
      ```
  * `-T`=`--dynamic-syms`：显示动态符号表
    * 说明
      * 输出目标文件的动态符号表（Dynamic Symbol Table），即目标ELF文件中名字叫做.dynsym节内的内容
      * 通过这张表内的信息，可以看出由本ELF文件中导出的符号，和需要从别的动态库中导入的符号。如果第三列显示“*UND*”表明这个符号在本ELF文件中未定义，也就是说这个符号要从别的动态库中导入，其它的情况表明这个符号由本ELF文件中定义。
    * 语法
      ```bash
      objdump -T elfFile
      ```
  * `-r`=`--reloc`：显示静态重定位入口
    * 语法
      ```bash
      objdump -r elfFile
      ```
  * `-R`=`--dynamic-reloc`：显示动态重定位入口
    * 说明
      * 这个参数仅仅对于动态目标文件有意义，比如动态库文件（`.so`）
    * 语法
      ```bash
      objdump -R elfFile
      ```
  * 反汇编
    * `-d`=`--disassemble`：反汇编可执行指令的内容
      * 语法
        ```bash
        objdump -d elfFile
        ```
    * `-D`=`--disassemble-all`：反汇编所有指令的内容
      * 语法
        ```bash
        objdump -D elfFile
        ```
* 组合参数
  * `-x`=`--all-headers`==`-h --syms --reloc`：显示全部头信息
    * 语法
      ```bash
      objdump -x elfFile
      ```
