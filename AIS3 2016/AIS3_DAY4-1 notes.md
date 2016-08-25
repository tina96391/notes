# AIS3 DAY4-1 Web Security & Hacking hands-on practice

��U�o��hacking���ϡGmap.norsecorp.com

### 0x03
#### Major Web Hacking Cases
- Still Web and Malicious code are two major threats from out-side attacker
- It's easy too attack than system and network hacking layers
- There are currently over 1 Billion websites on the web

https://www.youtube.com/watch?v=1FhD_cKaRKA 

#### http Protocol 
```
			�� Http request �� 
Web browser					 Server
			�� Http request �� 
```			
�b�����W���UF12�i�H�ݨ줸��
�bnetwork���ӥi�H�ݨ���������\�h�ɮ׸��

#### Get / POST Methods
Get is more dangerous
client��http://.....?id= ��server (Get) </br>
client��http://..... ��server (POST)

Client side script�G (�Τ�ݥi�H����)
Javascript,HTML

Server side�G (�u��Server��)
PHP,JSP,ASP
 
#### User auth
```
		��ID:AAA,PW:BBBB�� 
client 						server
		��COOKIE:SESSIONID=CCCC��
	
	
		��COOKIE:SESSIONID=CCCC��
client 						server
				��OK��
```
�bconsole �W��document.cookie�i�H�o��cookie </br>
�άO�b���}�C�Wjavascript:document.cookie�]�i�H

### 0x04 Web Hacking & Security Techniques
to web application </br>
1. file upload </br>
2. SQL injection </br>
	Web DB</br>
3. SQL injection(in to DB)

#### High Risk : file upload Vulunerability
Ex:: Member Login(Vuln.) </br>
²��}�Ѥ覡�A�b���K�X��J[' or ''=']

#### Middle Risk : XSS,File Download (Directory Traversal)
EX:: Board </br>
name:test </br>
pwd:test </br>
subject:test </br>
Content: XSS Test
```
<script>document.write(document.cookie)</script>
```
�i�H�s�Xcookie

---

Web security principle </br>
1. Do not trust user input </br>
2. Do not give full check at client side </br>
3. Do not trust black-list filter rule </br>
	- white list �O�ŦX�W�h�� and more Secure </br>

### 0x05 Exercise web hacking wargame

EX:: Member Login(Secure) 
�ϥΤW����k�O�椣�q��
�ҥH�i�H���D�o�O����w����

<!-- �m�ߥκ��� http://onesecurity.kr/AIS3/
ID : ais3
Password : ais3_anesra -->

�m�ߤG
�ϥ�Burp Suit </br>
�]�w�nproxy�� </br>
����T������user��anesra��intercept off�����N�令�\�F </br>

�m�ߤT
- �ϥ�Burp Suit¶�L�h����J�u���K�X��i��Burp Suit�令���T��
- �ˬd��l�X��ƻsfunction�Aconsole�W�K�W�⭭����󮳱���N��ﱼ�쥻���{���X�F
- �]�i�H�����bBurp Suit��Forward�M���{���X

�˼ƲĤG </br>
403��ܭ����s�b http://www.onesecurity.kr/AIS3/wargame/admin </br>
�ҥH�~�� http://www.onesecurity.kr/AIS3/wargame/admin/login.asp </br>
�b���K�X��J' or ''='�N�i�H�i�h�F