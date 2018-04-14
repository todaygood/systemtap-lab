How to analyis userspace program with systemtap 
====================================================

## Ref
http://blog.yufeng.info/archives/2033

debuginfo-install glibc

gcc -g -o malloc_program malloc_program.c 

```bash
[root@cloud01 process]# stap -d malloc_program  malloc.stp -c ./malloc_program
~
 0x7f41a3b6af70 : __libc_malloc+0x0/0xe0 [/usr/lib64/libc-2.17.so]
 0x40053b : fun+0xe/0x10 [...me/margin/todaygood/systemtap-lwtools/process/malloc_program]
 0x400556 : main+0x19/0x23 [...me/margin/todaygood/systemtap-lwtools/process/malloc_program
 0x7f41a3b0cb35 : __libc_start_main+0xf5/0x1c0 [/usr/lib64/libc-2.17.so]
 0x400469 : _start+0x29/0x30 [...me/margin/todaygood/systemtap-lwtools/process/malloc_program]

[root@cloud01 process]# addr2line -e ./malloc_program 0x40053b
/home/margin/todaygood/systemtap-lwtools/process/malloc_program.c:5
```
