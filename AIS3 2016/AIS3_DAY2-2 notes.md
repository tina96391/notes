# AIS3 DAY2-2 Binary Exploitation
<!-- http://lab.winesap.tw/ais3-2016/#/1 -->

### Vulnerability and Exploitation
##### �|�}�Q��
- �Q�� (exploit) �{�������s�b���|�} (vulnerability)�A���o�{���������v
	- ���a���v local(flash)
	- ���ݧQ�� Web�W���|�}�A�i�H�J�I����server
- Binary exploitation: �M���� binary �������|�}�Q��(�������I)

#### ���o�����v
- ����{��������A���X�D�w�����欰
	- Control-Flow Hijack (���o�����v)
	- Return Oriented Programming (ROP)
	- ���� shellcode

#### Shellcode
- �{�b�D�y���p����[�c���Adata �M machine code �O�V�b�O����̪��A�èS�����O
- �� assembler �ͦ��� machine code ���� data �e�i�h�A�u�n��u����v�o�� data �N�వ������

#### ���ծɷ|�Ψ쪺�u��
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
nasm a.asm -o a.o -felf32 //��Ķ
objdump -d -M intel a.o //����
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
objcopy -O binary a.o code //������shellcode��X��
xxd -i code //�i�H����0x__ ��code

xxd code
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