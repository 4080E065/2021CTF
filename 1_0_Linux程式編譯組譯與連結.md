# Linux C 程式的編譯與運行
## 範例
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
# Ubuntu 16.04(32bit)
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













