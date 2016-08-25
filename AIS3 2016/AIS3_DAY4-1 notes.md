# AIS3 DAY4-1 Web Security & Hacking hands-on practice

當下發生hacking的圖：map.norsecorp.com

### 0x03
#### Major Web Hacking Cases
- Still Web and Malicious code are two major threats from out-side attacker
- It's easy too attack than system and network hacking layers
- There are currently over 1 Billion websites on the web

https://www.youtube.com/watch?v=1FhD_cKaRKA 

#### http Protocol 
```
			→ Http request → 
Web browser					 Server
			← Http request ← 
```			
在網頁上按下F12可以看到元素
在network那個可以看到網頁內的許多檔案資料

#### Get / POST Methods
Get is more dangerous
client→http://.....?id= →server (Get) </br>
client→http://..... →server (POST)

Client side script： (用戶端可以更變)
Javascript,HTML

Server side： (只有Server有)
PHP,JSP,ASP
 
#### User auth
```
		→ID:AAA,PW:BBBB→ 
client 						server
		→COOKIE:SESSIONID=CCCC←
	
	
		→COOKIE:SESSIONID=CCCC→
client 						server
				←OK←
```
在console 上打document.cookie可以得到cookie
或是在網址列上javascript:document.cookie也可以

### 0x04 Web Hacking & Security Techniques
to web application </br>
1. file upload
2. SQL injection
	Web DB
3. SQL injection(in to DB)

#### High Risk : file upload Vulunerability
Ex:: Member Login(Vuln.) </br>
簡單破解方式，帳號密碼輸入[' or ''=']

#### Middle Risk : XSS,File Download (Directory Traversal)
EX:: Board </br>
name:test </br>
pwd:test </br>
subject:test </br>
Content: XSS Test
```
<script>document.write(document.cookie)</script>
```
可以叫出cookie

---

Web security principle </br>
1. Do not trust user input
2. Do not give full check at client side
3. Do not trust black-list filter rule
	- white list 是符合規則的 and more Secure

### 0x05 Exercise web hacking wargame

EX:: Member Login(Secure) 
使用上次方法是行不通的
所以可以知道這是比較安全的

<!-- 練習用網站 http://onesecurity.kr/AIS3/
ID : ais3
Password : ais3_anesra -->

練習二
使用Burp Suit
設定好proxy後
接到訊息後更改user成anesra後intercept off網頁就改成功了

練習三
1. 使用Burp Suit繞過去先輸入短的密碼後進到Burp Suit改成正確的
2. 檢查原始碼後複製function，console上貼上把限制條件拿掉後就能改掉原本的程式碼了
3. 也可以直接在Burp Suit案Forward然後改程式碼

倒數第二
403表示頁面存在 http://www.onesecurity.kr/AIS3/wargame/admin
所以繼續 http://www.onesecurity.kr/AIS3/wargame/admin/login.asp
帳號密碼輸入' or ''='就可以進去了