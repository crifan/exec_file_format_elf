# 可执行文件格式：ELF

* 最新版本：`v1.1.0`
* 更新时间：`20240824`

## 简介

介绍常见的可执行文件格式：ELF。主要是Linux和Android的常见格式。先是ELF概览，包括ELF文件类型和术语和概念；然后是ELF结构详解，包括两种视图、结构图、链接和执行过程以及section节和segment段；然后介绍ELF的解析工具，包括读取信息的和解析修改的；读取信息的有Linux通用的readelf、objdump、rabin2等和Android专用的JEB等。且都有详细的安装、用法和举例；解析工具包括LIEF；然后专门介绍Android中的ELF格式。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### HonKit源码

* [crifan/exec_file_format_elf: 可执行文件格式：ELF](https://github.com/crifan/exec_file_format_elf)

#### 如何使用此HonKit源码去生成发布为电子书

详见：[crifan/honkit_template: demo how to use crifan honkit template and demo](https://github.com/crifan/honkit_template)

### 在线浏览

* [可执行文件格式：ELF book.crifan.org](https://book.crifan.org/books/exec_file_format_elf/website/)
* [可执行文件格式：ELF crifan.github.io](https://crifan.github.io/exec_file_format_elf/website/)

### 离线下载阅读

* [可执行文件格式：ELF PDF](https://book.crifan.org/books/exec_file_format_elf/pdf/exec_file_format_elf.pdf)
* [可执行文件格式：ELF ePub](https://book.crifan.org/books/exec_file_format_elf/epub/exec_file_format_elf.epub)
* [可执行文件格式：ELF Mobi](https://book.crifan.org/books/exec_file_format_elf/mobi/exec_file_format_elf.mobi)

## 版权和用途说明

此电子书教程的全部内容，如无特别说明，均为本人原创。其中部分内容参考自网络，均已备注了出处。如发现有侵权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

各种技术类教程，仅作为学习和研究使用。请勿用于任何非法用途。如有非法用途，均与本人无关。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 其他

### 作者的其他电子书

本人`crifan`还写了其他`150+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)

### 关于作者

关于作者更多介绍，详见：

[关于CrifanLi李茂 – 在路上](https://www.crifan.org/about/)
