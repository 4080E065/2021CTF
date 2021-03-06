# Linux C 程式的編譯與運行
## 範例
```
檔名：helloCTFer.c
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
  ==> gcc helloCTFer.c  ==> 產生a.out執行檔
  ==> gcc helloCTFer.c -o helloCTFer
  ==> gcc helloCTFer.c -o helloCTFer.exe
(2)執行
  ==>./a.out
  ==>./helloCTFer
  ==>./helloCTFer.exe
(3)檢查執行檔檔案格式
  ==>file ./a.out
  ==>file ./helloCTFer
  ==>file ./helloCTFer.exe
```



