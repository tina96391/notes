# AIS3 DAY1 Exploit Generation
download tools first</br>

**Exploit Generation**
 - Random testing
 - Symbolic execution
 - Concolic execution
	- Concrete+Symbolic=Concolic

**Hacker’s Tool Chain**

- Bug Fuzzer
  - Crash
  - meta-fuzz,  smart-fuzzed, zzuf, peach, tainstscope
- Crash detector or Failure Monitor
  - Taint Track
  - gdb, ollydbg, Pin, valgrind, CRED, Beagle, !exploitable,...
- Exploit-code Generator ← missing link of the tool chain
  - Manually Efforts with Expertise
  - Heelan’s, AEG, Q, MAUHEM, and CRAX
- Shell-code forger
  - Customised Payload
  - An Easier Botnet Builder
  - MSF
  
--- 

## LAB
**Z3**「聰明暴力破解」-解數學or密碼學相關題目</br>
<!-- https://hackmd.io/s/HkKE0fIc -->
1. Reverse the algorthm
2. Re-implement in Python
3. Ask Z3


環境準備→編譯安裝 z3 及 python binding</br>
```
$ git clone https://github.com/Z3Prover/z3
$ cd z3
$ python scripts/mk_make.py
$ cd build
$ make
$ sudo make install
```
測試 python binding
```
$ python
Python 2.7.6 (default, Jun 22 2015, 17:58:13)
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from z3 import *
>>>
```
簡單測試
x + y = 6
2x = 3y + 2
```
from z3 import *

x = Int('x')
y = Int('y')

s = Solver()
s.add(x + y == 6)
s.add(2 * x == 3 * y + 2)

print(s.check())
print(s.model())
```
sat
[y = 2, x = 4]

**KLEE**「無腦且快速的暴力破解」</br>
<!-- https://hackmd.io/s/Hkq3bEU9 -->
1. Need to go through complicated condition
2. Source code

**CRAX**
see https://github.com/SQLab/CRAX-lab 

**angr**
- Open-source: https://github.com/angr
- a binary analysis framework created by the computer security lab at UC Santa Barbara
- python-based
-  both static and dynamic symbolic ("concolic") analysis 
-  Architecture independent 
-  use docker