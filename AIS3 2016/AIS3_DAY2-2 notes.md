# AIS3 DAY2-2 Binary Exploitation
<!-- http://lab.winesap.tw/ais3-2016/#/1 -->

### Vulnerability and Exploitation
##### 漏洞利用
- 利用 (exploit) 程式本身存在的漏洞 (vulnerability)，取得程式的控制權
	- 本地提權 local(flash)
	- 遠端利用 Web上有漏洞，可以入侵遠端server
- Binary exploitation: 專指跟 binary 相關的漏洞利用(本次重點)

#### 取得控制權
- 控制程式的執行，做出非預期的行為
	- Control-Flow Hijack (取得控制權)
	- Return Oriented Programming (ROP)
	- 執行 shellcode

#### Shellcode
- 現在主流的計算機架構中，data 和 machine code 是混在記憶體裡的，並沒有分別
- 把 assembler 生成的 machine code 做為 data 送進去，只要能「執行」這塊 data 就能做到任何事

#### 測試時會用到的工具
- nasm, gdb, gcc, objdump, objcopy, hexedit
- In Ubuntu, install them by
```
apt-get install nasm gdb gcc binutils hexedit
```

nasm a.asm -o a.o -felf32 //編譯
objdump -d -M intel a.o //執行
objcopy -O binary a.o code //中間的shellcode抽出來
xxd -i code //xxd code
Run shellcode
gcc test.c -o test -m32(在32bite環境下) -zexecstack(關掉保護)

GDB指令
b = breakpoint
si = step instruction 
ni= next instruction
r = run
c = continue

GDB要會!
IDA