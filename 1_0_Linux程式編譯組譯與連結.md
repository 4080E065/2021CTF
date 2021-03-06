# Linux C 程式的編譯與運行
### 範例
```
檔名：helloCTFer.c
指令：gedit helloCTFer.c
程式碼：
#include <stdio.h>
int main()
{
  printf("Hello CTFer\n");
  return 0;
}
```
## Ubuntu 16.04(32bit)
```
(1)編譯
  ==> gcc helloCTFer.c  ==> 產生a.out執行檔,ls檢查是否有a.out
  ==> gcc helloCTFer.c -o helloCTFer  ==> 產生helloCTFer,ls檢查是否有helloCTFer
  ==> gcc helloCTFer.c -o helloCTFer.exe  ==> 產生helloCTFer.exe,ls檢查是否有helloCTFer.exe
(2)執行
  ==>./a.out
      執行結果：Hello CTFer
  ==>./helloCTFer
      執行結果：Hello CTFer
  ==>./helloCTFer.exe
      執行結果：Hello CTFer
(3)檢查執行檔檔案格式
  ==>file ./a.out
      執行結果：./a.out: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=4258888fd293dae24c8143c584f1514ddcc7db0e, not stripped
  ==>file ./helloCTFer
      執行結果：./helloCTFer: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=4258888fd293dae24c8143c584f1514ddcc7db0e, not stripped
  ==>file ./helloCTFer.exe
      執行結果：./helloCTFer.exe: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=4258888fd293dae24c8143c584f1514ddcc7db0e, not stripped
```
```
指令：ls -al helloCTFer.*
執行結果：
-rw-rw-r-- 1 ksu ksu   73  三   6 20:11 helloCTFer.c
-rwxrwxr-x 1 ksu ksu 7352  三   6 20:12 helloCTFer.exe
```
```
指令：hexdump -C helloCTFer.exe
執行結果：
00000000  7f 45 4c 46 01 01 01 00  00 00 00 00 00 00 00 00  |.ELF............|
00000010  02 00 03 00 01 00 00 00  10 83 04 08 34 00 00 00  |............4...|
00000020  e0 17 00 00 00 00 00 00  34 00 20 00 09 00 28 00  |........4. ...(.|
00000030  1f 00 1c 00 06 00 00 00  34 00 00 00 34 80 04 08  |........4...4...|
00000040  34 80 04 08 20 01 00 00  20 01 00 00 05 00 00 00  |4... ... .......|
00000050  04 00 00 00 03 00 00 00  54 01 00 00 54 81 04 08  |........T...T...|
00000060  54 81 04 08 13 00 00 00  13 00 00 00 04 00 00 00  |T...............|
.........
```
### ELF File magic
```
ELF ==>可執行與可鏈結格式 （英語：Executable and Linkable Format，縮寫為ELF），常被稱為ELF格式，在電腦科學中，是一種用於執行檔、目的檔、共享庫和核心轉儲(core dump)的標準檔案格式。
參考網址：https://zh.wikipedia.org/zhtw/%E5%8F%AF%E5%9F%B7%E8%A1%8C%E8%88%87%E5%8F%AF%E9%8F%88%E6%8E%A5%E6%A0%BC%E5%BC%8F
```
### hexdump的用法
```
說明：有時候需要檢視一些二進位制檔案的內容,比如二進位制檔案中包含的某些字串。這個時候可以用hexdump工具看檢視。
參考網址：https://www.itread01.com/p/1385440.html
可用參數：[-bcCdovx] [-e format_string] [-f format_file] [-n length] [-s skip] file ...
hexdump還有很多的用法，具體可以參看man hexdump
參考網址：http://linux.51yip.com/search/hexdump
```
# Linux C 程式的編譯與運行:
```
編譯的各階段
 原始程式碼 ===>  helloCTFer.c
 預處理 ===> gcc –E helloCTFer.c –o helloCTFer.i    ===> 查看.i的架構
 編譯 ===> gcc –S helloCTFer.i  -o helloCTFer.s   ===> 查看.s的架構
 彙編 ===> gcc -c helloCTFer.s -o helloCTFer.o ===> 查看.o的架構
 連結 ===> gcc  helloCTFer.o -o helloCTFer  ===> 查看helloCTFer的架構
```
### 預處理
```
指令：gcc –E helloCTFer.c –o helloCTFer.i
```
```
指令：ls -al helloCTFer.*
執行結果：
-rw-rw-r-- 1 ksu ksu    73  三   6 20:11 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   6 20:12 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17538  三   6 20:33 helloCTFer.i
```
```
cat helloCTFer.i

# 1 "helloCTFer.c"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 1 "<command-line>" 2
# 1 "helloCTFer.c"
# 1 "/usr/include/stdio.h" 1 3 4
# 27 "/usr/include/stdio.h" 3 4
# 1 "/usr/include/features.h" 1 3 4
# 367 "/usr/include/features.h" 3 4
# 1 "/usr/include/i386-linux-gnu/sys/cdefs.h" 1 3 4
# 410 "/usr/include/i386-linux-gnu/sys/cdefs.h" 3 4
# 1 "/usr/include/i386-linux-gnu/bits/wordsize.h" 1 3 4
# 411 "/usr/include/i386-linux-gnu/sys/cdefs.h" 2 3 4
# 368 "/usr/include/features.h" 2 3 4
# 391 "/usr/include/features.h" 3 4
# 1 "/usr/include/i386-linux-gnu/gnu/stubs.h" 1 3 4

# 1 "/usr/include/i386-linux-gnu/gnu/stubs-32.h" 1 3 4
# 8 "/usr/include/i386-linux-gnu/gnu/stubs.h" 2 3 4
# 392 "/usr/include/features.h" 2 3 4
# 28 "/usr/include/stdio.h" 2 3 4

# 1 "/usr/lib/gcc/i686-linux-gnu/5/include/stddef.h" 1 3 4
# 216 "/usr/lib/gcc/i686-linux-gnu/5/include/stddef.h" 3 4

 .............................
# 2 "helloCTFer.c" 2

# 3 "helloCTFer.c"
int main()
{
   printf("Hello CTFer\n");
   return 0;
}
```
### 編譯
```
指令：gcc -S helloCTFer.i -o helloCTFer.s
```
```
指令：ls -al helloCTFer.*
執行結果：
-rw-rw-r-- 1 ksu ksu    73  三   6 20:11 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   6 20:12 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17538  三   6 20:33 helloCTFer.i
-rw-rw-r-- 1 ksu ksu   659  三   6 20:36 helloCTFer.s
```
### AT&T
```
指令：cat helloCTFer.s
執行結果：
	.file	"helloCTFer.c"
	.section	.rodata
.LC0:
	.string	"Hello CTFer"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	leal	4(%esp), %ecx
	.cfi_def_cfa 1, 0
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	.cfi_escape 0x10,0x5,0x2,0x75,0
	movl	%esp, %ebp
	pushl	%ecx
	.cfi_escape 0xf,0x3,0x75,0x7c,0x6
	subl	$4, %esp
	subl	$12, %esp
	pushl	$.LC0
	call	puts
	addl	$16, %esp
	movl	$0, %eax
	movl	-4(%ebp), %ecx
	.cfi_def_cfa 1, 0
	leave
	.cfi_restore 5
	leal	-4(%ecx), %esp
	.cfi_def_cfa 4, 4
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609"
	.section	.note.GNU-stack,"",@progbits
```
### 彙編
```
指令：gcc -c helloCTFer.s -o helloCTFer.o
```
```
指令：ls -al helloCTFer.*
執行結果：
-rw-rw-r-- 1 ksu ksu    73  三   6 20:11 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   6 20:12 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17538  三   6 20:33 helloCTFer.i
-rw-rw-r-- 1 ksu ksu  1072  三   6 20:39 helloCTFer.o
-rw-rw-r-- 1 ksu ksu   659  三   6 20:36 helloCTFer.s
```
### 查看helloCTFer.o
```
指令：hexdump -C helloCTFer.o
執行結果：
00000000  7f 45 4c 46 01 01 01 00  00 00 00 00 00 00 00 00  |.ELF............|
00000010  01 00 03 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  28 02 00 00 00 00 00 00  34 00 00 00 00 00 28 00  |(.......4.....(.|
00000030  0d 00 0a 00 8d 4c 24 04  83 e4 f0 ff 71 fc 55 89  |.....L$.....q.U.|
00000040  e5 51 83 ec 04 83 ec 0c  68 00 00 00 00 e8 fc ff  |.Q......h.......|
00000050  ff ff 83 c4 10 b8 00 00  00 00 8b 4d fc c9 8d 61  |...........M...a|
00000060  fc c3 48 65 6c 6c 6f 20  43 54 46 65 72 00 00 47  |..Hello CTFer..G|
00000070  43 43 3a 20 28 55 62 75  6e 74 75 20 35 2e 34 2e  |CC: (Ubuntu 5.4.|
00000080  30 2d 36 75 62 75 6e 74  75 31 7e 31 36 2e 30 34  |0-6ubuntu1~16.04|
00000090  2e 31 32 29 20 35 2e 34  2e 30 20 32 30 31 36 30  |.12) 5.4.0 20160|
000000a0  36 30 39 00 14 00 00 00  00 00 00 00 01 7a 52 00  |609..........zR.|
000000b0  01 7c 08 01 1b 0c 04 04  88 01 00 00 28 00 00 00  |.|..........(...|
000000c0  1c 00 00 00 00 00 00 00  2e 00 00 00 00 44 0c 01  |.............D..|
000000d0  00 47 10 05 02 75 00 43  0f 03 75 7c 06 5b 0c 01  |.G...u.C..u|.[..|
000000e0  00 41 c5 43 0c 04 04 00  00 00 00 00 00 00 00 00  |.A.C............|
..........
```
```
指令：file helloCTFer.o
執行結果：
helloCTFer.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
```
### 連結
```
指令：gcc helloCTFer.o -o helloCTFer
```
```
指令：./helloCTFer
執行結果：
Hello CTFer
```
```
指令：ls -al helloCTFer*
執行結果：
-rwxrwxr-x 1 ksu ksu  7352  三   6 20:43 helloCTFer
-rw-rw-r-- 1 ksu ksu    73  三   6 20:11 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   6 20:12 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17538  三   6 20:33 helloCTFer.i
-rw-rw-r-- 1 ksu ksu  1072  三   6 20:39 helloCTFer.o
-rw-rw-r-- 1 ksu ksu   659  三   6 20:36 helloCTFer.s
```





