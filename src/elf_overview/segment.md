# Segment段

* `segment`=`段`的类型和含义：
  * `DYNAMIC`：对于动态二进制，此段保存了动态链接信息
    * =ELF的链接视图时的：`.dynamic`节
  * `GNU_EH_FRAME`：Frame unwind information (EH = Exception Handling). This segment is usually the same as .eh_frame_hdr section in ELF's linking view.
  * `GNU_RELRO`：This segment indicates the memory region which should be made Read-Only after relocation is done. This segment usually appears in a dynamic link library and it contains .ctors, .dtors, .dynamic, .got sections. See paragraph below.
  * `GNU_STACK`：The permission flag of this segment indicates whether the stack is executable or not. This segment does not have any content; it is just an indicator.
  * `INTERP`：For dynamic binaries, this holds the full pathname of runtime linker `ld.so`
    * =ELF的链接视图时的：`.interp`节
  * `LOAD`：Loadable program segment. Only segments of this type are loaded into memory during execution.
  * `NOTE`：Auxiliary information.
    * For core dumps, this segment contains the status of the process (when the core dump is created), such as the signal (the process received and caused it to dump core), pending & held signals, process ID, parent process ID, user ID, nice value, cumulative user & system time, values of registers (including the program counter!)
    * For more info, see struct elf_prstatus and struct elf_prpsinfo in Linux kernel source file include/linux/elfcore.h and struct user_regs_struct in arch/x86/include/asm/user_64.h
  * `TLS`：Thread-Local Storage
