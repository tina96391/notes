# AIS3 DAY2-2 Binary Exploitation
<!-- http://lab.winesap.tw/ais3-2016/#/1 -->
nasm a.asm -o a.o -felf32 //�sĶ
objdump -d -M intel a.o //����
objcopy -O binary a.o code //������shellcode��X��
xxd -i code //xxd code
Run shellcode
gcc test.c -o test -m32(�b32bite���ҤU) -zexecstack(�����O�@)

GDB���O
b = breakpoint
si = step instruction 
ni= next instruction
r = run
c = continue

GDB�n�|!
IDA