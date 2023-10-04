# ELF的2种视图

* ELF的2种视图views
  * 概述
    * Linking View
      * Linking链接时：需要Section Header Table，不需要Program Header Table
    * Execution View
      * Execution执行时：需要Program Header Table，不需要Section Header Table
  * ELF的2种视图
    * ![elf_obj_file_format](../assets/img/elf_obj_file_format.png)
    * ![elf_linking_execution_view](../assets/img/elf_linking_execution_view.jpg)
    * ![elf_linking_execution_view_blue](../assets/img/elf_linking_execution_view_blue.jpg)
    * 文字版
      * ![elf_linking_execution_view_text](../assets/img/elf_linking_execution_view_text.png)
        ```bash
                      +-----------------+
                +----| ELF File Header |----+
                |    +-----------------+    |
                v                           v
        +-----------------+      +-----------------+
        | Program Headers |      | Section Headers |
        +-----------------+      +-----------------+
              ||                               ||
              ||                               ||
              ||                               ||
              ||   +------------------------+  ||
              +--> | Contents (Byte Stream) |<--+
                  +------------------------+
        ```
