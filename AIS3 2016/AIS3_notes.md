# AIS3 DAY1
download tools</br>
**Exploit Generation**</br>
--Random testing</br>
--Symbolic execution</br>
Concolic execution</br>
	.Concrete+Symbolic=Concolic</br>
--LAB</br>
**Z3**「聰明暴力破解」-解數學or密碼學相關題目</br>
1.Reverse the algorthm</br>
2.Re-implement in Python</br>
3.Ask Z3</br>

編譯安裝 z3 及 python binding</br>
$ git clone https://github.com/Z3Prover/z3</br>
$ cd z3</br>
$ python scripts/mk_make.py</br>
$ cd build</br>
$ make</br>
$ sudo make install</br>

**KLEE**「無腦且快速的暴力破解」</br>
1.Need to go through complicated condition</br>
2.Source code</br>