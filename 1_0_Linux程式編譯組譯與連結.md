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













