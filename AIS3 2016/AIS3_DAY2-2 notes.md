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

#### nasm & objdump
Assemble / disassemble shellcode
```
$ nano a.asm

push 861096257
mov eax, 4
mov ebx, 1
mov ecx, esp
mov edx, 4
int 0x80
ret

$ nasm a.asm -o a.o -felf32
$ objdump -d -M intel a.o
```
nasm a.asm -o a.o -felf32 //組譯
objdump -d -M intel a.o //執行
then you can get 
```
a.o file format elf32-i386

Disassembly of section .text

00000000 <.text>:
 0:  68 41 49 53 53   push   0X33534941
 5:  b8 04 00 00 00   mov    eax,0x4
 a:  bb 01 00 00 00   mov    ebx,0x1
 f:  89 e1            mov    ecx,esp
11:  ba 04 00 00 00   mov    edx,0x4
16:  cd 80            int    0x80
18:  c3               ret
```
#### Extract Shellcode
```
$ objcopy -O binary a.o code
$ xxd -i code
```
objcopy -O binary a.o code //中間的shellcode抽出來
xxd -i code //可以產生0x__ 的code

xxd code
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