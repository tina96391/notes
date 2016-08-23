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