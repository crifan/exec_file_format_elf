# ELF结构图

* ELF结构布局图=ELF layout
  * ![elf_layout_text](../assets/img/elf_layout_text.png)
  * 文字版
    ```bash
        +-------------------------------+
        | ELF File Header               |
        +-------------------------------+
        | Program Header for segment #1 |
        +-------------------------------+
        | Program Header for segment #2 |
        +-------------------------------+
        | ...                           |
        +-------------------------------+
        | Contents (Byte Stream)        |
        | ...                           |
        +-------------------------------+
        | Section Header for section #1 |
        +-------------------------------+
        | Section Header for section #2 |
        +-------------------------------+
        | ...                           |
        +-------------------------------+
        | ".shstrtab" section           |
        +-------------------------------+
        | ".symtab"   section           |
        +-------------------------------+
        | ".strtab"   section           |
        +-------------------------------+
    ```
    * 举例
      * 打开so可以看到顶部有ELF字样
        * ![elf_header_show_elf](../assets/img/elf_header_show_elf.png)
  * ![elf_layout_2](../assets/img/elf_layout_2.jpg)
  * ![elf_layout_offset](../assets/img/elf_layout_offset.jpg)


## 举例

### Android ELF 文件格式

* Android ELF 文件格式
  * ![android_elf_file_foramt_example](../assets/img/android_elf_file_foramt_example.png)
