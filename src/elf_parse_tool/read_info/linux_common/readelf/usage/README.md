# readelf用法

概述：

* 单个参数
  * 显示头信息
    * file-header
      * `-h`=`--file-header`: 显示ELF文件头信息
        ```bash
        readelf -h elfFile
        ```
    * program-headers
      * `-l`=`--program-headers`=`--segments`: 显示程序的头信息和段信息
        ```bash
        readelf -l elfFile
        ```
    * section-headers
      * `-S`=`--section-headers`=`--sections`: 显示节的头信息
        ```bash
        readelf -S elfFile
        ```
  * `-s`=`--syms`=`--symbols`: 显示符号表
    ```bash
    readelf -s elfFile
    ```
    -sV：显示符号表且带版本信息
  * `-r`=`--relocs`: 显示重定位信息
    ```bash
    readelf -r elfFile
    ```
  * 打印信息
    * 以`hex`=`十六进制`=`二进制`方式
      * `-x`=`--hex-dump=<number|name>`
        ```bash
        readelf -x .dynsym elfFile
        readelf -x 8 elfFile
        ```
    * 以`string`=`字符串`形式
      * `-p`=`--string-dump=<number|name>`
        ```bash
        readelf -p .dynsym elfFile
        readelf -p 8 elfFile
        ```
* 组合参数
  * `-e`=`--headers`=`-h -l -S`
    ```bash
    readelf -e elfFile
    ```
  * `-a`=`--all` == `-h -l -S -s -r -d -V -A -I`
    ```bash
    readelf -a elfFile
    ```
  * `-sV`=`--syms --version-info`: 显示符号表且带版本信息
    ```bash
    readelf -sV elfFile
    ```
