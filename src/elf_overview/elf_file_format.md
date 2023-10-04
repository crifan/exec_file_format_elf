# ELF文件类型

* ELF文件类型
  * `Relocatable File`=`可重定位文件`
    * an object file that holds code and data suitable for linking with other object files to create an executable or a shared object file. In other word, you can say that relocatable file is a foundation for creating executables and libraries
    * 常见后缀
      * object file=`.o`文件
        * 举例
          * `gcc -c test.c`
            * 生成：`test.o`
      * Kernel module = `.o`或`.ko`
  * `Executable File`=`可执行文件`
    * object file that holds a program suitable for execution
    * 常见后缀：无后缀
      * 二进制文件
        * `gcc -o test test.c`
          * 生成（无后缀的）：`test`
  * `Shared Object File`=`共享对象文件`=SO文件=`Shared object`==`DYNamic link library`
    * A shared object file holds code and data suitable for linking in two contexts
      1. the link editor may process it with other relocatable and shared object files to create another object file
      2. the dynamic linker combines it with an executable file and other shared objects to create a process image
    * 常见后缀
      * `.so`文件

## 举例说明

### 用readelf查看header中文件类型

* 举例1

可以用`readelf`查看header，确定一个文件的类型到底是什么：`Relocatable file`/`Executable file`/`Shared object file`

```bash
$ readelf -h /bin/ls
Type: EXEC (Executable file)

$ readelf -h /usr/lib/crt1.o
Type: REL (Relocatable file)

$ readelf-h /lib/libc-2.3.2.so
Type: DYN (Shared object file)
```

* 举例2

```bash
➜  arm64-v8a readelf -h libtacker.so
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF64
...
  Type:                              DYN (Shared object file)
```

-》

* ARM64架构的`Shared Object File`=`DYN`=`Dynamic Library`
