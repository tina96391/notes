# AIS3 DAY2-2 Binary Exploitation
<!-- http://lab.winesap.tw/ais3-2016/#/1 -->
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